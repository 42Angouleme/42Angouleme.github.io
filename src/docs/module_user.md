# Module Utilisateur - User

Vous êtes ici dans la documentation du module Utilisateur du robot.

Ce module permet de gérer les utilisateurs du robot.
Il vous permet de créer, modifier, supprimer des utilisateurs du robot.

!!!Warning
    Avant d’utiliser un module, il faudra toujours le lancer sinon il vous sera impossible d’utiliser le module et les méthodes lier à celui-ci.

!!!Note
    Il faut lancer le module fenêtre et Caméra avant de lancer le module Utilisateur.  
    Et ouvrir la webapp pour pouvoir utiliser les méthodes liées à ce module.  
    Voir [webapp](module_robot.md#la-webapp) pour plus d'informations.

## Introduction

Tout au long de cette partie vous allez être ammenés à manipuler des seuils de détection.
Un seuil de détection est une valeur comprise entre **0.00** et **1.00**.
Dans notre cas, le seuil sera utilisé pour comparer des images:

- plus le score sera proche de 1.00 plus les images se ressemblent.  
- plus le score se rapproche de 0.00 plus les images sont différentes.

Les deux seuils à manipuler :

- **seuil_minimal**: seules les cartes dépassant se seuil seront sélectionnées comme potentiellement bonnes.  
- **seuil_arret_recherche**: si une carte dépasse ce seuil, la recherche s'arrête : il s'agit de la bonne carte.

!!! Note
    Le code de détection de carte ne donnera jamais 1.00, car même s'il sagit de la même image, l'ordinateur va prendre en compte: la lumière, la position, l'inclinaison de la carte par rapport à la caméra...

!!! warning
    Plus on prend un score d arrêt de recherche:  
    - bas: plus on a de chances de mal interpréter les cartes.  
    - haut: moins on detectera de carte.

## Connexion/ Deconnexion

### Connaitre le statut de connexion

Avant de connecter ou de déconnecter une personne, il est important de savoir si une personne est déjà connectée à l'application.
Pour cela, on peut utiliser la méthode `verifier_session()` (fr) - `check_session()` (en).

!!!Success
    ```python
    if robot.utilisateur.verifier_session():
        print("Une personne est connectée")
    else:
        print("Personne n'est connectée")

    ou alors

    if robot.user.check_session():
        print("Une personne est connectée")
    else:
        print("Personne n'est connectée")
    ```

### Se connecter

Si on veut se connecter, on peut utiliser la méthode `connecter(seuil_minimal : float, seuil_arret_recherche : float)` (fr) - `login(self, minimum_threshold: float, search_stop_threshold: float) : (en)`.

!!!Success "Connexion"
    ```python
    robot.utilisateur.connecter(0.5, 0.7)

    ou alors

    robot.user.login(0.5, 0.7)
    ```

!!!Note
    Les seuils sont optionnels, si on ne les met pas, ils prendront les valeurs par défaut qui sont 0.75 et 0.85.

!!!Warning
    Si la fonction est appelée alors que l application web n' est pas lancée ou bien que la caméra n' est pas allumée alors la fonction ne marchera pas.

### Se déconnecter

Pour se déconnecter, on peut utiliser la méthode `deconnecter()` (fr) - `logout()` (en).

!!!Success "Déconnexion"
    ```python
    robot.utilisateur.deconnecter()

    ou alors

    robot.user.logout()
    ```

## Créer/ Supprimer un compte utilisateur

### Créer une session

Pour pouvoir se connecter, il faut avoir un compte utilisateur, pour avoir un compte utilisateur, il faut le créer.
Pour créer un utilisateur il faut utiliser la méthode `creer_utilisateur(prenom, nom, carte)` (fr) - `create(firstname, lastname, card)` (en).

!!!Success "Création d'un utilisateur"
    ```python
    robot.utilisateur.creer_utilisateur("Jean", "Dupont", carte)

    ou alors

    robot.user.create("Jean", "Dupont", card)
    ```

!!! Note
    La carte en paramètre de la méthode créer_utilisateur(prenom, nom, **carte**) doit être une image récupérée avec la méthode [detecter_carte()` (fr) - `detect_card() (en)](module_user.md#récuperer-la-carte-detectée-àlécran).

!!! Warning
    La personne qui vient de créer son compte ne sera pas connecté, il faut appeler la méthode [`connecter()` (fr) - `login()` (en)](module_user.md#se-connecter) pour se connecter.

### Supprimer une session

Pour supprimer un utilisateur, il faut faire appel à la méthode `supprimer_utilisateur()` (fr) - `delete()` (en).

!!!Success "Suppression d'un utilisateur"
    ```python
    robot.utilisateur.supprimer_utilisateur()

    ou alors

    robot.user.delete()
    ```

!!! Warning
    Si la personne est connectée, elle sera déconnectée.
    Cette méthode supprime définitivement **l'utilisateur connecté**.

## Methodes utiles liées aux cartes et sessions

### Récupérer les informations de la personne connectée

Pour récupérer les informations de la personne connectée, on peut utiliser la méthode `obtenir_utilisateur_connecte()` (fr) - `get_logged_in_user()` (en).

!!!Success
    ```python
    if robot.verifier_session():
            utilisateur_connecte = robot.utilisateur.obtenir_utilisateur_connecte()
            print("Le prenom de la personne connectée est: ", utilisateur_connecte.prenom)
            print("Le nom de la personne connectée est:", utilisateur_connecte.nom)
    
    ou alors

    if robot.user.check_session():
            logged_in_user = robot.user.get_logged_in_user()
            print("Le prenom de la personne connectée est: ", logged_in_user.firstname)
            print("Le nom de la personne connectée est: ", logged_in_user.lastname)
    ```

Ce code permet d' afficher dans le terminal le prenom et le nom de l' utilisateur.
Voir [User](general.md#user) pour plus d'informations sur la structure de données utilisateur.

### Récuperer la carte detectée à l'écran

Pour récupérer la carte détectée à l'écran, on peut utiliser la méthode `detecter_carte(seuil_minimal : float, seuil_arret_recherche : float)` (fr) - `detect_card(minimum_threshold: float, search_stop_threshold: float)` (en).
Cette méthode retourne l'image detectée à l'écran.

!!!Note
    Les seuils sont optionnels, si on ne les met pas, ils prendront les valeurs par défaut qui sont 0.75 et 0.85.

!!!Success
    ```python
    carte = robot.utilisateur.detecter_carte()

    ou alors

    card = robot.user.detect_card()
    ```

!!!Warning
    Cette fonction retourne l'image qui n appartient pas selon le programme à un utilisateur déjà connu.

## Exemple Complet

```python
from pybot import Robot, Couleur

robot = Robot()

robot.demarrer_webapp()

robot.initialiser_module_fenetre()

robot.fenetre.ouvrir_fenetre(1500, 1000)
robot.initialiser_module_camera()

robot.initialiser_module_utilisateur()

boutons = robot.attributs.boutons
boutons.quitter = robot.fenetre.creer_bouton(100, 50, 10, 80, Couleur.BLANC)
boutons.quitter.ajouter_texte("quitter", 10, 10, 20, Couleur.NOIR)

boutons.deconnecter = robot.fenetre.creer_bouton(200, 50, 10, 10, Couleur.BLANC)
boutons.deconnecter.ajouter_texte("deconnecter", 10, 10, 20, Couleur.NOIR)

robot.attributs.mettre_a_jour_affichage = False

while robot.est_actif():

    robot.verifier_evenements()
    boutons = robot.attributs.boutons
    boutons.quitter.afficher() 
    boutons.deconnecter.afficher()

    if boutons.quitter.est_actif():
        robot.desactiver()
    
    if robot.utilisateur.verifier_session() == False:
        robot.utilisateur.connecter()
        if robot.utilisateur.verifier_session():
            user = robot.utilisateur.obtenir_utilisateur_connecte()
            robot.fenetre.afficher_fond()
            robot.fenetre.afficher_texte("Bonjour " + user.prenom + " " + user.nom, 400, 600, 20, Couleur.BLANC)
        
    if boutons.deconnecter.est_actif():
        if robot.utilisateur.verifier_session():
            robot.utilisateur.deconnecter()
            robot.fenetre.afficher_fond()
            robot.fenetre.afficher_texte("Deconnexion reussie", 400, 600, 20, Couleur.BLANC)
        else:
            robot.fenetre.afficher_fond()
            robot.fenetre.afficher_texte("Personne n'est connectée", 400, 600, 20, Couleur.BLANC)

    robot.camera.afficher_camera(300, 10)
    robot.fenetre.actualiser_affichage()
```

## Historique de conversation

### Sauvegarder l'historique de conversation

Un fois que vous avez recuperer l'historique de conversation, grace à la méthode `obtenir_historique_conversation()` (fr) - `get_current_conversation_history()` (en) du module [IA](module_ai.md#recuperer-la-memoire-du-robot), vous pouvez la sauvegarder dans la base de données.

Pour cela, vous pouvez utiliser la méthode `sauvegarder_historique_conversation(historique)` (fr) - `save_conversation_history(history)` (en).

!!!Success "Sauvegarder l'historique de conversation"
    ```python
    historique = robot.IA.obtenir_historique_conversation()
    robot.utilisateur.sauvegarder_historique_conversation(historique)

    ou alors

    history = robot.AI.get_current_conversation_history()
    robot.user.save_conversation_history(history)
    ```

!!!Note
    Un utilisateur doit être connecté pour pouvoir sauvegarder un historique de conversation.

!!!Warning
    L'ancien historique de conversation sera ecrasé par le nouveau.

### Récupérer l'historique de conversation

Pour récupérer l'historique de conversation, vous pouvez utiliser la méthode `obtenir_historique_conversation_utilisateur()` (fr) - `get_user_conversation_history()` (en).

!!!Success "Récupérer l'historique de conversation"
    ```python
    historique = robot.utilisateur.obtenir_historique_conversation_utilisateur()
    robot.IA.charger_historique_conversation(historique)

    ou alors

    history = robot.user.get_user_conversation_history()
    robot.AI.load_conversation_history(history)
    ```

!!!Warning
    Si un historique de conversation est déjà chargé et qu'un autre historique vient à être chargé l'ancien historique sera écrasé.
