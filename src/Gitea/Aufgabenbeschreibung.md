# Aufgabenbeschreibung

Diese Aufgabe führt dich durch die Installation des Git-Dienstes Gitea.

Ziel ist es, die Software zu installieren und dabei die Schritte so zu automatisieren, dass sie später auch mit Ansible ausgeführt werden können. Wir orientieren uns dabei an der offiziellen Installationsanleitung von Gitea.

## Schritte zur Installation:

1. Gitea-Benutzer erstellen:
    Damit Gitea sicher läuft, wird ein spezieller Benutzer git und eine gleichnamige Gruppe benötigt.
    Aufgabe: Erstelle den Benutzer git mit seiner Gruppe.

2. **Verzeichnisse anlegen:** Es müssen für die Installation mehrere Verzeichnisse angelegt werden.
    - /etc/gitea (root:git // 770)
    - unter /var/lib/gitea/ (git:git // 750)
        - custom
        - data
        - log
3. Gitea-Binary herunterladen:
    Lade die aktuelle Gitea-Binary-Datei herunter.
    Speicher die Datei in **/usr/local/bin/gitea** und stelle sicher, dass sie ausführbar ist.

4. Gitea-Service starten:
Starte Gitea entweder direkt über die Kommandozeile oder durch das Erstellen einer .service-Datei:


    **Option 1:** Kommandozeile: Führe das Gitea-Startkommando aus.

        
    **Option 2:** Erstelle eine .service-Datei und aktiviere sie mit systemd.

**Nächste Schritte:**

Erstelle eine ***gitea-install.yml*** und schreibe darin deinen Code!
Nutze Ansible, um die Aufgaben zu automatisieren. Hinweise dazu findest du in der manuellen Installationsanleitung.

Viel Erfolg bei der Installation! 🛠️