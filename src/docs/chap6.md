# Chapitre 6: Parler au robot

## Discuter avec le robot

### Commencer à discuter avec le robot

Pour commencer une discussion avec le robot, il faut utiliser la méthode **demarrer_discussion()**.

!!! success
    ```python
    - robot.demarrer_discussion()
    ```

!!! warning
    Il faut toujours commencer une discussion avec le robot avant d'utiliser les méthodes suivantes.

### Arrêter de discuter avec le robot

Pour arrêter la discussion avec le robot, il faut utiliser la méthode **arreter_discussion()**.

!!! success
    ```python
    - robot.arreter_discussion()
    ```

!!! warning
    A partir de ce moment là le robot ne pourra plus vous répondre et il faudra recommencer la discussion avec **demarrer_discussion()**.

### Poser une question / parler au robot

Pour pouvoir parler au robot (poser des questions, donner des informations, ...), il faut utiliser la méthode **repondre_question(question)**.

!!! success
    ```python
    - robot.repondre_question(question)
    ```

Le robot répondra à la question posée en paramètre.
Cette fonction retourne la réponse du robot.

!!! info
    La réponse du robot apparaîtra dans le terminal. Quelques lignes de code supplémentaire permettront de récupérer la réponse pour la manipuler.
    
    Le robot peut prendre un certain temps de réflexion pour vous répondre pendant ce temps de réflexion le robot semblera être en pause (inutilisable). Il suffit simplement d'attendre sa réponse pour qu'il ne soit plus en pause (utilisable).

!!! warning
    Tant qu'aucun historique n'est chargé le robot est dépourvu de mémoire de précédents messages.

## La mémoire du robot

Comme dit précédemment si on ne donne pas de mémoire au robot, il ne se rappellera de rien entre les questions.

La méthode **creer_historique()** permet au robot de lui demander de garder en mémoire l'historique de la conversation à venir.

!!! success
    ```python
    - robot.creer_historique()
    ```

!!! note
    Il est préférable d'avoir un historique de conversation par utilisateur et aussi de sauvegarder l'historique de conversation dans les données de l'utilisateur correspondant.

### Gérer l'historique de conversation

#### Se souvenir

Une fois l'historique de conversation créé il faut le charger dans le robot avec la méthode **charger_historique(historique_de_conversation)**. Ici, vous donnez donc au robot la capacité de se souvenir des interactions qu'il a eues avec l'utilisateur.

!!! success
    ```python
    - robot.charger_historique(historique_de_conversation)
    ```

!!! warning
    Si un historique de conversation est déjà chargé et qu'un autre historique vient à être chargé l'ancien historique sera écrasé.

!!! note
    Si l'historique n'est pas vide, le robot reprendra la discussion là où l'utilisateur l'avait arrêtée la dernière fois.

#### Effacer la mémoire

Si vous voulez changer de discussion ou bien effacer l'historique de la conversation vous pouvez utilisez la méthode **supprimer_historique()**.

!!! success
    ```python
    - robot.supprimer_historique()
    ```

!!! warning
    Pensez à recuperer et sauvegarder l'historique avant de le supprimer

#### Récupérer la mémoire du robot

Pour pouvoir sauvegarder l'historique de conversation (mémoire du robot), il faut pouvoir récupérer l'historique de conversation pour cela il faut utiliser la méthode **recuperer_historique_de_conversation()**.

!!! success
    ```python
    - robot.recuperer_historique_de_conversation()
    ```

Cette méthode renvoit la mémoire du robot permettant ainsi la sauvegarde de celle-ci.

## Exemple 5 :

Voilà un exemple de fonction permettant la gestion de la discussion avec le robot

!!! warning
    Cela n'est qu'un exemple, il n'est pas parfait car par exemple l'entrée de l'utilisateur n'est pas effacée, le robot n'a pas de mémoire (historique de conversation), etc.

    Je vous conseille donc de vous en inspirer mais pas de le copier-coller.
    De plus, il manque toutes les parties (vu précédemment) nécessaires au fonctionnement du robot.

```python
def declencher_discussion(robot : Robot):
    global mettre_a_jour_affichage, discussion_commencer, text_area, bouton_question
    if bouton_question.est_actif():
        discussion_commencer = not discussion_commencer
        if discussion_commencer :
            robot.demarrer_discussion()
            bouton_question.ajouter_texte("Arreter la discussion")
        else :
            bouton_question.ajouter_texte("Poser question")
            robot.arreter_discussion()
        mettre_a_jour_affichage = True
    if discussion_commencer and text_area.est_actif() :
        user_entry = robot.ecrire(text_area)
        robot.repondre_question(user_entry)
```
