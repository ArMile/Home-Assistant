# Gestion des Modes de Planning

Gestion des différents modes de Planning.
Détachement de la gestion du chauffage car utilisés sur plusieurs de mes automations

- Etat Planning
- Paramétrage Planning : Configuration des dates début/Fin de chaque mode 1. 🛫Vacances → 2. ✋Manuel → 3. 🔥Boost → 4. 💼Télétravail → 5. 🏖️Vac. Maison → 6. 🎉Weekend+ → 7. 📅Planning Normal → 8. 💚Éco. Mode Manuel et Mode Boost disponible. Synchrionisation (ou pas) des dates de vacances Scolaire pour parmamétrage auto du mode. Synchrionisation (ou pas) des Télétravails paramétrés dans le caldendrier Google avec Gestion de "blocs" pour parmamétrage auto du mode. 
- Configuration des horaires pour chaque mode de planning (Normal / Vacances à la maison / Télétravail / Weekend Prolongé)

## Dashboards Modes Planning

![Dashboard Etat Planning](screenshots/Etat-Planning.png)
![Dashboard Paramétrage Planning](screenshots/Parametrage-Planning.png)
![Dashboard Configuration des Horaires Planning](screenshots/Config-Horaires.png)


Le dossier contient :
- `helpers.yaml` — helpers HA (input_number, input_boolean, input_datetime, template sensors)
- `automations.yaml` — automations liées à cette fonctionnalité
- `sensors.yaml` — sensors
- `dashboard.yaml` — Code YAML du dashboard Bureau Arnaud
- `README.md` — documentation spécifique

## Dashboards
Utilisation des extentions HACS suivantes dans mes dashboards :
- Mushroom
- Lovelace Mini Graph Card
- Button Card by @RomRider
- card-mod 4
- layout-card
- template-entity-row