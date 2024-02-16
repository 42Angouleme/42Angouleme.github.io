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
    robot.demarrer_module_IA()

    ou alors

    robot.start_AI_module()
    ```

À partir de ce moment, l'objet IA est initialisé dans le robot il est donc utilisable.

!!!Note
    La méthode `demarrer_module_IA()` initialise l'objet IA et AI dans le robot et c'est pareil pour `start_AI_module()`.

## Discuter avec le robot

### Commencer à discuter avec le robot

Pour commencer une discussion avec le robot, il faut utiliser la méthode `demarrer_discussion() (fr) - start_conversation() (en)`.

!!!Success "Demarrer une discussion"
    ```python
    robot.IA.demarrer_discussion()

    ou alors

    robot.AI.start_conversation()
    ```

!!!Warning
    Il faut toujours commencer une discussion avec le robot avant d'utiliser les méthodes suivantes.

### Arrêter de discuter avec le robot

Pour arrêter la discussion avec le robot, il faut utiliser la méthode `arreter_discussion() (fr) - stop_conversation() (en)`.

!!!Success "Arreter une discussion"
    ```python
    robot.IA.arreter_discussion()

    ou alors

    robot.AI.stop_conversation()
    ```

!!! warning
    A partir de ce moment là le robot ne pourra plus vous répondre et il faudra recommencer la discussion avec [`demarrer_discussion()`](#commencer-à-discuter-avec-le-robot).

### Poser une question / parler au robot

Pour pouvoir parler au robot (poser des questions, donner des informations, ...), il faut utiliser la méthode `poser_question(question : str) (fr) - ask_question(question : str) (en)`.

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
    Tant qu'aucun historique n'est chargé le robot ne fera pas un suivit de la conversation et ne pourra pas se souvenir de la conversation précédente.
    Car tout sera oublié à la fin de la discussion.

## La mémoire du robot

Comme dit précédemment si on ne donne pas de mémoire au robot, il ne pourra pas se souvenir de la conversation précédente.

La méthode `creer_historique_conversation() (fr) - create_conversation_history() (en)` permet au robot de lui demander créer un historique de conversation.

!!!Success "Créer un historique de conversation"
    ```python
    robot.IA.creer_historique_conversation()

    ou alors

    robot.AI.create_conversation_history()
    ```

!!!Note
    Il est préférable d'avoir un historique de conversation par utilisateur et aussi de sauvegarder l'historique de conversation dans les données de l'utilisateur correspondant.
    L'enregistrement de l'historique de conversation dans les données de l'utilisateur n'est pas encore implémenté.

### Gérer l'historique de conversation

#### Se souvenir

Une fois l'historique de conversation créé il faut le charger dans le robot avec la méthode `charger_historique(historique_de_conversation : ConversationSummaryBufferMemory) (fr) - load_history(conversation_history : ConversationSummaryBufferMemory) (en)`.  
Ici, vous donnez donc au robot la capacité de se souvenir des interactions qu'il a eu avec l'utilisateur.

!!!Success "Charger un historique de conversation"
    ```python
    historique = robot.IA.cree_historique_conversation()
    robot.IA.charger_historique(historique)

    ou alors

    history = robot.AI.create_conversation_history()
    robot.AI.load_history(history)
    ```

!!!Warning
    Si un historique de conversation est déjà chargé et qu'un autre historique vient à être chargé l'ancien historique sera écrasé.

!!!Note
    Si l'historique n'est pas vide, le robot reprendra la discussion là où l'utilisateur l'avait arrêtée la dernière fois.

#### Effacer la mémoire

Si vous voulez changer de discussion ou bien effacer l'historique de la conversation vous pouvez utilisez la méthode `supprimer_historique() (fr) - delete_history() (en)`.

!!!Success "Supprimer l'historique de conversation"
    ```python
    robot.IA.supprimer_historique()

    ou alors

    robot.AI.delete_history()
    ```

A partir de ce moment là le robot n'aura plus de mémoire de conversation.

!!!Warning
    Pensez à recuperer et sauvegarder l'historique avant de le supprimer

#### Récupérer la mémoire du robot

Pour pouvoir sauvegarder l'historique de conversation (mémoire du robot), il faut pouvoir récupérer l'historique de conversation pour cela il faut utiliser la méthode `obtenir_historique_conversation() (fr) - get_current_conversation_history() (en)`.

!!!Success "Récupérer l'historique de conversation"
    ```python
    robot.IA.obtenir_historique_conversation()

    ou alors

    robot.AI.get_current_conversation_history()
    ```

Cette méthode renvoit la mémoire du robot permettant ainsi la sauvegarde de celle-ci.

## Exemple complet 1

```python
from pybot import Robot

robot = Robot()

robot.demarrer_module_IA()

robot.IA.demarrer_discussion()

while True:
    question = input("Vous : ")
    if question == "stop":
        robot.IA.arreter_discussion()
        break
    if question == "recommencer":
        robot.IA.supprimer_historique()
        continue # Permet de revenir au début de la boucle sans poser de question
    if question == "sauvegarder":
        historique = robot.IA.create_conversation_history()
        robot.IA.charger_historique(historique)
        continue # Permet de revenir au début de la boucle sans poser de question
    reponse = robot.IA.poser_question(question)
    print("Pybot : ", reponse)
```

!!!Warning
    L'appel à la fonction `input()` devra etre remplacé par la méthode permettant de récupérer les questions posées par l'utilisateur.  
    On pourra le remplacer par une zone de texte dans la fenêtre ou alors l'audio du micro.  

    De meme le print devra etre remplacé par la méthode permettant d'afficher les réponses du robot.
    On pourra le remplacer par un appel à la méthode afficher_texte() de la fenêtre ou autre.

## Les émotions du robot

Le robot peut avoir des émotions et des réactions.
Pour cela il faut utiliser la méthode `obtenir_emotion(phrase : str) (fr) - get_emotion(sentence : str) (en)`.
Cette méthode prend en paramètre une phrase (chaîne de caractère) et renvoit l'émotion que le robot exprime en fonction de celle-ci.
Si aucune émotion enregistrée ne correspond a la phrase, il reste Neutre.

!!!Success "Obtenir l'émotion du robot"
    ```python
    phrase = "Je suis content"
    emotion = robot.IA.obtenir_emotion(phrase)

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

robot.demarrer_module_fenetre()
robot.demarrer_module_IA()

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

    emotion = robot.IA.obtenir_emotion(phrase)
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
