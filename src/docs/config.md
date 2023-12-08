# Configurer l'éditeur VS Code pour programmer le robot

## Configurer l'environnement python et installer les dépendances

```
git clone git@github.com:42Angouleme/initiation_python.git
cd initiation_python
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Ajouter un package python et mettre à jour le fichier requirements.txt

```
python3 -m pip install <package_name>
python3 -m pip freeze > requirements.txt
```

## Lancer le programme principal

```
python3 main.py
```

ou

```
chmod +x main.py
./main.py
```

## Pour préparer vscode

```
code --install-extension ms-python.python
code --install-extension MS-CEINTL.vscode-language-pack-fr
cd initiation_python
code main.py
```

# Cliquer sur l'icone extension


![width:800px](config/python1.png)


# Chercher python et installer


![width:800px](config/python2.png)


# Python est installé


![width:800px](config/python3.png)


# Ouvrir l'explorateur de fichiers


![width:800px](config/vscode0.png)


# Créer un nouveau fichier


![width:800px](config/vscode1.png)


# Nommer le fichier


![width:800px](config/vscode2.png)


# Écrire son code dans le fichier


![width:800px](config/vscode3.png)


# Lancer le programme


![width:800px](config/vscode4.png)

