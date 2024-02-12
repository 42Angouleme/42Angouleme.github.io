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
robot.nom_de_la_methode(argument_de_la_methode)
```

```python
desactiver()
deactivate()
```

```python
est_actif()
is_active()
```

```python
dort(secondes : int)
sleep(secondes : int)
```

```python
ajouter_evenement(touche : str, nom : str)
add_event(key : str, name : str)
```

```python
verifier_evenements()
check_events()
```

```python
supprimer_evenement(nom : str)
delete_event(nom : str)
```

```python
demarrer_webapp()
start_webapp()
```

### Module Fenetre - Window

```python
robot.demarrer_module_fenetre()
robot.start_window_module()
```

```python
robot.fenetre.nom_de_la_methode(argument_de_la_methode)
robot.window.method_name(method_argument)
```

```python
ouvrir_fenetre(longueur: int, hauteur: int)
open_window(width : int, height : int)
```

```python
fermer_fenetre()
close_window()
```

```python
actualiser_affichage()
refresh_display()
```

```python
plein_ecran(changer : bool)
full_screen(change : bool)
```

```python
changer_titre(titre : str)
change_title(title : str)
```

```python
changer_couleur_fond(couleur : str)
change_background_color(color : str)
```

```python
afficher_fond()
display_background()
```

```python
dessiner_rectangle(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
draw_rectangle(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
afficher_texte(texte : str, position_x: int, position_y: int, taille: int, couleur: Couleur)
display_text(text : str, position_x: int, position_y: int, size: int, color: Couleur)
```

```python
afficher_image(chemin_fichier : str, position_x: int, position_y: int)
display_image(file_path : str, position_x: int, position_y: int)
```

```python
creer_bouton(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
create_button(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
creer_zone_texte(longueur: int, hauteur: int, position_x: int, position_y: int, couleur: Couleur)
create_text_area(width: int, height: int, position_x: int, position_y: int, color: Couleur)
```

```python
afficher_carte_detectee(self, detected_card: MatLike, position_x: int, position_y: int)
display_detected_card(self, detected_card: MatLike, position_x: int, position_y: int)
```

```python
obtenir_image_emotion(emotion : str)
get_emotion_image(emotion : str)
```

### Module Camera

```python
robot.demarrer_module_camera()
robot.start_camera_module()
```

```python
robot.camera.nom_de_la_methode(argument_de_la_methode)
robot.camera.method_name(method_argument)
```

```python
afficher_camera(position_x: int, position_y: int)
display_camera(position_x : int, position_y : int)
```

```python
prendre_photo(nom_fichier: str)
take_picture(file_name : str)
```

```python
appliquer_filtre(chemin_fichier: str, nom_filtre: str)
apply_filter(file_name : str, filter_name : str)
```

### Module IA - AI

```python
robot.demarrer_module_IA()
robot.start_AI_module()
```

```python
robot.IA.nom_de_la_m(argument_de_la_methode)
robot.AI.method_name(method_argument)
```

```python
demarrer_discussion()
start_conversation()
```

```python
arreter_discussion()
stop_conversation()
```

```python
poser_question(question : str)
ask_question(question : str)
```

```python
creer_historique_conversation()
create_conversation_history()
```

```python
charger_historique(historique_de_conversation : ConversationSummaryBufferMemory)
load_history(conversation_history : ConversationSummaryBufferMemory)
```

```python
supprimer_historique()
delete_history()
```

```python
obtenir_historique_conversation()
get_current_conversation_history()
```

```python
obtenir_emotion(phrase : str)
get_emotion(sentence : str)
```

### Module Utilisateur - User

```python
robot.demarrer_module_utilisateur()
robot.start_user_module()
```

```python
robot.utilisateur.nom_de_la_methode(argument_de_la_methode)
robot.user.method_name(method_argument)
```

```python
verifier_session()
check_session()
```

```python
connecter(seuil_minimal : float, seuil_arret_recherche : float)
logging(self, minimum_threshold: float, search_stop_threshold: float)
```

```python
deconnecter()
logout()
```

```python
creer_utilisateur(prenom, nom, carte)
create_user(firstname, lastname, card)
```

```python
supprimer_utilisateur()
delete_user()
```

```python
obtenir_utilisateur_connecte()
get_logged_in_user()
```

```python
detecter_carte(seuil_minimal : float, seuil_arret_recherche : float)
detect_card(minimum_threshold: float, search_stop_threshold: float)
```

### Module Audio

Aucune Actuellement

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
