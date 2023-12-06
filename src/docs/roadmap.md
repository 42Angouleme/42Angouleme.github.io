# Progression générale

> L'objectif est d'obtenir une librairie qui permettra aux élèves d'interagir avec lui par la voix, le texte et l’image. Une IA (conversationnelle) interagira avec eux. Ce robot aura pour fonction principale d'accueillir le public dans le Hall de l'établissement et pourrait par exemple, si entrainé avec les données du collège, répondre à des questions comme: *"Que mange t'on ce midi à la cantine ?"*.

Le projet se découpe en deux niveaux, la classe générale **Robot** qui doit avoir des méthodes accédant à toutes les fonctionnalités des modules de manière simple, correctement nommées et documentées (en français) pour l'utilisation par les élèves.

Les **modules**, avec leurs fonctionnalités plus bas niveau doivent aussi étre documenté pour que les étudiants de 42 puisse s'intégrer plus facilement et participer au développement.

## Liste des fonctionnalités de la classe Robot et leur avancement:

## fonctionnalitées à créer, commenter et documenter
- robot.demarrer_webapp() : créé :white_check_mark:, commentaire :x:, documentation :white_check_mark:
- robot.is_actif() : créé :white_check_mark:, commentaire :white_check_mark:, documentation :x:
- robot.allumer_ecran(longueur, hauteur) : créé :white_check_mark:, commentaire :white_check_mark:, documentation :x:
- robot.eteindre_ecran() : créé :white_check_mark:, commentaire :white_check_mark:, documentation :x:
- robot.changer_titre() : créé :white_check_mark:, commentaire :x:, documentation :x:
- robot.dort() : créé :white_check_mark:, commentaire :x:, documentation :x:
- robot.plein_ecran(changer) : créé :x:, commentaire :x:, documentation :x:
- robot.dessiner_ecran() : créé :x:, commentaire :x:, documentation :x:
---
- robot.ajouter_evenement(touche, fonction) : créé :x:, commentaire :x:, documentation :x:
- robot.supprimer_evenement(touche) : créé :x:, commentaire :x:, documentation :x:
- robot.verifier_evenement(touche) : créé :x:, commentaire :x:, documentation :x:
- robot.ajouter_bouton(nom, fonction) : créé :x:, commentaire :x:, documentation :x:
- robot.supprimer_bouton(nom) : créé :x:, commentaire :x:, documentation :x:
- robot.xxx() : créé :x:, commentaire :x:, documentation :x:
---
- robot.message_erreur() : créé :white_check_mark:, commentaire :x:, documentation :x:
- robot.xxx() : créé :x:, commentaire :x:, documentation :x:

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

## Documentation

* Documentation en français, accessible par le web, décrivant les fonctions et fonctionnalités du robot.
