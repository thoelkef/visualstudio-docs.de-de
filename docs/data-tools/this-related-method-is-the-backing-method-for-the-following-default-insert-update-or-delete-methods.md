---
title: "Diese verkn&#252;pfte Methode ist die dahinter liegende Methode f&#252;r die folgenden standardm&#228;&#223;igen Insert-, Update- und Delete-Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Diese verkn&#252;pfte Methode ist die dahinter liegende Methode f&#252;r die folgenden standardm&#228;&#223;igen Insert-, Update- und Delete-Methoden
Diese verknüpfte Methode ist die dahinter liegende Methode für die folgenden standardmäßigen Insert\-, Update\- und Delete\-Methoden.Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht.Möchten Sie den Vorgang fortsetzen?  
  
 Die ausgewählte `DataContext`\-Methode wird derzeit als eine der Insert\-, Update\- oder Delete\-Methoden für eine der Entitätsklassen im O\/R\-Designer verwendet.Durch das Löschen der ausgewählten Methode greift die Entitätsklasse, die diese Methode verwendete, auf das Standardlaufzeitverhalten zurück, um die Aktionen Einfügen, Aktualisieren oder Löschen bei einem Update auszuführen.  
  
### So löschen Sie die ausgewählte Methode und bewirken, dass die Entitätsklasse Laufzeitupdates verwendet  
  
-   Klicken Sie auf **Ja**.  
  
     Die ausgewählte Methode wird gelöscht und alle Klassen, die diese Methode zum Überschreiben des Updateverhaltens verwendet hatten, greifen wieder auf das standardmäßige LINQ to SQL\-Laufzeitverhalten zurück.  
  
### So schließen Sie das Meldungsfeld, ohne die ausgewählte Methode zu ändern  
  
-   Klicken Sie auf **Nein**.  
  
     Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.  
  
## Siehe auch  
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)