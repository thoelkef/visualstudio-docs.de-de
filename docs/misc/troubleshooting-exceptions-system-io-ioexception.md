---
title: "Problembehandlung bei Ausnahmen: System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException-Klasse"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.IOException
Eine <xref:System.IO.IOException> wird ausgelöst, wenn ein E\/A\-Fehler auftritt, also z. B. das Lesen aus einer Datei oder das Schreiben in eine Datei fehlschlägt.  
  
## Tipps  
 **Stellen Sie sicher, dass die Datei und das Verzeichnis vorhanden sind.**  
 Stellen Sie sicher, dass das Verzeichnis, aus dem gelesen bzw. in das geschrieben werden soll, vorhanden ist. Stellen Sie sicher, dass die Datei, aus der Sie versuchen zu lesen, vorhanden ist.  
  
### Hinweise  
 <xref:System.IO.IOException> ist die Basisklasse für Ausnahmen, die ausgelöst werden, während Sie über Streams, Dateien und Verzeichnisse auf Informationen zugreifen.  
  
 Die Basisklassenbibliothek schließt folgende Typen ein, die ausschließlich abgeleitete Klassen von <xref:System.IO.IOException> sind:  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## Siehe auch  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD Gewusst wie: Erstellen von CLR\-Konsolenanwendungen](http://msdn.microsoft.com/de-de/b8af4197-e65f-4b17-b18e-b9e92965d026)