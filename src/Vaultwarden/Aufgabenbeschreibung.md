# Aufgabenbeschreibung

Ziel dieser Aufgabe ist die Installation des Passwortmanager-Services Vaultwarden. Hier wird eine manuelle Installation, d.h. ohne fertiges Paket, durchgeführt. Installationspakete nehmen einem einige Schritte ab, die hier durch eine manuelle Installation erforderlich sind.


Die folgenden Schritte sollen per Ansible oder manuell auf den Systemen umgesetzt werden.

Zu deiner Referenz ist unter [Manuelle Installation](./Manuelle%20Installation.md) eine vollständig manuelle Installation dokumentiert. Dort findest du auch einige Tipps zur Automatisierung mit Ansible.


1. **Docker-Umgebung bereitstellen:**
Stelle sicher, dass Docker korrekt läuft und der aktuelle Benutzer die notwendigen Berechtigungen hat, um Docker-Container zu verwalten.
Optional: Installiere docker-compose, falls erforderlich.


1.5?. **Netzwerk und Benutzer anlegen + Speicherort:**
Für die Container-Isolation und Sicherheit:
Ein Docker-Netzwerk für Vaultwarden erstellen (z. B. vaultwarden-net).
Sicherstellen, dass der Vaultwarden-Container in einer isolierten Umgebung läuft.


2. **Docker-Container für Vaultwarden anlegen:**
Erstelle eine docker-compose.yml mit den notwendigen Parametern.

3. **Docker-Container starten:**
Der Docker Container muss nun gestartet werden.
