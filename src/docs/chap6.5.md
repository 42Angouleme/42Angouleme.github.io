# Chapitre 6: Zone de texte / Entrée Utilisateur

## Récupérer les entrées utilisateur

### Zone de texte

#### Créer une zone de texte

Créer et retourner une zone texte qui peut être affiché et vérifié plus tard

!!! success
    ```python
    - creer_zone_texte(longueur, hauteur, position_x, position_y, couleur)
    ```

Les paramètres attendus sont :  
    * la longueur et la hauteur de la zone de texte.  
    * la position x et y du de la zone de texte (son coin en haut à gauche).  
    * la couleur du de la zone de texte.

!!! note
    La couleur est au format variable = (R, G, B), comme vu avec les boutons.

!!! warning "Les positions x et y sur l'écran"
    Les coordonnées sur un écran informatique sont généralement définies à partir du coin supérieur gauche.  
    Le **premier pixel** qui se trouve en haut à gauche correspond aux coordonnées **x = 0 et y = 0**.  
    Alors que le dernier pixel en bas à droite correspond à la coordonnée x maximale et à la coordonnée y maximale.  
    Par exemple, si l'écran fait 300 pixels de long et 200 pixels de haut. Le **dernier pixel** a les coordonnées **x = 299 et y = 199**.

![Les coordonnées en informatique](coordinates.jpg)

#### Afficher la zone de texte

Pour afficher la zone de texte dans la fenêtre principale.

!!! success
    ```python
	zone_texte.afficher()
	```

!!! note
    La méthode s'applique sur la zone de texte (et non le robot comme avec les boutons).

#### Vérifier le clique sur la zone de texte

Pour vérifier que la zone de texte est cliqué ou non, une valeur vraie (True) ou fausse (False) est retournée, voir l'exemple.

!!! success
    ```python
	zone_texte.verifier_contact()
	```

Cela fonctionne comme avec les boutons

#### Écrire dans la zone de texte

Une fois la zone de texte déclenchée, il faut faire appelle à la méthode **ecrire()** pour pouvoir écrire dans la zone de texte.

!!! success
    ```pyhton
    robot.ecrire(self, zone_texte)
    ```

Cette fonction renvoie le texte après que l'utilisateur ait quitté la zone de texte.

!!! warning
    Lorsque l'utilisateur écrit, le reste du robot est mise en pause tant que l'utilisateur n'a pas quitté la zone d'écriture en cliquant en dehors de celle-ci ou alors en tapant sur Entrée.

!!! note
    Cette méthode est un peu spéciale car elle s'applique sur le robot et elle prend en paramètre la zone de texte touchée.

### Récupérer l'entrée utilisateur

Une fois que l'utilisateur à fini d'entrer son texte, vous pouvez avoir envie de gérer cette entrée en la récupérant pour cela il y a les méthode **renvoi_texte()** ou **effacer_texte()**.

!!! success
    ```pyhton
    zone_texte.renvoi_texte()
    ```

Cette fonction renvoie le texte contenue de la zone de texte sans l'effacer.

!!! success
    ```pyhton
    zone_texte.effacer_texte()
    ```

Cette fonction renvoie le texte contenue de la zone de texte en l'effaçant.

!!! warning
    Cette fonction efface le texte contenu dans la zone de texte, le texte n'est donc plus récupérable après.

### Personnaliser la zone de texte

Si vous voulez modifier la taille d'écriture du texte dans la zone de texte vous pouvez utiliser la méthode **modifier_taille_ecriture(taille)**.

!!! success
    ```pyhton
    zone_texte.modifier_taille_ecriture(taille)
    ```

!!! info
    Si vous ne mettez aucun paramètre, cela réinitialisera la taille d'écriture.

!!! note
    Il est mieux que la taille d'écriture reste petite.

Si vous voulez modifier la couleur du texte dans la zone de texte vous pouvez utiliser la méthode **modifier_couleur_ecriture(couleur)**.

!!! success
    ```pyhton
    zone_texte.modifier_couleur_ecriture(couleur)
    ```

!!! info
    Si vous ne mettez aucun paramètre, cela réinitialisera la couleur du texte.

!!! note
    La couleur est au format variable = (R, G, B), comme vu avec les boutons.
