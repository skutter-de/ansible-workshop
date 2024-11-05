# Lösung

Auf dieser Seite befindet sich ein Lösungsbeispiel für die automatisierte Installation von Gitea mittels eines Binaries.

### Playbook-Header:
``` yml
{{#include gitea_install.yml:1:4 }}
```

### Erstellen der Gruppe "git"

``` yml
{{#include gitea_install.yml:5:8 }}
```

### Erstellen des Users "git"

``` yml
{{#include gitea_install.yml:10:18 }}
```

### Erstellen der Gitea Verzeichnisse mittels einer Schleife

``` yml
{{#include gitea_install.yml:20:30 }}
```

### Erstellen des /etc/gitea Verzeichnisses mit spezifischen Rechten


``` yml
{{#include gitea_install.yml:32:38 }}
```

### Herunterladen der Gitea Binary und ablegen in ein globales Verzeichnis

``` yml
{{#include gitea_install.yml:40:46 }}
```

### Kopieren der gitea.service Datei auf den Zielhost

``` yml
{{#include gitea_install.yml:48:54 }}
```

### Aktivieren des Systemd Services mit anschließendem Daemon-Reload

``` yml
{{#include gitea_install.yml:56:61 }}
```



## Fertiges Playbook


``` yml
{{#include gitea_install.yml }}
```



### Das ist natürlich nur ein Lösungsvorschlag.