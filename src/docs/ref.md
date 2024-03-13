# Référence de la bibliothèque

Pour en savoir plus, dans un éditeur tel que _visual studio code_, il suffit de passer la souris sur une fonction pour voir les commentaires la concernant.

![Commentaires](ref.png)

## Les évènements

Liste des touches pour créer des évènements:

```
* echap (touche Échap)
* espace (touche Espace)
* 0
* 1
* 2
* 3
* 4
* 5
* 6
* 7
* 8
* 9
* a
* b
* c
* d
* e
* f
* g
* h
* i
* j
* k
* l
* m
* n
* o
* p
* q
* r
* s
* t
* u
* v
* w
* x
* y
* z
* F1
* F2
* F3
* F4
* F5
* F6
* F7
* F8
* F9
* F10
* F11
* F12
* F13
* F14
* F15
```

## Les filtres

Liste des filtres que l'on peut appliquer sur une image

```
* cartoon
* ocean
* alien
* rose
* flou
* noir_et_blanc
* tourner
* vernis
```

## Liste des méthodes disponible par modules

### Module Robot

```python
robot = Robot()
```

```python
robot.desactiver()
robot.deactivate()
```

```python
robot.est_actif()
robot.is_active()
```

```python
robot.dort(secondes : int)
robot.sleep(secondes : int)
```

```python
robot.ajouter_evenement(touche : str, nom : str)
robot.add_event(key : str, name : str)
```

```python
robot.verifier_evenements()
robot.check_events()
```

```python
robot.supprimer_evenement(nom : str)
robot.delete_event(nom : str)
```

```python
robot.demarrer_webapp()
robot.init_webapp()
```

### Module Fenetre - Window

```python
robot.initialiser_module_fenetre()
robot.init_window_module()
```

```python
robot.fenetre.ouvrir_fenetre(longueur: int, hauteur: int)
robot.window.open_window(width : int, height : int)
```

```python
robot.fenetre.fermer_fenetre()
robot.window.close_window()
```

```python
robot.fenetre.actualiser_affichage()
robot.window.refresh_display()
```

```python
robot.fenetre.plein_ecran(changer : bool)
robot.window.full_screen(change : bool)
```

```python
robot.fenetre.changer_titre(titre : str)
robot.window.change_title(title : str)
```

```python
robot.fenetre.changer_couleur_fond(couleur : str)
robot.window.change_background_color(color : str)
```

```python
robot.fenetre.afficher_fond()
robot.window.display_background()
```

```python
robot.fenetre.dessiner_rectangle(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
robot.window.draw_rectangle(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
robot.fenetre.afficher_texte(texte : str, position_x: int, position_y: int, taille: int, couleur: Couleur)
robot.window.display_text(text : str, position_x: int, position_y: int, size: int, color: Couleur)
```

```python
robot.fenetre.afficher_image(chemin_fichier : str, position_x: int, position_y: int)
robot.window.display_image(file_path : str, position_x: int, position_y: int)
```

```python
robot.fenetre.creer_bouton(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
robot.window.create_button(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
robot.fenetre.creer_zone_texte(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
robot.window.create_text_area(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
robot.fenetre.afficher_carte_detectee(self, detected_card: MatLike, position_x: int, position_y: int)
robot.window.display_detected_card(self, detected_card: MatLike, position_x: int, position_y: int)
```

```python
robot.fenetre.obtenir_image_emotion(emotion : str)
robot.window.get_emotion_image(emotion : str)
```

### Module Camera

```python
robot.initialiser_module_camera()
robot.init_camera_module()
```

```python
robot.camera.afficher_camera(position_x: int, position_y: int)
robot.camera.display_camera(position_x : int, position_y : int)
```

```python
robot.camera.prendre_photo(nom_fichier: str)
robot.camera.take_picture(file_name : str)
```

```python
robot.camera.appliquer_filtre(chemin_fichier: str, nom_filtre: str)
robot.camera.apply_filter(file_name : str, filter_name : str)
```

### Module IA - AI

```python
robot.initialiser_module_IA()
robot.init_AI_module()
```

```python
robot.IA.demarrer_discussion()
robot.AI.init_conversation()
```

```python
robot.IA.arreter_discussion()
robot.AI.stop_conversation()
```

```python
robot.IA.poser_question(question : str)
robot.AI.ask_question(question : str)
```

```python
robot.IA.creer_historique_conversation()
robot.AI.create_conversation_history()
```

```python
robot.IA.charger_historique(historique_de_conversation : ConversationSummaryBufferMemory)
robot.AI.load_history(conversation_history : ConversationSummaryBufferMemory)
```

```python
robot.IA.supprimer_historique()
robot.AI.delete_history()
```

```python
robot.IA.obtenir_historique_conversation()
robot.AI.get_current_conversation_history()
```

```python
robot.IA.donner_emotion(phrase : str)
robot.AI.get_emotion(sentence : str)
```

### Module Utilisateur - User

```python
robot.initialiser_module_utilisateur()
robot.init_user_module()
```

```python
robot.utilisateur.verifier_session()
robot.user.check_session()
```

```python
robot.utilisateur.connecter(seuil_minimal : float, seuil_arret_recherche : float)
robot.user.login(self, minimum_threshold: float, search_stop_threshold: float)
```

```python
robot.utilisateur.deconnecter()
robot.user.logout()
```

```python
robot.utilisateur.creer_utilisateur(prenom, nom, carte)
robot.user.create(firstname, lastname, card)
```

```python
robot.utilisateur.supprimer_utilisateur()
robot.user.delete()
```

```python
robot.utilisateur.obtenir_utilisateur_connecte()
robot.user.get_logged_in_user()
```

```python
robot.utilisateur.detecter_carte(seuil_minimal : float, seuil_arret_recherche : float)
robot.user.detect_card(minimum_threshold: float, search_stop_threshold: float)
```

### Module HautParleur - Speaker

```python
robot.initialiser_module_haut_parleur()
robot.init_speaker_module()
```

```python
robot.haut_parleur.charger_voix(voix: VoiceKey)
robot.speaker.load_voice(voice: VoiceKey)
```

```python
robot.haut_parleur.utiliser_voix(voix: VoiceKey)
robot.speaker.use_voice(voice: VoiceKey)
```

```python
robot.haut_parleur.dire(phrase: str)
robot.speaker.say(sentence: str)
```

```python
robot.haut_parleur.lecture_en_cours()
robot.speaker.is_currently_reading()
```

```python
robot.haut_parleur.enregistrer_audio_dans_fichier(voix: VoiceKey, texte: str, chemin: str)
robot.speaker.record_audio_to_file(voice: VoiceKey, text: str, path: str)
```

### Module Microphone

```python
robot.initialiser_module_microphone()
robot.init_microphone_module()
```

```python
robot.microphone.une_phrase()
robot.microphone.one_sentence()
```

```python
robot.microphone.pour_chaque_phrase(callback: Callable[[TraitementAudio], None])
robot.microphone.for_each_sentence(callback: Callable[[TraitementAudio], None])
```

```python
robot.microphone.pendant(duree: str | float, delai: str | float | None = None)
robot.microphone.during(duree: str | float, delai: str | float | None = None)
```

## Les boutons

```python
ajouter_texte(texte : str, position_x : int, position_y : int, taille : int, couleur : Couleur)
add_text(text : str, position_x : int, position_y : int, size : int, color : Couleur)
```

```python
afficher()
display()
```

```python
est_actif()
is_active()
```

## Les zones de texte

```python
afficher()
display()
```

```python
est_actif()
is_active()
```

```python
ecrire(robot : Robot)
write(robot : Robot)
```

```python
obtenir_texte()
get_text()
```

```python
effacer_texte()
erase_text()
```

```python
modifier_taille_police(taille : int)
change_font_size(size : int)
```

```python
modifier_couleur_police(couleur : Couleur)
change_font_color(color : Couleur)
```
