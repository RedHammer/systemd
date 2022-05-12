# systemd
info zum autostrart

Einen eigenen Service erstellen
Der Service wird unter /etc/systemd/system angelegt. Dabei kann der Name beliebig gewählt werden.

Unter Umständen muss die Berechtigung geändert werden:
sudo chmod 644 /lib/systemd/system/test.service

cd /etc /systemd /system
nano your-service.service
In die Datei your-service.service muss folgendes eingetragen werden:

[Unit]
Description=Example systemd service.

[Service]
Type=simple
ExecStart=/bin/bash /path/to/your-script.sh

[Install]
WantedBy=multi-user.target

Unit – In diesem Block können Abhängigkeiten von anderen Services beschrieben werden, aber auch die Beschreibung für den eigentlichen Service selbst.

Service - Hier werden genaue Anweisungen für den Service definiert.

Install - Beschreibt alle benötigten Informationen um den Service beim Systemstart zu starten.

Für weitere Informationen zu der Service-Datei, empfehle ich die Doku von Red Hat.

Nach der Erstellung der Datei kann der Service bei jedem Neustart ausgeführt werden:

systemctl enable your-service.service
