# Proxmox VE - Intégration Home Assistant

## Cluster

- 2 nœuds identiques : Intel i9-12900H, 32 Go RAM
- Proxmox VE 9.1.4
- Quorum surveillé via `command_line` sensor dans HA

## Sensor Quorum HA

```yaml
command_line:
  - sensor:
      name: "Proxmox Quorum Status"
      command: "ssh -i /config/ssh_keys/id_rsa_proxmox -o StrictHostKeyChecking=no root@<IP_NOEUD> 'pvecm status | grep \"Total votes\" | tr -s \" \" | cut -d\" \" -f3'"
      scan_interval: 60
      value_template: >
        {% set count = value | trim | int %}
        {% if count == 3 %}
          OK
        {% elif count == 2 %}
          DEGRADED
        {% else %}
          CRITICAL
        {% endif %}
```

## Prérequis

- Clé SSH sans passphrase générée et déposée dans `/config/ssh_keys/`
- Autorisation dans `authorized_keys` sur le nœud Proxmox
