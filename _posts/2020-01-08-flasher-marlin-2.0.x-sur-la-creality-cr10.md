---
title:  "Flasher Marlin 2.0.x sur la Creality CR10"
categories: ["Impression 3D"]
tags: [3dprinting]
date:   2020-01-08 22:00:00
comments: true
---

Le problème d'avoir une vieille imprimante 3D, c'est qu'il devient de plus en plus difficile de trouver de la documentation à jour avec les nouveaux outils ou les nouvelles versions.

<!--more-->

Ca va bientot faire deux ans que j'ai acheté ma première imprimante 3D, une Creality CR-10 première du nom. A l'époque c'était l'une des imprimantes les plus appréciées, déjà pour son grand volume d'impression (300x300x400mm) mais surtout pour son prix qui était sous la barre des 400€.

![Creality3D CR-10][CR10 Image]{: width='400px' .center}

Même s'il est encore possible de la trouver [sur gearbest pour environ 350€][Creality3D Gearbest], je vous conseille quand même de regarder les nouveaux modèles sortient depuis.

## Un peu de contexte
Le problème avec cette imprimante 3D a toujours était le firmware. Basé sur une version modifiée de [Marlin][MarlinFW], il est pourtant difficile de mettre à jour l'imprimante pour bénificier des nouvelles fonctionnalités offertes par une version récente de Marlin. La cause principale étant la carte mère Melzi utilisée par le fabricant qui ne dispose pas d'un bootloader.

Je ne parlerai pas dans cet article de comment faire un burn du bootloader afin de permettre le flash d'un firmware. Ce sujet est déjà bien assez traité sur le net pour que je le fasse moi même.
La méthode repose sur un arduino et des outils open source. [Plus d'information ici.][Burn Bootloader] 

Rien d'illégal la dedans, pas d'inquiétude à avoir du moment qu'on sait que la garantie de l'imprimante va sauter.

## Passons au flash

Depuis quelques temps, il est beaucoup plus simple de compiler et flasher Marlin sur son imprimante. Fini d'avoir à utiliser cet IDE des enfers qu'est Arduino IDE, maintenant il est enfin possible d'utiliser des outils modernes. 


### 1. Installer VSCode et PlatformIO
Pour commencer il vous faudra Visual Studio Code [disponible ici][VSCode] et l'extension Platform.io [disponible ici][PlatformIO] ou directement depuis le gestionnaire d'extensions.

![Installation de PlatformIO][PlatformIO Installation]

### 2. Télécharger Marlin
De mon coté, je récupère les sources de marlin directement via une commande *git*. Mais pour ceux que ca peut effrayer, MalinFW a eu le bon gout de proposer des liens de téléchargement direct:

              Description               |   Version    |                  Download
--------------------------------------- | ------------ | ------------------------------------------
Latest release *(supports AVR and ARM)* | 2.0.1        | [2.0.x.zip][DL Marlin 2.0.x]
Marlin 2.0 with bug fixes               | bugfix-2.0.x | [bugfix-2.0.x.zip][DL Marlin bugfix 2.0.x]
Previous release *(supports AVR)*       | 1.1.9        | [1.1.x.zip][DL Marlin 1.1.x]
Marlin 1.1 with bug fixes               | bugfix-1.1.x | [bugfix-1.1.x.zip][DL Marlin bugfix 1.1.x]

De manière générale, je conseille d'utiliser la version "bugfix". Souvent, cela permettra d'avoir accès aux derniers correctifs d'une version et de ne pas avoir les bugs déjà rencontrés par certains bidouilleurs avant vous.

### 3. Ouvrir le projet PlatformIO
Après avoir téléchargé l'archive, il sera nécessaire de l'extraire dans le dossier de votre choix et l'ouvrir avec PlatformIO.
Après avoir lancé Visual Studio Code, PlatformIO s'ouvrira par défaut. Il vous suffira alors de cliquer sur le bouton "Open Project" et choisir le dossier que vous venez d'extraire.

![Ouverture du projet PlatformIO][PlatformIO Open Project]

### 4. Changement de l'environnement par défaut
La configuration de PlatformIO consiste à choisir la carte mère que l'on souhaite flasher par défaut. 
Dans le cas de la CR10 et de sa carte mère Melzi, il faudra choisir l'environnement "sanguino_atmega1284p".
Pour configurer cet environnement, ouvrez le fichier "platformio.ini" et modifiez la ligne 21 de la manière suivante:

```properties
default_envs = sanguino_atmega1284p
```

### 5. Configuration Marlin pour la CR10
Il ne vous reste plus qu'à configurer Marlin avec la configuration de base d'une CR10.
Copiez/collez tous les fichiers présents dans le dossier "config/examples/Creality/CR-10/" dans le dossier "Marlin".
Attention, il faudra remplacer les fichiers "Configuration.h" et "Configuration_adv.h" déjà présents dans le dossier Marlin par ceux du dossier exemple.

### 6. Compilation et déploiement
Branchez la CR10 en USB (après avoir coupé l'alimentation) à votre ordinateur et lancez la compilation et le déploiement.
Rien de plus simple, il suffit d'aller dans la partie "tasks" de PlatformIO et lancer la tache "Build" puis la tache "Upload".

![Compilation dans PlatformIO][PlatformIO Build]

## C'est fini !
Si ça se passe bien, vous aurez un message de succès et il ne vous restera plus qu'à débrancher votre cable usb de l'imprimante et l'alimenter.
Elle devrait démarrer sur la dernière version de Marlin.

En cas d'erreur, il faudra regarder du coté des logs pour savoir ce qui n'a pas fonctionné.

*That's all folks!*

[CR10 Image]: /images/2020/01/08/cr-10.jpg
[PlatformIO Installation]: /images/2020/01/08/install_platformio_vscode.png
[PlatformIO Open Project]: /images/2020/01/08/platformio_open_project.png
[PlatformIO Build]: /images/2020/01/08/platformio_build.png

[Creality3D Gearbest]: https://fr.gearbest.com/3d-printers-3d-printer-kits/pp_627176.html?wid=1433363&lkid=78193946
[MarlinFW]: http://marlinfw.org/
[Burn Bootloader]: http://www.cr10.fr/ameliorations/marlin/
[VSCode]: https://code.visualstudio.com/
[PlatformIO]: https://marketplace.visualstudio.com/items?itemName=platformio.platformio-ide
[DL Marlin 2.0.x]: https://github.com/MarlinFirmware/Marlin/archive/2.0.x.zip
[DL Marlin bugfix 2.0.x]: https://github.com/MarlinFirmware/Marlin/archive/bugfix-2.0.x.zip
[DL Marlin 1.1.x]: https://github.com/MarlinFirmware/Marlin/archive/1.1.x.zip
[DL Marlin bugfix 1.1.x]: https://github.com/MarlinFirmware/Marlin/archive/bugfix-1.1.x.zip