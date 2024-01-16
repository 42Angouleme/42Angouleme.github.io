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
    Le site sera accessible localement, à l'adresse : http://127.0.0.1:5000

!!! note
    Il est possible de configurer le raspberry pi pour faire serveur et rendre le site accessible sur le réseau local pour ainsi se connecter à distance au robot.

!!! warning
    Pour arreter le serveur il faut taper dans le terminal la combinaison au clavier : **CTRL+C**.

## 3. Créer fenêtre pour démarrer l'affichage.

Il est ensuite important d'ouvrir une fenêtre qui permet d'interagir avec le robot. La méthode **creer_fenetre** utilise deux paramètres, la **longueur** et la **hauteur** de la fenêtre qui correspondent aux nombres de pixels horizontaux et verticaux. Ces deux paramètres sont optionnels. Si aucun paramètre n'est donné (ou un seul), la fenêtre aura pour taille 800 pixels de longueur et 600 pixels de hauteur.

!!! Success "creer_fenetre(longueur, hauteur)"
    ```python
    robot.creer_fenetre()
    ```
    ou bien
    ```python
    l = 1000
    h = 400
    robot.creer_fenetre(l, h)
    ```

## 4. Changer le titre de la fenêtre.

La méthode **changer_titre(titre)** change le titre de la fenêtre avec le paramètre **titre**.

!!! Success "changer_titre(titre)"
    ```python
    titre = "Mon Programme"
    robot.changer_titre(titre)
    ```

!!! warning "Une message d'erreur"
    Il est a noter qu'il est important d'avoir démarré la fenêtre avant de pouvoir changer son titre.
    Des erreurs avec plusieurs méthodes peuvent survenir et il est utile de regarder dans le terminal le message d'erreur pour pouvoir ensuite réparer le programme.
    `python
        robot.changer_titre("Mon super titre")
        robot.creer_fenetre()
        `
    Dans le terminal:
    `Erreur: Le titre doit être défini aprés création de la fenêtre.`

## 5. Mettre à jour l'affichage de la fenêtre.

À chaque fois qu'une modification est faite (ex: un changement de titre, un nouveau bouton, un texte à afficher), il est important de mettre à jour l'affichage de la fenêtre. On utilise la méthode **actualiser_affichage**.

Idéalement, cette méthode est appelée dans une boucle afin de garder l'affichage à jour.

!!! Success "actualiser_affichage()"
    ```python
    robot.actualiser_affichage()
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
robot.creer_fenetre()
robot.changer_titre("bonjour,pybot!")
robot.actualiser_affichage()
robot.dort(1)
robot.changer_titre("plein écran dans une seconde")
robot.actualiser_affichage()
robot.dort(1)
robot.plein_ecran(True)
robot.actualiser_affichage()
robot.dort(1)
robot.changer_titre("fin du programme dans une seconde")
robot.plein_ecran(False)
robot.actualiser_affichage()
robot.dort(1)
```
