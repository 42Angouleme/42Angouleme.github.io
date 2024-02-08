# La bibliothèque Pybot

!!! note "Ce qu'est *Pybot*"
    *Pybot* est une bibliothèque logicielle permettant à des élèves de collège de programmer eux même un robot immobile.

Vous trouverez ici les informations pour utiliser la bibliothèque *pybot* avec des exemples concret pour réaliser des programmes d'un simple affichage de caméra jusqu'à un robot conversationnel complet.

## Les fonctionnalités du robot

!!! note "Le robot complet."
    Le Robot a été pensé pour fonctionner sur un Raspberry Pi configuré avec Linux (Debian). Un écran pour le **visage**, une caméra pour les **yeux**, un haut-parleur pour la **bouche** et un microphone pour les **oreilles**. La coquille entourant le raspberry pi est libre d'interprétation esthétique.

Avec la bibliothèque, vous avez accès aux modules :

> **Robot :** Module principal regroupant tous les autres modules et servant de corps au code du robot.  
**Fenêtre - Window:** Module permettant de construire une interface graphique pour interagir avec le robot.  
**Caméra - Camera :** Module permettant de prendre des photos, d’y appliquer des filtres, reconnaissance par caméra (pas biométrique comme le visage, mais des dessins sur cartes).  
**IA - AI :** Module permettant de discuter avec le robot grâce à une IA conversationnelle de type ChatGPT et permettant aussi de donner des "émotions" au robot.  
**Utilisateur - User :** Module permettant de créer et de gérer la connexion/déconnexion des utilisateurs à l'aide des cartes.  
**Audio (Non fonctionnel) :** Module permettant à l’utilisateur de parler directement au robot.  
**Microphone (Non fonctionnel) :** Module permettant au robot de parler à l’utilisateur.

!!!Warning "Avant d'utiliser un module"
    Avant d’utiliser un module, il faudra toujours le lancer sinon il vous sera impossible d’utiliser le module et les méthodes lier à celui-ci.

!!!Note "Important"
    Les exemples d'utilisation des méthodes sont en français et en anglais.  
    Et il suppose pour la plus part d'avoir déjà un code de base fonctionnel pour le robot.  
    Seul les exemples complet de programme sont en français et ne suppose pas d'avoir un code de base.

## Utilisation de la bibliothèque

```python
print("bonjour, Pybot!")
```

*Pybot* se présente comme un objet avec des méthodes et des sous-objets (modules présentés ci-dessus) que l’on peut utiliser ensemble pour faire le programme et ainsi créer le robot.  
Les chapitres suivants vont vous présenter les différentes méthodes et modules possibles avec des exemples d'utilisation.

Avant de suivre ce tutoriel, vous souhaitez peut-être savoir [comment configurer et utiliser pybot](https://42angouleme.github.io/config/).

Ensuite, pour démarrer à programmer le robot, il faudra toujours commencer par ces deux lignes de code.

```python
from pybot import Robot

robot = Robot()
```

Ce robot est utilisable en français et en anglais.  
En effet, toutes les méthodes et les modules présentés dans la suite de la documentation sont disponibles en français comme en anglais (avec les commentaires des fonctions traduits aussi).  
Le mélange des langues et d’ailleurs possible même si fortement déconseiller pour des questions de lisibilité et de compréhension du code.
