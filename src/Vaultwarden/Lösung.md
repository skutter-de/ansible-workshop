# Lösung

Auf dieser Seite befindet sich ein Lösungsbeispiel für die automatisierte Installation von Vaultwarden mittels Docker.


### Playbook-Header:

``` yml
{{#include vaultwarden_install.yml:1:4 }}
```

### Docker

``` yml
{{#include vaultwarden_install.yml:5:11 }}
```

### Docker und Docker Compose installieren
``` yml
{{#include vaultwarden_install.yml:13:19 }}
```

### Docker ist aktiviert und gestartet

``` yml
{{#include vaultwarden_install.yml:21:25 }}
```

### Erstellen des Vaultwarden Verzeichnisses

``` yml
{{#include vaultwarden_install.yml:27:33 }}
```

### Docker-compose.yml auf das Zielsystem kopieren

``` yml
{{#include vaultwarden_install.yml:35:41 }}
```

### Compose starten

Das Modul [***community.docker.docker_compose_v2***](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_v2_module.html) ist ein Ansible-Modul aus der Community Docker Collection. Mit diesem Modul können Konfigurationen direkt über Ansible bereitgestellt und verwaltet werden.

- `project_src`: Der Pfad auf dem Zielsystem, an welcher Stelle die Compose-File liegt

``` yml
{{#include vaultwarden_install.yml:43:46 }}
```

## Fertiges Playbook

``` yml
{{#include vaultwarden_install.yml}}
```

## Das ist natürlich nur ein Lösungsvorschlag.