# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a **Home Assistant YAML configuration repository** — no build system, no tests, no package manager. All configuration is pure YAML consumed directly by Home Assistant.

## Architecture

The repository uses a **feature-module pattern**: each functional area lives in its own directory and is self-contained. Modules can be copied independently.

### Root files
- `helpers.yaml` — Global input helpers (temperatures, thresholds, planning modes, utility meters) shared across modules
- `dashboard.yaml` — Main home dashboard aggregating all views
- `secrets.yaml.example` — Template for `secrets.yaml` (never committed); requires `gmail_password`, `alarm_code`, `cisco_password`

### Internal files
- `.claude/settings.local.json` — Claude AI configuration (local settings, not committed)

### Feature modules (each contains its own README, dashboard, automations, helpers, etc.)
| Module | Purpose |
|--------|---------|
| `chauffage/` | Pellet stove — 8 priority modes, dynamic planning, Google Calendar + school holidays sync |
| `energie-solaire/` | Solar surplus throttling for water heater and fridge (3-tier logic) |
| `ups-nas/` | APC UPS monitoring, automatic NAS/server shutdown on low battery |
| `tv-salon/` | OLED TV circuit breaker with auto-shutoff and cooling delays |
| `bureaux/` | 3 office desks — auto-shutoff, schedule-based restart, telework planning |
| `modes-planning/` | Global planning mode management (extracted from chauffage for reuse across automations) |
| `robot/` | Dreame X50 vacuum — alarm triggers, room selection |
| `sonos/` | Sonos platform dashboard and helpers |
| `infra/` | Infrastructure status (Proxmox, Cisco 3650, Synology) |

### File conventions within each module
- `automations.yaml` — Automation rules (can be very large: chauffage is ~100 KB)
- `dashboard.yaml` / `dashboard_<variant>.yaml` — Lovelace UI definitions
- `helpers.yaml` — Module-specific input helpers
- `scripts.yaml` — Reusable scripts (chauffage, robot)
- `sensors.yaml` — Template sensors

## Key HACS UI components in use
- Mushroom, Button Card (RomRider), card-mod 4, Lovelace Mini Graph Card
- layout-card, template-entity-row, Sonos Card, Lovelace Vacuum Map card

## Hardware / Integrations context
- Zigbee: Sonoff Dongle Max via Zigbee2MQTT
- Energy: ZLinky TIC Standard (Linky meter), ECU-R (solar PV)
- Network: OPNsense, Cisco Catalyst 3650-48PS, VLANs
- Infra: Proxmox 2-node cluster + Corosync quorum on Odroid C2, Synology RS4017xs+, APC SMC1000I-2UC

## Secrets
`secrets.yaml` is gitignored. Use `secrets.yaml.example` as a reference for required keys. Never commit actual secrets.

## Index file
`Table Matieres configuration et automations.yaml` serves as a human-readable index of all automations and configurations across the repository.
