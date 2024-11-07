# Ansible Grundlagen

## Was ist Ansible?

Ansible ist eine Open Source Software zur Automatisierung von verschiedensten Geräten oder Services. Man kann mit Ansible sowohl Software automatisiert installieren, als auch die Konfiguration von Software automatisieren. Es ist auch möglich, Ansible zur Orchestrierung (bspw. zur Durchführung von Softwareupdates auf vielen Hosts gleichzeitig) zu verwenden. 

## Voraussetzungen für Ansible

### Control Node

Eine **Control Node** ist das System, auf dem die Ansible-CLI-Tools (ansible-playbook, ansible, ansible-vault und andere) ausgeführt werden können. Es kann jeder Computer, der die Softwareanforderungen erfüllt, als Control Node verwenden - Laptops, gemeinsam genutzte Desktops und Server können alle Ansible ausführen. Es kann Ansible auch in Containern (Docker, Podman) ausgeführt werden. Außerdem gibt es Software wie die Ansible Automation Platform (oder die Open Source Variante AWX) oder Semaphore, die über die CLI Tools hinaus viele zusätzliche Funktionen bieten (GUI, API, mehr Steuerungsmöglichkeiten, etc).

#### Hardware

**Prozessor:** Mindestens ein Dual-Core-Prozessor wird empfohlen.

**RAM:** Mindestens 1 GB RAM für kleine Umgebungen, für größere Umgebungen wird mehr Arbeitsspeicher empfohlen.

**Festplatte:** Ansible selbst benötigt nur wenig Speicherplatz (wenige hundert MB). Allerdings kann der Speicherbedarf je nach Anzahl der Playbooks, Rollen und Logs steigen.

#### Betriebssysteme

Für die **"Control Node"** kann fast jedes UNIX-ähnliche Betriebssystem verwenden, auf dem Python installiert ist. Dazu gehören Linux Distributionen wie Red Hat Enterprise Linux, Debian, oder Ubuntu, sowie andere UNIX-ähnliche Systeme wie macOS, BSD. Windows direkt wird nicht als Control Node für Ansible unterstützt, allerdings kann man hierfür das Windows Subsystem für Linux (WSL) verwenden, da man hiermit ein Linux erhält.

#### Python

Ansible erfordert **Python 3.8 oder höher**.
Die benötigten Python-Pakete und Abhängigkeiten werden automatisch installiert, wenn Ansible über **pip** oder ein Paketverwaltungssystem installiert wird.

### Managed Node

**Managed Nodes** werden auch als „Hosts“ bezeichnet und sind die Zielgeräte (Server, Netzwerkgeräte oder beliebige Computer), die mit Ansible verwaltet werden können.

Bestimmte Hardwareanforderungen gibt es hier nicht, allerdings müssen softwarseitig einige Dinge beachtet werden, bspw. muss bei Verwendung von SSH (Standard bei Ansible) SCP/SFTP möglich sein. Außerdem muss auf der Managed Node eine unterstützte Version von Python installiert sein. Für andere Arten von Managed Nodes, bspw. Netzwerkgeräten oder Geräten, die nur über eine REST API verfügen, gibt es andere Anforderungen, auf die hier allerdingss nicht näher eingegangen wird, da es von Gerät zu Gerät unterschiedlich sein kann.