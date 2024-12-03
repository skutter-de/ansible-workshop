# Vaultwarden

Vaultwarden ist eine leichtgewichtige, quelloffene Alternative zum beliebten Passwortmanager Bitwarden, die speziell für das Selbst-Hosting entwickelt wurde. 

Während Bitwarden auf eine proprietäre Serverlösung setzt, bietet Vaultwarden eine effiziente und minimalistische Implementierung des Serverteils in Rust. Vaultwarden ist vollständig kompatibel mit den offiziellen Bitwarden-Clients (Web, Desktop, Mobile und Browser-Erweiterungen), was eine nahtlose Integration gewährleistet.


### Was macht eine Vaultwarden-Instanz für uns als Ansible-Entwickler interessant?

- **Infrastruktur als Code (IaC) in der Praxis**: Vaultwarden bietet ein reales Szenario, um die Prinzipien von IaC anzuwenden. Durch die Erstellung von Ansible-Playbooks zur Installation, Konfiguration und Verwaltung von Vaultwarden kannst du zeigen, wie Infrastruktur mit Code beschrieben und wiederholbar bereitgestellt wird.

- **Sicherheit automatisieren**: Vaultwarden ist ein sicherheitskritischer Dienst, da es sensible Daten wie Passwörter und Identitäten verwaltet. Du kannst automatisiert Benutzer und Berechtigungen anlegen und anpassen.

- **Integration in DevOps-Workflows**: Vaultwarden kann als zentraler Dienst in DevOps-Prozesse integriert werden, z. B. durch die Speicherung und Verwaltung von Zugangsdaten für andere automatisierte Workflows.

- **Automatisierte Verwaltung und Updates**: Die Wartung ist vollends mit Ansible möglich. Das beinhaltet Updates, Backups und auch die Service-Überwachung



### Zusammengefasst ist Vaultwarden eine exzellente Plattform, um die Vielseitigkeit und die Vorteile von Ansible zu präsentieren.