# La bibliothèque Pybot

!!! note "Ce qu'est *Pybot*"
    *Pybot* est une bibliothèque logicielle permettant à des élèves de collège de programmer eux même un robot immobile.

Vous trouverez ici les informations pour utiliser la bibliothèque *pybot* avec des exemples concret pour réaliser des programmes d'un simple affichage de caméra jusqu'à un robot conversationnel complet.


## Les fonctionnalités du robot :

!!! note "Le robot complet."
    Le Robot a été pensé pour fonctionner sur un Raspberry Pi configuré avec Linux (Debian). Un écran pour le **visage**, une caméra pour les **yeux**, un haut-parleur pour la **bouche** et un microphone pour les **oreilles**. La coquille entourant le raspberry pi est libre d'interprétation esthétique.

Avec la bibliothèque vous pouvez :

> :one: :arrow_right: Construire une interface graphique pour intéragir avec le robot.  
:two: :arrow_right: Utiliser une reconnaissance visuelle par caméra (pas biométrique comme le visage mais des dessins sur cartes).  
:three: :arrow_right: Des fonctionnalités de communication avec une IA utilisant une transformation de l'audio en texte (microphone) et de texte en audio (haut parleur) qui interagisse avec une IA conversationnelle de type chatGPT.  
:four: :arrow_right: Une base de donnée et une administration web pour configurer le robot, par exemple: enregistrer les cartes d'identification des élèves, préparer des questions qui seront posé aux élèves et dont les réponses seront enregistré en base de donnée pour consultation.


## Utilisation de la bibliothèque

```python
print("bonjour, Pybot!")
```

*Pybot* se présente comme un objet avec des méthodes que l'on peut utiliser ensemble pour faire le programme.

Les chapitres suivant vous présentent les différentes méthodes possibles et des exemples d'utilisation.

Avant de suivre ce tutoriel, vous souhaitez peut-être savoir [comment configurer et utiliser pybot](config.md).