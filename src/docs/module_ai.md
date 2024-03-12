# Module IA - AI

Vous êtes ici dans la documentation du module IA du robot.

Ce module sert a dialoguer avec le robot, il est capable de comprendre et de répondre à des questions.  
Il peut aussi avoir des emotions et des réactions.

!!!Warning
    Avant d’utiliser un module, il faudra toujours le lancer sinon il vous sera impossible d’utiliser le module et les méthodes lier à celui-ci.

!!!Note
    Il est conseiller de lancer le module fenêtre avant de lancer le module IA pour pouvoir voir les réactions du robot et recuperer plus facilement les questions et les réponses.

!!!Success "Demmarer le module IA"
    ```python
    robot.initialiser_module_IA()

    ou alors

    robot.init_AI_module()
    ```

À partir de ce moment, l'objet IA est initialisé dans le robot il est donc utilisable.

!!!Note
    La méthode `initialiser_module_IA()` (fr) - `init_AI_module()` (en).

## Discuter avec le robot

### Commencer à discuter avec le robot

Pour commencer une discussion avec le robot, il faut utiliser la méthode `demarrer_discussion()` (fr) - `init_conversation()` (en).

!!!Success "Demarrer une discussion"
    ```python
    robot.IA.demarrer_discussion()

    ou alors

    robot.AI.init_conversation()
    ```

!!!Warning
    Il faut toujours commencer une discussion avec le robot avant d'utiliser les méthodes suivantes.

### Arrêter de discuter avec le robot

Pour arrêter la discussion avec le robot, il faut utiliser la méthode `arreter_discussion()` (fr) - `stop_conversation()` (en).

!!!Success "Arreter une discussion"
    ```python
    robot.IA.arreter_discussion()

    ou alors

    robot.AI.stop_conversation()
    ```

!!! warning
    A partir de ce moment là le robot ne pourra plus vous répondre et il faudra recommencer la discussion avec [`demarrer_discussion()`](#commencer-à-discuter-avec-le-robot).

### Poser une question / parler au robot

Pour pouvoir parler au robot (poser des questions, donner des informations, ...), il faut utiliser la méthode `poser_question(question : str)` (fr) - `ask_question(question : str)` (en).

!!!Success "Poser une question"
    ```python

    question = "Quel est ton nom ?"
    robot.IA.poser_question(question)

    ou alors

    question = "Quel est ton nom ?"
    robot.AI.ask_question(question)
    ```

Le robot répondra à la question posée en paramètre.  
Cette fonction retourne la réponse du robot.

!!!Info
    Le robot peut prendre un certain temps de réflexion pour vous répondre pendant ce temps de réflexion le robot semblera être en pause (inutilisable).  
    Il suffit simplement d'attendre sa réponse pour qu'il ne soit plus en pause (utilisable).

!!!Warning
    Tant qu'aucun historique de conversation n'est chargé, le robot ne pourra pas se souvenir de la conversation précédente.
    Le robot ne se souviendra pas des interactions qu'il a pu avoir avec l'utilisateur tant que l'historique de conversation n'est pas chargé.

## L'historique de conversation du robot

Comme dit précédemment si on ne donne pas d'historique de conversation au robot, il ne pourra pas se souvenir de la conversation précédente.

### Gérer l'historique de conversation

#### Se souvenir

!!!Warning
    Avant cette étape, il faut avoir récupéré l'historique de conversation de l'utilisateur.  
    Note : voir la documentation du module [utilisateur](module_user.md#historique-de-conversation) pour récupérer l'historique de conversation.

Pour que le robot se souvienne des échanges qu'il a eu avec l'utilisateur, il faut charger un historique de conversation.  
On peut charger l'historique dans le robot avec la méthode `charger_historique_conversation(historique_de_conversation : str)` (fr) - `load_conversation_history(conversation_history : str)` (en).  

Ici, vous donnez donc au robot la capacité de se souvenir des interactions qu'il a eues avec l'utilisateur, ainsi il pourra reprendre la discussion là où elle s'était arrêtée la dernière fois.

!!!Success "Charger un historique de conversation"
    ```python
    historique = robot.utilisateur.obtenir_historique_conversation_utilisateur()
    robot.IA.charger_historique_conversation(historique)

    ou alors

    history = robot.user.get_user_conversation_history()
    robot.AI.load_conversation_history(history)
    ```

!!!Warning
    Si un historique de conversation est déjà chargé et qu'un autre historique vient à être chargé l'ancien historique sera écrasé.

!!!Note
    Si l'historique n'est pas vide, le robot reprendra la discussion là où l'utilisateur l'avait arrêtée la dernière fois.

#### Effacer la mémoire

Si vous voulez changer de discussion ou bien effacer l'historique de la conversation vous pouvez utilisez la méthode `effacer_historique_conversation()` (fr) - `clear_conversation_history()` (en).

!!!Note
    Pensez à effacer l'historique quand l'utilisateur se déconnecte.

!!!Success "Supprimer l'historique de conversation"
    ```python
    robot.IA.effacer_historique_conversation()

    ou alors

    robot.AI.clear_conversation_history()
    ```

A partir de ce moment le robot oubliera tout des échanges précédents avec l'utilisateur.

!!!Warning
    Pensez à récupérer et sauvegarder l'historique avant de le supprimer

#### Récupérer la mémoire du robot

Pour pouvoir sauvegarder l'historique de conversation (mémoire du robot), il faut pouvoir récupérer l'historique de conversation pour cela il faut utiliser la méthode `obtenir_historique_conversation()` (fr) - `get_current_conversation_history()` (en).

!!!Success "Récupérer l'historique de conversation"
    ```python
    robot.IA.obtenir_historique_conversation()

    ou alors

    robot.AI.get_current_conversation_history()
    ```

Cette méthode renvoit la mémoire du robot permettant ainsi la sauvegarde de celle-ci.

!!!Note
    Voir la documentation du module [utilisateur](module_user.md#historique-de-conversation) pour voir comment sauvegarder l'historique de conversation.

## Exemple complet 1

```python
from pybot import Robot

robot = Robot()

robot.initialiser_module_IA()

robot.IA.demarrer_discussion()

while True:
    question = input("Vous : ")
    reponse = robot.IA.poser_question(question)
    print("Pybot : ", reponse)
```

!!!Warning
    L'appel à la fonction `input()` devra etre remplacé par la méthode permettant de récupérer les questions posées par l'utilisateur.  
    On pourra le remplacer par une zone de texte dans la fenêtre.  

    De même le print devra être remplacé par la méthode permettant d'afficher les réponses du robot.  
    On pourra le remplacer par exemple via un appel à la méthode afficher_texte() du module *Fenetre*.

## Les émotions du robot

Le robot peut avoir des émotions et des réactions.  
Pour lui donner des émotions, il faut utiliser la méthode `donner_emotion(phrase : str)` (fr) - `get_emotion(sentence : str)` (en).
Cette méthode prend en paramètre une phrase (chaîne de caractère) et renvoie l'émotion que le robot exprime en fonction de celle-ci.  
Si aucune émotion enregistrée ne correspond a la phrase, il reste *Neutre*.  

!!!Success "Obtenir l'émotion du robot"
    ```python
    phrase = "Je suis content"
    emotion = robot.IA.donner_emotion(phrase)

    ou alors

    sentence = "I am happy"
    emotion = robot.AI.get_emotion(sentence)
    ```

!!! Note
    Voici la liste des émotions que le robot peut interpreter :
        - Célébration
        - Joie
        - Amusement
        - Soulagement
        - Suprise
        - Neutre
        - Réflexion
        - Incomprehension
        - Fatigue
        - Inquiétude
        - Contrariété
        - Tristesse
        - Colère
        - Peur

Voir la documentation de la [fenêtre](module_window.md#obtenir-limage-de-lémotion) pour voir comment afficher les émotions du robot.

## Exemple complet 2

```python
from pybot import Robot

robot = Robot()

robot.initialiser_module_fenetre()
robot.initialiser_module_IA()

robot.fenetre.ouvrir_fenetre()
robot.ajouter_evenement("echap", "stop")

i = 0
while i < 15 :

    evenement =  robot.verifier_evenements()
    if evenement == "stop" :
        robot.desactiver()
        break

    if i == 0 :
        phrase = "Je celebre ma victoire"
    elif i == 1 :
        phrase = "Je suis content"
    elif i == 2 :
        phrase = "Je suis amusé"
    elif i == 3 :
        phrase = "Je suis soulagé"
    elif i == 4 :
        phrase = "Je suis surpris"
    elif i == 5 :
        phrase = "Je suis neutre"
    elif i == 6 :
        phrase = "Je suis en pleine reflexion"
    elif i == 7 :
        phrase = "Je ne comprends pas"
    elif i == 8 :
        phrase = "Je suis fatigué"
    elif i == 9 :
        phrase = "Je suis inquiet"
    elif i == 10 :
        phrase = "Je suis très contrarié"
    elif i == 11 :
        phrase = "Je suis triste"
    elif i == 12 :
        phrase = "Je suis très en colère"
    elif i == 13 :
        phrase = "Je suis effrayé"
    elif i == 14 :
        robot.desactiver()
        break

    emotion = robot.IA.donner_emotion(phrase)
    print(phrase, " : ", emotion)
    chemin_image_emotion = robot.fenetre.obtenir_image_emotion(emotion)
    robot.fenetre.afficher_fond()
    robot.fenetre.afficher_image(chemin_image_emotion, 346, 246)
    robot.fenetre.actualiser_affichage()
    robot.dort(1)
    i += 1
```

!!!Warning
    La compréhension des emotions est quelque chose de complexe et il se peut que le robot ne comprenne pas l'émotion que vous voulez lui faire exprimer.
