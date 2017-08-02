---
title: "Arbeitsbereiche in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>Steuern, wo R-Code mit Arbeitsbereichen ausgeführt wird

Mit einem Arbeitsbereich in R Tools für Visual Studio (RTVS) lässt sich konfigurieren, wo eine R-Sitzung ausgeführt wird (lokal oder auf Remotecomputern). Das Ziel ist, Ihnen in beiden Fällen die Arbeit auf einer vergleichbaren Benutzeroberfläche zu ermöglichen, sodass Sie leistungsfähigere cloudbasierte Computer nutzen können.

Um das Fenster **Arbeitsbereiche** zu öffnen, verwenden Sie den Befehl **R Tools > Windows > Arbeitsbereiche**, oder drücken Sie STRG+9.

![Fenster „Arbeitsbereiche“ in R Tools für Visual Studio (VS 2017)](~/docs/rtvs/media/workspaces-window.png)

Das grüne Häkchen in diesem Fenster gibt den aktiven Arbeitsbereich an, mit dem RTVS verbunden ist. Der blaue Pfeil legt den aktiven Arbeitsbereich fest. Über das Einstellungssymbol (Zahnrad) rechts neben jedem Arbeitsbereich können Sie den Namen, den Speicherort und die Befehlszeilenargumente ändern. Mit dem roten X wird ein manuell hinzugefügter Arbeitsbereich entfernt.

In diesem Thema:

- [Speichern und Zurücksetzen eines Arbeitsbereichs](#saving-and-resetting-a-workspace)
- [Lokale Arbeitsbereiche](#local-workspaces)
- [Remotearbeitsbereiche](#remote-workspaces)
- [Wechseln zwischen Arbeitsbereichen](#switching-between-workspaces)
- [Verzeichnisse auf lokalen und Remotecomputern](#directories-on-local-and-remote-computers)
- [Kopieren von Projektdateien in einen Remotearbeitsbereich](#copying-project-files-to-remote-workspaces)
- [Kopieren von Dateien aus einem Remotearbeitsbereich](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Speichern und Zurücksetzen eines Arbeitsbereichs

In der Standardeinstellung speichert RTVS den Zustand von Arbeitsbereichen beim Schließen und erneuten Öffnen eines Projekts nicht. Sie können dieses Verhalten jedoch über die [Arbeitsbereichsoptionen](options.md#workspace) ändern.

Der Befehl **R Tools > Sitzung > Zurücksetzen** und die Symbolleistenschaltfläche „Zurücksetzen“ im interaktiven Fenster setzen den Zustand von Arbeitsbereichen auch jederzeit zurück. Im Fall von Remotearbeitsbereichen wird beim Zurücksetzen das Benutzerprofil gelöscht, das beider ersten Anmeldung beim Remoteserver erstellt wurde. Dadurch werden effektiv alle Dateien gelöscht, die dort gesammelt wurden.

## <a name="local-workspaces"></a>Lokale Arbeitsbereiche

Die Liste lokaler Arbeitsbereiche führt alle R-Interpreter auf, die auf Ihrem Computer installiert sind. 

RTVS versucht, automatisch alle installierten Versionen von R zu erkennen, indem der `HKEY_LOCAL_MACHINE\Software\R-Core\`-Registrierungsschlüssel beim Start von Visual Studio durchsucht wird. Da diese Überprüfung nur beim Start ausgeführt wird, müssen Sie Visual Studio neu starten, wenn Sie einen neuen R-Interpreter installieren.

RTVS erkennt möglicherweise keine R-Interpreter, die auf nicht standardmäßige Weise installiert wurden (z.B. durch Kopieren von Dateien in einen Ordner statt eines Installationsprogramms). Erstellen Sie in diesem Fall wie folgt einen neuen lokalen R-Arbeitsbereich:

1. Wählen Sie im Fenster „Arbeitsbereiche“ die Schaltfläche **Hinzufügen** aus.
1. Geben Sie einen Namen für den neuen Arbeitsbereich ein.
1. Geben Sie den Pfad zum R-Stammordner, der den `bin`-Ordner mit den Interpreter enthält, und optionale Befehlszeilenargumente ein, damit der Interpreter beim Start von RTVS übergeben wird.
1. Wählen Sie **Speichern** aus, wenn Sie fertig sind.

![Einen neuen Arbeitsbereich hinzufügen](~/docs/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Remotearbeitsbereiche

Mit Remotearbeitsbereichen können Sie auf einem Remotecomputer eine Verbindung zu einer R-Sitzung herstellen. (Informationen zum Konfigurieren eines Computers dafür finden Sie unter [Setting up remote workspaces (Einrichten von Remotearbeitsbereichen)](workspaces-remote-setup.md).)

Remotearbeitsbereiche werden nicht automatisch von RTVS erkannt. Deshalb müssen Sie sie manuell mithilfe der Schaltfläche **Hinzufügen** im Fenster „Arbeitsbereiche“ hinzufügen, wie im vorherigen Abschnitt beschrieben. Geben Sie in diesem Fall statt eines lokalen Pfads den URI des Remotecomputers ein.

> [!Important]
> Remotearbeitsbereiche werden über einen URI identifiziert, der *das HTTPS-Protokoll verwenden* muss, damit die Vertraulichkeit und Integrität der Kommunikation mit dem Remotecomputer gewährleistet wird. RTVS stellt keine Verbindung mit einem Remotecomputer her, der HTTPS nicht unterstützt.

> [!Note]
> Remotearbeitsbereiche befinden sich in der Vorschau. Wir arbeiten für ein künftiges Release an einer besseren Implementierung des Problems bei der Dateisynchronisierung und freuen uns über Ihre Ideen und Ihr Feedback.


## <a name="switching-between-workspaces"></a>Wechseln zwischen Arbeitsbereichen

RTVS wird jeweils nur mit einem Arbeitsbereich verbunden. Dies wird im Fenster „Arbeitsbereiche“ durch ein kleines grünes Häkchen neben diesem Arbeitsbereich angezeigt. Standardmäßig wird RTVS mit dem letzten lokalen Arbeitsbereich verbunden, den Sie in einer vorherigen Sitzung geöffnet haben.

Um den aktiven Arbeitsbereich zu ändern, wählen Sie den blauen Pfeil neben dem gewünschten Arbeitsbereich aus. Daraufhin werden Sie zum Speichern der Sitzung aufgefordert, der aktuelle Arbeitsbereich wird beendet, und es wird zum neuen Arbeitsbereich gewechselt.

> [!Tip]
> Um die Speicheraufforderung zu deaktivieren, wählen Sie den Befehl **R Tools > Optionen** aus, und legen Sie die Option **Vor dem Arbeitsbereichswechsel Bestätigungsdialogfeld anzeigen** auf `No` fest. Informationen finden Sie unter [R Tools for Visual Studio options (Optionen in R Tools für Visual Studio)](options.md#workspace).

Wenn Sie versuchen, zu einem lokalen Arbeitsbereich zu wechseln, der deinstalliert oder in einem nicht verfügbaren Remotearbeitsbereich installiert wurde, kann ein RTVS-Projekt auch mit gar keinem Arbeitsbereich verbunden sein. Infolge wird möglicherweise ein Fehler wie der folgende angezeigt, wenn Sie im interaktiven Fenster Code eingeben oder versuchen, den Code auf andere Weise auszuführen. Um dies zu korrigieren, wechseln Sie im Fenster „Arbeitsbereiche“ einfach zu einem anderen Arbeitsbereich. Wenn keiner verfügbar ist, müssen Sie einen R-Interpreter installieren. Sie können auch versuchen, Visual Studio neu zu starten, falls Sie während der Ausführung von Visual Studio einen Interpreter installiert haben.

![Fehler, wenn kein Arbeitsbereich mit RTVS verbunden ist](~/docs/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>Wechseln zu einem Remotearbeitsbereich

RTVS fordert Sie bei der ersten Verbindungserstellung mit einem Remotearbeitsbereich zur Eingabe von Anmeldeinformationen auf und speichert die Anmeldeinformationen dann (mithilfe des sicheren Schließfachs für Anmeldeinformationen) für späteren Sitzungen im Cache. Kommunikation mit dem Remoteserver erfolgt sicher über HTTPS (erforderlich).

Je nach Serverkonfiguration wird bei der Verbindungserstellung die folgende Zertifikatwarnung angezeigt: „Anhand des von den Remote-R Services vorgelegten Sicherheitszertifikats können wir nicht nachweisen, dass Sie tatsächlich eine Verbindung mit dem Computer "Name" herstellen“.

![Selbstsignierte Zertifikatwarnung beim Verbinden mit einem Remotearbeitsbereich](~/docs/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

Das Zertifikat ist ein Dokument, das RTVS von dem Computer präsentiert wird, mit dem Sie eine Verbindung herstellen möchten. Das Dokument enthält ein Feld, das den URI des Computers identifiziert. Die Warnung wird angezeigt, wenn RTVS einen Konflikt zwischen dem URI im Zertifikat und dem zum Verbinden mit dem Computer verwendeten URI erkennt, und gibt an, dass die Sicherheit des Servers möglicherweise gefährdet ist.

Diese Warnung wird aber auch angezeigt, wenn statt eines vertrauenswürdigen Anbieters ein *selbstsigniertes Zertifikat* zur Aktivierung von HTTPS auf einem Remotecomputer verwendet wurde. Weitere Informationen finden Sie unter [Setting up remote workspaces (Einrichten von Remotearbeitsbereichen)](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Verzeichnisse auf lokalen und Remotecomputern

Wenn Sie einen neuen R-Interpreter in einem lokalen Arbeitsbereich starten, lautet Ihr aktuelle Arbeitsverzeichnis standardmäßig `%userprofile%\Documents`. Sie können dies jederzeit mithilfe der Befehle **R Tools > Working Directory** ändern, oder indem Sie mit einem Rechtsklick auf ein Projekt im Visual Studio-Projektmappen-Explorer klicken und Befehle wie **Arbeitsverzeichnis hier festlegen** auswählen.

Auf Remotecomputern erstellt RTVS bei der ersten Verbindungserstellung zu dem Server automatisch ein Benutzerprofil anhand Ihrer Anmeldeinformationen, damit das Arbeitsverzeichnis in diesem Profil der `Documents`-Ordner ist. Dies wird für alle nachfolgenden Remotesitzungen genutzt, die die gleichen Anmeldeinformationen verwenden. 

Daher kann sich der exakte Speicherort, an dem Ihr Code ausgeführt wird, bei lokalen und Remotearbeitsbereichen unterscheiden. Vermeiden Sie es, in Ihrem Code absolute Pfade für Datendateien usw. zu verwenden, da Ihr Code wahrscheinlich nicht auf andere Arbeitsbereiche übertragbar ist. Verwenden Sie stattdessen besser relative Pfade.

Beachten Sie außerdem, dass bei Remotearbeitsbereichen alle Dateien im Arbeitsverzeichnis für ein Benutzerprofil sitzungsübergreifend beibehalten werden. Wie bereits erwähnt, können Sie sie mit dem Befehl **R Tools > Sitzung > Zurücksetzen** löschen (oder mit der Schaltfläche „Zurücksetzen“ im interaktiven Fenster), wenn Sie einen Remotearbeitsbereich nutzen. Dadurch wird das Benutzerprofil erneut vom Server gelöscht. Beim Wiederherstellen der Verbindung wird auch das Profil wiederhergestellt.

## <a name="copying-project-files-to-remote-workspaces"></a>Kopieren von Projektdateien in einen Remotearbeitsbereich

Beim Arbeiten mit R-Projekte in Visual Studio hat der lokale Computer immer die neuesten Projektdateien, selbst wenn Sie einen Remotearbeitsbereich verwenden. Das bedeutet, dass wenn Sie ein Projekt in Visual Studio öffnen (in der Regel bedeutet dies, eine Projektmappe mit einem Projekt zu öffnen), nimmt RTVS an, dass sich der Inhalt des Projekts vollständig auf dem lokalen Computer befindet. Der Remotearbeitsbereich ist im Grunde nur ein temporärer Host für die Projektdateien und die Codeausgabe. Dies bedeutet beispielsweise, dass beim Laden einer Datei mithilfe von `source` im interaktiven Fenster, die Datei bereits mit dem angegebenen Pfad auf dem Remotecomputer oder im aktuellen Arbeitsverzeichnis des R-Remoteinterpreters vorhanden sein muss (festgelegt mit der `setwd()`-Funktion).

Dateien werden wie folgt auf den Remoteserver kopiert:

- Um über das interaktive Fenster remote mit Dateien arbeiten zu können, müssen Sie sie zuerst manuell mit einem Rechtsklick auf diese Dateien (oder dieses Projekt) im Projektmappen-Explorer kopieren und **Quelle ausgewählt** auswählen. Einzelne Dateien werden in das Arbeitsverzeichnis auf dem Server kopiert. Beim Kopieren eines Projekts erstellt RTVS einen Projektordner.

- Sie können Dateien auch kopieren, indem Sie sie im Projektmappen-Explorer und dann die Option **Ausgewählte Datei(en) einbinden** auswählen. Dadurch werden sie in das interaktive Fenster geladen und dort ausgeführt. Wenn die Sitzung mit einem Remotecomputer verbunden ist, werden die Dateien zuerst dorthin kopiert.

- Wenn RTVS mit einem Remotearbeitsbereich verbunden ist und Sie F5 drücken, **Debuggen > Debugging starten** auswählen oder anderweitig die Codeausführung starten, kopiert RTVS die Projektdatei standardmäßig automatisch in den Remotearbeitsbereich (Informationen zur Steuerung dieses Vorgangs weiter unten).

- Alle Dateien, die bereits auf dem Server vorhanden sind, werden überschrieben.

> [!Note]
> Da RTVS nicht alle R-Funktionsaufrufe zuverlässig abfangen kann, werden Dateien durch das Aufrufen von Funktionen wie `source()` oder `runApp()` (für Shiny-Anwendungen) über das interaktive Fenster *nicht* in den Remotearbeitsbereich kopiert.

Ob RTVS bei der Ausführung eines Projekts Dateien kopiert, und welche Dateien kopiert werden, wird über die [Projekteigenschaften](projects.md#project-properties) gesteuert. Um diese Seite zu öffnen, wählen Sie den Menübefehl **Projekt > Eigenschaften von (Projektname)...** aus, oder klicken Sie mit der echten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie **Eigenschaften...** aus.

![Ausführungsregisterkarte der Projekteigenschaften mit den Einstellungen für die Übertragung von Dateien](~/docs/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

Hier bestimmt **Transfer files on run** (Dateien bei der Ausführung übertragen), ob RTVS Projektdateien automatisch kopiert. Der Wert der **Dateien für die Übertragung** filtert dann genau, welche Dateien übertragen werden. Standardmäßig werden nur die Dateitypen `.R`, `.Rmd`, `.sql`, `.md` und `.cpp` kopiert. Damit wird vermieden, dass versehentlich große Datendateien mit jeder Ausführung auf den Server kopiert werden. 

## <a name="copying-files-from-a-remote-workspace"></a>Kopieren von Dateien aus einem Remotearbeitsbereich

Wenn Ihr R-Skript auf dem Server Dateien generiert, können Sie diese Dateien mithilfe der `rtvs::fetch_file`-Funktion zurück auf den Client kopieren. Diese Funktion akzeptiert mindestens den Remotepfad zur Datei, die Sie auf den Computer kopieren möchten, und optional den Pfad auf dem Computer, in den diese Datei kopiert werden soll. Wenn Sie keinen Pfad angeben, wird die Datei in den `%userprofile%\Downloads`-Ordner kopiert.

