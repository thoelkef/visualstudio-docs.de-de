---
title: Suchen in Dateien | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 430f2a55f180428c781e7a8cbe1f78d3a0355128
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804358"
---
# <a name="find-in-files"></a>Suchen in Dateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Option **In Dateien suchen** können Sie bestimmte Dateien durchsuchen. Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster **Suchergebnisse** angezeigt, das unter **Ergebnisoptionen** ausgewählt wurde.  
  
 Rufen Sie die Option **Suchen in Dateien** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.  
  
### <a name="to-display-find-in-files"></a>So rufen Sie die Option "In Dateien suchen" auf  
  
1. Wählen Sie in der Menüleiste **Bearbeiten** und **Suchen und Ersetzen** aus.  
  
2. Wählen Sie die Option **Suchen in Dateien** aus.  
  
   Drücken Sie zum Abbrechen eines Suchvorgangs STRG+UNTBR.  
  
> [!NOTE]
>  Das Tool zum Suchen und Ersetzen durchsucht keine Verzeichnisse, für die das `Hidden`-Attribut oder das `System`-Attribut festgelegt wurden.  
  
## <a name="find-what"></a>Suchen nach  
 Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein. Um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben, öffnen Sie die Liste, und wählen Sie die Zeichenfolge aus, nach der Sie suchen möchten. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Suchen in  
 Die in der Dropdownliste **Suchen in** ausgewählte Option bestimmt, ob mit der Option **Suchen in Dateien** nur die derzeit aktiven Dateien oder alle Dateien in bestimmten Ordnern durchsucht werden. Wählen Sie einen Suchbereich aus der Liste aus, oder klicken Sie auf die Schaltfläche **Durchsuchen (...)**, um das Dialogfeld **Suchordner auswählen** aufzurufen und Ihre eigene Gruppe von Verzeichnissen anzugeben. Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.  
  
> [!WARNING]
>  Mit den Optionen **Gesamte Projektmappe** oder **Aktuelles Projekt** werden Projekt- und Projektmappendateien nicht durchsucht. Wenn Sie die Projektdateien durchsuchen möchten, wählen Sie einen Suchordner aus.  
  
> [!NOTE]
>  Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.  
  
## <a name="include-subfolders"></a>Unterordner einschließen  
 Gibt an, dass auch die Unterordner des im Feld **Suchen in** angegebenen Ordners durchsucht werden.  
  
## <a name="find-options"></a>Suchoptionen  
 Der Bereich **Suchoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Groß-/Kleinschreibung beachten  
 Wenn diese Option ausgewählt ist, wird im Fenster **Suchergebnisse** zwischen Groß- und Kleinschreibung unterschieden.  
  
 Nur ganzes Wort suchen  
 Wenn diese Option ausgewählt ist, werden im Fenster **Suchergebnisse** nur Übereinstimmungen zurückgegeben, bei denen die gefundene Wortfolge vollständig mit der Suchzeichenfolge übereinstimmt.  
  
 Reguläre Ausdrücke verwenden  
 Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen zur Definition von Textmustern verwenden, die mit den Textfeldern **Suchen nach** oder **Ersetzen durch** übereinstimmen. Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Nach diesen Dateitypen suchen  
 Diese Liste gibt Dateitypen an, die in den unter **Suchen in** angegebenen Verzeichnissen durchsucht werden sollen. Wenn dieses Feld leer ist, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.  
  
 Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.  
  
## <a name="result-options"></a>Ergebnisoptionen  
 Der Bereich **Ergebnisoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Fenster "Suchergebnisse: 1"  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 1**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.  
  
 Fenster "Suchergebnisse: 2"  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 2**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 2** aus.  
  
 Nur Dateinamen anzeigen  
 Zeigt eine Liste mit Dateien an, in denen die gefundenen Übereinstimmungen enthalten sind, und nicht die Übereinstimmungen selbst.  
  
 Ergebnisse anfügen  
 Fügt die Ergebnisse der Suche den Ergebnissen der vorherigen Suche hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)   
 [In Dateien ersetzen](../ide/replace-in-files.md)   
 [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md)
