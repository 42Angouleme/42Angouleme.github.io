# La bibliothèque Pybot

> Pybot est une bibliothèque logicielle permettant à des élèves de collége à programmer eux même un robot.

Bonjour vous trouverez ici les informations pour utiliser la bibliothèque pybot avec des exemples concret pour réaliser des programmes jusqu'à un robot conversationnel complet.

## Les fonctionnalités du robot :

* Une interface graphique pour intéragir avec le robot.
* Une reconnaissance visuelle par caméra (pas biométrique comme le visage mais des dessins sur cartes).
* Une base de donnée et une administration web pour enregistrer les cartes des élèves.
* Des fonctionnalités de communication avec une IA utilisant un microphone et un haut parleur.

## Utilisation de la bibliothèque

```python
print("bonjour, pybot")
```

Pybot est une bibliothèque avec une Class Robot que l'on peut utiliser pour faire un programme graphique.

Voici les méthodes et des exemples d'utilisation:

### Pour demarrer nous avons besoin d'importer la bibliothèque et de démarrer le robot :

```python
from pybot import Robot

robot = Robot()
```

### Pour allumer l'écran avec une longueur et une hauteur :

```python
robot.allumer_ecran(800, 600)
```


### Pour éteindre l'écran :

```python
robot.eteindre_ecran()
```

### Pour changer le titre :

```python
robot.changer_titre("Exemple 1")
```

### Pour terminer le programme nous avons besoin de lancer la boucle :

```python
robot.lancer_boucle()
```

### Un exemple de programme complet :

```python
from pybot import Robot

robot = Robot()

robot.allumer_ecran()

robot.changer_titre("Exemple 1")

robot.lancer_boucle()
```

### Pour ajouter un bouton, avec le nom du bouton et la fonction executée au click de ce bouton :

```python
robot.ajouter_bouton("Quitter", robot.eteindre_ecran)
```

### Pour afficher la caméra :

```python
robot.afficher_camera()
```

### Pour éteindre la caméra :

```python
robot.éteindre_camera()
```

### Pour enregistrer une photo :

```python
robot.enregistrer_photo()
```

### Pour afficher une photo :

```python
robot.afficher_photo()
```

### Pour supprimer une photo :

```python
robot.supprimer_photo()
```

### Pour afficher un visage :

```python
robot.afficher_visage_triste()
robot.afficher_visage_content()
robot.afficher_visage_colere()
robot.afficher_visage_fier()
```

### Pour appliquer un filtre sur une photo :

```python
robot.appliquer_filtre_noir_et_blanc()
robot.appliquer_filtre_amour()
robot.tourner_photo()
```


### Un autre exemple de programme complet :

```python
from pybot import Robot

robot = Robot()

longueur = 800
hauteur = 600

robot.allumer_ecran(longueur, hauteur)

robot.changer_titre("Exemple 2")

robot.ajouter_bouton("Quitter", robot.eteindre_ecran)
robot.ajouter_bouton("Afficher visage", robot.afficher_visage_content)

robot.lancer_boucle()
```

### Objectif du programme à réaliser aujourd'hui:

```
Faire un programme qui affiche la caméra, prend une photo et qui applique un filtre sur la photo.
```
