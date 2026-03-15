# Home Assistant - Configuration & Détails

Configuration complète de mon installation Home Assistant, organisée par fonctionnalité.

## Dashboard Accueil

![Dashboard Accueil 1](screenshots/dashboard_accueil_1.png)
![Dashboard Accueil 2](screenshots/dashboard_accueil_2.png)

Dans chaque dossier, vous retrouverez un fichier dashboard.yaml qui sera le code du dashboard

## Fonctionnalités

| # | Dossier | Description |
|---|---|---|
| 1 | [chauffage/](chauffage/) | Poêle à granulés — 8 modes de priorité, plannings dynamiques, sync vacances scolaires, syncro télétravail depuis agenda Google |
| 2 | [energie-solaire/](energie-solaire/) | Surplus solaire → Ballon eau chaude (palier 2) + Frigo américain (3 paliers), ZLinky TIC Standard |
| 3 | [ups-nas/](ups-nas/) | APC SMC1000I-2UC + NAS Synology — extinction automatique sur batterie faible |
| 4 | [infra/](infra/) | Documentation infrastructure : Quorum Proxmox, Cisco 3650, Synology |
| 5 | [tv-salon/](tv-salon/) | Disjoncteur TV OLED — coupures automatiques avec délai refroidissement, rallumages planifiés selon modes de planning chauffage |
| 6 | [bureaux/](bureaux/) | Switches Bureau Arnaud / Maxence / Julie — coupures auto, extinctions forcées, rallumages planifiés selon modes de planning chauffage |
| 7 | [robot/](robot/) | Dreame X50 Ultra Complete — lancement automatique alarme, sélection pièces ordonnée |


## Stack technique

- **Home Assistant** : HA OS, Zigbee2MQTT (coordinateur Sonoff Dongle Max Zigbee)
- **Énergie** : ZLinky TIC Standard, ECU-R (pilotage production photovoltaïque), EDF Tempo
- **Réseau** : OPNsense, Cisco Catalyst 3650-48PS, VLANs segmentés
- **Infra** : Proxmox VE Cluster 2 nœuds + Corosync sur Odroid c2 pour Quorum, Synology RS4017xs+, APC SMC1000I-2UC

## Utilisation

Chaque dossier est **autonome** : tu peux copier uniquement les fichiers qui t'intéressent.
Tu pourras retrouver des fonctionnalités dans plusieurs dossiers. Par exemple tv-salon et bureaux s'appuient sur les modes de plannings du chauffage

Chaque dossier contient :
- `helpers.yaml` — helpers HA (input_number, input_boolean, input_datetime, template sensors)
- `automations.yaml` — automations liées à cette fonctionnalité
- `scripts.yaml` — scripts si applicable
- `sensors.yaml` — sensors si applicable
- `dashboard.yaml` — Code YAML du ou des dashboard(s). Commencera toujours par dashbord_xxx.yaml
- `README.md` — documentation spécifique

## Dashboards
Utilisation des extentions HACS suivantes dans mes dashboards :
- Mushroom
- Lovelace Mini Graph Card
- Button Card by @RomRider
- Lovelace Vacuum Map card (pour mon Dreame X50)
- card-mod 4
- layout-card
- Sonos Card
- template-entity-row

## Sécurité

Le fichier `secrets.yaml` n'est **jamais** commité. Un exemple anonymisé est disponible : [`secrets.yaml.example`](secrets.yaml.example)
