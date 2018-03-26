# M300
TBZ

**Mit Repository arbeiten:**

git clone git@github.com:P3RF3KT/M300.git

# add & commit
Du kannst �nderungen vorschlagen (zum Index hinzuf�gen) mit
** gti add **

Das ist der erste Schritt im git workflow, man best�tigt die �nderungen mit:

** git commit -m "Commit-Nachricht"

Jetzt befindet sich die �nderung im HEAD, aber noch nicht im entfernten Repository. 

# �nderungen hochladen

Die �nderungen sind jetzt im HEAD deines lokalen Repositories. Um die �nderungen an dein entferntes Repository zu senden, f�hre:
** git push origin master **
aus. Du kannst master auch mit einem beliebigen anderen Branch ersetzen, mehr �ber Branches erf�hrst du sp�ter.

Wenn du dein lokales Repository nicht von einem entfernten geklont hast und du diese aber mit einem anderen Repository verbinden m�chtest, musst du dieses mit
** git remote add origin <server> **
hinzuf�gen. Jetzt bist du bereit, deine �nderungen hochzuladen

# branching

Branches werden benutzt, um verschiedene Funktionen isoliert voneinander zu entwickeln. Der master-Branch ist der "Standard"-Branch, wenn du ein neues Repository erstellst. Du solltest aber f�r die Entwicklung andere Branches verwenden und diese dann in den Master-Branch zusammenf�hren (mergen). Auch das lernst du sp�ter.

Erstelle einen neuen Branch mit dem Namen "feature_x" und wechsle zu diesem:
** git checkout -b feature_x **
Um zum Master zur�ck zu wechseln:
** git checkout master **
Und um den eben erstellten Branch wieder zu l�schen:
** git branch -d feature_x **
Ein Branch ist nicht f�r andere verf�gbar, bis du diesen in dein entferntes Repository hochl�dst:
** git push origin <branch> **

#update & merge
Um dein lokales Repository mit den neuesten �nderungen zu aktualisieren, verwende:
** git pull **
in deiner Arbeitskopie, um die �nderungen erst herunterzuladen (fetch) und dann mit deinem Stand zusammenzuf�hren (merge).
Wenn du einen anderen Branch mit deinem aktuellen (z.B. master) zusammenf�hren willst, benutze:
** git merge <branch> **
In beiden F�llen versucht git die �nderungen automatisch zusammenzuf�hren. Ungl�cklicherweise ist dies nicht immer m�glich und endet in Konflikten. Du bist verantwortlich, diese Konflikte durch manuelles Editieren der betroffenen Dateien zu l�sen. Bist du damit fertig, musst du das git mit folgendem Befehl mitteilen:
** git add <dateiname> **
Bevor du �nderungen zusammenf�hrst, kannst du dir die Differenzen auch anschauen:
** git diff <quell_branch> <ziel_branch> **

# tagging
Es wird empfohlen, f�r Software Releasestags zu verwenden. Dies ist ein bekanntes Konzept, das es schon mit SVN gab. Du kannst einen neuen Tag namens 1.0.0 mit folgendem Befehl erstellen:
** git tag 1.0.0 1b2e1d63ff **
1b2e1d63ff steht f�r die ersten 10 Zeichen der Commit-Id, die du mit deinem Tag referenzieren m�chtest. Du erh�ltst die Liste der Commit-IDs mit:
** git log **
Du kannst auch weniger Zeichen verwenden, es muss einfach eindeutig sein. 

# �nderungen r�ckg�ngig machen

Falls du mal etwas falsch machst (was nat�rlich nie passiert ;) ) kannst du die lokalen �nderungen mit:
** git checkout -- <filename> **
auf den letzten Stand im HEAD zur�cksetzen. �nderungen, die du bereits zum Index hinzugef�gt hast, bleiben bestehen.

Wenn du aber deine lokalen �nderungen komplett entfernen m�chtest, holst du dir den letzten Stand vom entfernten Repository mit folgenden Befehlen:
** git fetch origin **
** git reset --hard origin/master **

# n�tzliche tricks
Eingebaute git-GUI:
** gitk **
Farbige Konsolenausgabe:
** git config color.ui true **
Eine Zeile pro Commit in der Logausgabe:
** git config format.pretty oneline **
Interaktives Hinzuf�gen von �nderungen:
** git add -i **