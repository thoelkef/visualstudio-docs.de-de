---
title: Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung, als die, die der Designer derzeit nutzt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 23abfbdc1b0bf922e3d15f0181afd7d01aa7ee2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935657"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Die, die Sie dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als im designer

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?

Beim Hinzufügen von Elementen, die **Object Relational Designer** (**O/R Designer**), verwenden alle Elemente eine gemeinsame Datenverbindung. (Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Sie können auch auswählen, das Objekt hinzuzufügen und die <xref:System.Data.Linq.DataContext>-Verbindung auf die neue Verbindung festlegen.

> [!NOTE]
> Wenn Sie auf **Ja**, alle Entitätsklassen der **O/R Designer** zugeordnet sind, auf die neue Verbindung.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>So ersetzen Sie die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung

- Klicken Sie auf **Ja**.

    Das ausgewählte Objekt wird hinzugefügt, um die **O/R Designer**, und die *DataContext.Connection* festgelegt ist, auf die neue Verbindung.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>So verwenden Sie weiterhin die vorhandene Verbindung und brechen das Hinzufügen des ausgewählten Objekts ab

- Klicken Sie auf Nein **.

    Die Aktion wird abgebrochen. Die DataContext.Connection bleibt weiterhin auf die vorhandene Verbindung festgelegt.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
