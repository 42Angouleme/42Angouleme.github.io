# Chapitre 5: Reconnaissance d'un élève avec sa carte.

## Introduction

Tout au long de cette partie on va être ammené à utiliser des seuil de détection.
Un seuil de détection est une valeur comprise entre **0.00** et **1.00**.
Dans notre cas, le seuil sera utiliser pour comparer des images:

- plus le score sera proche de 1.00 plus les images se ressembleront.<br>
- plus on se rapproche de 0.00 plus les images sont différentes.

Les deux seuils qui vont nous intéresser dans cette parties sont:

- **seuil_minimal**: valeur permettant de sélectionner une carte comme probablement la bonne.
- **seuil_arret_recherche**: valeur permettant de définir une carte comme la bonne (si cette valeur est atteinte, la fonction retournera cette carte)

!!! Note
    Le code de détection de carte ne donnera jamais 1.00, car même s' il s agit de la même image, l' ordinateur va prendre en compte:
    la lumière, la position, l inclinaison de la carte par rapport à la caméra...

!!! warning
    Plus on prend un score d' arrêt de recherche:<br>
    - bas: plus on a de chances de mal interpréter les cartes.<br>
    - haut: moins on detectera de carte.


## Connexion/ Deconnexion

### Connaitre le statut de connexion

Afin de savoir si une personne est connecté à l application on peut utiliser:
```python
robot.verifier_session()
```

### Se dé/ connecter

Pour se connecter au robot avec une carte il faut appeler la fonction suivante:

```python
# Ici les seuils sont optionnels
robot.connecter(seuil_minimal, seuil_arret_recherche)
```

!!! warning
	Si la fonction est appelée alors que l application web n' est pas lancée ou bien que la caméra n' est pas allumée alors la fonction ne marchera pas.

... Et pour se déconnecter:
```python
robot.deconnecter()
```

## Créer/ Supprimer un compte utilisateur

### Créer une session

Pour créer un utilisateur, nous devons utiliser:

```python
robot.creer_utilisateur(prenom, nom, carte)
```

!!! Note
    La carte en paramètre de la méthode créer_utilisateur(prenom, nom, **carte**) doit être une image récupérée avec [robot.detecter_carte(...)](#recuperer-la-carte-detectee-a-lecran)

!!! Warning
    La personne qui vient de créer son compte ne sera pas connecté, il faut appeler la méthode **Robot.connecter()**

### Supprimer une session

Pour supprimer un utilisateur, il faut qu' il se connecte, puis appeler la fonction:
```python
robot.supprimer_utilisateur()
```

## Methodes utiles liées aux cartes et sessions

### Récupérer les informations de la personne connectée

Pour récupérer un objet contenant le nom et le prénom de la personne conmnectée.

```python
robot.recuperer_utilisateur_connecte()
```

!!! Success
    ```python
    if robot.verifier_session():
        utilisateur_connecte = robot.recuperer_utilisateur_connecte()
        print("Le prenom de la personne connectée est:", utilisateur_connecte.prenom)
        print("Le nom de la personne connectée est:", utilisateur_connecte.nom)
    ```
    Ce code permet d' afficher dans le terminal le prenom et le nom de l' utilisateur.

### Récuperer la carte detectée à l'écran

Pour avoir l' image de la carte detectée à l' écran s'il y en a une, on peut utiliser cette fonction:

```python
# Ici les seuils sont optionnels
robot.detecter_carte(seuil_minimal, seuil_arret_recherche)
```

!!! Warning
    Cette fonction retourne l'image qui n appartient pas selon le programme à un utilisateur déjà connu.


### Afficher la carte detectée

Popur afficher à l' écran l'image de la carte détectée juste avant on doit utiliser:
```python
robot.afficher_carte_detectee(carte, position_x, position_y)
```

!!! Success
    ```python
    carte = robot.detecter_carte()
    robot.afficher_carte_detectee(carte, 42, 42)
    ```
    Cette simple implementation de la méthode **afficher_carte_detectee()** va mettre à l' écran à la position (42, 42) la carte détectée, si il en a trouvé à l' écran.
