---
title: Die Objekte, die Sie zum Designer hinzufügen, verwenden eine andere Datenverbindung, als die, die der Designer derzeit nutzt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22307115893407fa4703475e727b1e77355cad57
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460554"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Die, die Sie dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als im designer

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?

Beim Hinzufügen von Elementen, die **Object Relational Designer** (**O/R Designer**), verwenden alle Elemente eine gemeinsame Datenverbindung. (Die Entwurfsoberfläche stellt den <xref:System.Data.Linq.DataContext> dar, von dem für alle Objekte auf der Oberfläche dieselbe Verbindung verwendet wird.) Diese Meldung wird angezeigt, wenn dem Designer ein Objekt hinzugefügt wird, das eine andere Datenverbindung verwendet als die derzeit vom Designer verwendete. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Sie können auch auswählen, dass das Objekt hinzugefügt und die <xref:System.Data.Linq.DataContext>-Verbindung auf die neue Verbindung festgelegt wird.

## <a name="connection-options"></a>Verbindungsoptionen

- Um die vorhandene Verbindung durch die vom ausgewählten Objekt verwendete Verbindung ersetzen möchten, klicken Sie auf **Ja**.

   Das ausgewählte Objekt wird hinzugefügt, um die **O/R Designer**, und die *DataContext.Connection* festgelegt ist, auf die neue Verbindung.

   > [!NOTE]
   > Wenn Sie auf **Ja**, alle Entitätsklassen der **O/R Designer** zugeordnet sind, auf die neue Verbindung.

- Um den Vorgang fortzusetzen, verwenden Sie die vorhandene Verbindung und Hinzufügen des ausgewählten Objekts "Abbrechen", klicken Sie auf **keine**.

   Die Aktion wird abgebrochen. Die *DataContext.Connection* bleibt weiterhin auf die vorhandene Verbindung festgelegt.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
