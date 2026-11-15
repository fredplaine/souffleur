# 🎭 Le Souffleur — Studio universel de mémorisation

**Le Souffleur** est une application web gratuite et 100 % autonome permettant aux comédiens, orateurs et étudiants de répéter leurs textes à l'italienne, seuls ou en déplacement.

👉 **Accéder à l'application en ligne :** [https://fredplaine.github.io/souffleur/](https://fredplaine.github.io/souffleur/)

---

## 📱 1. L'installer comme une application sur téléphone
Ouvrez le lien ci-dessus sur votre smartphone et ajoutez-le à votre écran d'accueil :
* **Sur iPhone (Safari) :** Appuyez sur le bouton **Partager** (carré avec la flèche vers le haut) ➡️ **Sur l'écran d'accueil**.
* **Sur Android (Chrome) :** Appuyez sur les **3 petits points** en haut à droite ➡️ **Ajouter à l'écran d'accueil**.

---

## 📝 2. Textes préchargés & Importation
* **Prêt à l'emploi :** *Le Petit Prince* (les 26 scènes), *Aquaplaning* et *La Serveuse* sont déjà inclus dans la bibliothèque.
* **Importer vos textes :** Cliquez sur **＋ Importer un texte** (ou **＋ Nouveau texte**) pour coller un texte ou glisser un fichier `.txt` / `.md`.
* **Détection automatique :** L'application reconnaît automatiquement les personnages (`NOM — réplique` ou `NOM : réplique`), les scènes (`# SCÈNE 1`, `# Scène IV`...), ou découpe les textes libres (poèmes, discours, pitchs) par phrases, paragraphes ou vers.
* **Édition directe sur mobile :** Modifiez n'importe quel texte à tout moment (**✎ Éditer** sur la carte ou **✎ Modifier le texte source** dans la Régie) pour corriger une réplique ou ajouter vos annotations de jeu.
* **Didascalies intelligentes :** Tout texte placé `(entre parenthèses)` s'affiche en italique à l'écran pour vous guider visuellement, mais est **ignoré à l'oral** par la synthèse vocale.

---

## 🎯 3. Comment répéter ?
1. Depuis l'accueil, cliquez sur **▶ Reprendre le dernier** pour retrouver instantanément votre dernière séance.
2. En haut de l'écran, **choisissez votre personnage** (vos répliques sont masquées, celles de vos partenaires restent visibles) ainsi que votre **scène de départ**.
3. Appuyez sur **Lecture (▶)** en bas : l'application lit les répliques de vos partenaires à voix haute et s'arrête dès que c'est **À TOI**.
4. **Souffleur intelligent :** Le compte à rebours calcule automatiquement le temps nécessaire pour dire votre réplique (selon sa longueur et votre vitesse de lecture) et y ajoute votre délai de sécurité (0 à 12 s).
   * Vous savez votre texte ? Cliquez sur **✓ Dite !** (la réplique passe en *Acquise*).
   * Un trou de mémoire ? Cliquez sur **👁 Souffler** (ou laissez le compte à rebours se terminer) pour révéler et écouter votre réplique.

---

## ⚡ 4. Fonctions avancées
* **Mode Turbo (`⚡` en bas ou touche `T`) :** Saute directement les longs passages sans réplique jusqu'à la dernière réplique avant votre tour, et ne lit que les **8 derniers mots** pour vous donner l'amorce.
* **Mode Révision (`🎯` en haut) :** Filtre uniquement les répliques sur lesquelles vous avez hésité ou demandé le souffleur.
* **La Régie (panneau latéral) :** Personnalisez la vitesse de lecture, les voix et la gravité par personnage, le délai avant soufflage, le style de masquage (*Flou*, *Caviardé*, *Initiales*), le décor animé (*Sable d'or au Sahara*, *Pluie sur l'asphalte*, *Bistrot de nuit*...) ou imprimez votre fiche. **Chaque pièce mémorise automatiquement ses propres réglages.**

---

## 🔒 Confidentialité & Open Source
* **100 % local :** Vos textes, annotations, réglages et statistiques sont enregistrés uniquement dans la mémoire de votre navigateur (`localStorage`). Aucun compte ni serveur externe n'est requis.
* **Open Source :** Ce projet tient dans un seul fichier `index.html`. Vous pouvez librement cloner ou forker ce dépôt pour l'adapter à vos besoins !
