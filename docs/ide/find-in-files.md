---
title: "Suchen in Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.findinfiles"
  - "vs.findinfiles"
helpviewer_keywords: 
  - "Objekte [Visual Studio], suchen"
  - "Textsuche, Ersetzen von Text"
  - "Objekte [Visual Studio], suchen nach"
  - "Suchen und Ersetzen (Fenster), In Dateien suchen (Registerkarte)"
  - "Textsuche, Suchen und Ersetzen (Fenster)"
  - "Dokumente, suchen in"
  - "Dateien, suchen in"
  - "In Dateien suchen (Registerkarte), Suchen und Ersetzen (Fenster)"
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 41
caps.handback.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Suchen in Dateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Option **In Dateien suchen** können Sie einen bestimmten Satz Dateien durchsuchen.  Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster **Suchergebnisse** angezeigt, das unter **Ergebnisoptionen** ausgewählt wurde.  
  
 Rufen Sie die Option **In Dateien suchen** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.  
  
### So rufen Sie die Option "In Dateien suchen" auf  
  
1.  Wählen Sie in der Menüleiste **Bearbeiten** und **Suchen und Ersetzen** aus.  
  
2.  Wählen Sie die Option **In Dateien suchen** aus.  
  
 Drücken Sie zum Abbrechen eines Suchvorgangs STRG\+UNTBR.  
  
> [!NOTE]
>  Das Tool zum Suchen und Ersetzen durchsucht keine Verzeichnisse, für die das `Hidden`\-Attribut oder das `System`\-Attribut festgelegt wurden.  
  
## Suchen nach  
 Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein.  Um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben, öffnen Sie die Liste, und wählen Sie die Zeichenfolge aus, nach der Sie suchen möchten.  Wählen Sie die benachbarte Schaltfläche **Ausdrucks\-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten.  Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Suchen in  
 Die in der Dropdownliste **Suchen in** ausgewählte Option bestimmt, ob mit der Option **In Dateien suchen** nur die derzeit aktiven Dateien oder alle Dateien in bestimmten Ordnern durchsucht werden.  Wählen Sie einen Suchbereich aus der Liste aus, oder klicken Sie auf die Schaltfläche **Durchsuchen \(...\)**, um das Dialogfeld **Suchordner auswählen** aufzurufen und Ihre eigene Gruppe von Verzeichnissen anzugeben.  Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.  
  
> [!WARNING]
>  Mit den Optionen **Gesamte Projektmappe** oder **Aktuelles Projekt** werden Projekt\- und Projektmappendateien nicht durchsucht.  Wenn Sie die Projektdateien durchsuchen möchten, wählen Sie einen Suchordner aus.  
  
> [!NOTE]
>  Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.  
  
## Unterordner einschließen  
 Gibt an, dass auch die Unterordner des im Feld **Suchen in** angegebenen Ordners durchsucht werden.  
  
## Suchoptionen  
 Der Bereich **Suchoptionen** kann erweitert oder reduziert werden.  Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Groß\-\/Kleinschreibung beachten  
 Wenn diese Option ausgewählt ist, wird im Fenster **Suchergebnisse** zwischen Groß\- und Kleinschreibung unterschieden.  
  
 Nur ganzes Wort suchen  
 Wenn diese Option ausgewählt ist, werden im Fenster **Suchergebnisse** nur Übereinstimmungen zurückgegeben, bei denen die gefundene Wortfolge vollständig mit der Suchzeichenfolge übereinstimmt.  
  
 Reguläre Ausdrücke verwenden  
 Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen zur Definition von Textmustern verwenden, die mit den Textfeldern **Suchen nach** oder **Ersetzen durch** übereinstimmen.  Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Nach diesen Dateitypen suchen  
 Diese Liste gibt Dateitypen an, die in den unter **Suchen in** angegebenen Verzeichnissen durchsucht werden sollen.  Wenn dieses Feld leer ist, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.  
  
 Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.  
  
## Ergebnisoptionen  
 Der Bereich **Ergebnisoptionen** kann erweitert oder reduziert werden.  Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Fenster "Suchergebnisse: 1"  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 1**.  Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen.  Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.  
  
 Fenster "Suchergebnisse: 2"  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 2**.  Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen.  Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 2** aus.  
  
 Nur Dateinamen anzeigen  
 Zeigt eine Liste mit Dateien an, in denen die gefundenen Übereinstimmungen enthalten sind, und nicht die Übereinstimmungen selbst.  
  
 Ergebnisse anfügen  
 Fügt die Ergebnisse der Suche den Ergebnissen der vorherigen Suche hinzu.  
  
## Siehe auch  
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)   
 [In Dateien ersetzen](../ide/replace-in-files.md)   
 [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md)