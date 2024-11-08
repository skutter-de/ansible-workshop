# Warum automatisieren?

Automatisierung kann ein komplexes Thema sein, das viele Vor- und auch einige Nachteile mit sich bringt.

## Vorteile

- Wenn man einmal automatisiert hat, kann man damit immer wieder den gwünschten Stand herstellen. Dadurch ist die Anpassung der Konfiguration recht einfach und ein Neudeployment auf einer neuen Maschine unkompliziert.
- Man kann durch die Automatisierung einen bestimmten Zustand wahren. Es ist möglich, manuell getätigte Änderungen zurückzuspielen, um wieder zu dem in der Automatisierung festgelegten Standard zurückzukehren.
- Ansible ist durch seine gute Lesbarkeit selbstdokumentierend. Man muss keine separate Dokumentation für die Installation schreiben, da der Ansible Code die Dokumentation recht gut ersetzen kann.
- Automatisierung eignet sich auch, um komplexe Umgebungen aus mehreren Komponenten aufzusetzen. Durch immer wiederkehrende, gleiche Abläufe werden dabei Fehlerquellen ausgeschlossen.
- Dadurch, dass die Automatisierungen als Code geschrieben wird, ist die Konfiguration der Systeme leicht auditierbar, da man sich nicht jedes System einzeln sondern nur die Automatisierung der Systeme anschauen kann.
- Wiederkehrende Aufgaben, bspw. Software-Updates, können durch Automatisierung stark vereinfacht und beschleunigt werden. Dinge, wie z.B. die Aktualisierung von Servern nacheinander, und nur wenn der vorherige Server wieder erreichar ist, lässt sich dadurch ztuverlässig umsetzen.

## Nachteile

- Du musst das entsprechende Wissen haben oder aufbauen, um automatisieren und vor allem die Automatisierung langfristig betreiben zu können. Änderungen sollten natürlich nur in der Automatisierung und nicht manuell vorgenommen werden.
- Man macht sich von der Automatisierung abhängig. Wenn es Probleme mit der Automatisierung, oder den Systemen, gibt, ist durch die Automatisierung der Prozesse möglicherweise Fachwissen über die manuellen Prozesse verloren gegangen, was die Fehlerbehebung negativ beeinträchtigen kann. Außerdem ist man mehr oder weniger handlungsunfähig, wenn die Automatisierung ausfällt.
- Wenn es Änderungen an dem Automatisierungstool gibt, entstehen eventuell ungeplante Aufwände, um die Automatisierung anzupassen.
- Wenn du Automatisierung fehlerhaft ist, kann man die ganze Umgebung lahm legen.
- Fehlerhafte Automatisierung kann ein Einfallstor für Angreifer bieten, da man bei Übernahme der steuernden Instanz großflächig Backdoors deployen oder andere Schäden anrichten kann.
- Die Behandlung von Spezialfällen verursacht zusätzliche Aufwände.