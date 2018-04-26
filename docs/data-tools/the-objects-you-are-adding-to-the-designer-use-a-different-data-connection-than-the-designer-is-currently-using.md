---
title: Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung, als die, die der Designer derzeit nutzt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33a6083fb9e52ebdafbc827fc19666c1df9a3f7e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung als im designer

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?

Beim Hinzufügen von Elementen, die [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), verwenden alle Elemente eine gemeinsame Datenverbindung. (Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Alternativ können Sie auch zum Hinzufügen des Objekts und zum Zurücksetzen der <xref:System.Data.Linq.DataContext> -Verbindung auf die neue Verbindung.

> [!NOTE]
> Wenn Sie auf **Ja**, alle Entitätsklassen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] der neuen Verbindung zugeordnet sind.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>So ersetzen Sie die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung

- Klicken Sie auf **Ja**.

    Das ausgewählte Objekt wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt, und die DataContext.Connection wird auf die neue Verbindung festgelegt.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>So verwenden Sie weiterhin die vorhandene Verbindung und brechen das Hinzufügen des ausgewählten Objekts ab

- Click **No**.

    Die Aktion wird abgebrochen. Die DataContext.Connection bleibt weiterhin auf die vorhandene Verbindung festgelegt.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
