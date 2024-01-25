# Chapitre 8: Le visage et les émotions du robot.

Dans cette section vous allez voir comment donner des émotions au robot.

## Trouver l'émotion d'un texte.

Pour donner une émotion au robot, il faut utiliser la méthode **emotion()**.

!!! success
    ```python
    robot.emotion(texte : str)
    ```

Cette méthode prend en paramètre du texte (chaîne de caractère) et renvoit l'émotion que le robot exprime en fonction de ce texte.
Si aucune émotion enregistrée ne correspond au texte, il reste Neutre.

!!! Exemple
    ```python
    chaine_de_caracteres = "Hier je me suis amusé au parc"
    emotion = robot.emotion(chaine_de_caracteres)
    print(emotion) # Affiche Amusement dans le terminal
    ```

!!! Note
    Voici la liste des émotions que le robot peut ressentir :
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
        - Dégout

## Mettre un visage sur une émotion

Pour récuperer le chemin vers l'image correspondant à une émotion, il faut utiliser la méthode **avoir_image_emotion()**

!!! success
    ```python
    robot.avoir_image_emotion(emotion : str)
    ```

Cette méthode renvoit un chemin vers l'image correspondant à l'émotion

!!! exemple
    ```python
    chaine_de_caracteres = "Hier je me suis amusé au parc"
    emotion = robot.emotion(chaine_de_caracteres)
    
    image_emotion = robot.avoir_image_emotion(emotion)
    robot.afficher_image(image_emotion)
    ```

!!! Note
    Vous pouvez changer l'image liée à une émotion. Pour cela il faut remplacer l'image située dans le fichier images/emotion par une nouvelle image.
    
    Par exemple, si vous voulez changer la tête que le robot fait quand il est content il faut remplacer l'image /image/emotion/amusement.png (donc la nouvelle image doit également s'appeler amusement.png).

## Pour afficher un visage, si les émotions correspondent à une image.

[voir documentation pour afficher une image](chap4.md)
