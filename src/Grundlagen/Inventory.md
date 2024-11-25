# Inventory

Ein Ansible Inventory organisiert Hosts und Gruppen, um sie gezielt in Playbooks ansprechen zu können, und erlaubt die Festlegung von Variablen und Verbindungsparametern für eine flexible und effiziente Verwaltung.

Das Inventory kann in einer einfachen INI-Datei oder in YAML verfasst sein und ermöglicht es, Hosts in logische Gruppen zu unterteilen.

Eine beispielhafte Inventory-Datei könnte wie folgt aussehen:

``` yml
webserver:
  hosts:
    web1.example.com:
    web2.example.com:
    combined-host-1.example.com:
databases:
  hosts:
    db1.example.com:
    db2.example.com:
    combined-host-1.example.com:
```


In diesem Inventory-Beispiel werden die Hosts in zwei logische Gruppen aufgeteilt: **webserver** und **databases**.

Jede Gruppe enthält spezifische Hosts. Diese Unterteilung erleichtert es, bestimmte Playbooks gezielt auf die jeweiligen Hosts anzuwenden.

In diesem Beispiel kommt der Host ***combined-host-1.example.com*** in beiden Gruppen vor. Das ist zulässig und unter gewissen Umständen sinnvoll. Wenn nun ein Playbook ausgeführt wird und auf die Gruppe ***webserver*** abzielt, wird dieser eben wie ein Webserver behandelt. Bei ***databases*** verhält es sich genau so. Wichtig ist hierbei jedoch, dass es keine doppelten Ausführungen gibt, sollten beide Gruppen angesprochen werden.


### Aufgabe: Schreibe ein Inventory für das Lab!

Es soll ein Inventory geschrieben werden, welches in diesem Lab benutzt werden kann.
In diesem soll es eine Gruppe **all** geben, mit folgenden Hosts:
- **git.lab.internal**
- **vault.lab.internal**


Hier ist die [Lösung](Inventory%20Lösung.md)
