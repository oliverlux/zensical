---
icon: lucide/monitor-play
---

# Umgang mit Virtuellen Maschinen (VM)

## Starten von VMs
Für die VMs im Unterricht ist der [VMWare Workstation Player](https://www.vmware.com/ch/products/workstation-player/workstation-player-evaluation.html) notwendig. Zudem muss die Virtualisierung im BIOS des Rechners eingeschaltet sein. Die VMs (und der VMWare Workstation Player) liegen unter [MyDrive](https://mydrive.ch) und die Logindaten können bei der Lehrperson bezogen werden.

## Internetzugriff für VMs
Standardmässig haben die VMs keinen Internetzugriff. Falls Sie Zugriff auf das Internet benötigen, müssen Sie zuerst die `vmLF1` (Linux-Firewall) starten. Nachdem die `vmLF1` gestartet ist (kein Login notwendig) und geöffnet bleibt, sollten Sie Internetzugriff in den anderen VMs haben.
In einem PC-Labor am GBS muss die Lehrperson den Internet-Zugriff der VM freigeben. Bitte fragen Sie daher zuerst die Lehrperson, bevor Sie die `vmLF1` gemäss oben starten.

## Windows Lizenz verlängern
Wenn in der VM der Hinweis erscheint, dass die Windows-Lizenz abläuft, kann diese mit dem folgenden Vorgehen verlängert werden.

- CMD starten
- Befehl `slmgr -rearm` absetzen
- VM neu starten