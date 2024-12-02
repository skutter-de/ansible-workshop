# Installation von Vaultwarden – Aufgabenbeschreibung

Diese Aufgabe führt dich durch die Installation der Passwortverwaltung Vaultwarden.

Ziel ist es, die Software zu installieren und die Schritte so zu automatisieren, dass sie später auch mit Ansible ausgeführt werden können. Wir orientieren uns dabei an den offiziellen Installationsschritten und setzen sie mit Ansible um.

Die folgenden Schritte sollen per Ansible oder manuell auf den Systemen umgesetzt werden.

Zu deiner Referenz ist unter [Manuelle Installation](./Manuelle%20Installation.md) eine vollständig manuelle Installation dokumentiert. Dort findest du auch einige Tipps zur Automatisierung mit Ansible.


## Schritte zur Installation:

**1. Docker-Repository hinzufügen:**
Um Docker zu installieren, muss zunächst das Docker-Repository hinzugefügt werden.


**2. Docker und Docker Compose installieren:**
Installiere Docker und Docker Compose, um die Vaultwarden-Umgebung bereitzustellen.


**3. Docker aktivieren und starten:**
Damit Docker automatisch gestartet wird, aktiviere und starte den Docker-Dienst.



**4. Verzeichnis für Vaultwarden erstellen:**
Vaultwarden benötigt ein eigenes Verzeichnis, in dem die Daten gespeichert werden.


**5. Docker-Compose-Datei für Vaultwarden erstellen:**
Erstelle eine docker-compose.yml-Datei, um den Vaultwarden-Dienst zu definieren.


**6. Vaultwarden mit Docker Compose starten:**
Starte Vaultwarden mit Docker Compose.



## Nächste Schritte:

Erstelle ein Ansible-Playbook namens `vaultwarden-install.yml` und schreibe darin den Code, um die oben genannten Aufgaben zu automatisieren. Hinweise dazu findest du in der detaillierten Installationsanleitung.

**Viel Erfolg bei der Installation!**
