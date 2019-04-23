---
title: Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die vom Designer derzeit verwendete | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 773d3ea2e0d5574b194a44783b14d35db25d6f7f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661827"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung, als die, die der Designer derzeit nutzt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?  
  
 Beim Hinzufügen von Elementen, die [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), verwenden alle Elemente eine gemeinsame Datenverbindung. (Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Sie können auch auswählen, dass das Objekt hinzugefügt und die <xref:System.Data.Linq.DataContext>-Verbindung auf die neue Verbindung festgelegt wird.  
  
> [!NOTE]
>  Wenn Sie auf **Ja**, alle Entitätsklassen der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zugeordnet sind, auf die neue Verbindung.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>So ersetzen Sie die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung  
  
-   Klicken Sie auf **Ja**.  
  
     Das ausgewählte Objekt wird dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] hinzugefügt, und die DataContext.Connection wird auf die neue Verbindung festgelegt.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>So verwenden Sie weiterhin die vorhandene Verbindung und brechen das Hinzufügen des ausgewählten Objekts ab  
  
-   Klicken Sie auf **Nein**.  
  
     Die Aktion wird abgebrochen. Die DataContext.Connection bleibt weiterhin auf die vorhandene Verbindung festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   