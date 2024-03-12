# Les Boutons - Buttons

Les boutons sont des éléments graphiques qui permettent à l'utilisateur d'interagir avec le robot. Ils sont utilisés pour déclencher des actions lorsqu'ils sont cliqués.

## Créer un bouton

Voir [la documentation de la fenêtre](module_window.md#creer-un-bouton).

Après avoir créé un bouton, vous obtenez un objet (le bouton) qui vous permet de manipuler et personnaliser le bouton.
Pour cela, vous pouvez utiliser les méthodes qui vont vous être présentées ci-dessous.

!!!Warning "Attention"
    Les méthodes présentées ci-dessous sont utilisables uniquement sur un objet créé par la méthode `creer_bouton()` (fr) - `create_button()` (en).

## Ajouter un texte au bouton

Pour afficher le fond de la fenêtre, il suffit d’appeler la méthode `ajouter_texte(texte : str, position_x : int, position_y : int, taille : int, couleur : Couleur)` (fr) - `add_text(text : str, position_x : int, position_y : int, size : int, color : Couleur)` (en).

!!!Success "Ajouter un texte au bouton"
    ```python

    bouton = robot.fenetre.creer_bouton(100, 100, 100, 100, Couleur.BLANC)
    bouton.ajouter_texte("Cliquez-moi", 10, 10, 20, Couleur.NOIR)

    ou alors

    button = robot.window.create_button(100, 100, 100, 100, Couleur.BLANC)
    button.add_text("Click me", 10, 10, 20, Couleur.NOIR)
    ```

## Afficher le bouton

Quand vous créez un bouton, il n'est pas affiché dans la fenêtre.  
Pour l'afficher, il suffit d’appeler la méthode `afficher()` (fr) - `display()` (en).

!!!Success "Afficher le bouton"
    ```python

    bouton = robot.fenetre.creer_bouton(100, 100, 100, 100, Couleur.BLANC)
    bouton.afficher()

    ou alors

    button = robot.window.create_button(100, 100, 100, 100, Couleur.BLANC)
    button.display()
    ```

## Vérifier si le bouton est cliqué

Pour vérifier si le bouton est cliqué, il suffit d’appeler la méthode `est_actif()` (fr) - `is_active()` (en).
Cela permet de savoir si le bouton a été cliqué ou non pour ainsi déclencher une action.

!!!Warning
    Il faut absolument que la fonction verifier_evenements() soit appelée pour que la méthode est_actif() fonctionne.

!!!Success "Vérifier si le bouton est cliqué"
    ```python

    bouton = robot.fenetre.creer_bouton(100, 100, 100, 100, Couleur.BLANC)
    bouton.afficher()
    if bouton.est_actif():
        print("Le bouton a été cliqué")

    ou alors

    button = robot.window.create_button(100, 100, 100, 100, Couleur.BLANC)
    button.display()
    if button.is_active():
        print("The button has been clicked")
    ```

## Exemple complet

```python
from pybot import Robot, Couleur

robot = Robot()
robot.initialiser_module_fenetre()

robot.fenetre.ouvrir_fenetre(1200, 900)

boutons = robot.attributs.boutons
boutons.quitter = robot.fenetre.creer_bouton(100, 100, 100, 100, Couleur.BLANC)
boutons.quitter.ajouter_texte("quitter", 10, 10, 20, Couleur.NOIR)

while robot.est_actif():
    boutons = robot.attributs.boutons
    robot.verifier_evenements()
    boutons.quitter.afficher()
    if boutons.quitter.est_actif():
        robot.desactiver()
    robot.fenetre.actualiser_affichage()
```

!!!Note "Conseil"
    Il est conseillé de mettre un nom différent à chaque bouton dans les attributs pour ne pas écraser le bouton qui etait déjà enregistré sous ce nom.

Voir la documentation sur les [attributs du robot](module_robot.md#les-attributs-du-robot) pour plus d'informations.
