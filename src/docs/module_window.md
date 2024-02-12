# Module Fenêtre - Window

Vous êtes ici dans la documentation du module fenêtre - window du robot.

Ce module sert à gérer l’interface graphique (fenêtre), cette interface graphique servira d’intermédiaire entre l’utilisateur et le robot ainsi que ses autres modules.

En effet, ce module est le module le plus important, car c’est lui qui vous permettra d’interagir avec le robot en déclenchant des comportements selon vos actions (appui sur un bouton pour démarrer une discussion avec le robot…).

!!!Warning
    Avant d’utiliser un module, il faudra toujours le lancer sinon il vous sera impossible d’utiliser le module et les méthodes lier à celui-ci.

!!!Success "Demmarer le module fenetre"
    ```python
    robot.demarrer_module_fenetre()

    ou alors

    robot.start_window_module()
    ```

À partir de ce moment, les objets fenetre et window sont initialisés dans le robot, ils sont donc utilisables.

!!!Note
    La methode `demarrer_module_fenetre()` initialise les objets fenetre et window dans le robot et c'est pareil pour `start_window_module()`.

## Ouvrir une fenêtre

La première chose que vous allez vouloir faire avec la fenêtre, c'est de l’ouvrir, en effet tant que vous n’ouvrez pas la fenêtre, celle-ci est inutilisable.

Pour cela, on va donc faire appelle à la méthode `ouvrir_fenetre(longueur: int, hauteur: int) (fr) - open_window(width : int, height : int) (en)` en lui passant en paramètre la longueur et la largeur de la fenêtre.

!!!Success "Ouvrir la fenetre"
    ```python
    l = 1200
    h = 900
    robot.fenetre.ouvir_fenetre(l, h)

    ou alors

    w = 1200
    h = 900
    robot.window.open_window(w, h)
    ```

!!!Note
    Si vous ne donnez pas de paramètre à la méthode, alors la fenêtre s’ouvrira avec une taille de 800 sur 600.

## Fermer la fenêtre

Pour fermer la fenêtre, il suffit d’appeler la méthode `fermer_fenetre() (fr) - close_window() (en)`.

!!!Success "Fermer la fenetre"
    ```python
    robot.fenetre.fermer_fenetre()

    ou alors

    robot.window.close_window()
    ```

## Actualiser l’affichage

À chaque fois qu'une modification est faite (ex: un changement de titre, un nouveau bouton, un texte à afficher), il est important de mettre à jour l'affichage de la fenêtre.  
On utilise la méthode `actualiser_affichage() (fr) - refresh_display() (en)`.

Idéalement, cette méthode est appelée dans une boucle afin de garder l'affichage à jour.

!!!Success "Actualiser l'affichage"
    ```python
    robot.fenetre.actualiser_affichage()

    ou alors

    robot.window.refresh_display()
    ```

## Passer la fenêtre en plein écran

Pour passer la fenêtre en plein écran, il suffit d’appeler la méthode `plein_ecran(changer : bool) (fr) - full_screen(change : bool) (en)`.

!!!Success "Plein écran"
    ```python
    robot.fenetre.plein_ecran(True) # pour passer en plein écran
    robot.fenetre.plein_ecran(False) # pour sortir du plein écran

    ou alors

    robot.window.full_screen(True) # for full screen
    robot.window.full_screen(False) # for exit full screen
    ```

## Modifier le titre de la fenêtre

Pour modifier le titre de la fenêtre, il suffit d’appeler la méthode `changer_titre(titre : str) (fr) - change_title(title : str) (en)`.

!!!Success "Modifier le titre"
    ```python
    titre = "Nouveau titre"
    robot.fenetre.changer_titre(titre)

    ou alors

    title = "New title"
    robot.window.change_title(title)
    ```

## Changer la couleur de fond de la fenêtre

Pour changer la couleur de fond de la fenêtre, il suffit d’appeler la méthode `changer_couleur_fond(couleur : str) (fr) - change_background_color(color : str) (en)`.

!!!Success "Changer la couleur de fond"
    ```python
    couleur = (255, 255, 255) # blanc
    robot.fenetre.changer_couleur_fond(couleur)

    ou alors

    color = (0, 0, 0) # black
    robot.window.change_background_color(color)
    ```

!!!Note
    Voir la documentation sur [les couleurs](general.md#les-couleurs) pour plus d'informations.

## Afficher le fond de la fenêtre

Pour afficher le fond de la fenêtre, il suffit d’appeler la méthode `afficher_fond() (fr) - display_background() (en)`.

!!!Success "Afficher le fond"
    ```python
    robot.fenetre.afficher_fond()

    ou alors

    robot.window.display_background()
    ```

!!!Note
    Cette méthode est utile si vous avez modifié la couleur de fond de la fenêtre et que vous voulez voir le changement.

## Exemple complet 1

```python
from pybot import Robot, Couleur

robot = Robot()
robot.demarrer_module_fenetre()

robot.fenetre.ouvrir_fenetre(1200, 900)
robot.fenetre.changer_titre("Nouveau titre")
robot.fenetre.changer_couleur_fond(Couleur.BLANC)
robot.fenetre.afficher_fond()
robot.ajouter_evenement("echap", "sortir")

while robot.est_actif() :
    evenement = robot.verifier_evenements()
    if "sortir" in evenement:
        robot.desactiver()
        break # Sortie de la boucle
    robot.fenetre.actualiser_affichage()
```

## Dessiner un rectangle

Pour dessiner un rectangle, il suffit d’appeler la méthode `dessiner_rectangle(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur) (fr) - draw_rectangle(width: int, height: int, position_x: int, position_y: int, color: Couleur)  (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche du rectangle.

!!!Success "Dessiner un rectangle"
    ```python
    l = 100
    h = 50
    x = 100
    y = 100
    couleur = Couleur.BLEU
    robot.fenetre.dessiner_rectangle(l, h, x, y, couleur)

    ou alors

    w = 100
    h = 50
    x = 100
    y = 100
    color = Couleur.BLEU
    robot.window.draw_rectangle(w, h, x, y, color)
    ```

!!!Note
    Voir la documentation sur [les positions](general.md#les-positions) pour plus d'informations.

## Afficher un texte

Pour afficher une ligne de texte, il suffit d’appeler la méthode `afficher_texte(texte : str, position_x: int, position_y: int, taille: int, couleur: Couleur) (fr) -`  
`display_text(text : str, position_x: int, position_y: int, size: int, color: Couleur) (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche du texte.

!!!Success "Afficher un texte"
    ```python
    texte = "Bonjour"
    x = 100
    y = 100
    taille = 24
    couleur = Couleur.NOIR
    robot.fenetre.afficher_texte(texte, x, y, taille, couleur)

    ou alors

    text = "Hello"
    x = 100
    y = 100
    size = 24
    color = Couleur.NOIR
    robot.window.display_text(text, x, y, size, color)
    ```

## Afficher une image

Pour afficher une image, il suffit d’appeler la méthode `afficher_image(chemin_fichier : str, position_x: int, position_y: int) (fr) -`  
`display_image(file_path : str, position_x: int, position_y: int) (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche de l'image.

!!!Success "Afficher une image"
    ```python
    chemin = "/images/photo.png"
    x = 100
    y = 100
    robot.fenetre.afficher_image(chemin, x, y)

    ou alors

    path = "/images/picture.png"
    x = 100
    y = 100
    robot.window.display_image(path, x, y)
    ```

!!!Note
    Le module [Caméra - Camera](module_camera.md) permet de prendre des photos et de les enregistrer dans un fichier.

## Exemple complet 2

```python
from pybot import Robot, Couleur

robot = Robot()
robot.demarrer_module_fenetre()

robot.fenetre.ouvrir_fenetre(1200, 900)
robot.fenetre.changer_titre("Nouveau titre")
robot.fenetre.changer_couleur_fond(Couleur.BLANC)
robot.fenetre.afficher_fond()
robot.ajouter_evenement("echap", "sortir")

robot.fenetre.dessiner_rectangle(100, 50, 100, 100, Couleur.BLEU_CIEL)
robot.fenetre.afficher_texte("Bonjour", 100, 100, 24, Couleur.NOIR)
robot.fenetre.afficher_image("images/photo.png", 100, 100) # à remplacer par le chemin de votre image

while robot.est_actif() :
    evenement = robot.verifier_evenements()
    if "sortir" in evenement:
        robot.desactiver()
    robot.fenetre.actualiser_affichage()
```

## Creer un bouton

Pour créer un bouton, il suffit d’appeler la méthode `creer_bouton(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur) (fr) -`  
`create_button(width: int, height: int, position_x: int, position_y: int, color: Couleur) (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche du bouton.

!!!Success "Créer un bouton"
    ```python
    l = 100
    h = 50
    x = 100
    y = 100
    couleur = Couleur.BLEU
    bouton = robot.fenetre.creer_bouton(l, h, x, y, couleur)

    ou alors

    w = 100
    h = 50
    x = 100
    y = 100
    color = Couleur.BLEU
    button = robot.window.create_button(w, h, x, y, color)
    ```

!!!Note
    Voir la documentation sur [les boutons](button.md) pour plus d'informations.
    Regarder la documentation sur les [attributs du robot](module_robot.md#les-attributs-du-robot) pour plus d'informations.

## Creer une zone de texte

Pour créer une zone de texte, il suffit d’appeler la méthode `creer_zone_texte(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur) (fr) -`
`create_text_area(width: int, height: int, position_x: int, position_y: int, color: Couleur) (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche de la zone de texte.

!!!Success "Créer une zone de texte"
    ```python
    l = 100
    h = 50
    x = 100
    y = 100
    couleur = Couleur.BLEU
    zone_texte = robot.fenetre.creer_zone_texte(l, h, x, y, couleur)

    ou alors

    w = 100
    h = 50
    x = 100
    y = 100
    color = Couleur.BLEU
    text_area = robot.window.create_text_area(w, h, x, y, color)
    ```

!!!Note
    Voir la documentation sur [les zones de texte](text_area.md) pour plus d'informations.
    Regarder la documentation sur les [attributs du robot](module_robot.md#les-attributs-du-robot) pour plus d'informations.

## Afficher carte détectée

Une fois une carte détectée, il est possible de l'afficher sur la fenêtre.
Pour afficher une carte détectée, il suffit d’appeler la méthode `afficher_carte_detectee(self, detected_card: MatLike, position_x: int, position_y: int) (fr)`  
`- display_detected_card(self, detected_card: MatLike, position_x: int, position_y: int) (en)`.

!!!Warning
    La position (x, y) est le coin en haut à gauche de l'image.

!!!Success "Afficher une carte détectée"
    ```python
    carte = robot.utilisateur.detecter_carte()
    x = 100
    y = 100
    robot.fenetre.afficher_carte_detectee(carte, x, y)

    ou alors

    card = robot.user.detect_card()
    x = 100
    y = 100
    robot.window.display_detected_card(card, x, y)
    ```

Voici où trouver la documentation sur la méthode [`detecter_carte() (fr) - detect_card() (en)`](module_user.md#detecter-une-carte).

## Obtenir l'image de l'émotion

Le module [IA - AI](module_ai.md#les-émotions-du-robot) permet de donner des "émotions" au robot.  
Pour afficher l'image de l'émotion, il faut appeler la méthode `obtenir_image_emotion(emotion : str) (fr) - get_emotion_image(emotion : str) (en)`.

Et ensuite, afficher l'image avec la méthode [`afficher_image(chemin : str, position_x: int, position_y: int) (fr) - display_image(path : str, position_x: int, position_y: int) (en)`](#afficher-une-image)

!!!Success "Obtenir l'image de l'émotion"
    ```python
    emotion = "heureux"
    chemin = robot.fenetre.obtenir_image_emotion(emotion)
    x = 100
    y = 100
    robot.fenetre.afficher_image(chemin, x, y)

    ou alors

    emotion = "heureux"
    path = robot.window.get_emotion_image(emotion)
    x = 100
    y = 100
    robot.window.display_image(path, x, y)
    ```

!!!Info
    Les images des emotions sont stockées dans le dossier `images/emotions`.  
    Elles peuvent être remplacées par des images personnalisées.  
    Les images de bases font du 108x108 pixels.  
    La taille de l'image peut changer si vous la remplacez.  
    Mais essayez de garder la meme taille entre toute les images pour un meilleur rendu.

!!!Note
    Voir la documentation sur les émotions pour plus d'informations. [IA - AI](module_ai.md#les-émotions-du-robot)
