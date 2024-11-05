# Was ist Gitea?

Gitea ist ein selbst gehosteter All-in-One-Dienst für die Softwareentwicklung, einschließlich Git-Hosting, Code-Review, Teamzusammenarbeit, Paketregistrierung und CI/CD. 
Es ist Open Source und steht unter der MIT-Lizenz. 
Gitea ist leichtgewichtig, benutzerfreundlich und in hohem Maße anpassbar, was es letztendlich sehr flexibel macht.

Was macht ein Git-Service für einen Ansible Entwickler interessant?

- **Versionskontrolle**: Durch die Versionskontrolle von Gitea, können wir Änderungen nachverfolgen, ältere Versionen wiederherstellen und sehen, wer welche Änderungen vorgenommen hat.

- **Zusammenarbeit**: Mithilfe von Git können mehrere Entwickler am gleichen Code arbeiten. Features von Gitea wie z.B. dem Issue-Board und Merge-Requests ermöglichen zusätzlich ein einfaches Projektmanagement.

- **Automatisierung CI/CD**: Durch Continuous Integration (CI) und Continuous Deployment (CD) Pipelines kann man bei Änderungen im Code automatisiert Deployments durchführen.

- **Rollbacks**: Es ist einfach Änderungen rückgängig zu machen und zu einer früheren Version zurückzukehren, wenn Probleme auftreten. Gerade das ist bei einer automatisierten Infrastruktur mit Ansible wichtig. Allerdings wird das, was auf den Servern ausgerollt wurde, nicht zurückgespielt.


# Warum nun mit Ansible?

Die Installation von Gitea mit Ansible ist ein praktisches Beispiel dafür, wie einfach Softwarebereitstellungen und Konfigurationen automatisiert werden können. Ansible übernimmt hier die Aufgabe, die notwendigen Pakete zu installieren, Konfigurationsdateien bereitzustellen und den Gitea-Dienst zu starten. 

Durch ein wiederverwendbares Ansible-Playbook kann die Installation von Gitea schnell und konsistent auf mehreren Servern durchgeführt werden, ohne dass manuelle Eingriffe nötig sind. Dieser Ansatz soll zeigen, wie man Zeit spart, Fehlerquellen minimiert und zukünfitge Updates erleichtert.

