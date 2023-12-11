# Chapitre 2: Une boucle et des évènements.

## 1. Boucle et contrôle de l'activité du robot.

À l'initiation du robot, il est possible de vérifier ce status avec la méthode **robot.est_actif()** qui peut alors servir de vérification dans une boucle **while** et ainsi maintenir le programme en cours d'exécution.

!!! note 
    Au lancement du programme **robot.est_actif()** retourn vrai (True).
    Il est possible de rendre le robot inactif avec la méthode **robot.desactiver()** qui fera simplement retourner Faux (False) à la méthode **robot.est_actif()**.

!!! Success "Activité du robot"
    ```python
    while robot.est_actif():
        robot.dort(2)
        robot.desactiver()
    ```

## 2. Éteindre l'écran et terminer le programme.

La méthode **robot.eteindre_ecran** permet d'arrêter l'affichage de l'écran.

!!! note 
    Le status du robot devient inactif, la méthode **robot.est_actif()** retournera alors False.

!!! Success "Éteindre écran"
    ```python
    while robot.est_actif():
        robot.dort(2)
        robot.eteindre_ecran()
    ```

!!! note
    En général, il est préférable d'utiliser **robot.eteindre_ecran** car le programme s'arrêtera plus proprement qu'en sortant simplement de la boucle avec **robot.desactiver**.

# 3. Créer un évènement.

!!! note
    Un évènement est une action sur le clavier associée à un nom d'évènement. Nous créons un nouvel évènement avec la méthode **ajouter_evenement(touche, nom)**.

!!! Success "Ajouter un évènement"
    ```python
    robot.ajouter_evenement("echap", "stop")
    ```

!!! info
    Voir la référence pour voir une liste des touches possible, par exemple la touche du clavier **a** s'appelera **"a"**. À noter, les touches qui se nomment **"espace"** et **"echap"** pour la barre d'espace et la touche d'échappement.

# 4. Vérifier un évènement.

Nous pouvons récupérer les évènements dans une boucle en faisant appel à la méthode **robot.verifier_evenements()**.

!!! info
    La méthode retourne une liste avec les évènements qui viennent d'être executés. Il est possible ensuite d'utiliser une vérification avec if ... in ...: comme dans l'exemple si dessous.

!!! Success "Vérifier les évènements."
    ```python
        evenements = robot.verifier_evenements("echap", "stop")
        if "stop" in evenements:
            print("stop")
    ```

# 5. Supprimer un évènement.

Il est ensuite possible de supprimer un évènement avec la méthode **robot.supprimer_evenement(nom)**.

!!! Success "Supprimer un évènement."
    ```python
        robot.supprimer_evenement("stop")
    ```

!!! warning
    Si plusieurs touches sont attribuées au même évènement, elles seront toutes supprimées de la liste des évènements.

## Exemple 2: Utiliser des évènements.

!!! info
    Le robot final n'utilisera pas de clavier mais simplement une intéraction par la voix et par le touché sur écran. Ces évènements par clavier servent principalement à l'apprentissage du code python. Il s'agit d'une période de transition.

!!! warning
    Pour travailler avec cet exemple, pensez à garder un oeil sur le terminal pour voir l'affichage des fonctions print.

```python
from pybot import Robot
robot = Robot()

long = 1024
haut = 800

def ecrire_nom_evenement(event_name):
    print("L'évènement est:", event_name)

def preparer_robot():
    robot.allumer_ecran(long, haut)
    robot.changer_titre("Bonjour!")
    robot.ajouter_evenement("echap", "stop")
    robot.ajouter_evenement("B", "banane")
    robot.ajouter_evenement("C", "carotte")
    print("Vous pouvez maintenant utiliser Echap et C")

preparer_robot()

nom = "poireau"
while robot.est_actif():
    evenements = robot.verifier_evenements()    
    if "stop" in evenements:
        robot.eteindre_ecran()
    elif "carotte" in evenements:
        print("Vous pouvez maintenant utiliser P")
        ecrire_nom_evenement("carotte")
        robot.supprimer_evenement("carotte")
        robot.ajouter_evenement("P", "poireau")
    elif nom in evenements:
        ecrire_nom_evenement(nom)
        if nom == "poireau":
            print("Vous pouvez maintenant utiliser B")
            robot.supprimer_evenement("poireau")
            nom = "banane"
        elif nom == "banane":
            print("Echap ne permet plus de quitter, il faut maintenant utiliser Q")
            robot.supprimer_evenement("stop")
            robot.supprimer_evenement("banane")
            robot.ajouter_evenement("Q", "stop")
    robot.dessiner_ecran()
```