# Chapitre 6: Zone de texte / Entrée Utilisateur

## Récupérer les entrées utilisateur

### Zone de texte

#### Créer une zone de texte

Créer et retourner une zone texte qui peut être affichée et vérifiée plus tard

!!! success
    ```python
    - creer_zone_texte(longueur, hauteur, position_x, position_y, couleur)
    ```

Les paramètres attendus sont :  
 _ la longueur et la hauteur de la zone de texte.  
 _ la position x et y de la zone de texte (son coin en haut à gauche).  
 \* la couleur de la zone de texte.

!!! note
    La couleur est au format (R, G, B), comme vu avec les boutons.

!!! warning "Les positions x et y dans la fenêtre"
    Les coordonnées sur un écran informatique sont généralement définies à partir du coin supérieur gauche.
    Le **premier pixel** qui se trouve en haut à gauche de la fenêtre correspond aux coordonnées **x = 0 et y = 0**.
    Alors que le dernier pixel en bas à droite correspond à la coordonnée _x_ maximale et à la coordonnée _y_ maximale.

Par exemple, si la fenêtre fait 300 pixels de long et 200 pixels de haut : le **dernier pixel** a les coordonnées **x = 299 et y = 199**.

![Les coordonnées en informatique](coordinates.jpg)

#### Afficher la zone de texte

Pour afficher la zone de texte dans la fenêtre principale.

!!! success
    ```python
	zone_texte.afficher()
	```

!!! note
    La méthode s'applique sur la zone de texte (et non le robot comme avec les boutons).

#### Vérifier le clic sur la zone de texte

Pour vérifier que la zone de texte soit active ou non, une valeur vraie (True) ou fausse (False) est retournée, voir l'exemple.

!!! success
    ```python
	zone_texte.est_actif()
	```

Cela fonctionne comme avec les boutons.

#### Écrire dans la zone de texte

Une fois la zone de texte active, il faut faire appel à la méthode **ecrire()** pour pouvoir écrire dans la zone de texte.

!!! success
    ```pyhton
    robot.ecrire(self, zone_texte)
    ```

Cette fonction renvoie le texte après que l'utilisateur ait quitté la zone de texte.

!!! warning
    Lorsque l'utilisateur écrit, le robot est mis en pause tant que l'utilisateur n'a pas quitté la zone d'écriture en cliquant en dehors de celle-ci ou alors en tapant sur la touche _entrée_.

!!! note
    Cette méthode est spéciale : elle s'applique sur le robot et elle prend en paramètre la zone de texte active.

### Récupérer l'entrée utilisateur

Une fois que l'utilisateur a terminé d'entrer son texte, vous pouvez récupérer cette entrée grâce aux méthodes **recuperer_texte()** ou **effacer_texte()**.

!!! success
    ```pyhton
    zone_texte.recuperer_texte()
    ```

Cette fonction renvoit le texte contenu dans la zone de texte sans l'effacer.

!!! success
    ```pyhton
    zone_texte.effacer_texte()
    ```

Cette fonction renvoit le texte contenu dans la zone de texte en l'effaçant.

!!! warning
    Cette fonction efface le texte contenu dans la zone de texte, le texte n'est donc plus récupérable après.

### Personnaliser la zone de texte

Si vous voulez modifier la taille d'écriture du texte dans la zone de texte vous pouvez utiliser la méthode **modifier_taille_police(taille)**.

!!! success
    ```pyhton
    zone_texte.modifier_taille_police(taille)
    ```

!!! info
    Si vous ne mettez aucun paramètre, cela réinitialisera la taille d'écriture.

Si vous voulez modifier la couleur du texte dans la zone de texte vous pouvez utiliser la méthode **modifier_couleur_police(couleur)**.

!!! success
    ```pyhton
    zone_texte.modifier_couleur_police(couleur)
    ```

!!! info
    Si vous ne mettez aucun paramètre, cela réinitialisera la couleur du texte.

!!! note
    La couleur est au format variable = (R, G, B), comme vu avec les boutons.
