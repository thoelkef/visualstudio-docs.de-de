---
title: "Projekte in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 732b73cf-2014-4f98-838e-4141ef9dedac
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 00ccd6319f13fc6be32ca7bde4e2c5f76a5cbc49
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-projects-in-visual-studio"></a>Erstellen von R-Projekten in Visual Studio

Ein R-Projekt (eine `.rxproj`-Datei) identifiziert alle Quell- und Inhaltsdateien, die mit einem Projekt verknüpft sind. Außerdem enthält es Buildinformationen für jede Datei, verwaltet diese Informationen zur Integration in Quellcodeverwaltungssysteme und unterstützt Sie bei der Organisation Ihrer Anwendung in logische Komponenten. Arbeitsbereichbezogene Informationen wie die Liste der installierten Pakete im Arbeitsbereich selbst werden getrennt verwaltet.

Darüber hinaus werden Projekte immer in einer Visual Studio-*Projektmappe* verwaltet, die eine beliebige Anzahl von aufeinander verweisenden Projekten enthalten kann. Weitere Informationen finden Sie unter [Verwenden von verschiedenen Projekttypen in Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Erstellen eines neuen R-Projekts

1. Starten Sie Visual Studio.
1. Wählen Sie **Datei > Neu > Projekt...** aus. (Strg+Umschalt+N)
1. Wählen Sie unter **Vorlagen > R** „R-Projekt“ aus, weisen Sie dem Projekt einen Namen und Speicherort zu, und wählen Sie **OK** aus:

    ![Dialogfeld „Neues Projekt“ für R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

Mit diesem Befehl wird ein Projekt mit einer leeren, im Editor geöffneten `script.R`-Datei erstellt. Im **Projektmappen-Explorer** sind im Projekt noch zwei weitere Dateien vorhanden:

![Inhalt eines R-Projekts, das aus der Vorlage erstellt wurde](media/projects-template-results.png)

Die Datei `.Rhistory` zeichnet alle Befehle auf, die Sie im Fenster [R Interaktive](interactive-repl.md) eingeben. Sie können ein Fenster zum dedizierten Verlauf mit dem Befehl **R Tools > Windows > Verlauf** öffnen. Dieses Fenster hat eine Schaltfläche in der Symbolleiste und Elemente im Kontextmenü, um den Inhalt des Verlaufs zu löschen.

Die Datei `rproject.rproj` behält bestimmte R-spezifische Projekteinstellungen bei, die anderweitig nicht von Visual Studio verwaltet werden:

| Eigenschaft | Standard | Beschreibung |
| --- | --- | --- |
| Version | 1,0 | Die Version von R Tools für Visual Studio, die für die Projekterstellung verwendet wurde |
| RestoreWorkspace | Standard | Lädt automatisch vorherige Arbeitsbereichsvariablen aus der Datei `.RData` im Projektverzeichnis |
| SaveWorkspace | Standard | Speichert aktuelle Arbeitsbereichsvariablen beim Schließen eines Projekts in der Datei `.RData` im Projektverzeichnis |
| AlwaysSaveHistory | Standard | Speichert die aktuelle Versionsgeschichte des interaktiven Fensters beim Schließen eines Projekts in der Datei `.RHistory` im Projektverzeichnis |
| EnableCodeIndexing | Ja | Bestimmt, ob zur Beschleunigung von Codesuchen im Hintergrund eine Indizierungsaufgabe ausgeführt werden soll |
| UseSpacesForTab | Ja | Bestimmt, ob Leerzeichen (Ja) oder ein Tabstoppzeichen (Nein) eingefügt werden soll, wenn im Editor die TAB-TASTE gedrückt wird |
| NumSpacesForTab | 2 | Die Anzahl der einzufügenden Leerzeichen, wenn UseSpacesForTab „Ja“ lautet |
| Codierung | UTF-8 | Die Standardcodierung für `.R`-Dateien |
| RnwWeave | Sweave | Das beim Einbinden einer RNW-Datei zu verwendende Paket |
| LaTeX | pdfLaTeX | Die beim Konvertieren von RMarkdwon in PDF zu verwendende Bibliothek |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Konvertieren eines Dateiordners in ein R-Projekt

Wenn Sie einen vorhandenen Ordner mit `.R`-Dateien in einem Projekt verwalten möchten, gehen Sie folgendermaßen vor:

1. Erstellen Sie wie im vorherigen Abschnitt ein neues Projekt in Visual Studio.
1. Kopieren Sie die Dateien in den Projektordner.
1. Klicken Sie mit der rechten Maustaste in den Visual Studio Projektmappen-Explorer, wählen Sie **Add > Exiting Item** (Hinzufügen > Element beenden) aus, und navigieren Sie zu den Dateien, die Sie hinzufügen möchten. Diese Dateien werden in Ihrer Projektstruktur angezeigt, nachdem Sie auf **OK** geklickt haben.
1. Um Code in Unterordnern zu organisieren, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie zuerst **Hinzufügen > Neuer Ordner** aus, kopieren Sie dann die Dateien in diesen Ordner, und fügen Sie vorhandene Elemente im dritten Schritt hinzu.

## <a name="project-properties"></a>Projekteigenschaften

Zum Öffnen der Seiten mit den Projekteigenschaften klicken Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** und wählen **Eigenschaften** aus, oder wählen Sie das Menüelement *Projekt > (Projektname) > Eigenschaften* aus. Das geöffnete Fenster zeigt die Projekteigenschaften an:

| Registerkarte | Eigenschaft | Beschreibung |
| --- | --- | --- |
| Run | Startup file | Der Name der Datei, die mit dem Befehl **Source startup file**, F5, **Debuggen > Debuggen starten** oder **Debuggen > Starten ohne Debugging** ausgeführt wird. Sie können die Startdatei auch im Projekt über einen Rechtsklick auf die Datei und die Option **Als R-Startskript festlegen** festlegen. |
| | R Interactive beim Ausführen zurücksetzen | Löscht alle Variablen aus dem Arbeitsbereich des interaktiven Fensters, wenn das Projekt ausgeführt wird. So wird sichergestellt, dass keine Inhalte des Arbeitsbereichs aus vorherigen Ausführungen übrig bleiben. |
| | Remote Project Path | Pfad zu einem Remotearbeitsbereich |
| | Transfer files on run | Gibt an, ob die Projektdateien, die dem Filter in **Files to transfer** unterliegen, bei jeder Ausführung in einen Remotearbeitsbereich kopiert werden sollen |
| | Files to transfer | Dateinamen und Platzhalter, die die genauen Dateien angeben, die in einen Remotearbeitsbereich kopiert werden sollen, wenn **Transfer files on run** ausgewählt ist. |
| Einstellungen | (Settings.R-Datei) | Die Einstellungen des R-Projekts stammen aus `Settings.R`- oder `*.Settings.R`-Dateien, die sich innerhalb des Projekts befinden. Wenn keine Einstellungsdatei vorhanden ist, können Sie Variablen hinzufügen und die Seite speichern. Außerdem wird die Standard-`Settings.R`-Datei für Sie erstellt. Sie können dem Projekt die Einstellungsdatei auch über den Menübefehl **Datei > Neues Element hinzufügen...* hinzufügen. <br/> Einstellungen werden als R-Code gespeichert, und die Datei kann vor dem Ausführen anderer Module und dem Vorabausfüllen der Umgebung mit den vordefinierten Einstellungen zurückverfolgt werden. |

## <a name="r-specific-project-commands"></a>R-spezifische Projektbefehle

Visual Studio-Projekte unterstützen sowohl über das Kontextmenü als auch über das **Projektmenü** eine Reihe von allgemeinen Befehlen. Weitere Informationen zu diesen allgemeinen Funktionen finden Sie unter [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Denken Sie jedoch daran, dass 

R Tools für Visual Studio dem Kontextmenü eines R-Projekts eine Reihe eigener Befehle sowie dem Projekt Dateien und Ordner hinzufügt.

| Befehl | Beschreibung |
| --- | --- |
| Arbeitsverzeichnis hier festlegen | Legt das Arbeitsverzeichnis des Fensters von R Interactive auf den Projektordner fest, der auch für jeden Unterordner eines Projekts verwendet werden kann. |
| Enthaltenden Ordner öffnen | Öffnet den Windows-Explorer am Speicherort der ausgewählten Datei | 
| R-Skript hinzufügen | Erstellt und öffnet eine neue `.R`-Datei mit einem Standardnamen. Sie können auch den Befehl **Hinzufügen > Neues Element...** zum Erstellen von `.R`-Dateien und einer Reihe anderer Dateitypen verwenden. Weitere Informationen finden Sie unter [R-spezifische Elementvorlagen](#r-specific-item-templates). |
| R Markdown hinzufügen | Erstellt und öffnet ein neues `.rmd`-Dokument mit einem Standardnamen. Sie können auch den Befehl **Hinzufügen > Neues Element...** zum Erstellen von `.rmd`-Dateien und einer Reihe anderer Dateitypen verwenden. Weitere Informationen finden Sie unter [R-spezifische Elementvorlagen](#r-specific-item-templates).  | 
| Gespeicherte Prozeduren veröffentlichen | Startet einen Prozess zum Veröffentlichen von in R-Skripts enthaltenen gespeicherten Prozeduren. Informationen finden Sie unter [Working with SQL Server stored procedures (Arbeiten mit gespeicherten SQL Server-Prozeduren)](sql-server.md#working-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>R-spezifische Elementvorlagen

RTVS umfasst eine Reihe von Vorlagen für bestimmte Dateitypen. Zugriff auf Vorlagen erhalten Sie über einen Rechtsklick auf ein R-Projekt und das Kicken auf **Hinzufügen > Neues Element...**, auf **Projekt > Neues Element hinzufügen...** oder auf **Datei > Neu > Datei...** und das Klicken auf die Registerkarte **R**. Die beste Möglichkeit, eine Vorlage kennenzulernen, ist, einfach ein neues Projekt zu erstellen und Dateien jedes Typs einzufügen.

> [!Note]
> Die Befehle **Hinzufügen > Neues Element...** zeigen auch allgemeine Dateitypen an, die in der Tabelle nicht aufgelistet sind. Mit **Datei > Neu > Datei...** werden diese Typen stattdessen auf der Registerkarte **Allgemein** aufgeführt.

| Dateityp | Beschreibung |
| --- | --- |
| R-Skript | Eine Textdatei, die dieselben Befehle enthält, die in der R-Befehlszeile eingegeben werden können |
| R Markdown | Eine Datei mit einem [R Markdown](rmarkdown.md)-Dokument |
| R-Einstellungen | Eine Datei, die die R-Anwendungseinstellungen enthält | 
| R-Dokumentation | Eine generische R-Dokumentationsdatei, die nur die Namens-, Alias-, und Titelfelder enthält |
| R-Dokumentation (Funktion) | Eine R-Dokumentationsdatei, die viele Felder mit Kommentaren zum Beschreiben einer Funktion enthält |
| R-Dokumentation (Dataset) | Eine R-Dokumentationsdatei, die viele Felder mit Kommentaren zum Beschreiben eines Datasets enthält |
| SQL-Abfrage | Eine leere `.sql`-Datei. Informationen finden Sie unter [SQL Server integration (SQL Server-Integration)](sql-server.md). |
| Gespeicherte Prozeduren mit R | Eine R-Datei mit untergeordneten SQL-Abfragen und einer Vorlagendatei für die untergeordnete gespeicherte Prozedur. Informationen finden Sie unter [SQL Server integration (SQL Server-Integration)](sql-server.md). |


## <a name="use-multiple-project-types-in-visual-studio"></a>Verwenden von verschiedenen Projekttypen in Visual Studio

Visual Studio-Projektmappen stellen eine bequeme Möglichkeit zum Sammeln und Verwalten verwandter Projekte in einem logischen Ort bereit. Mit Projektmappen bleibt Ihr Code organisiert. Darüber hinaus erleichtern sie das Arbeiten in Teams.

Im folgenden Beispiel enthält die Projektmappe ein R-Projekt mit einem Modell, das mithilfe von R und Azure Machine Learning erstellt wurde, ein Python/SciKit-learn-Projekt, ein C++-Projekt, das Module für rechenintensive Rechenaufwand enthält, ein SQL-Projekt für die Datenverwaltung und ein Python/Bottle-Projekt für die Website, die das Ergebnis veröffentlicht:

![Visual Studio-Projektmappen-Explorer mit mehreren verwandten Projekte in einer Projektmappe](media/projects-polyglot.png)

Das fett markierte Projekt ist das „Startprojekt“ der Projektmappe. Um es zu ändern, klicken Sie mit der rechten Maustaste auf ein anderes Projekt, und wählen Sie **Als Startprojekt festlegen** aus.

> [!Note]
> Derzeit ist keine explizite Sprachintegration für R in C#/C++ vorhanden (wie bei Python, siehe [Erstellen einer C++-Erweiterung für Python](../python/cpp-and-python.md)).  Es gibt jedoch Bibliotheken, die C#- und C++-Brücken für R bereitstellen.

Weitere Informationen zum Verwalten von Projekten und Projektmappen im Allgemeinen finden Sie unter [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

