---
title: "In Dateien ersetzen | Microsoft Docs"
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
  - "vs.findreplace.replaceinfiles"
  - "vs.replaceinfiles"
helpviewer_keywords: 
  - "Textsuche, Ersetzen von Text"
  - "Suchen und Ersetzen (Fenster), In Dateien ersetzen (Registerkarte)"
  - "In Dateien suchen (Registerkarte), Suchen und Ersetzen (Fenster)"
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# In Dateien ersetzen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Option **In Dateien ersetzen** können Sie den Code in einem bestimmten Satz Dateien nach einer Zeichenfolge oder einem Ausdruck durchsuchen und einige oder alle Fundstellen ändern.  Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster **Suchergebnisse** angezeigt, das unter **Ergebnisoptionen** ausgewählt wurde.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Rufen Sie die Option **In Dateien ersetzen** mit einer der folgenden Methoden im Fenster **Suchen und Ersetzen** auf.  
  
### So rufen Sie die Option In Dateien ersetzen auf  
  
1.  Erweitern Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen**.  
  
2.  Wählen Sie die Option **In Dateien ersetzen** aus.  
  
     \- oder \-  
  
     Wenn die  **Suchen und Ersetzen** Fenster ist bereits geöffnet, auf der Symbolleiste, wählen Sie  **in Dateien ersetzen**.  
  
## Suchen nach  
 Um eine neue Textzeichenfolge oder Ausdrucks zu suchen, geben sie im Feld.  Um eine der 20 Zeichenfolgen suchen, das Sie vor kurzem gesucht, öffnen Sie die Liste und wählen Sie die Zeichenfolge für die Sie suchen möchten.  Wählen Sie die angrenzende  **Ausdrucks\-Generator** Schaltfläche, wenn Sie eine oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten.  Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Ersetzen durch  
 Ersetzen Sie die Instanzen der Zeichenfolge in der  **Suchen nach** box mit einer anderen Zeichenfolge, geben Sie die Ersatzzeichenfolge in die  **Ersetzen durch** Box.  Löschen von Instanzen der Zeichenfolge in der  **Suchen nach** box, lassen Sie dieses Feld leer.  Öffnen Sie die Liste zum Anzeigen der 20 Zeichenfolgen, für die Sie vor kurzem gesucht.  Wählen Sie die angrenzende  **Ausdrucks\-Generator** Schaltfläche, wenn Sie eine oder mehrere reguläre Ausdrücke in der Ersetzungszeichenfolge verwenden möchten.  Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Suchen in  
 Die Option, die Sie aus der Dropdownliste **Suchen in** auswählen, bestimmt, ob mit der Option **In Dateien ersetzen** nur die derzeit aktiven Dateien oder alle Dateien in bestimmten Ordnern durchsucht werden.  Wählen Sie einen Suchbereich aus der Liste, geben Sie einen Pfad oder klicken Sie auf die  **Durchsuchen \(...\)** Schaltfläche, um die Anzeige der  **Suchordner auswählen** Dialogfeld und wählen Sie eine Reihe von Ordnern zu suchen.  Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.  
  
> [!NOTE]
>  Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur die Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.  
  
## Suchoptionen  
 Der Bereich **Suchoptionen** kann erweitert oder reduziert werden.  Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Groß\-\/Kleinschreibung beachten  
 Wenn diese Option aktiviert ist, werden in den Fenstern **Suchergebnisse** nur diejenigen Übereinstimmungen angezeigt, bei denen sowohl der Inhalt als auch die Groß\-\/Kleinschreibung mit der Suchzeichenfolge unter **Suchen nach** übereinstimmen.  Beispielsweise gibt die Suche nach "MyObject", wenn **Groß\-\/Kleinschreibung beachten** aktiviert ist, nur "MyObject" zurück, nicht jedoch "myobject" oder "MYOBJECT".  
  
 Nur ganzes Wort suchen  
 Wenn diese Option aktiviert ist, werden in den Fenstern **Suchergebnisse** nur diejenigen Übereinstimmungen angezeigt, bei denen die gefundene Wortfolge mit dem Suchzeichenfolge unter **Suchen nach** übereinstimmt.  Eine Suche nach "MyObject" gibt z. B. den Treffer "MyObject" zurück, nicht jedoch "CMyObject" oder "MyObjectC".  
  
 Verwenden von regulären Ausdrücken  
 Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen definieren Textmuster in der  **Suchen nach** oder  **Ersetzen durch** Textfelder.  Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Nach diesen Dateitypen suchen  
 Diese Liste gibt die Dateitypen an, die in den unter **Suchen in** angegebenen Verzeichnissen durchsucht werden sollen.  Wenn dieses Feld leer ist, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.  
  
 Wählen Sie ein beliebiges Element in der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.  
  
## Ergebnisoptionen  
 Der Bereich **Ergebnisoptionen** kann erweitert oder reduziert werden.  Die folgenden Optionen können aktiviert oder deaktiviert werden:  
  
 Suchergebnisse: 1  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 1**.  Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen.  Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.  
  
 Suchergebnisse: 2  
 Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 2**.  Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen.  Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 2** aus.  
  
 Nur Dateinamen anzeigen  
 Wenn dieses Kontrollkästchen aktiviert ist, Listen Sie Fenster Suchergebnisse, die vollständigen Namen und Pfade für alle Dateien, die die Suchzeichenfolge enthalten.  Jedoch enthalten nicht die Ergebnisse die Codezeile, in denen die Zeichenfolge angezeigt wird.  Dieses Kontrollkästchen ist nur verfügbar für in Dateien suchen.  
  
 Geänderte Dateien offen lassen, nachdem alles ersetzt wurde  
 Wenn diese Option ausgewählt ist, bleiben alle Dateien, in denen Ersetzungen vorgenommen wurden, geöffnet, sodass Sie die Änderungen rückgängig machen oder speichern können.  Speicherplatzeinschränkungen können u. U. die Anzahl der Dateien, die nach einem Ersetzungsvorgang geöffnet sein können, einschränken.  
  
> [!CAUTION]
>  Sie können die Option **Rückgängig** nur für Dateien verwenden, die zur Bearbeitung geöffnet bleiben.  Wenn diese Option nicht ausgewählt ist, bleiben Dateien, die nicht ohnehin zur Bearbeitung geöffnet wurden, geschlossen, und die Option **Rückgängig** steht für diese Dateien nicht zur Verfügung.  
  
## Siehe auch  
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)   
 [Suchen in Dateien](../ide/find-in-files.md)   
 [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md)