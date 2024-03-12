# Les zones de texte - text_area

Les zones de texte sont des éléments graphiques permettant de récupérer des informations de l'utilisateur.  
Elles sont utilisées pour permettre à l'utilisateur de saisir des informations dans le robot.

!!!Warning
    Le robot à la fin n'est pas censé utiliser le clavier pour saisir des informations.  
    Ceci est une fonctionnalité qui sert d'entre deux avant l'ajout du module audio.

## Créer une zone de texte

Voir [la documentation de la fenêtre](module_window.md#creer-une-zone-de-texte).

Après avoir créé une zone de texte, vous obtenez un objet (la zone de texte) qui vous permet de manipuler et personnaliser la zone de texte.  
Pour cela, vous pouvez utiliser les méthodes qui vont vous être présentées ci-dessous.

!!!Warning "Attention"
    Les méthodes présentées ci-dessous sont utilisables uniquement sur un objet créé par la méthode `creer_zone_texte()` (fr) - `create_text_area()` (en).

!!!Note
    Pensé à donner une taille assez grande à la zone de texte pour que l'utilisateur puisse saisir des informations, sans que cela sorte de la zone de texte, créant un effet de "dépassement" de la zone de texte.

## Afficher la zone de texte

Quand vous créez une zone de texte, elle n'est pas affichée dans la fenêtre.  
Pour l'afficher, il suffit d’appeler la méthode `afficher()` (fr) - `display()` (en).

!!!Success "Afficher la zone de texte"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.afficher()

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.display()
    ```

## Verifier si la zone de texte est cliquée

Pour verifier si la zone de texte est cliquée, il suffit d’appeler la méthode `est_actif()` (fr) - `is_active()` (en).  
Cela permet de savoir si la zone de texte a été cliquée ou non pour ainsi déclencher l'ecriture.

!!!Warning
    Il faut absolument que la fonction verifier_evenements() soit appelée pour que la méthode est_actif() fonctionne.

!!!Success "Vérifier si la zone de texte est cliquée"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.afficher()
    if zone_texte.est_actif():
        print("La zone de texte a été cliquée")

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.display()
    if text_area.is_active():
        print("The text area has been clicked")
    ```

## Ecrire dans la zone de texte

Pour écrire dans la zone de texte, il suffit d’appeler la méthode `ecrire(robot : Robot)` (fr) - `write(robot : Robot)` (en).  
Utilisez cette méthode en combinaison avec la méthode `est_actif()` (fr) - `is_active()` (en) pour vérifier si la zone de texte est cliquée.
Sinon, vous vous exposez à des erreurs.

!!!Success "Écrire dans la zone de texte"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.afficher()
    if zone_texte.est_actif():
        zone_texte.ecrire(robot)

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.display()
    if text_area.is_active():
        text_area.write(robot)
    ```

Cette méthode renvoie le texte après que l'utilisateur a quitté la zone de texte.

!!!Warning
    Lorsque l'utilisateur écrit, le robot est mis en pause tant que l'utilisateur n'a pas quitté la zone d'écriture en cliquant en dehors de celle-ci ou alors en tapant sur la touche entrée.

!!!Note
    Cette méthode est spéciale, elle prend en paramètre le robot pour pouvoir récupérer les informations saisies par l'utilisateur.

## Récupérer le texte de la zone de texte

Pour récupérer le texte de la zone de texte, il suffit d’appeler la méthode `obtenir_texte()` (fr) - `get_text()` (en).

!!!Success "Récupérer le texte de la zone de texte"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.afficher()
    if zone_texte.est_actif():
        zone_texte.ecrire(robot)
    texte = zone_texte.obtenir_texte()
    print(texte)

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.display()
    if text_area.is_active():
        text_area.write(robot)
    text = text_area.get_text()
    print(text)
    ```

## Effacer le texte de la zone de texte

Pour effacer le texte de la zone de texte, il suffit d’appeler la méthode `effacer_texte()` (fr) - `erase_text()` (en).
Cela permet de vider la zone de texte pour une nouvelle saisie.
Renvoi le texte effacé.

!!!Success "Effacer le texte de la zone de texte"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.afficher()
    if zone_texte.est_actif():
        zone_texte.ecrire(robot)
    texte = zone_texte.effacer_texte()
    print(texte)

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.display()
    if text_area.is_active():
        text_area.write(robot)
    text = text_area.erase_text()
    print(text)
    ```

## Exemple complet 1

```python
from pybot import Robot, Couleur

robot = Robot()
robot.initialiser_module_fenetre()

robot.fenetre.ouvrir_fenetre(1200, 900)

zones_de_texte = robot.attributs.zones_de_texte
zones_de_texte.zone_texte_quitter = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)

while robot.est_actif() :
    zones_de_texte = robot.attributs.zones_de_texte
    evenement = robot.verifier_evenements()
    if zones_de_texte.zone_texte_quitter.est_actif():
        zones_de_texte.zone_texte_quitter.ecrire(robot)
        texte = zones_de_texte.zone_texte_quitter.obtenir_texte()
        if texte == "Quitter":
            robot.desactiver()
            break
    zones_de_texte.zone_texte_quitter.afficher()
    robot.fenetre.actualiser_affichage()
```

## Personnaliser la zone de texte

### Modifier la taille de la police

Pour modifier la taille de la police, il suffit d’appeler la méthode `modifier_taille_police(taille : int)` (fr) - `change_font_size(size : int)` (en).
Par defaut, la taille de la police est de 16.

!!!Success "Modifier la taille de la police"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.modifier_taille_police(20)
    zone_texte.afficher()

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.change_font_size(20)
    text_area.display()
    ```

### Modifier la couleur de la police

Pour modifier la couleur de la police, il suffit d’appeler la méthode `modifier_couleur_police(couleur : Couleur)` (fr) - `change_font_color(color : Couleur)` (en).

!!!Success "Modifier la couleur de la police"
    ```python

    zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)
    zone_texte.modifier_couleur_police(Couleur.ROUGE)
    zone_texte.afficher()

    ou alors

    text_area = robot.window.create_text_area(100, 100, 100, 100, Couleur.BLANC)
    text_area.change_font_color(Couleur.ROUGE)
    text_area.display()
    ```

## Exemple complet 2

```python
from pybot import Robot, Couleur

robot = Robot()
robot.initialiser_module_fenetre()

robot.fenetre.ouvrir_fenetre(1200, 900)

zones_de_texte = robot.attributs.zones_de_texte
zones_de_texte.zone_texte = robot.fenetre.creer_zone_texte(100, 100, 100, 100, Couleur.BLANC)

while robot.est_actif() :
    zones_de_texte = robot.attributs.zones_de_texte
    evenement = robot.verifier_evenements()
    if zones_de_texte.zone_texte.est_actif():
        zones_de_texte.zone_texte.ecrire(robot)
        texte = zones_de_texte.zone_texte.effacer_texte()
        if texte == "Quitter":
            robot.desactiver()
            break
        elif texte == "Rouge":
            zones_de_texte.zone_texte.modifier_couleur_police(Couleur.ROUGE)
        elif texte == "20":
            zones_de_texte.zone_texte.modifier_taille_police(20)
    zones_de_texte.zone_texte.afficher()
    robot.fenetre.actualiser_affichage()
```
