# Warum automatisieren?

Automatisierung kann ein komplexes Thema sein, das viele Vor- und auch einige Nachteile mit sich bringt.

## Vorteile

- Einmal automatisiert, ermöglicht es Ansible, den gewünschten Systemzustand jederzeit wiederherzustellen. Dies erleichtert nicht nur die Anpassung von Konfigurationen, sondern macht auch ein Neudeployment auf einer neuen Maschine unkompliziert.
- Durch die Automatisierung kann ein bestimmter Standard dauerhaft gewahrt werden. Manuell vorgenommene Änderungen lassen sich zurücksetzen, sodass der ursprünglich definierte Zustand wiederhergestellt werden kann.
- Ansible ist durch seine gute Lesbarkeit selbstdokumentierend. Separate Installationsdokumentationen sind oft überflüssig, da der Ansible-Code als umfassende Dokumentation dient.
- Automatisierung ist besonders hilfreich, um komplexe Umgebungen mit mehreren Komponenten aufzubauen. Wiederholbare und konsistente Abläufe minimieren dabei potenzielle Fehlerquellen.
- Da die Automatisierung als Code geschrieben wird, ist die Systemkonfiguration leicht auditierbar. Statt jedes System einzeln zu prüfen, genügt ein Blick auf den Automatisierungscode, um den Zustand und die Konfiguration der Systeme nachzuvollziehen.
- Wiederkehrende Aufgaben wie Software-Updates können durch Automatisierung erheblich vereinfacht und beschleunigt werden. Szenarien wie das schrittweise Aktualisieren von Servern, bei dem der nächste Server erst nach erfolgreicher Verfügbarkeit des vorherigen aktualisiert wird, lassen sich zuverlässig und effizient umsetzen.

## Nachteile

- Um Automatisierung erfolgreich umzusetzen und langfristig zu betreiben, ist entsprechendes Wissen erforderlich, das zunächst aufgebaut und kontinuierlich erweitert werden muss. Änderungen sollten ausschließlich über die Automatisierung erfolgen, nicht manuell, um Konsistenz zu gewährleisten.
- Automatisierung bringt eine gewisse Abhängigkeit mit sich. Treten Probleme mit der Automatisierung oder den Systemen auf, könnte das Wissen über die manuellen Prozesse durch den automatisierten Betrieb verloren gehen, was die Fehlerbehebung erschwert. Bei einem Ausfall der Automatisierung ist man zudem oft handlungsunfähig.
- Änderungen am genutzten Automatisierungstool können ungeplanten Anpassungsaufwand verursachen, um die bestehenden Prozesse an die neuen Gegebenheiten anzupassen.
- Fehler in der Automatisierung können weitreichende Konsequenzen haben und im schlimmsten Fall die gesamte Umgebung beeinträchtigen oder lahmlegen.
- Eine unsichere oder fehlerhafte Automatisierung kann zudem ein potenzielles Sicherheitsrisiko darstellen. Wird die steuernde Instanz kompromittiert, könnten Angreifer großflächig Backdoors einrichten oder andere Schäden verursachen.
- Die Behandlung von Sonderfällen innerhalb der Automatisierung führt häufig zu zusätzlichen Aufwand, da diese nicht immer leicht in standardisierte Prozesse zu integrieren sind.