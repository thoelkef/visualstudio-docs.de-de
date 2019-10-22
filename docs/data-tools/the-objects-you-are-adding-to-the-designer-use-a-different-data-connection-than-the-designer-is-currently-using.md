---
title: Dem Designer hinzugefügte Objekte verwenden eine andere Datenverbindung
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 915860c2559335f37869f5c6009f7a38dde6abcd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640841"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als der Designer.

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?

Wenn Sie dem **objektrelationaler Designer** (**O/R-Designer**) Elemente hinzufügen, verwenden alle Elemente eine freigegebene Datenverbindung. (Die Entwurfs Oberfläche stellt die <xref:System.Data.Linq.DataContext> dar, die eine einzelne Verbindung für alle Objekte auf der-Oberfläche verwendet.) Wenn Sie dem Designer ein Objekt hinzufügen, das eine Datenverbindung verwendet, die von der derzeit vom Designer verwendeten Datenverbindung abweicht, wird diese Meldung angezeigt. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Sie können auch auswählen, dass das Objekt hinzugefügt und die <xref:System.Data.Linq.DataContext>-Verbindung auf die neue Verbindung festgelegt wird.

## <a name="connection-options"></a>Verbindungsoptionen

- Um die vorhandene Verbindung durch die Verbindung zu ersetzen, die vom ausgewählten Objekt verwendet wird, klicken Sie auf **Ja**.

   Das ausgewählte Objekt wird dem **O/R-Designer**hinzugefügt, und die *DataContext. Connection* wird auf die neue Verbindung festgelegt.

   > [!NOTE]
   > Wenn Sie auf **Ja**klicken, werden alle Entitäts Klassen im **O/R-Designer** der neuen Verbindung zugeordnet.

- Um die vorhandene Verbindung weiterhin zu verwenden und das Hinzufügen des ausgewählten Objekts abzubrechen, klicken Sie auf **Nein**.

   Die Aktion wird abgebrochen. Die *DataContext.Connection* bleibt weiterhin auf die vorhandene Verbindung festgelegt.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
