# Ansible Grundlagen
- [ ]## Was ist Ansible?

# Was ist Ansible?
Ansible ist ein leistungsfähiges Open-Source-Tool für IT-Automatisierung, das die Bereitstellung und Verwaltung von IT-Infrastruktur in einem konsistenten, reproduzierbaren und agentenlosen Ansatz ermöglicht. Es ist besonders beliebt für Aufgaben wie Konfigurationsmanagement, Softwarebereitstellung, Netzwerkautomatisierung und Orchestrierung komplexer Workflows.


## Vorteile von Ansible
- **Einfachheit und Benutzerfreundlichkeit:** Ansible verwendet YAML, was leicht zu lesen und zu verstehen ist.
- **Agentenlose Architektur:** Durch die agentenlose Struktur ist Ansible einfach zu verwalten und sicher, da keine zusätzliche Software auf den Zielsystemen erforderlich ist.
- **Schnell und zuverlässig:** Ansible ist durch seine einfache Konfiguration und agentenlose Architektur schnell einsetzbar und reduziert die Zeit für Implementierung und Ausführung von Aufgaben.
- **Hohe Flexibilität:** Es unterstützt eine Vielzahl von Plattformen und kann in heterogenen Umgebungen eingesetzt werden – ob Cloud, On-Premises oder hybride Infrastruktur.
- **Aktive Community und Erweiterbarkeit:** Ansible hat eine große und aktive Community, die viele Plugins, Module und Erweiterungen für Ansible entwickelt, wodurch das Tool ständig verbessert und erweitert wird.

## Voraussetzungen

### Python

Ansible erfordert **Python 3.8 oder höher** (Python 2.7 ist ebenfalls kompatibel, aber Python 3 wird empfohlen, da Python 2.7 veraltet ist).
Die benötigten Python-Pakete und Abhängigkeiten werden automatisch installiert, wenn Ansible über **pip** oder ein Paketverwaltungssystem installiert wird.

### Hardware

**Prozessor:** Mindestens ein Dual-Core-Prozessor wird empfohlen.

**RAM:** Mindestens 1 GB RAM für kleine Umgebungen, für größere Umgebungen wird mehr Arbeitsspeicher empfohlen.

**Festplatte:** Ansible selbst benötigt nur wenig Speicherplatz (wenige hundert MB). Allerdings kann der Speicherbedarf je nach Anzahl der Playbooks, Rollen und Logs steigen.

### Control Node

Eine **Control Node** ist das System, auf dem die Ansible-CLI-Tools wie ansible-playbook, ansible, ansible-vault und andere ausgeführt werden. Jeder Computer, der die Softwareanforderungen erfüllt, kann als Control Node dienen – von Laptops und gemeinsam genutzten Desktops bis hin zu Servern. Ansible kann zudem in Containern wie Docker oder Podman betrieben werden. Für erweiterte Funktionen, wie eine grafische Benutzeroberfläche (GUI), eine API oder zusätzliche Steuerungsmöglichkeiten, stehen Tools wie die Ansible Automation Platform, die Open-Source-Variante AWX oder Semaphore zur Verfügung, die über die Funktionen der CLI-Tools hinausgehen.

### Managed Node

**Managed Nodes** werden auch als „Hosts“ bezeichnet und sind die Zielgeräte (Server, Netzwerkgeräte oder beliebige Computer), die mit Ansible verwaltet werden können.

# Ziele des jeweiligen Aufbaus ???

Für die **"Control Node"** (das System, auf dem Ansible läuft) kann fast jeder UNIX-ähnlichen Rechner verwenden, auf dem Python installiert ist. Dazu gehören Red Hat, Debian, Ubuntu, macOS, BSD und Windows unter einer Windows Subsystem for Linux (WSL) Distribution. Windows ohne WSL wird nicht von Haus aus als "Control Node" unterstützt;



# Verlinkungen
#   ansible galaxy
#   ansible docs
#   github ansible
#   netapp --> Zur Not nur zur Präsentation
#   redhat ansible




# Einfache Ansible Befehle



# Coole Tipps zum arbeiten in VSC mit Ansible

