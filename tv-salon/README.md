# TV Salon

Gestion de la coupure/allumage de la TV / Home Cinéma Salon selon les modes de plannings (chauffage) actifs
Calcul des temps de fonctionnement et consommations énergétiques.

## Dashboards TV Salon

![Dashboard TV Salon](screenshots/dashboard_tv_salon.png)

## Utilisation

Le dashboard "TV Salon" s'appuie sur les modes de plannings du chauffage

Le dossier contient :
- `helpers.yaml` — helpers HA (input_number, input_boolean, input_datetime, template sensors)
- `automations.yaml` — automations liées à cette fonctionnalité
- `sensors.yaml` — sensors
- `dashboard.yaml` — Code YAML du dashboard TV Salon
- `README.md` — documentation spécifique

## Dashboards
Utilisation des extentions HACS suivantes dans mes dashboards :
- Mushroom
- Lovelace Mini Graph Card
- Button Card by @RomRider
- card-mod 4
- layout-card
- Sonos Card
- template-entity-row