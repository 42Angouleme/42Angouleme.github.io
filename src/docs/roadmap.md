# Progression générale

> L'objectif est d'obtenir une librairie qui permettra aux élèves d'interagir avec lui par la voix, le texte et l’image. Une IA (conversationnelle) interagira avec eux. Ce robot aura pour fonction principale d'accueillir le public dans le Hall de l'établissement et pourrait par exemple, si entrainé avec les données du collège, répondre à des questions comme: *"Que mange t'on ce midi à la cantine ?"*.

Le projet se découpe en deux niveaux, la classe générale **Robot** qui doit avoir des méthodes accédant à toutes les fonctionnalités des modules de manière simple, correctement nommées et documentées (en français) pour l'utilisation par les élèves.

Les **modules**, avec leurs fonctionnalités plus bas niveau doivent aussi étre documenté pour que les étudiants de 42 puisse s'intégrer plus facilement et participer au développement.

## Liste des fonctionnalités de la classe Robot et leur avancement:

## fonctionnalitées à créer, commenter et documenter

* :one: commentaire attaché à la fonction dans le code
* :two: fonction documentée dans un chapitre et la référence

### part 1 - screen basics

- robot.demarrer_webapp() : :one::white_check_mark: , :two::white_check_mark:
- robot.allumer_ecran(longueur, hauteur) : :one::white_check_mark: , :two::white_check_mark:
- robot.changer_titre() : :one::white_check_mark: , :two::white_check_mark:
- robot.dessiner_ecran() : :one::white_check_mark: , :two::white_check_mark:
- robot.plein_ecran(changer) : :one::white_check_mark: , :two::white_check_mark:
- robot.dort() : :one::white_check_mark: , :two::white_check_mark:

### part 2 - loop and events

- robot.est_actif() : :one::white_check_mark: , :two::x:
- robot.eteindre_ecran() : :one::white_check_mark: , :two::x:
- robot.ajouter_evenement(touche, nom) : :one::x: , :two::x:
- robot.supprimer_evenement(touche) : :one::x: , :two::x:
- robot.verifier_evenements() : :one::x: , :two::x:

### part 3 - buttons, layout and theming

- robot.couleur_fond(couleur) : :one::x: , :two::x:
- robot.ajouter_bouton(longueur, hauteur, couleur, nom, fonction) : :one::x: , :two::x:
- robot.supprimer_bouton(nom) : :one::x: , :two::x:
- robot.ajouter_espace_de_texte(longueur, hauteur, couleur, nom) : :one::x: , :two::x:
- robot.afficher_texte(nom_espace_de_texte, texte) : :one::x: , :two::x:
- robot.supprimer_espace_de_texte(nom) : :one::x: , :two::x:

### part 4 - camera, photo and filters

### part 5 - card detection

### part 6 - talk to robot

### part 7 - robot is talking

### part 8 - robot face and emotions

### extra
- robot.message_erreur() : :one::x: , :two::x:
- robot.xxx() : :one::x: , :two::x:

## Liste des différent modules et leur avancement:

### Module écran
* Wrapper pygame et pygame_gui
* Visage minimaliste avec expressions. S’anime en cas de connexion ou réagit aux erreurs.
* Possibilité d'affichage de texte défilant des interactions, pouvant remplacer le speaker.
* Un application graphique (pygame GUI) client pour afficher le stream camera, des boutons, du texte ou des images depuis la base de données.

* Dès l’identification :
 * saluer, variable
 * déclencher les questions pré-enregistrées actives de la DB
 * échange libre

### Module caméra

* Reconnaissance (identification) via la caméra d’un élève grâce à son motif.

### Module webapp

* Permet de faire le backend pour travailler avec la base de donnée, propose aussi un interface client web pour aider à l'administration du robot.
* Un serveur web flask local avec base de données dans laquelle se
trouvent les élèves. Cette base de donnée contient a minima:
 * nom
 * prénom
 * image carte (chemin vers un dossier local)
 * année ou date de création (RGPD)
 * string: résumé du dernier échange pour des conversations filées

* Application web permettant :
    - CRUD : formulaire nom + prénom + image.
    - Avec bouton image qui déclenche une photo, en analyse la validité : carte valide (sens, présence d’une carte), et pas de match d’un motif existant.
    - Puis l’enregistre.
    - Modifier des champs existants.
    - Supprimer un utilisateur.
    - Lire le tableau des utilisateurs.
    - Page de logs (erreurs)

* DB question à poser avec fenêtre de temps (deux dates), avec une liste définie de réponses possibles : oui/non, ou une “enum” (chat gpt saura retranscrire la réponse de l’élève).
* Champs :
    * from
    * to
    * question
    * réponse valide
    * Liste<Réponse &élève>
* Liste des questions actives
* Liste des réponses à une question + nombre d’occurences de chaque
réponse

### Module IA

* Communiquer avec chatgpt

### Module Audio (Speaker)

* Text to speech. Le texte est l’output de l’IA vers speaker.
* Capable de réagir de manière adaptee au public, répondre à des questions. Réponses courtes.

### Module Microphone

* Speech to text. Capture du son et transformation en texte pour donner en input a l’IA.
* Partir d’un input (module microphone), préparer un prompt pour obtenir la réponse qui servira d’output (module speaker et module écran).
* Limitations des tokens, réponses courtes. Des sujets de discussions.
* Donner de la donnée concernant le college en apprentissage au modèle. (Par exemple renseigner sur les horaires cantines.)
* Actif sur commande (fonction listen on/off), capable d’écouter la voix en isolant les bruits parasites et transcrire le contenu en texte.

## Liste des différent matériel et fonctionnement :

* Raspberry PI alimente un microphone, une camera, des hauts-parleurs

    - Raspberry 4B 4GO
    - 2 cartes micro SD 64 GO
    - écran tactile LCD tactile
    - câble HDMI vers micro-hdmi
    - alimentation 48W
    - heat sinks
    - camera v3
    - camera HQ
    - objectif camera HQ
    - Nappe câble
    - mini haut parleur usb
    - microphone usb
