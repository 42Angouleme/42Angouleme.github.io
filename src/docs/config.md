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


# Configurer la librairie pybot sur Debian (La distribution linux sur le raspberry pi)


# Démo interractives avec JupyterLab

### Setup

Setup à ne faire qu'une fois. Placez-vous à la racine du projet avec l'environnement virtuel activé et lancez la commande suivante.

```sh
ipython profile create && echo "c.InteractiveShellApp.exec_lines = ['import sys; sys.path.append(\"$(pwd)\")']" >> ~/.ipython/profile_default/ipython_config.py
```

> Celà permet au notebook de trouver les modules locaux à notre package

La dernière ligne du fichier `~/.ipython/profile_default/ipython_config.py` devraient maintenant contenir:

```python
c.InteractiveShellApp.exec_lines = ['import sys; sys.path.append("<chemin_vers_robot-python>")']
```

### Lancer les démo

```sh
jupyter lab notebooks/sommaire.ipynb
```

> Les notebooks [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/index.html) combinent descriptions Markdown et sections de code interractif.
