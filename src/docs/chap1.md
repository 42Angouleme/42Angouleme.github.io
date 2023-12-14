# Chapitre 1: Un premier programme.

## 1. Pour demarrer nous avons besoin d'importer la bibliothèque et de démarrer le robot

Le programme doit toujours commencer par ces deux lignes de code.

!!! Success "Importer et activer le robot"
    ```python
    from pybot import Robot
    robot = Robot()
    ```
        

## 2. Lancer l'application web pour faire tourner la base de données.

Une des premières choses à faire est de lancer le serveur qui permettra d'accéder à l'application web et ainsi travailler avec la base de donnée, on utilise pour cela la méthode **demarrer_webapp**. 
Il est aussi possible de configurer le robot depuis un site web, par exemple pour ajouter des élèves à la base de données.
!!! Success "demarrer_webapp()"
    ```python
    robot.demarrer_webapp()
    ```

Le serveur web se lance et ne bloque pas le programme, on peut donc ensuite s'occuper de programmer le robot.

!!! info
    Le site sera accessible en local à l'adresse : http://127.0.0.1:5000

!!! note
    Il est possible de configurer le raspberry pi pour faire serveur et rendre le site accessible sur le réseau local pour ainsi se connecter à distance au robot.

!!! warning
    Pour terminer le serveur il faut taper dans le terminal la combinaison au clavier : **CTRL+C**.

## 3. Allumer l'écran pour démarrer l'affichage.

Il est ensuite important de démarrer l'affichage qui met en action le robot. La méthode **allumer_ecran** utilise deux paramètres, la **longueur** et la **hauteur** de la fenêtre qui correspond aux nombres de pixels horizontal et vertical. Ces deux paramètres sont optionnels, si aucun paramètre n'est donné (ou un seul), la fenetre aura pour taille 800 pixels de longueur et 600 pixels de hauteur.

!!! Success "allumer_ecran(longueur, hauteur)"
    ```python
    robot.allumer_ecran()
    ```
    ou bien
    ```python
    l = 1000
    h = 400
    robot.allumer_ecran(l, h)
    ```

## 4. Changer le titre de la fenêtre.

La méthode **changer_titre(titre)** change le titre de la fenêtre avec le paramètre **titre**.

!!! Success "changer_titre(titre)"
    ```python
    titre = "Mon Programme"
    robot.changer_titre(titre)
    ```

!!! warning "Une message d'erreur"
    Il est a noter qu'il important d'avoir allumé l'écran avant de pouvoir changer son titre. Des erreurs avec plusieurs méthodes peuvent survenir et il est utile de regarder dans le terminal le message d'erreur pour pouvoir ensuite réparer le programme.
    ```python
    robot.changer_titre("Mon super titre")
    robot.allumer_ecran()
    ```
    Dans le terminal:
    ```
    Erreur: Le titre doit être défini aprés création de l'écran.
    ```

## 5. Mettre à jour l'affichage de l'écran.

À chaque fois qu'une modification est faites (ex: un changement de titre, un nouveau bouton, un texte à afficher), il est important de mettre à jour l'affichage de l'écran. On utilise la méthode **dessiner_ecran**.

Idéalement, cette méthode est appelée dans une boucle afin de garder l'affichage à jour.

!!! Success "dessiner_ecran()"
    ```python
    robot.dessiner_ecran()
    ```

## 6. Passer l'affichage en plein écran.

Pour que l'affichage remplisse l'écran, on peut utiliser la méthode **plein_ecran(changer)** avec le paramètre changer ayant la valeur vrai (**True**) ou faux (**False**). 

!!! Success "plein_ecran(changer)"
    pour passer en plein écran
    ```python
    robot.plein_ecran(True)
    ```
    ou pour en sortir
    ```python
    robot.plein_ecran(False)
    ```

## 7. Faire dormir le robot.

Il est parfois utile de ralentir l'exécution du programme en lui faisant faire des pauses. La méthode **dort(secondes)** le permet, il suffit de passer en paramètre le nombre de secondes à attendre.

!!! Success "dort(secondes)"
    ```python
    secondes = 2
    robot.dort(secondes)
    ```

## Exemple 1: Un premier programme.

!!! warning
    Il est recommandé de ne pas copier l'exemple mais de chercher par vous même des utilisations possibles.

Nous verrons aprés comment maintenir le programme actif avec une boucle et des évènements. Mais pour le moment nous allons faire dormir le robot pour ralentir l'exécution du robot.

```python
from pybot import Robot
robot = Robot()

robot.changer_titre("bonjour,pybot!") # Erreur
robot.allumer_ecran()
robot.changer_titre("bonjour,pybot!")
robot.dessiner_ecran()
robot.dort(1)
robot.changer_titre("plein écran dans une seconde")
robot.dessiner_ecran()
robot.dort(1)
robot.plein_ecran(True)
robot.dessiner_ecran()
robot.dort(1)
robot.changer_titre("fin du programme dans une seconde")
robot.plein_ecran(False)
robot.dessiner_ecran()
robot.dort(1)
```
