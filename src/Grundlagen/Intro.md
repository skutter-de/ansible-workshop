# Ansible Grundlagen

## Was ist Ansible?

Ansible ist eine Open Source Software zur Automatisierung von verschiedensten Geräten oder Services. Man kann mit Ansible sowohl Software automatisiert installieren, als auch die Konfiguration von Software automatisieren. Es ist auch möglich, Ansible zur Orchestrierung (bspw. zur Durchführung von Softwareupdates auf vielen Hosts gleichzeitig) zu verwenden. 

## Voraussetzungen für Ansible

### Control Node

Eine **Control Node** ist das System, auf dem die Ansible-CLI-Tools wie ansible-playbook, ansible, ansible-vault und andere ausgeführt werden. Jeder Computer, der die Softwareanforderungen erfüllt, kann als Control Node dienen – von Laptops und gemeinsam genutzten Desktops bis hin zu Servern. Ansible kann zudem in Containern wie Docker oder Podman betrieben werden. Für erweiterte Funktionen, wie eine grafische Benutzeroberfläche (GUI), eine API oder zusätzliche Steuerungsmöglichkeiten, stehen Tools wie die Ansible Automation Platform, die Open-Source-Variante AWX oder Semaphore zur Verfügung, die über die Funktionen der CLI-Tools hinausgehen.

#### Hardware

*Prozessor:* Mindestens ein Dual-Core-Prozessor wird empfohlen.

*RAM:* Mindestens 1 GB RAM für kleine Umgebungen, für größere Umgebungen wird mehr Arbeitsspeicher empfohlen.

*Festplatte:* Ansible selbst benötigt nur wenig Speicherplatz (wenige hundert MB). Allerdings kann der Speicherbedarf je nach Anzahl der Playbooks, Rollen und Logs steigen.

### Betriebssysteme

Für die **"Control Node"** kann nahezu jedes UNIX-ähnliche Betriebssystem verwendet werden, auf dem Python installiert ist. Dazu zählen Linux-Distributionen wie Red Hat Enterprise Linux, Debian oder Ubuntu, aber auch andere UNIX-ähnliche Systeme wie macOS oder BSD. Windows wird hingegen nicht nativ als Control Node für Ansible unterstützt. Mit dem Windows Subsystem for Linux (WSL) lässt sich jedoch ein Linux-System auf Windows ausführen, wodurch auch Windows als Control Node genutzt werden kann.

#### Python

Ansible erfordert **Python 3.8 oder höher**.
Die benötigten Python-Pakete und Abhängigkeiten werden automatisch installiert, wenn Ansible über **pip** oder ein Paketverwaltungssystem installiert wird.

### Managed Node

**Managed Nodes**, auch „Hosts“ genannt, sind die Zielsysteme (z.B. Server, Netzwerkgeräte oder andere Computer), die mit Ansible verwaltet werden können.

Es gibt keine spezifischen Hardwareanforderungen für Managed Nodes, allerdings müssen einige Softwarevoraussetzungen erfüllt sein. Bei der standardmäßigen Nutzung von SSH mit Ansible muss die Managed Node beispielsweise SCP oder SFTP unterstützen. Außerdem wird eine kompatible Python-Version auf der Managed Node benötigt.
Für spezielle Managed Nodes, wie Netzwerkgeräte oder Systeme, die nur über eine REST API gesteuert werden können, gelten andere Anforderungen. Diese variieren je nach Gerät und werden hier nicht im Detail behandelt.