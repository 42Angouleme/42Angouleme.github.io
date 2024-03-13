# Module Microphone - Microphone

Vous êtes ici dans la documentation du module Microphone (enregistrement audio) du robot.

Ce module permet au robot d'enregistrer votre voix dans le but de la convertir en texte.

!!!Warning
    Avant d’utiliser un module, il faut systématiquement l'initialiser, sans quoi il vous sera impossible d’utiliser ce module et ses méthodes.

!!!Success "Démarrer le module *microphone*"
    ```python
    robot.initialiser_module_microphone()

    ou alors

    robot.init_microphone_module()
    ```

À partir de ce moment, l'objet microphone est initialisé dans le robot.

!!!Note
    La méthode `initialiser_module_microphone()` (ou `init_microphone_module()`) initialise l'objet microphone dans le robot.
