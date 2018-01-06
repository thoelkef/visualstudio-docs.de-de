---
title: "Die Objekte, die Sie zum Designer hinzufügen verwenden eine andere Datenverbindung als die vom Designer derzeit verwendete | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 715bb696819af901c04fc0d95747b51186868003
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung, als die, die der Designer derzeit nutzt.
Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?  
  
 Beim Hinzufügen von Elementen, die [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), verwenden alle Elemente eine gemeinsame Datenverbindung. (Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Alternativ können Sie auch zum Hinzufügen des Objekts und zum Zurücksetzen der <xref:System.Data.Linq.DataContext> -Verbindung auf die neue Verbindung.  
  
> [!NOTE]
>  Wenn Sie auf **Ja**, alle Entitätsklassen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] der neuen Verbindung zugeordnet sind.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>So ersetzen Sie die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung  
  
-   Klicken Sie auf **Ja**.  
  
     Das ausgewählte Objekt wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt, und die DataContext.Connection wird auf die neue Verbindung festgelegt.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>So verwenden Sie weiterhin die vorhandene Verbindung und brechen das Hinzufügen des ausgewählten Objekts ab  
  
-   Click **No**.  
  
     Die Aktion wird abgebrochen. Die DataContext.Connection bleibt weiterhin auf die vorhandene Verbindung festgelegt.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 