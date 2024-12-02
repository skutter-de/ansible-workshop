# Lösung

Auf dieser Seite befindet sich ein Lösungsbeispiel für die automatisierte Installation von Gitea mittels eines Binaries.

### Playbook-Header:

Wie schon erwähnt, besteht ein Playbook aus einem oder mehreren Plays. Daher ist das Hauptelement der Datei eine Liste, darum beginnt die erste Zeile mit einem `- `.

Als nächstes geben wir dem Play einen Namen. Plays einen Namen zu geben ist zwar nicht zwingend erforderlich, aber empfohlen.

Unter `hosts` geben wir an, auf welchen Hosts das Play ausgeührt werden soll. Hier kann verschiedenes angegeben werden, bspw. einzelne Hosts, eine Liste von Hosts; auch Gruppen können angegeben werden. Man kann auch bestimmen, dass sich ein Host in mehreren Gruppen befinden muss, oder man kann einzelne Hosts oder Gruppen ausschließen. Hier sprechen wir direkt den Host `git.lab.internal` an.

Mit `remote_user` geben wir an, als welcher User sich Ansible auf dem Zielsystem anmelden soll. Dafür verwenden wir hier `root`. Es ist auch möglich, andere User anzugeben, dafür muss der User aber sudo-Rechte haben und muss mit `become: true` angeben, dass Ansible sich zu `root` machen soll.

``` yml
{{#include gitea_install.yml:1:4 }}
```

### Erstellen der Gruppe "git"

Mit dem Modul [ansible.builtin.group](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/group_module.html) können Gruppen erzeugt werden. Hier genügt der Name der Gruppe im Parameter `name` sowie die Angabe, ob die Gruppe existieren soll (`present`) oder nicht (`absent`). Dies wird im Parameter `state` angegeben. Wir wollen allerdings keine normale sondern eine System-Gruppe anlegen, daher müssen wir noch den Parameter `system` übergeben.

``` yml
{{#include gitea_install.yml:5:9 }}
```

### Erstellen des Benutzers "git"

Mit dem Modul [ansible.builtin.user](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html) werden Benutzer angelegt. Um den Benutzer für Gitea anzulegen, brauchen wir einige Parameter:

- `name` gibt den Namen des Benutzers an. Hierbei ist allerdings nicht der "Volle Name" des Benutzers gemeint, dieser wird mit dem Feld `comment` angegeben.
- `comment` ist der eben erwähnte "Volle Name" des Benutzers.
- `group` gibt an, welcher Gruppe der Benutzer angehört
- `system` gibt an, ob es sich hierbei um einen Systembenutzer handelt.
- Mit `create_home` wird abgegeben, dass für den Benutzer ein Home-Verzeichnis angelegt werden soll.
- Der gewünschte Pfad für das Home-Verzeichnis wird mit `home` angegeben.
- Als Standardshell wird `/bin/bash` gefordert, diese wird in `shell` hinterlegt.
- Zuletzt geben wir mit `state` an, ob der Benutzer existieren soll oder nicht.

``` yml
{{#include gitea_install.yml:11:20 }}
```

### Erstellen der Gitea Verzeichnisse mittels einer Schleife

Da wir hier 3 Verzeichnisse mit den gleichen Berechtigungen anlegen, werden wir hier das erste mal eine Schleife verwenden. Wie schon in den Grundlagen erwähnt wird das aktuelle Element in der Variable `item` gespeichert. Dies nutzen wir hier, um die frei Unterverzeichnisse `custom`, `data` und `log` unter `/var/lib/gitea` anzulegen.

``` yml
{{#include gitea_install.yml:22:32 }}
```

### Erstellen des /etc/gitea Verzeichnisses mit spezifischen Rechten

Hier wird, ähnlich wie beim vorherigen Task, das Verzeichnis `/etc/gitea` mit den entsprechenden Rechten angelegt. Hier brauchen wir keine Schleife, daher steht hier im Parameter `path` direkt der ganze Pfad.

``` yml
{{#include gitea_install.yml:34:40 }}
```

### Herunterladen der Gitea Binary und ablegen in ein globales Verzeichnis

Mit disem Task wird die Gitea Binary von dem Anbieter heruntergeladen. Erklärung der Parameter:

- `url`: Die zu ladende URL
- `dest`: Der Pfad auf dem Zielsystem, auf dem die Datei abgelegt werden soll
- `owner`: Der Besitzer der Datei
- `group`: Die Gruppe der Datei
- `mode`: Die Rechte der Datei

``` yml
{{#include gitea_install.yml:42:48 }}
```

### Kopieren der gitea.service Datei auf den Zielhost

Mit dem [`ansible.builtin.copy`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html) Modul wird die `gitea.service` Datei von dem Controller aus das Zielsystem hochgeladen. Erklärung der Parameter:

- `dest`: Der Pfad auf dem Zielsystem, auf dem die Datei abgelegt werden soll
- `owner`: Der Besitzer der Datei
- `group`: Die Gruppe der Datei
- `mode`: Die Rechte der Datei

``` yml
{{#include gitea_install.yml:50:56 }}
```

### Aktivieren des Systemd Services mit anschließendem Daemon-Reload

``` yml
{{#include gitea_install.yml:58:63 }}
```

## Fertiges Playbook


``` yml
{{#include gitea_install.yml }}
```



### Das ist natürlich nur ein Lösungsvorschlag.