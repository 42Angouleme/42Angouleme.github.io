# Chapitre 5: Reconnaissance d'un élève par sa carte.

## 1. Détecter une carte

La méthode **robot.detecter_carte()** permet de récupérer l'identité de la personne sous la forme d'une chaîne de caractères : "`Nom Prénom`".

Si une carte est invalide, n'appartient à personne ou bien qu'aucune carte n'est visible pour la caméra, alors la méthode retournera une chaîne de caractères vide: "` `".

!!! warning
	Si la fonction est appelée alors que l application web n' est pas lancée ou bien que la caméra n' est pas allumée alors la fonction retournera aussi une chaine vide: "` `".

!!! Success
	```python
	robot.demarrer_webapp()
	# [...]
	nom_eleve = robot.detecter_carte()
	print(nom_eleve)
	```
	Si une carte valide est présente et que la caméra est allumée alors ce morceau de code affichera dans le terminal le nom de la personne.

## 2. Créer/ Fermer une session
```python
- robot.creer_session(nom_eleve)
```
```python
- robot.fermer_session()
```

## 3. Vérifier une session
```python
- robot.verifier_session()
```
