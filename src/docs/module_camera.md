# Module Camera

Vous êtes ici dans la documentation du module Camera du robot.

Ce module permet de prendre des photos, d’y appliquer des filtres, reconnaissance par caméra (pas biométrique comme le visage, mais des dessins sur cartes).

!!!Warning
    Avant d’utiliser un module, il faudra toujours le lancer sinon il vous sera impossible d’utiliser le module et les méthodes lier à celui-ci.

!!!Note
    Il faut avoir demarrer le module fenêtre et l'avoir ouverte pour pouvoir utliser la méthode `demarrer_module_camera` ou `start_camera_module`.  
    Voir la documentation du module [fenêtre](module_window.md) pour plus d'informations.

!!!Success "Demmarer le module Camera"
    ```python
    robot.demarrer_module_camera()

    ou alors

    robot.start_camera_module()
    ```

À partir de ce moment, l'objet camera est initialisé dans le robot il est donc utilisable.

!!!Note
    La méthode `demarrer_module_camera()` initialise l'objet camera dans le robot et c'est pareil pour `start_camera_module()`.

## Afficher la caméra

Pour afficher la caméra, il suffit d'utiliser la méthode `afficher_camera(position_x: int, position_y: int) (fr) - display_camera(position_x : int, position_y : int) (en)`.

!!!Warning
    Mettez cette méthode dans une boucle pour que l'image de la caméra soit actualisée et reste fluide.

!!!Success "Afficher la caméra"
    ```python

    while robot.est_actif():
        robot.afficher_camera(100, 100)
        robot.fenetre.actualiser_affichage()

    ou alors

    while robot.is_active():
        robot.display_camera(100, 100)
        robot.window.refresh_display()
    ```

!!!Note
    La caméra afficher fait 640 pixels de long et 480 pixels de haut. Le **dernier pixel** a les coordonnées **x = 299 et y = 199**.

## Prendre une photo

Pour prendre une photo, il suffit d'utiliser la méthode `prendre_photo(nom_fichier: str) (fr) - take_picture(file_name : str) (en)`.  
La photo sera enregistrée dans le dossier `images` du robot.

!!!Warning
    Si le fichier existe déjà, il sera écrasé.

!!!Success "Prendre une photo"
    ```python

    robot.prendre_photo("photo1")

    ou alors

    robot.take_picture("photo1")
    ```

!!!Note "Conseil"
    Il est conseillé de mettre un nom de fichier différent à chaque photo pour ne pas écraser les photos précédentes.  
    Declenché cette méthode par un bouton dans l'interface graphique.

!!!Note
    Voir la documentation du module [fenêtre](module_window.md#afficher-une-image) pour pouvoir afficher la photo prise.  
    L'image sera de la même taille que la caméra soit 640 pixels de long et 480 pixels de haut.

## Appliquer un filtre

Pour appliquer un filtre à une photo, il suffit d'utiliser la méthode `appliquer_filtre(chemin_fichier: str, nom_filtre: str) (fr) - apply_filter(file_name : str, filter_name : str) (en)`.

Voir la réference pour la liste complète des [filtres](ref.md#les-filtres)

!!!Warning
    Le fichier sera écrasé par la photo avec le filtre appliqué.

!!!Success "Appliquer un filtre"
    ```python

    robot.appliquer_filtre("/images/photo1.jpg", "cartoon")

    ou alors

    robot.apply_filter("/images/photo1.jpg", "cartoon")
    ```

## Exemple complet

```python
from pybot import Robot, Couleur

robot = Robot()

robot.demarrer_module_fenetre()
robot.fenetre.ouvrir_fenetre(1500, 1000)

robot.demarrer_module_camera()

boutons = robot.attributs.boutons
boutons.bouton_photo = robot.fenetre.creer_bouton(200, 50, 10, 10, Couleur.BLANC)
boutons.bouton_photo.ajouter_texte("prendre_photo", 10, 10, 20, Couleur.NOIR)
boutons.quitter = robot.fenetre.creer_bouton(100, 50, 10, 80, Couleur.BLANC)
boutons.quitter.ajouter_texte("quitter", 10, 10, 20, Couleur.NOIR)

while robot.est_actif():

    boutons = robot.attributs.boutons
    robot.verifier_evenements()
    boutons.bouton_photo.afficher()
    boutons.quitter.afficher() 

    if boutons.bouton_photo.est_actif():
        robot.camera.prendre_photo("photo1")
        robot.fenetre.afficher_image("/images/photo1.jpg",  10, 500)
        robot.camera.appliquer_filtre("/images/photo1.jpg", "cartoon")
        robot.fenetre.afficher_image("/images/photo1.jpg",  655, 500)
    if boutons.quitter.est_actif():
        robot.desactiver()
    
    robot.camera.afficher_camera(300, 10)
    robot.fenetre.actualiser_affichage()
```
