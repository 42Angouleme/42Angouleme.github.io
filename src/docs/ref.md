# Référence de la bibliothèque

Pour en savoir plus, dans un éditeur tel que vscode, il suffit de passer la souris sur une fonction pour voir les commentaires la concernant.

![Commentaires](ref.png)

## l'écran

* Importer et utiliser pybot
```python
from pybot import Robot
robot = Robot()
```

* Démarrer webapp.
```python
robot.demarrer_webapp()
```

* Allumer l'écran.
```python
robot.allumer_ecran(longeur, hauteur)
```

* Changer le titre.
```python
robot.changer_titre(titre)
```

* Mettre à jour l'affichage dans la fenêtre.
```python
robot.dessiner_ecran()
```

* Entrer ou sortir du plein écran.
```python
plein_ecran(changer)
```

* Mettre en pause le robot.
```python
robot.dort(secondes)
```

* est_actif

* eteindre_ecran

## les évènements

* ajouter_evenement

* supprimer_evenement

* verifier_evenements

### les boutons
### la caméra et la carte
### parler avec le robot