# Progression générale

> L'objectif est d'obtenir une bibliothèque composée de modules dont l'utilisation combinée permet d'interagir avec un bot (épaulé par une IA conversationnelle) par la voix, le texte ou l’image.
>
> Le premier cas d'usage prévu est l'assemblage d'un robot : un programme faisant appel à cette bibliothèque allié à une enveloppe physique et des composants variés : caméra, haut-parleurs, microphone, écran notamment.
> Ce robot aura pour fonction principale d'accueillir des collégiens dans le hall de l'établissement et pourrait par exemple, si entrainé avec les données du collège, répondre à des questions comme: _"Dans quelle salle se déroule le cours de la 3e B dans 10 minutes ?"_.

Le projet se découpe en deux niveaux : la classe générale **Robot** qui doit avoir des méthodes accédant à toutes les fonctionnalités des modules de manière simple, correctement nommées et documentées (en français) pour une utilisation par les élèves.

Les **modules**, avec leurs fonctionnalités plus bas niveau doivent aussi être documentés pour que les étudiants de 42 puissent s'intégrer plus facilement et participer au développement.

## Liste des fonctionnalités de la classe Robot et leur avancement:

## Fonctionnalités à créer, commenter et documenter

- :zero: fonction fonctionnelle et stable
- :one: fonction proprement commentée
- :two: fonction documentée (documentation externe)

### part 1 - screen basics

- robot.demarrer_webapp() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.creer_fenetre(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.changer_titre() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.actualiser_affichage() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.plein_ecran(changer) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.dort() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:

### part 2 - loop and events

- robot.est_actif() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.desactiver() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.fermer_fenetre() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.ajouter_evenement(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.verifier_evenements() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.supprimer_evenement(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:

### part 3 - buttons and layout

- robot.couleur_fond(couleur) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.afficher_fond() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.creer_bouton(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
  - bouton.ajouter_texte(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
  - bouton.afficher() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
  - bouton.est_actif() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.dessiner_rectangle(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.afficher_texte(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:

### part 4 - camera and photos

- robot.afficher_camera() : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.prendre_photo(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.afficher_image(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:
- robot.appliquer_filtre(...) : :zero::white_check_mark:, :one::white_check_mark: , :two::white_check_mark:

### part 5 - card detection and user session

- robot.detecter_carte() : :zero::x:, :one::x: , :two::x:
- robot.creer_session(...) : :zero::x:, :one::x: , :two::x:
- robot.fermer_session(): :zero::x:, :one::x: , :two::x:
- robot.verifier_session(): :zero::x:, :one::x: , :two::x:

### part 6 - talk to robot

- robot.entrainer(...) : :zero::x:, :one::x: , :two::x:
- robot.repondre_question(...) : :zero::x:, :one::x: , :two::x:

### part 7 - robot is talking

- robot.parler(...) : :zero::x:, :one::x: , :two::x:

### part 8 - robot emotions

- robot.choisir_emotion(...) : :zero::x:, :one::x: , :two::x:

### extra

- robot.message_erreur() : :zero::white_check_mark:, :one::x: , :two::x:

## Liste des différent modules et leur avancement:

### Module fenêtre

- Wrapper pygame et pygame_gui
- Visage minimaliste avec expressions. S’anime en cas de connexion ou réagit aux erreurs.
- Possibilité d'affichage de texte défilant des interactions, pouvant remplacer le speaker.
- Un application graphique (pygame GUI) client pour afficher le stream camera, des boutons, du texte ou des images depuis la base de données.

- Dès l’identification :
- saluer, variable
- déclencher les questions pré-enregistrées actives de la DB
- échange libre

### Module caméra

- Reconnaissance (identification) via la caméra d’un élève grâce à son motif.

### Module webapp

- Permet de faire le backend pour travailler avec la base de donnée, propose aussi un interface client web pour aider à l'administration du robot.
- Un serveur web flask local avec base de données dans laquelle se
  trouvent les élèves. Cette base de donnée contient a minima:
- nom
- prénom
- image carte (chemin vers un dossier local)
- année ou date de création (RGPD)
- string: résumé du dernier échange pour des conversations filées

- Application web permettant :

  - CRUD : formulaire nom + prénom + image.
  - Avec bouton image qui déclenche une photo, en analyse la validité : carte valide (sens, présence d’une carte), et pas de match d’un motif existant.
  - Puis l’enregistre.
  - Modifier des champs existants.
  - Supprimer un utilisateur.
  - Lire le tableau des utilisateurs.
  - Page de logs (erreurs)

- DB question à poser avec fenêtre de temps (deux dates), avec une liste définie de réponses possibles : oui/non, ou une “enum” (chat gpt saura retranscrire la réponse de l’élève).
  - Champs :
    - from
    - to
    - question
    - réponse valide
    - Liste<Réponse &élève>
- Liste des questions actives
- Liste des réponses à une question + nombre d’occurences de chaque
  réponse

### Module IA

- Communiquer avec chatgpt

### Module Audio (Speaker)

- Text to speech. Le texte est l’output de l’IA vers speaker.
- Capable de réagir de manière adaptee au public, répondre à des questions. Réponses courtes.

### Module Microphone

- Speech to text. Capture du son et transformation en texte pour donner en input a l’IA.
- Partir d’un input (module microphone), préparer un prompt pour obtenir la réponse qui servira d’output (module speaker et module écran).
- Limitations des tokens, réponses courtes. Des sujets de discussions.
- Donner de la donnée concernant le college en apprentissage au modèle. (Par exemple renseigner sur les horaires cantines.)
- Actif sur commande (fonction listen on/off), capable d’écouter la voix en isolant les bruits parasites et transcrire le contenu en texte.

## Liste des différent matériel et fonctionnement :

- Raspberry PI alimente un microphone, une camera, des hauts-parleurs

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
