# 🎭 Le Souffleur — Studio universel de mémorisation

**Le Souffleur** est une application web gratuite, légère et 100 % autonome permettant aux comédiens, orateurs et étudiants de répéter leurs textes à l'italienne, seuls ou en déplacement.

👉 **Accéder à l'application en ligne :** [https://fredplaine.github.io/souffleur/](https://fredplaine.github.io/souffleur/)

---

## 📱 1. L'installer comme une application sur téléphone
Ouvrez le lien ci-dessus sur votre smartphone et ajoutez-le à votre écran d'accueil :
* **Sur iPhone (Safari) :** Appuyez sur le bouton **Partager** (carré avec la flèche vers le haut) ➡️ **Sur l'écran d'accueil**.
* **Sur Android (Chrome) :** Appuyez sur les **3 petits points** en haut à droite ➡️ **Ajouter à l'écran d'accueil**.

---

## 📚 2. Bibliothèque dynamique & Importation
* **Catalogue `/textes` synchronisé :** Au démarrage, l'application scanne automatiquement le dossier `/textes` du dépôt GitHub (`textes/catalogue.json` + fichiers `.txt` / `.md`) pour alimenter votre bibliothèque sans alourdir le code.
  * *Mise à jour d'un texte du dépôt :* Comme vos copies locales sont protégées dans le navigateur, supprimez l'ancienne carte avec **`🗑`** puis rechargez la page pour récupérer la nouvelle version depuis GitHub.
* **Importer vos propres textes :** Cliquez sur **＋ Nouveau texte** (ou **＋ Importer un texte**) pour coller un texte ou glisser un fichier `.txt` / `.md`.
* **Détection automatique intelligente :**
  * Reconnaît les dialogues (`NOM — réplique`, `Nom : réplique`, `NOM - réplique`) ainsi que les scènes (`# SCÈNE UN`, `Scène 2 : Titre`, `# Scène IV`… converties en chiffres romains).
  * Découpe automatiquement les textes libres (poèmes, discours, pitchs) par **phrases**, **paragraphes** ou **vers**.
* **Gestion & Export `.txt` :** Recherchez, filtrez (*Dialogues*, *Textes libres*, *En cours*, *Maîtrisés*), réorganisez vos cartes par glisser-déposer, dupliquez une pièce ou téléchargez n'importe quel texte modifié au format `.txt` via le bouton **Exporter (`📥`)**.

---

## 🎯 3. Comment répéter ?
1. Depuis l'accueil, cliquez sur **▶ Reprendre le dernier** (ou **▶ Réviser** sur une carte) pour retrouver instantanément votre dernière séance.
2. Dans la barre supérieure, **choisissez votre personnage** (vos répliques sont masquées, celles de vos partenaires restent visibles — ou *Tous les rôles* pour un monologue) ainsi que votre **scène de départ**.
3. Appuyez sur **Lecture (`▶`)** en bas : l'application lit les répliques de vos partenaires à voix haute et s'arrête dès que c'est **À TOI**.
4. **Souffleur intelligent :** Le compte à rebours calcule automatiquement le temps nécessaire pour dire votre réplique (selon sa longueur hors didascalies et votre vitesse de lecture) et y ajoute votre délai de sécurité (0 à 12 s).
   * Vous savez votre texte ? Cliquez sur **✓ Dite !** (la réplique passe en *✓ acquise*).
   * Un trou de mémoire ? Cliquez sur **👁 Souffler** (ou laissez le compte à rebours se terminer) pour révéler et écouter votre réplique.
5. **Didascalies intelligentes :** Tout texte placé `(entre parenthèses)` s'affiche en italique à l'écran pour vous guider visuellement, mais est **ignoré à l'oral** par la synthèse vocale.

---

## ⚡ 4. Fonctions avancées & Régie
* **Mode Turbo (`⚡` en bas ou touche `T`) :** Saute directement les longs passages sans réplique jusqu'à la dernière réplique avant votre tour, et ne lit que les **8 derniers mots** pour vous donner l'amorce.
* **Mode Révision (`🎯` en haut) :** Filtre uniquement les répliques sur lesquelles vous avez hésité ou demandé le souffleur (avec la réplique-amorce juste avant).
* **Favoris (`⭐` sur chaque réplique, dans la bannière « À TOI » ou touche `B`) :** Épinglez vos passages clés ou difficiles pour les retravailler à part via le mode **⭐ Favoris** en haut (les favoris sont conservés même lors d'une remise à zéro de la progression).
* **Édition directe en plein filage (`✎ Éditer` ou touche `E`) :** Corrigez une réplique, changez son personnage ou ajoutez vos annotations `(entre parenthèses)` directement pendant la répétition sans quitter la scène.
* **La Régie (panneau latéral) :**
  * **Voix par personnage :** Attribuez une voix système et une gravité (`×0.50` à `×1.50`) distinctes à chaque rôle, avec bouton de test instantané.
  * **Mode de filage :** Alternez entre *Récitation* (arrêt sur vos répliques) et *Lecture continue* (écoute intégrale).
  * **Masquage & Décors animés :** Choisissez entre *Flou*, *Caviardé* ou *Initiales*, activez l'ambiance sonore et sélectionnez l'un des **7 décors animés** (*Pluie sur l'asphalte*, *Sable d'or au Sahara*, *Carte céleste d'aviateur*, *Rideau de velours*, *Bistrot de nuit*, *Neige lente*, *Lucioles* ou *Aucun*).
  * **Impression :** Générez une fiche papier propre avec cases à cocher via **🖨 Imprimer la fiche**.
  * **Chaque pièce mémorise automatiquement ses propres réglages.**

---

## ⌨️ 5. Raccourcis clavier (en répétition)
| Touche | Action |
| :--- | :--- |
| **`Espace`** | Lecture / Pause |
| **`←` / `→`** | Réplique précédente / suivante |
| **`R`** | Révéler la réplique en cours |
| **`B`** | Ajouter / retirer la réplique en cours des **Favoris (`⭐`)** |
| **`E`** | **Éditer** directement la réplique en cours |
| **`T`** | Activer / désactiver le **Mode Turbo (`⚡`)** |
| **`M`** | Couper / réactiver le son |
| **`Échap`** | Fermer l'éditeur en cours ou mettre en pause |

---

## 🔒 Confidentialité & Architecture
* **100 % local :** Vos textes importés, annotations, favoris, réglages de Régie et statistiques sont enregistrés uniquement dans la mémoire de votre navigateur (`localStorage`). Aucun compte ni serveur externe n'est requis.
* **Architecture légère :** L'application repose sur un fichier unique `index.html` sans dépendances de build, complété par le dossier `/textes` pour le catalogue partagé.