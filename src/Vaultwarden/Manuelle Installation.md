# Installation von Vaultwarden – Schritt-für-Schritt-Anleitung

Diese Anleitung beschreibt die Installation von Vaultwarden und wie du die einzelnen Schritte mit Ansible automatisieren kannst. Ziel ist es, Vaultwarden effizient und sicher einzurichten.

## Übersicht

Die Installation erfolgt in folgenden Schritten:

1. Docker-Repository hinzufügen

2. Docker und Docker Compose installieren

3. Docker aktivieren und starten

4. Verzeichnis für Vaultwarden erstellen

5. Docker-Compose-Datei für Vaultwarden erstellen

6. Vaultwarden mit Docker Compose starten


---

## Detaillierte Installationsanleitung

### 1. Docker-Repository hinzufügen

Um Docker zu installieren, musst du zunächst das Docker-Repository hinzufügen. Führe folgenden Befehl aus:
```shell
curl -o /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
```

**Automatisierung mit Ansible**

Verwende das Modul [ansible.builtin.get_url](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html), um die Repository-Informationen herunterzuladen.

---

### 2. Docker und Docker Compose installieren

Nachdem das Repository hinzugefügt wurde, installierst du Docker und Docker Compose mit folgendem Befehl:
```shell
dnf install -y docker-ce docker-ce-cli docker-compose-plugin
```
**Automatisierung mit Ansible**

Nutze das Modul [ansible.builtin.dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html) zur Installation der benötigten Pakete.

---

### 3. Docker aktivieren und starten

Nun muss docker mit folgenden Befehlen enabled und gestartet werden:
```shell
systemctl enable docker
systemctl start docker
```
**Automatisierung mit Ansible**

Nutze das Modul [ansible.builtin.systemd](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/systemd_module.html) zum Aktivieren und Starten des Docker-Dienstes.


---

### 4. Verzeichnis für Vaultwarden erstellen

Vaultwarden benötigt ein eigenes Verzeichnis für die Daten. Erstelle dieses Verzeichnis mit folgendem Befehl:
```shell
mkdir -p /opt/vaultwarden
chmod 0755 /opt/vaultwarden
```
**Automatisierung mit Ansible**

Verwende das Modul [ansible.builtin.file](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html), um das Verzeichnis /opt/vaultwarden zu erstellen und die entsprechenden Berechtigungen zu setzen.

---

### 5. Docker-Compose-Datei für Vaultwarden erstellen

Erstelle die ***docker-compose.yml***-Datei in deinem ***file***-Verzeichnis, um den Vaultwarden-Dienst zu definieren. Füge folgende Parameter in die Datei hinzu:

```yml
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    environment:
      DOMAIN: "LAB-ID+FQDN BITTE AUS TELEPORT ENTNEHMEN"
      SIGNUPS_ALLOWED: "true"
    volumes:
      - ./data:/data
    ports:
      - 8000:80
```

> [!IMPORTANT]
>
> Der Wert für die Variable `DOMAIN` (URL) ist in Teleport auf der Karte **labXXX-vaultarden** zu finden.

**Automatisierung mit Ansible**

Die Konfigurationsdatei mit der schon korrekt gesetzten `DOMAIN`-Variable ist schon im Verzeichnis `files` zu finden. Kopiere sie mit dem Modul [ansible.builtin.copy](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html) in das Verzeichnis `/opt/vaultwarden`.

---

### 6. Vaultwarden mit Docker Compose starten

Zum Starten von Vaultwarden verwende Docker Compose mit folgendem Befehl:
```shell
cd /opt/vaultwarden
docker compose up -d
```

> [!TIP]
> 
> Mit dem Befehl `docker compose ps` kannst du prüfen, ob die Container laufen. Der Healthcheck stimmt aktuell aufgrund eines Fehlers nicht. Mit `docker compose logs` kannst du die Logs einsehen


**Automatisierung mit Ansible**

Nutze das Modul [community.docker.docker_compose_v2](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_v2_module.html), um das Projekt Vaultwarden zu starten!

---

Damit ist die Installation von Vaultwarden abgeschlossen!