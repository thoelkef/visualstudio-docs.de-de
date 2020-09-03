---
title: In Dateien suchen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655903"
---
# <a name="find-in-files"></a>In Dateien suchen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Option **In Dateien suchen** können Sie bestimmte Dateien durchsuchen. Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster Such **Ergebnisse** aufgelistet, das unter **Ergebnis Optionen**ausgewählt wurde.

 Rufen Sie die Option **Suchen in Dateien** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.

### <a name="to-display-find-in-files"></a>So rufen Sie die Option "In Dateien suchen" auf

1. Wählen Sie in der Menüleiste **Bearbeiten** und **Suchen und Ersetzen** aus.

2. Wählen Sie die Option **Suchen in Dateien** aus.

   Drücken Sie zum Abbrechen eines Suchvorgangs STRG+UNTBR.

> [!NOTE]
> Das Tool zum Suchen und Ersetzen durchsucht keine Verzeichnisse, für die das `Hidden`-Attribut oder das `System`-Attribut festgelegt wurden.

## <a name="find-what"></a>Suchen nach
 Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein. Um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben, öffnen Sie die Liste, und wählen Sie die Zeichenfolge aus, nach der Sie suchen möchten. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Suchen in
 Über die aus der Dropdownliste **Suchen in** ausgewählte Option legen Sie fest, ob die Funktion **In Dateien suchen** nur in den zurzeit aktiven Dateien oder in allen in bestimmten Ordnern gespeicherten Dateien sucht. Wählen Sie einen Suchbereich aus der Liste aus, oder klicken Sie auf die Schaltfläche **Durchsuchen (...)**, um das Dialogfeld **Suchordner auswählen** aufzurufen und Ihre eigene Gruppe von Verzeichnissen anzugeben. Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.

> [!WARNING]
> Mit den Optionen **Gesamte Projektmappe** oder **Aktuelles Projekt** werden Projekt- und Projektmappendateien nicht durchsucht. Wenn Sie die Projektdateien durchsuchen möchten, wählen Sie einen Suchordner aus.

> [!NOTE]
> Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.

## <a name="include-subfolders"></a>Unterordner einbeziehen
 Gibt an, dass auch die Unterordner des im Feld **Suchen in** angegebenen Ordners durchsucht werden.

## <a name="find-options"></a>Suchoptionen
 Sie können den Abschnitt Such **Optionen** erweitern oder reduzieren. Die folgenden Optionen können aktiviert oder deaktiviert werden:

 Groß-/Kleinschreibung bei **ausgewählter Suche**

 Ganzes Wort suchen wenn diese Option ausgewählt ist, werden die Such **Ergebnis** Fenster nur ganze Wort Übereinstimmungen zurückgeben.

 Reguläre Ausdrücke verwenden Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen verwenden, um Textmuster zu definieren, die mit den Textfeldern **Suchen** nach oder **Ersetzen durch** verglichen werden sollen. Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Sehen Sie sich diese Dateitypen an. diese Liste gibt die Dateitypen an, die in den Verzeichnissen " **Suchen in** " durchsucht werden sollen. Wenn dieses Feld leer ist, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.

 Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.

## <a name="result-options"></a>Ergebnisoptionen
 Sie können den Abschnitt **Ergebnis Optionen** erweitern oder reduzieren. Die folgenden Optionen können aktiviert oder deaktiviert werden:

 Fenster Ergebnisse 1 suchen wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters Such **Ergebnisse 1** . Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.

 Fenster "Suchergebnisse 2" Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters Such **Ergebnisse 2** . Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend** Suchergebnisse: 2** aus.

 Dateinamen anzeigen zeigt nur eine Liste der Dateien an, die Such Übereinstimmungen enthalten, anstatt die Such Übereinstimmungen anzuzeigen.

 Ergebnisse anfügen fügt die Ergebnisse aus der Suche an die vorherigen Suchergebnisse an.

## <a name="see-also"></a>Weitere Informationen
 Suchen [und Ersetzen von Text](../ide/finding-and-replacing-text.md) [Ersetzen in Dateien](../ide/replace-in-files.md) [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md)
