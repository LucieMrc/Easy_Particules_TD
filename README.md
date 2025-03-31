# Easy Particules dans TouchDesigner

Basé sur ce tutoriel d'Anya Maryina: [.PNG into particles | Reorder TOP explained | TouchDesigner Tutorial
](https://www.youtube.com/watch?v=CcvhTgD7IOI&ab_channel=anyamaryina)

## Créer le setup

Importer une image sur fond transparent (ou dont on enlevera le fond) avec un `Movie File In` TOP. Enlever le fond si besoin avec un `Chroma Key` TOP et croper si besoin avec un `Crop`.

!['interface de TD'](./images/screen1.png)

Créer également 2 `Ramp` TOP, un horizontal et un vertical.

!['interface de TD'](./images/screen2.png)

Créer un `Reorder` TOP et mettre les 2 `Ramp` dans les 2 premières entrées.

Dans les paramètres du `Reorder, sélectionner "Input 2" pour l'Output Green, et "Zero" pour l'Output Blue.

!['interface de TD'](./images/screen3.png)

Ajouter l'image qu'on a importé dans la quatrième entrée du `Reorder` TOP et choisir "Input 4" pour l'Output Alpha. On doit alors voir apparaître la forme de notre image sur le `Reorder`.

!['interface de TD'](./images/screen4.png)

## ParticlesGPU

Ouvrir la palette, et depuis le dossier "Tools" récuperer le node "ParticlesGpu".

Relier la sortie du `Reorder` à la première entrée du  "ParticlesGpu" et l'image importée à la seconde entrée.

!['interface de TD'](./images/screen5.png)

Dans les paramètres de "ParticlesGpu", dans l'onglet "ParticlesGPU", mettre 1000 dans "Birth" (on pourra modifier ce nombre plus tard), 2 et 1 dans "Life Min" et "Lifevariance" et décocher "Display Bounds".

!['interface de TD'](./images/screen6.png)

Dans l'onglet "Forces", mettre tous les paramètres qui finissent par " Magnitude" à 0.

!['interface de TD'](./images/screen7.png)

Dans l'onglet "Material", choisir "Line" dans la liste Material.

## Adapter la taille

Pour l'instant on ne voit vaguement qu'une petite version de notre image au milieu du node "ParticlesGpu".

Pour pouvoir modifier la taille et la position dans le rendu, commencer par aller dans les paramètres des `Ramp` TOP, dans l'onglet "Common", et dans "Pixel Format" choisir "32-bit float RGBA".

!['interface de TD'](./images/screen8.png)

Créer un `Point Transform` TOP entre le `Reorder` et le "particlesGpu" et modifier le paramètre "Uniform Scale" pour voir grandir les particules.

On peux aussi replacer le rendu au centre du node avec les paramètres "Translate".

!['interface de TD'](./images/screen10.png)

# To go further

- nothing yet
