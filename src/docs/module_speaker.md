# Module HautParleur - Speaker

Vous êtes ici dans la documentation du module HautParleur (audio) du robot.

Ce module permet au robot de lire des phrases avec différentes voix.

!!!Warning
    Avant d’utiliser un module, il faut systématiquement l'initialiser, sans quoi il vous sera impossible d’utiliser ce module et ses méthodes.

!!!Success "Démarrer le module *speaker*"
    ```python
    robot.demarrer_module_haut_parleur()

    ou alors

    robot.start_speaker_module()
    ```

À partir de ce moment, les objets haut-parleur / speaker sont initialisés dans le robot.

!!!Note
    La methode `demarrer_module_haut_parleur()` (ou `start_speaker_module()`) initialise les objets haut-parleur / speaker dans le robot.

## Charger une voix

Avant de lire une phrase, il faut charger une voix. Pour cela, il suffit d'utiliser la méthode `charger_voix(voix: VoiceKey) (fr) - load_voice(voice: VoiceKey) (en)`.

!!!Note
    La méthode `charger_voix(voix: VoiceKey) (fr) - load_voice(voice: VoiceKey) (en)` prend en paramètre une voix de type `VoiceKey`.
    Les valeurs possibles pour `VoiceKey` sont: "homme", "femme" et "homme_quebec".

!!!Success "charger une voix"
    ```python
    robot.haut_parleur.charger_voix("homme")

    ou alors

    robot.speaker.load_voice("homme")
    ```
    Après avoir chargé une voix, le robot peut utiliser cette voix pour lire des phrases.

!!!Note
    La méthode ne doit être appelée qu'une seule fois pour charger une voix.
    Plusieurs voix peuvent être chargées dans le robot.

## Choisir une voix

Pour choisir une voix parmi les voix chargées, il suffit d'utiliser la méthode `utiliser_voix(voix: VoiceKey) (fr) - use_voice(voice: VoiceKey) (en)`.

!!!Warning
    Avant d'utiliser une voix, il faut la charger avec la méthode `charger_voix(voix: VoiceKey) (fr) - load_voice(voice: VoiceKey) (en)`.

!!!Success "Choisir une voix"
    ```python
    robot.haut_parleur.utiliser_voix("homme")

    ou alors

    robot.speaker.use_voice("homme")
    ```

Après avoir choisi une voix, le robot utilisera cette voix pour lire des phrases.

!!!Note
    La méthode ne doit être appelée qu'une seule fois pour choisir une voix.  
    Pour changer de voix, il suffit d'utiliser la méthode `utiliser_voix(voix: VoiceKey) (fr) - use_voice(voice: VoiceKey) (en)` avec une autre voix chargée au préalable.

## Lire une phrase

Pour lire une phrase, il suffit d'utiliser la méthode `dire(phrase: str) (fr) - say(sentence: str) (en)`.

!!!Warning
    Avant de lire une phrase, il faut charger une voix avec la méthode `charger_voix(voix: VoiceKey) (fr) - load_voice(voice: VoiceKey) (en)` et choisir une voix avec la méthode `utiliser_voix(voix: VoiceKey) (fr) - use_voice(voice: VoiceKey) (en)`.

!!!Success "Lire une phrase"
    ```python
    robot.haut_parleur.dire("Bonjour, je suis un robot")

    ou alors

    robot.speaker.say("Hello, I am a robot")"
    ```

!!!Warning
    Il faut attendre que le robot finisse de lire une phrase avant de lui demander de lire une autre phrase.

## Attendre que le robot finisse de lire une phrase

Pour attendre que le robot finisse de lire une phrase, il suffit d'utiliser la propriété `lecture_en_cours` (fr) - `is_currently_reading` (en).

!!!Success "Attendre que le robot finisse de lire une phrase"
    ```python

    robot.haut_parleur.dire("Bonjour, je suis un robot")
    while robot.haut_parleur.lecture_en_cours :
        robot.dort(0.1)

    ou alors

    robot.speaker.say("Hello, I am a robot")"
    while robot.speaker.is_currently_reading :
        robot.sleep(0.1)
    ```

!!!Note
    La propriété `lecture_en_cours` (fr) - `is_currently_reading` (en) est un booléen qui est `True` si le robot est en train de lire une phrase et `False` sinon.

## Enregistrer une phrase dans un fichier audio

Pour enregistrer une phrase dans un fichier audio, il suffit d'utiliser la méthode `enregistrer_audio_dans_fichier(voix: VoiceKey, texte: str, chemin: str) (fr) - record_audio_to_file(voice: VoiceKey, text: str, path: str) (en)`.

!!!Warning
    Avant d'enregistrer une phrase dans un fichier audio, il faut charger une voix avec la méthode `charger_voix(voix: VoiceKey) (fr) - load_voice(voice: VoiceKey) (en)`.

!!!Success "Enregistrer une phrase dans un fichier audio"
    ```python
    robot.haut_parleur.enregistrer_audio_dans_fichier("homme", "Bonjour, je suis un robot", "chemin/vers/le/fichier/audio")

    ou alors

    robot.speaker.record_audio_to_file("homme", "Hello, I am a robot", "path/to/audio/file")
    ```

Après avoir enregistré une phrase dans un fichier audio, le robot pourra lire le fichier audio avec la méthode `lire_fichier_audio(chemin: str) (fr) - play_audio_file(path: str) (en)`.

## Lire un fichier audio

Pour lire un fichier audio, il suffit d'utiliser la méthode `lire_fichier_audio(chemin: str) (fr) - play_audio_file(path: str) (en)`.

!!!Success "Lire un fichier audio"
    ```python
    robot.haut_parleur.lire_fichier_audio("chemin/vers/le/fichier/audio")

    ou alors

    robot.speaker.play_audio_file("path/to/audio/file")
    ```

!!!Note
    Il faut attendre que le robot finisse de lire un fichier audio avant de lui demander de lire un autre fichier audio.

## Exemple Complet

```python
from robot import Robot

robot = Robot()

robot.demarrer_module_speaker()

robot.haut_parleur.charger_voix("homme")
robot.haut_parleur.charger_voix("femme")
robot.haut_parleur.utiliser_voix("homme")

robot.haut_parleur.dire("Bonjour, je suis un robot")

while robot.haut_parleur.lecture_en_cours :
    robot.dort(0.1)

robot.haut_parleur.charger_voix("femme")

robot.haut_parleur.enregistrer_audio_dans_fichier("homme", "Bonjour, je suis un robot", "chemin/vers/le/fichier/audio")

while robot.haut_parleur.lecture_en_cours :
    robot.dort(0.1)

robot.haut_parleur.lire_fichier_audio("chemin/vers/le/fichier/audio")
```
