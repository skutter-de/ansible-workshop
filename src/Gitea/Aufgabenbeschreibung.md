# Aufgabenbeschreibung

Um Gitea mithilfe von Ansible zu installieren, orientieren wir uns an der [offiziellen Anleitung zur Installation von Gitea ](https://docs.gitea.com/installation/install-from-binary).

Die folgenden Schriite sollen per Ansible auf den Labs umgesetzt werden.


1. **Benutzer anlegen:** Es soll ein Gitea-User und die dazugehörige Gruppe erstellt werden, damit Gitea sicher und isoliert ausgeführt werden kann.
    Dementsprechend muss der Systemuser: **git** mit der Gruppe: **git** erstellt werden.

2. **Verzeichnisse anlegen:** Es müssen für die Installation mehrere Verzeichnisse angelegt werden.
    - /etc/gitea (root:git // 770)
    - unter /var/lib/gitea/ (git:git // 750)
        - custom
        - data
        - log

3. **Die Datei muss heruntergeladen werden:** Die Gitea Binary muss auf das System heruntergeladen werden und an einen globalen Ort mit frei zugänglichen Rechten hinterlegt werden. (/usr/local/bin/gitea)

4. **Der Gitea Service muss per Command oder Service gestartet werden:** Da die Installation damit fertig gestellt worden ist, muss letztendlich der Service gestartet werden. Dies kann entweder durch:
    - einen Shell-Command

    **oder**

    - durch das schreiben und kopieren einer [.service Datei](https://docs.gitea.com/installation/linux-service)

    erreicht werden.



Anschließend kann, sofern vorhanden, der systemd Service gestartet werden. 

