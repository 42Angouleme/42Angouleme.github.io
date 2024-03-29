# Module Microphone - Microphone

Vous êtes ici dans la documentation du module Microphone (enregistrement audio) du robot.

Ce module permet au robot d'enregistrer votre voix dans le but de la convertir en texte.

!!!Warning
    Avant d’utiliser un module, il faut systématiquement l'initialiser, sans quoi il vous sera impossible d’utiliser ce module et ses méthodes.

!!!Success "Démarrer le module _microphone_"
    ```python
    robot.initialiser_module_microphone()
    ou
    robot.init_microphone_module()
    ```

À partir de ce moment, l'objet microphone est initialisé dans le robot.

!!!Note
La méthode `initialiser_module_microphone()` (ou `init_microphone_module()`) initialise l'objet microphone dans le robot.

## Enregistrer une phrase

Pour enregistrer une phrase, il suffit d'utiliser la méthode `une_phrase()` (fr) - `one_sentence()` (en).

!!!Note
    La méthode `une_phrase()` (fr) - `one_sentence()` (en) ne prend pas de
    paramètre.

!!!Success "Enregistrer une phrase"
    ```python
    robot.microphone.une_phrase()
    ou
    robot.microphone.one_sentence()
    ```

## Enregistrer plusieurs phrase

Pour enregistrer plusieurs phrases d'un seul coup, il suffit d'utiliser la
méthode `pour_chaque_phrase(callback: Callable[[TraitementAudio], None])` (fr) - `for_each_sentence(callback: Callable[[TraitementAudio], None])` (en).

!!!Note
    La méthode `pour_chaque_phrase(callback: Callable[[TraitementAudio], None])` (fr) - `for_each_sentence(callback: Callable[[TraitementAudio], None])` (en)
    prend en paramètre une fonction qui prend elle même en paramètre un `TraitementAudio` et renvoie None.

!!!Success "Enregistrer plusieurs phrases"
    ```python
    robot.microphone.pour_chaque_phrase()
    ou
    robot.microphone.for_each_sentence()
    ```

## Enregistrer pendant une durée

Pour enregistrer pendant une durée spécifiée, il suffit d'utiliser la
méthode `pendant(duree: str | float, delai: str | float | None = None)` (fr) - `during(duree: str | float, delai: str | float | None = None)` (en).

!!!Note
    La méthode `pendant(duree: str | float, delai: str | float | None = None)` (fr) - `during(duree: str | float, delai: str | float | None = None)` (en)
    prend en paramètre une durée en `str` ou en `float`, et un delai en `str`, en
    `float` ou `None`.

!!!Success "Enregistrer pendant une durée"
    ```python
    robot.microphone.pendant("5 secondes")
    ou
    robot.microphone.during("5 secondes")
    ```

## Exemple Complet

```python
from robot import Robot

robot = Robot()
robot.initialiser_module_microphone()
robot.microphone.une_phrase().enregistrer_sous("Ma_phrase.wav")
robot.microphone.pour_chaque_phrase().enregistrer_sous("Mon_texte.wav")
robot.microphone.pendant("5 secondes").enregistrer_sous("enregistrement.wav")
```
