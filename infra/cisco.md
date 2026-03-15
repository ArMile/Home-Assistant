# Cisco Catalyst 3650-48PS - Intégration Home Assistant

## Matériel

- Modèle : Catalyst 3650-48PS
- IOS-XE : 16.9.4 (max supporté : 16.12.x)
- 48 ports PoE+

## SNMP

Communauté `xxxxxxx` configurée avec ACL `acl-snmp-ha` restreinte à l'IP de HA.

```yaml
# configuration.yaml
sensor:
  - platform: snmp
    name: "Cisco 3650"
    host: 192.168.xxx.xxx
    community: xxxxxxx
    version: "2c"
    baseoid: 1.3.6.1.2.1.1.1.0
```

## SSH

Connexion SSH depuis HA nécessite des algorithmes legacy dans `~/.ssh/config` :

```
Host 192.168.xxx.xxx
  KexAlgorithms +diffie-hellman-group-exchange-sha1
  HostKeyAlgorithms +ssh-rsa
  PubkeyAcceptedAlgorithms +ssh-rsa
```

## Device Tracker (désactivé)

```yaml
# device_tracker:
#   - platform: cisco_ios
#     host: 192.168.xxx.xxx
#     username: xxxxxxx
#     password: !secret cisco_password
```
