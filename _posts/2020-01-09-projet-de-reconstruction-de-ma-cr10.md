---
title:  "Projet de reconstruction de ma CR10"
categories: ["Impression 3D"]
tags: [3dprinting]
date:   2020-01-09 21:00:00
comments: true
---

Ca fait plusieurs mois qu'une idée me traverse la tête, améliorer ma CR10 en ajoutant ou modifiant certains composants. J'avais déjà fait quelques modifications sur la tête d'impression il y a quelques mois pour changer le système de ventilation de la tête et ajouter un vrai système de ventilation de la buse pour permettre de faire des bridges de meilleure qualité.

<!--more-->

En haut la tête d'impression avant, en bas la version modifiée. Simple mais efficace !

![Modification de la tête d'impression][Modif CR10]{: width='600px' }

## Allons plus loin
Changer des ventilateurs c'est bien, mais ca reste très basique. Ca fait donc plusieurs mois que je réfléchis à refaire complètement mon imprimante 3D. Que ce soit la mécanique ou l'électronique j'ai envie de reprendre tout à zéro.

Voici la todo list concernant les modifications que j'aimerai apporter:
- [ ] Passage en standalone
- [ ] Remplacement de la tête d'impression
- [ ] Remplacement de l'éléctronique 

Le mode standalone consiste à supprimer le boitier externe contenant la carte mère et l'alimentation de la CR10 et faire en sorte que tout soit intégré sur le chassis de l'imprimante comme c'est le cas sur la créality Ender par exemple. L'idée principale étant le gain de place et le cable management qui permet de faire en sorte de rendre beaucoup plus sympa l'imprimante.

Pour la tête d'impression, j'avais en tête de passer sur un système d'extrusion direct (direct drive) afin de permettre l'extrusion de filament flexible comme le TPU. Chose presque impossible avec un extrudeur à moteur déporté (Bowden) présent sur la CR10 d'origine.

Enfin l'éléctronique, qui commence à dater un peu sera remplacée par des composants de meilleure qualité et permettant l'ajout de nouvelles fonctionnalités (écran tactile, diminution du bruit des moteurs, remplacement des ventilateurs, etc). 

### Le choix des composants

Pour le choix des composants, j'ai préféré suivre les conseils de la communauté. Pour ce qui est des têtes d'impression E3D est la marque la plus souvent citée. Du coté éléctronique c'est Biqu et BigTreeTech qui reviennent le plus.

Fonctionnalités que je voulais absolument:
- Un lecteur de carte SD
- Un port USB
- Un écran tactile
- Détection de fin de filament
- Nivellement automatique

Mon choix s'est porté sur les composants suivants:

Marque       | Composant         | Description                                                       | Prix
------------ | ----------------- | ----------------------------------------------------------------- | ----------
E3D          | Hemera Direct Kit | Tête d'impression V6 12V avec système d'extrusion direct drive    | 126,88 €
BIQU         | SKR V1.3          | Carte mère 32bit vierge sans driver                               |  25,99 €
BIQU         | BLTouch           | Capteur de nivellement automatique                                |  42,99 € 
BIGTREETECH  | TMC2209 V1.2 (x4) | Driver moteur                                                     |  19,72 €
BIGTREETECH  | TFT35 V3.0        | Ecran tactile 3.5" couleur                                        |  25,03 €
BIGTREETECH  | BTT SFS V1.0      | Détecteur de fin de filament                                      |  16,05 €

Niveau budget, on arrive à un total de 256,66 €. Ce n'est pas donné, c'est vrai.

Mais ce qu'il faut avant tout se dire, c'est que l'imprimante de base ne m'a couté que 350 € environ. 
Ce qui fait un total de 600 € en tout, donc environ 400 € de moins qu'une imprimante de grande marque qui d'origine intègre toutes ces fonctionnalités.

On ne va pas se le cacher, c'est avant tout le coté fun de reconstruire mon imprimante qui motive mon choix de le faire moi même façon DIY plutôt que d'acheter une nouvelle imprimante qui aurait déjà tout. Ca va me permettre d'améliorer mes skills en soudure, en modélisation 3D, en mécanique, en programmation, en gros, une source de découverte pour moi !

Si ce projet vous intéresse, je ne peux que vous conseiller de surveiller ce blog ou je posterai l'avancé du projet au fur et à mesure.

*See you!*

[Modif CR10]: https://scontent-cdg2-1.cdninstagram.com/v/t51.2885-15/e35/44196083_351156672124728_4479711465513782200_n.jpg?_nc_ht=scontent-cdg2-1.cdninstagram.com&_nc_cat=100&_nc_ohc=GiyG3_InkEoAX-qtkgp&oh=bc6c6b03c38b645c10c357f861d97312&oe=5EB52A04