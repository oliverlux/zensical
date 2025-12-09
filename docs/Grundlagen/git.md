---
icon: lucide/github
---

# Git

## Git Grundbefehle

### Git-Projekt aufsetzen
Mittels Terminal in das entsprechende Verzeichnis navigieren, in dem das entsprechende Projekt liegt. Danach mit `git init` ein neues Git-Repository anlegen. Falls bereits ein lokales / entferntes Git-Repository besteht, kann es in das entsprechende Verzeichnis mittels `git clone ...` kopiert werden. Entweder kann dazu die URL oder SSH verwendet werden.

### Remote Repositories
Generell sind alle Repositories die nicht lokal sind, als Remote Repositories bezeichnet. Das geklonte Repository heisst *origin*. Mit `git remote add name url` wird ein Repository von url mit name hinzugefügt. Mittels `git remote` können alle bekanntgemachten Repos angezeigt werden.

Um ein lokales Repo mit einem entfernten Repo bekannt zu machen, kann der Befehl `git remote add origin https://gitExample.com/user/repository.git` verwendet werden. 

### Änderungen hochladen

1. Geänderte Datei zum Staging hinzufügen: `git add datei` oder `git add *`.
2. Commit aller Dateien aus dem Stage: `git commit -m "Commit Nachricht"`.
3. Commits zum Repo pushen: `git push`.

Bei Pushen wird standardmässig der Master-Branch gepusht. Wenn ein Repo von mehreren Personen verwaltet wird, ist es sinnvoll mit Branches zu arbeiten. Diese können unabhängig abgeändert und am Ende wieder mit dem Master gemerged werden.

### Suchen im Repository

Der Befehl `git log --oneline` zeigt eine Übersicht aller Snapshots mit Hash-Wert und Kurzkommentar an. Mit `git log --name-only` werden nur die geänderten Dateien angezeigt und mit `git log --name-only --oneline --graph` das Ganz übersichtlich und grafisch dargestellt.

### Daten wiederherstellen

Um Daten wiederherzustellen gibt es verschiedene Ansätze:

1. Mit `git checkout <snapshot>` wird das Arbeitsverzeichnis auf einen älteren Snapshot gewechselt. Danach können die betroffenen Dateien kopiert werden. Mit `git checkout master` wird wieder in den Main-Branch gewechselt und die kopierten Daten können hinzugefügt werden.
2. Mit `git reset --hard <snapshot>` kann bis zum entsprechenden Snapshot alles "zurückgestellt" werden, d.h. alle Änderungen werden unwiederruflich zurückgesetzt. 
3. Mit `git revert <snapshot>` können die Änderungen, die mit dem entsprechenden Snapshot eingeflossen sind, wieder rückgängig gemacht werden. Die nachfolgenden Änderungen werden nicht angetastet. Schwierig wird es, wenn Dateien bei späteren Snapshots nochmals geändert wurden. Dann erscheinen Merge-Fehlermeldungen.

### Branching

1. Mit `git checkout -b feature` wird ein feature-Branch erstellt und das Repo automatisch darauf gewechselt. Besteht der Branch bereits, kann mit `git checkout feature` darauf gewechselt werden. Sämtliche Änderungen an diesem Branch können wie oben beschrieben vorgenommen werden. Um einen lokalen Branch auf das entfernte Repo zu pushen, kann der Befehl `git push origin feature` verwendet werden.
2. Mittels `git checkout master` und danach `git merge feature` können die Änderungen aus dem Feature-Branch in den Master gemergt werden. Um einen nicht mehr benötigten Branch zu löschen kann `git branch -d feature` abgesetzt werden.

### Lokales Repository aktualisieren
1. Änderungen vom Repo herunterladen: `git fetch` und mit `git merge` die Änderungen mergen. Mittels `git pull` können beide Befehle gleichzeitig ausgeführt werden.
2. Mögliche Merge-Konflikte müssen von Hand korrigiert werden.

### Zusätzliche Befehle

#### Nutzerinformationen anpassen
```
git config --global user.name "Max Muster"
git config --global user.email "max@muster.ch"
```


## Github

### SSH-Verbindung
Um mittels SSH auf Github zugreifen zu können, muss zuerst ein SSH-Schlüsselpaar generiert werden. Der Public-Key wird danach dem Github-Account und der Private-Key dem lokalen SSH-Agenten hinzugefügt.

#### Neuen SSH-Key generieren
In der Bash mittels `$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` ein neues Schlüsselpaar generieren

#### Public-Key Github Account hinzufügen
In den Einstellungen des eigenen Github-Accounts unter SSH-Keys den Public-Key hinzufügen.

#### Private-Key dem SSH-Agenten hinzufügen
Mittels `eval $(ssh-agent -s)` überprüfen, ob eine PID ausgegeben wird und damit der SSH-Agent läuft. Danach über `ssh-add ~/.ssh/id_rsa` den Private-Key dem SSH-Agenten hinzufügen. Dazu muss das entsprechende Passwort eingegeben werden (wenn der private Schlüssel mittels Passwort geschützt ist).

Um bereits beim Start der Bash den Private-Key dem SSH-Agenten hinzuzufügen, kann beim Start der Bash folgendes hinzugefügt werden...

!Todo


### Github Actions