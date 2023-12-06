# La bibliothèque Pybot

> Pybot est une bibliothèque logicielle permettant à des élèves de collége à programmer eux même un robot.

Bonjour vous trouverez ici les informations pour utiliser la bibliothèque pybot avec des exemples concret pour réaliser des programmes d'un simple affichage de caméra jusqu'à un robot conversationnel complet.


## Les fonctionnalités du robot :

* Une interface graphique pour intéragir avec le robot.
* Une reconnaissance visuelle par caméra (pas biométrique comme le visage mais des dessins sur cartes).
* Des fonctionnalités de communication avec une IA utilisant un microphone et un haut parleur.
* Une base de donnée et une administration web pour configurer le robot, par exemple: enregistrer les cartes d'identification des élèves.


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


### Lancer l'application web

La première chose à faire est de lancer le serveur, l'application web, qui permettra de travailler avec la base de donnée et de configurer le robot depuis un site web.

Le serveur web se lance et ne bloque pas le programme, on peut donc ensuite s'occuper de programmer le robot.

```python
robot.demarrer_webapp()
```

Le site sera accessible à l'adresse : http://127.0.0.1:5000

> Il est possible de configurer le raspberry pi pour faire serveur et rendre le site accessible sur le réseau local.


---> REPRENDRE ICI LA DOC


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
