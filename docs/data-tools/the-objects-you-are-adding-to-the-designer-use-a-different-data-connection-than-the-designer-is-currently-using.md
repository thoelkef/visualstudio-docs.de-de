---
title: "Die dem Designer hinzugef&#252;gten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die dem Designer hinzugef&#252;gten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete.
Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete.Soll die vom Designer verwendete Verbindung ersetzt werden?  
  
 Wenn dem [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) Elemente hinzugefügt werden, verwenden alle Elemente eine gemeinsame Datenverbindung.\(Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.\) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete.Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll.Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt.Sie können auch auswählen, das Objekt hinzuzufügen und die <xref:System.Data.Linq.DataContext>\-Verbindung auf die neue Verbindung festlegen.  
  
> [!NOTE]
>  Wenn Sie auf **Ja** klicken, werden alle Entitätsklassen im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] der neuen Verbindung zugeordnet.  
  
### So ersetzen Sie die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung  
  
-   Klicken Sie auf **Ja**.  
  
     Das ausgewählte Objekt wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt, und die DataContext.Connection wird auf die neue Verbindung festgelegt.  
  
### So verwenden Sie weiterhin die vorhandene Verbindung und brechen das Hinzufügen des ausgewählten Objekts ab  
  
-   Klicken Sie auf **Nein**.  
  
     Die Aktion wird abgebrochen.Die DataContext.Connection bleibt weiterhin auf die vorhandene Verbindung festgelegt.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)