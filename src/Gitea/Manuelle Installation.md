
# Installation von Gitea – Schritt-für-Schritt-Anleitung

Diese Anleitung beschreibt die manuelle Installation des Git-Services Gitea. Ziel ist es, alle notwendigen Schritte zur Einrichtung und Automatisierung per Ansible klar darzustellen.
Hierfür soll in VSC eine gitea-install.yml Datei angelegt werden!

## Übersicht

Die Installation erfolgt in folgenden Schritten:
1. **Anlegen eines Systembenutzers** für die sichere Ausführung von Gitea.
2. **Erstellen der Verzeichnisstruktur** mit den korrekten Berechtigungen.
3. **Herunterladen und Bereitstellen der Gitea-Binary**.
4. **Einrichten und Starten des Gitea-Services**.
5. **Durchführung des First-Install Wizards**.

---

## Detaillierte Installationsanleitung

### 1. Anlegen von Benutzer und Gruppe

Gitea benötigt einen eigenen Benutzer `git`, um sicher isoliert zu laufen. Dies erfolgt mit folgenden Befehlen:

```shell
# Gruppe anlegen
groupadd --system git

# Benutzer anlegen
useradd --system --shell /bin/bash --comment 'Git Version Control' --gid git --home-dir /home/git --create-home git
```

**Automatisierung mit Ansible**  
Verwende die Module [ansible.builtin.group](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/group_module.html) und [ansible.builtin.user](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html).

---

### 2. Erstellen der Verzeichnisstruktur

Folgende Verzeichnisse sind erforderlich:
- `/etc/gitea` (Owner: `root:git`, Rechte: `770`)
- `/var/lib/gitea/custom`, `/var/lib/gitea/data`, `/var/lib/gitea/log` (Owner: `git:git`, Rechte: `750`)

**Manuelle Erstellung:**
```shell
# Verzeichnisse anlegen
mkdir -p /var/lib/gitea/{custom,data,log}
mkdir /etc/gitea

# Berechtigungen setzen
chown -R git:git /var/lib/gitea
chmod -R 0750 /var/lib/gitea
chown root:git /etc/gitea
chmod 0770 /etc/gitea
```

**Automatisierung mit Ansible**  
Nutze das Modul [ansible.builtin.file](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html). Für `/var/lib/gitea` empfiehlt sich eine Schleife.
> [!Tip]
> 
> Das Modul kann allerdings nur ein Pfad gleichzeitig verwendet werden. 
> Daher ist empfohlen, für custom, data, log eine Schleife zu verwenden und /etc/gitea in einem eigenen Task zu behandeln.

---

### 3. Herunterladen und Bereitstellen der Gitea-Binary

Die Gitea-Binary wird heruntergeladen und in das globale Verzeichnis `/usr/local/bin` kopiert:

```shell
wget -O gitea https://dl.gitea.com/gitea/1.22.3/gitea-1.22.3-linux-amd64
chmod +x gitea
cp gitea /usr/local/bin/gitea
```

**Automatisierung mit Ansible**  
Nutze das Modul [ansible.builtin.get_url](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html). Lege dabei Owner, Gruppe und Berechtigungen direkt fest.

---

### 4. Einrichten und Starten des Gitea-Services

Erstelle eine .service Datei um Gitea automatisch zu starten. Hierfür verwenden wir folgendes Grundschema: [gitea.service](https://github.com/go-gitea/gitea/blob/release/v1.22/contrib/systemd/gitea.service)

Hierfür erstellst du die Datei `/etc/systemd/system/gitea.service` mit einem Texteditor (in folgendem Beispiel `nano`)

```shell
nano /etc/systemd/system/gitea.service
```

Inhalt:

```ini
{{#include gitea.service}}
```
Mittels des folgenden Befehls wird die Diensteverwaltung, systemd, angewiesen, seine Dateien neu einzulesen:
```shell
   systemctl daemon-reload
```

Danach muss der Dienst noch in den Autostart aufgenommen (`enable`) und anschließend gestartet (`start`) werden:

```shell
   systemctl enable gitea
   systemctl start gitea
```

> [!TIP]
> Wenn du Probleme mit dem Start von Gitea hast, kannst du versuchen, Gitea manuell per CLI zu starten (beenden mit `<CTRL> + C`)
> ``` shell
> GITEA_WORK_DIR=/var/lib/gitea/ /usr/local/bin/gitea web -c /etc/gitea/app.ini
> ```

Nutze [ansible.builtin.copy](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html) zum Übertragen der `.service`-Datei und [ansible.builtin.systemd](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/systemd_module.html) zum Verwalten des Services und zum Reloaden des Daemons. Die `.service`-Datei muss auf dem Ansible Controller in dem Verzeichnis `files` abgelegt werden.

---
### 5. Ausführen des First-Install Wizards von Gitea

Bei Teleport gibt es eine "Kachel" mit dem Namen: **gitea-username**. Dort soll nun der "Launch-Button" gedrückt werden.

<img src="images/01-teleport.png" width="55%" style="margin-left: auto; margin-right: auto; display: block; margin-top: 40px; margin-bottom: 40px">

Es öffnet sich der Install Wizard von Gitea. Bitte hier **SQLite3** als Datenbank auswählen! Alle anderen Einstellungen sollten auf Standard bleiben. Mit einem Click auf "Erstellen" ganz unten auf der Seite geht es weiter.

![Installations-Wizard](images/02-config.png)

Oben auf der Seite von dem Reiter "Anmelden" auf "Konto erstellen" wechseln und dort den Admin User registrieren.

![Admin User erstellen](images/03-admin_create.png) 

Herzlichen Glückwunsch, die Installation von Gitea ist fertig!

![fertig](images/04-finish.png)

Damit ist die manuelle Installation abgeschlossen!