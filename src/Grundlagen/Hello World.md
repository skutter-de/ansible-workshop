# Hello World! Dein erstes Playbook

Auf dieser Seite lernst du, ein einfaches Ansible-Playbook zu erstellen und auszuführen. Dieses Playbook gibt eine "Hello-World"-Nachricht auf jedem Host aus, den du in deinem Inventory definiert hast.

Dafür erstellst du nun eine Datei namens **hello-world.yml** und fügst folgendes Playbook ein.

### Hello-World Playbook

```yaml
- name: Hello World Playbook  # Name des gesamten Plays
  hosts: all                  # Definiert, auf welche Hosts dieses Playbook angewendet wird
  remote_user: root           # es soll sich als root user auf den Zielsystem authorisiert werden
  become: false               # Erlaubt die Ausführung von Aufgaben mit erhöhten Rechten (root)
  tasks:                      # Liste der Aufgaben, die auf den Hosts ausgeführt werden sollen
    - name: Print Hello World message
      ansible.builtin.debug:  # Ansible-Modul "debug", das eine Nachricht ausgibt
        msg: "Hello, World!"  # Die Nachricht, die angezeigt werden soll
```

**name:** Ein Name für das Playbook, mit den Zweck das Playbook zu erkennen.

**hosts:** Gibt die Hosts an, auf denen das Playbook ausgeführt werden soll. Hier verwenden wir ***all***

**remote_user:** Hier legst du fest, mit welchem User du dich auf die Zielsysteme verbindest.

**become:** Führt die Aufgaben mit erhöhter Berechtigung aus. Wenn du dich nicht als ***root*** anmeldest, muss hier **true** gesetzt werden!

**tasks:** Hier werden die Aufgaben definiert, die in diesem Playbook ausgeführt werden sollen. In unserem Fall soll das Debug-Modul die "Hello-World" Nachricht ausgeben.


### Ausführung des Playbooks

Nun kannst du das Playbook ausführen. Verwende dafür den folgenden Befehl:

``` shell
ansible-playbook -i inventory/inventory.yml hello-world.yml
```

### Ausgabe des Playbooks

Anbei ist die Ausgabe, welche durch das Playbook erzeugt wird.

```
PLAY [Hello World Playbook] ***************************************************************

TASK [Print Hello World message] **********************************************************
ok: [hostname] => {
    "msg": "Hello, World!"
}
```



#### **Damit hast du erfolgreich dein erstes Ansible-Playbook geschrieben und ausgeführt. Dies ist eine gute Grundlage um die folgenden Aufgaben dieses Labs zu verstehen und zu meistern!**