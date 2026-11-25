# Instructions — Correction des bugs (Priorité 1) — `index.html` (Le Souffleur)

Contexte : application mono-fichier `index.html` (~2100 lignes). Les textes préchargés ne sont plus dans le code ; ils sont servis depuis le dossier `/textes` (déjà en place, hors périmètre de ces corrections). **Ne réintroduis aucun texte préchargé dans l'application.**

Applique les 4 corrections ci-dessous, exactement et uniquement celles-là. Ne restructure pas le reste du code, ne change pas le style ni les chaînes utilisateur existantes. Après chaque correction, vérifie que la fonction appelante continue de fonctionner.

---

## Bug #1 — Doublon de `showBanner()` qui casse le bouton favori de la bannière « À TOI »

**Localisation :** deux définitions consécutives de `function showBanner(i)` (vers les lignes 1907–1923).

**Problème :** en JavaScript, la seconde déclaration `function` écrase la première (hoisting). Or la version écrasée est la bonne : elle appelle `updateBannerFavBtn(i)` (ligne ~1914), ce qui fait que l'étoile ⭐ de la bannière n'affiche jamais l'état favori réel pendant une séance.

**Correction :** supprimer la SECONDE définition (celle qui NE contient PAS `updateBannerFavBtn(i)`), et garder la première, intacte :

```js
function showBanner(i){
  var rSec=reciteSec(active.lines[i].t);
  $('banner').classList.add('show');
  $('bTitle').textContent='À TOI — '+active.lines[i].c;
  $('bSub').textContent='Réplique '+(i+1)+' (~'+rSec+' s de diction + '+cfg.delay+' s de délai) — dis-la puis « ✓ Dite ! »';
  $('btnSouffle').disabled=false;
  $('cdWrap').style.display='none';
  updateBannerFavBtn(i);
}
```

**Vérification :** il ne doit rester qu'une seule occurrence de `function showBanner` dans le fichier (`grep -c "function showBanner" index.html` → 1). Tester : mettre une réplique en favori, rejouer le texte, la bannière « À TOI » doit afficher l'étoile active.

---

## Bug #2 — Doublon de `updateModeChips()` qui casse le mode Favoris (⭐)

**Localisation :** deux définitions de `function updateModeChips()` (version complète vers les lignes 1947–1961, version tronquée à la ligne ~1962).

**Problème :** même mécanisme d'écrasement. La version tronquée (ligne 1962) écrase la version complète et ignore tout ce qui concerne les favoris : les compteurs `favCount` / `favCount2`, l'état actif du chip `modeFav`, son `aria-pressed`, son `disabled`, et le bouton `btnFavRun`. Résultat : le chip ⭐ Favoris ne se met jamais à jour (compteur figé à 0, surbrillance absente, boutons jamais activés).

**Correction :** supprimer la SECONDE définition (la version tronquée en une ligne commençant par `function updateModeChips(){var n=difficultIdx().length;$('reviewCount')...`) et garder la version complète :

```js
function updateModeChips(){
  var n=difficultIdx().length,f=favIdx().length;
  $('reviewCount').textContent=n;$('reviewCount2').textContent=n;
  $('favCount').textContent=f;$('favCount2').textContent=f;
  $('modeFull').classList.toggle('active',S.mode==='full');
  $('modeReview').classList.toggle('active',S.mode==='review');
  $('modeFav').classList.toggle('active',S.mode==='fav');
  $('modeFull').setAttribute('aria-pressed',S.mode==='full');
  $('modeReview').setAttribute('aria-pressed',S.mode==='review');
  $('modeFav').setAttribute('aria-pressed',S.mode==='fav');
  $('modeReview').disabled=n===0&&S.mode!=='review';
  $('modeFav').disabled=f===0&&S.mode!=='fav';
  $('btnReview').disabled=n===0;
  $('btnFavRun').disabled=f===0;
}
```

**Vérification :** une seule occurrence de `function updateModeChips` (`grep -c "function updateModeChips" index.html` → 1). Tester : ajouter des favoris → le compteur ⭐ doit s'incrémenter en direct, le chip doit pouvoir devenir actif, et « Réviser les favoris » doit s'activer.

---

## Bug #3 — `duplicateText()` perd les favoris et le schéma d'état des lignes

**Localisation :** fonction `duplicateText(id)` (vers la ligne 1178).

**Problème :** la copie régénère `c.st` avec `{peeks:0,reads:0,lastVisit:null}` sans la propriété `bookmarked`. Les objets d'état produits ailleurs (loadAll, toggleFav, btnReset) incluent `bookmarked:false` par défaut ; ici la propriété est `undefined`, et surtout **les favoris ⭐ de l'original sont perdus** dans la copie (alors que `btnReset` ligne ~2106 a explicitement décidé de les conserver — incohérence de comportement).

**Correction :** remplacer le `.map(...)` de régénération par une copie alignée sur l'original, en préservant `bookmarked` :

```js
c.st=t.lines.map(function(_,idx){return {peeks:0,reads:0,lastVisit:null,bookmarked:!!(t.st[idx]&&t.st[idx].bookmarked)};});
```

Le reste de la fonction (uid, titre « (copie) », dates, `c.study.idx=0`, `splice`, `persist`, `renderLibrary`, `toast`) est inchangé.

**Vérification :** dupliquer un texte contenant des favoris → la copie conserve les mêmes lignes en favori, et le mode ⭐ fonctionne immédiatement sur la copie.

---

## Bug #4 — Migrer `bookmark` lors d'un re-parse dans `loadAll()`

**Localisation :** bloc de re-parse dans `loadAll()` (vers les lignes 962–966).

**Problème :** quand le découpage détecté change (`t.scenes.length!==reparsed.scenes.length`), les lignes sont re-générées et l'ancien état est repris via `oldSt[i]||{peeks:0,reads:0,lastVisit:null}` — sans `bookmarked`. Si l'entrée ancienne vient d'une version antérieure du format (sans `bookmarked`), l'accès ultérieur produit un état incohérent jusqu'à la normalisation de fin de fonction. C'est aussi un point de fragilité pour la future persistance JSON des réglages : la migration doit être explicite.

**Correction :** remplacer la ligne :

```js
t.st=t.lines.map(function(_,i){return oldSt[i]||{peeks:0,reads:0,lastVisit:null};});
```

par :

```js
t.st=t.lines.map(function(_,i){var o=oldSt[i];return o?{peeks:o.peeks|0,reads:o.reads|0,lastVisit:o.lastVisit||null,bookmarked:!!o.bookmarked}:{peeks:0,reads:0,lastVisit:null,bookmarked:false};});
```

(La normalisation en fin de `loadAll` — ligne ~972 — garde la même logique, ne pas la toucher.)

**Vérification :** charger un localStorage ancien (sans `bookmarked`), puis modifier volontairement le source d'un texte pour changer le nombre de scènes → les favoris survivent là où l'index de ligne correspond, et aucune erreur n'apparaît dans la console.

---

## Contraintes transversales

1. Mono-fichier : toutes les modifications restent dans `index.html`, pas de nouveau fichier JS, pas de build.
2. Pas de régression XSS : ne pas introduire d'`innerHTML` sur du contenu texte utilisateur (utiliser `textContent` comme le code existant).
3. Conserver le style du code (var, fonctions globales, pas d'ES6 modules).
4. Après les 4 fixes, faire une passe de recherche de tout autre doublon de fonction (`grep -n "^function \|function .*(" | sort`) et signaler (sans corriger) les éventuels autres cas trouvés.
5. Tests manuels minimaux : chargement initial (bibliothèque vide puis peuplée depuis `/textes`), ajout de favoris, bascule modes Full/Review/Fav, duplication, reset progression, édition du source avec changement de découpage.
