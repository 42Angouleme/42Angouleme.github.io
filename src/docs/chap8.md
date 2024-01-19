# Chapitre 8: Le visage et les émotions du robot.

Dans cette section vous allez voir comment donner des émotions au robot.

## Trouver l'émotion d'un texte.

Pour donner une émotion au robot, il faut utiliser la méthode **emotion()**.

!!! success
    ```python
    robot.emotion(texte : str)
    ```

Cette méthode prend en paramètre une chaîne de caractère (texte) et renverra l'émotion que le robot exprime en fonction de la chaîne de caractère passée en paramètre
Si aucune des émotions qu'il connaît ne correspond à la chaîne de caractère il reste Neutre.

!!! Exemple
    ```python
    chaine_de_character = "Hier je me suis amuser au parc"
    emotion = robot.emotion(chaine_de_charactere)
    print(emotion) # Affiche Amuser dans le terminal
    ```

!!! Note
    Le robot peut exprimer toutes ces émotions :
    Neutre, Amour, Amuser, Anxiete, Celebration, Chagrin, Colere, Confusion, Content, Contrariete, Deception, Degout, Desespoir, Embarras, Emerveillement, Enthousiasme, Etonnement, Fatigue, Fierte, Frustration, Fureur, Incomprehension, Inquietude, Ironie, Joie, Mefiance, Peur, Reflexion, Soulagement, Supplique, Surprise, Tristesse.

## Mettre un visage sur une émotion

Pour recuperer le chemin vers l'image de la tête du robot par rapport à une emotion, il faut utiliser la méthode **avoir_image_emotion()**

!!! success
    ```python
    robot.avoir_image_emotion(emotion : str)
    ```

Cette méthode renvoi un chemin vers l'image correspondant à l'emotion

!!! exemple
    ```python
    chaine_de_character = "Hier je me suis amuser au parc"
    emotion = robot.emotion(chaine_de_charactere)
    
    image_emotion = robot.avoir_image_emotion(emotion)
    robot.afficher_image(image_emotion)
    ```

!!! Note
    Vous pouvez changer l'image liée au robot pour cela il faut remplacer l'image situer dans le fichier images/emotion par une nouvelle image.
    
    Par exemple, si vous voulez changer la tête que le robot fait quand il est content il faut remplacer l'image /image/emotion/content.png par une nouvelle image qui doit obligatoirement s'appeler content.png .

## Pour afficher un visage, si les émotions correspondent à une image.

[voir documentation pour afficher une image](/chap4)