---
title: "No files were found to look in. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_FRLookInEmpty"
  - "vs.message.0x800A00DE"
ms.assetid: d560aef3-7a55-4fbb-a541-1a43fc13c18b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No files were found to look in.
Dieser Fehler tritt normalerweise auf, wenn im Listenfeld **Suchen in** ein Datei\- oder Verzeichnisname angegeben wurde, der nicht vorhanden ist oder nicht gefunden wurde.  Dieser Fehler kann auch auftreten, wenn Sie ein gültiges Verzeichnis angeben, das keine in der Liste der Dateitypen aufgeführten Dateierweiterungen enthält, oder wenn das angegebene Verzeichnis keine Dateien enthält.  Der Fehler kann auch auftreten, wenn Sie mit dem `Hidden`\- oder `System`\-Attributsatz eine Suche in einem Verzeichnis ausführen.  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie das Dialogfeld **Benutzerdefinierter Verzeichnissatz**, um das Verzeichnis oder die Datei, das bzw. die durchsucht werden soll, mithilfe von Durchsuchen anzuzeigen, ohne dass der Pfad\- oder Dateiname eingegeben werden muss.  Zum Öffnen des Dialogfelds **Benutzerdefinierter Verzeichnissatz** klicken Sie neben dem Listenfeld **Suchen in** auf die Schaltfläche mit dem Auslassungszeichen.  
  
2.  Ändern Sie die im Listenfeld **Dateitypen** angegebene Dateierweiterung in \*.\*, um alle im angegebenen Verzeichnis enthaltenen Dateien zu durchsuchen.  
  
### So umgehen Sie diesen Fehler  
  
1.  Halten Sie die STRG\-TASTE gedrückt, und drücken Sie ROLLEN.  
  
     Das Dialogfeld wird abgebrochen.  
  
## Siehe auch  
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)   
 [Suchen in Dateien](../ide/find-in-files.md)   
 [Choose Search Folders](http://msdn.microsoft.com/de-de/85af6458-dcde-4a84-9ea4-f5cc6550dc80)