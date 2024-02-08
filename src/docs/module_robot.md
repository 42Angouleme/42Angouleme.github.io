# Module Robot

Et oui, le robot peut être considéré comme un module à part entière vu qu’il a ses propres méthodes qui lui sont attachées, même si vous verrez qu’il est impossible de les utiliser à proprement parler sans utiliser le module Fenêtre.

Pour utiliser le module Robot on vas directement utiliser l’objet Robot que l’on crée au début

```python
robot = Robot()
    ^ celui-ci
```

Ce module vous donne accès à des méthodes permettant la gestion globale du programme (début du programme, sortie du programme), mais aussi à une première manière de gérer les événements (interaction utilisateur -> robot).

!!!warning
    Il est fortement conseillé d’avoir au moins ouvert la fenêtre “voir module fenêtre — window” avant de continuer à lire cette section.

## Démarrer le robot

Une fois le robot créé (démarré), il passe dans l’état actif ; dans cet état, le robot peut être utilisé lui et tous ses modules.

!!!Success "Robot()"
    ```python
    from pybot import Robot
    robot = Robot()
    ```

## Éteindre le robot

Si l'on veut passer le robot dans l’état inactif (ce qui équivaut à éteindre le robot), on utilise la méthode `desactiver() (fr) - deactivate() (en).`

!!!Success "desactiver() - deactivate()"
    ``` python
    robot.desactiver()

    ou alors

    robot.deactivate()
    ```

Après l’appel de cette méthode, le robot change son état en inactif (il deviendra donc inutilisable).

## Vérifier l’état du robot

On peut obtenir l’état du robot grâce à la méthode `est_actif() (fr) - is_active() (en)`.

!!!Success "est_actif() - is_active()"
    ```python
    robot.est_actif()

    ou alors

    robot.is_active()
    ```

!!!Note
    **est_actif** renvoi True si le robot est actif sinon il renvoie False.

Cette méthode peut être utile à l’élaboration d’une boucle **While** qui déclencherait des actions tant que le robot est actif.

```python
Exemple :

while robot.est_actif() :
    robot.fenetre.actualise_affichage()
```

## Faire dormir le robot

Il est parfois utile de ralentir l'exécution du programme en lui faisant faire des pauses. La méthode `dort(secondes : int) (fr) - sleep(secondes : int) (en)` le permet, il suffit de passer en paramètre le nombre de secondes à attendre.

!!!Success "dort(int) - sleep(secondes)"
    ```python
    secondes = 2
    robot.dort(secondes)

    ou alors

    secondes = 2
    robot.sleep(secondes)
    ```

## Les attributs du robot

Le robot possède un moyen de contenir les boutons et les zones de texte que l’on peut créer avec le module Fenêtre.

Voir la documentation du module [fenêtre](module_window.md) pour plus d'informations.  
Avec celle des [boutons](button.md) et des [zones de texte](text_area.md) aussi.

### Ajouter un bouton aux attributs du robot

Pour ajouter un bouton aux attributs du robot il faut suivre les étapes suivantes :

```python
boutons = robot.attributs.boutons # On récupère l'endroit où sont stockés les boutons dans le robot
boutons.nom_du_bouton = robot.fenetre.creer_bouton("nom_du_bouton", 100, 100, 100, 100) # On crée un bouton et on l'ajoute aux attributs du robot.
```

!!!Note
    nom_du_bouton est le nom que l’on veut donner au bouton.  
    C’est ce nom qui sera utilisé pour accéder au bouton depuis les attributs du robot.
    Veillez à ne pas mettre d’espace dans le nom du bouton et gardez le nom simple.

### Accéder à un bouton depuis les attributs du robot

Pour accéder à un bouton depuis les attributs du robot il faut suivre les étapes suivantes :

```python
boutons = robot.attributs.boutons # On récupère l'endroit où sont stockés les boutons dans le robot.
boutons.nom_du_bouton # On accède au bouton grace à son nom.
```

!!!Note
    nom_du_bouton est le nom que l’on a donné au bouton lors de sa création.
    boutons.nom_du_bouton est un objet de type bouton sur lequel on peut appliquer les méthodes liées au [bouton](button.md).

### Ajouter une zone de texte aux attributs du robot

Pour ajouter une zone de texte aux attributs du robot il faut suivre les étapes suivantes :

```python
zones_de_texte = robot.attributs.zones_de_texte # On récupère l'endroit où sont stockées les zones de texte dans le robot.
zones_de_texte.nom_de_la_zone_de_texte = robot.fenetre.creer_zone_de_texte("nom_de_la_zone_de_texte", 100, 100, 100, 100) # On crée une zone de texte et on l'ajoute aux attributs du robot.
```

!!!Note
    nom_de_la_zone_de_texte est le nom que l’on veut donner à la zone de texte.  
    C’est ce nom qui sera utilisé pour accéder à la zone de texte depuis les attributs du robot.
    Veillez à ne pas mettre d’espace dans le nom de la zone de texte et gardez le nom simple.

### Accéder à une zone de texte depuis les attributs du robot

Pour accéder à une zone de texte depuis les attributs du robot il faut suivre les étapes suivantes :

```python
zones_de_texte = robot.attributs.zones_de_texte # On récupère l'endroit où sont stockées les zones de texte dans le robot.
zones_de_texte.nom_de_la_zone_de_texte # On accède à la zone de texte grace à son nom.
```

!!!Note
    nom_de_la_zone_de_texte est le nom que l’on a donné à la zone de texte lors de sa création.
    zones_de_texte.nom_de_la_zone_de_texte est un objet de type zone de texte sur lequel on peut appliquer les méthodes liées à la [zone de texte](text_area.md).

### Autre

Ces attributs sont utiles pour stocker les boutons et les zones de texte que l’on crée avec le module Fenêtre.
Mais ils peuvent aussi être utilisés pour stocker d’autres objets, variables, etc.

Pour cela, il suffit de créer un attribut dans l’objet attributs du robot.

```python
robot.attributs.nom_de_l_attribut = "valeur de l'attribut"
```

pour ensuite y accéder avec

```python
robot.attributs.nom_de_l_attribut
```

## Interaction avec l’utilisateur

En plus de tout cela, le robot offre une première manière assez rudimentaire pour gérer les interactions avec l’utilisateur.

On appelle cela **les événements**.

### Créer un évènement

Un évènement est une action sur le clavier associée à un nom d'évènement. Nous créons un nouvel évènement avec la méthode `ajouter_evenement(touche : str, nom : str) (fr) - add_event(key : str, name : str) (en)` en lui passant en paramètre la touche à laquelle on veut associer l’événement et le nom que l’on veut donner à celui-ci.

!!!Success "Ajouter un évènement"
    ```python
    robot.ajouter_evenement("echap", "stop")

    ou alors

    robot.add_event("echap", "stop")
    ```

!!! info
    Voir la [référence](ref.md) pour voir une liste des touches possible, par exemple la touche du clavier **a** s'appelera **"a"**. À noter, les touches qui se nomment **"espace"** et **"echap"** pour la barre d'espace et la touche d'échappement.

### Vérifier un évènement

Une fois un évènement enregistré, il faut vérifier si l’événement se produit ou non.

Pour cela, on a la méthode `verifier_evenements() (fr) - check_events() (en)` .

!!!info
    La méthode retourne une liste avec les évènements qui viennent d'être exécutés. Il est possible ensuite d'utiliser une vérification avec if… in ... : comme dans l'exemple ci-dessous.

!!!Success "Vérifier les évènements"
    ```python
    evenements = robot.verifier_evenements("echap", "stop")
    if "stop" in evenements:
        print("stop")

    ou alors

    evenements = robot.check_events("echap", "stop")
    if "stop" in evenements:
        print("stop")
    ```

### Supprimer un évènement

Si on ne veut plus qu’un évènement soit vérifié, il faudra le supprimer.

Pour cela, on a la méthode `supprimer_evenement(nom : str) (fr) — delete_event(nom : str) (en)` en lui passant le nom de l’événement que l’on veut supprimer..

!!!Success "Supprimer un évènement"
    ```python
    robot.supprimer_evenement("stop")

    ou alors

    robot.delete_event("stop")
    ```

!!!Warning
    Si plusieurs touches sont attribuées au même évènement, elles seront toutes supprimées de la liste des évènements.

from pybot import Robot

## Exemple 2: Utiliser des évènements

!!! warning
    Il est recommandé de ne pas copier l'exemple mais de chercher par vous même des utilisations possibles.

!!! info
    Le robot final n'utilisera pas de clavier mais simplement une intéraction par la voix et par le touché sur écran. Ces évènements par clavier servent principalement à l'apprentissage du code python. Il s'agit d'une période de transition.

```python

robot = Robot()

long = 1024
haut = 800

robot.demarrer_module_fenetre(long, haut)
robot.fenetre.ouvrir_fenetre()

robot.ajouter_evenement("echap", "stop")
while robot.est_actif():
    evenements = robot.verifier_evenements()
    if "stop" in evenements:
        robot.desactiver()
    robot.fenetre.actualiser_affichage()
```
