---
title: 'Vorgehensweise: Hinzufügen ein Filterdeskriptors zu einer Finder-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc6492b52cb739c49bdba9f231ebcda313a66105
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068664"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Vorgehensweise: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode
  Filterdeskriptoren ermöglichen Consumern des Modells, um Werte an Methoden übergeben werden, bevor sie ausgeführt werden. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Ein häufiges Szenario ist, dass Benutzer in SharePoint soll, um Instanzen von einem externen Inhaltstyp abzurufen, die bestimmte Kriterien erfüllen. Sie können dieses Szenario unterstützen, durch das Hinzufügen eines Filterdeskriptors zu einer Finder-Methode.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Hinzufügen ein Filterdeskriptors zu einer Finder-Methode

1. In der **BDC-Methodendetails** Fenster, erweitern Sie den Knoten einer Finder-Methode, erweitern Sie die **Parameter** Knoten, und fügen Sie dann einen Eingabeparameter hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Fügen Sie einen Parameter an eine Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. In der **Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters.

3. Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.

4. In der **Eigenschaften** legen die **Typnamen** Eigenschaft in einen Datentyp, der für den Filter geeignet ist.

     Z. B. möglicherweise einen Filter ein Bestelldatum verwenden, um die Anzahl der von der Methode zurückgegebenen Aufträge zu beschränken. Um den Filter, unterstützen die **Typnamen** Eigenschaft des Typdeskriptors muss festgelegt werden, um **System.DateTime**.

5. In der **Methodendetails** Fenster, erweitern Sie die **Filterdeskriptoren** Knoten.

6. In **Hinzufügen eines Filterdeskriptors** wählen **Filterdeskriptor erstellen**.

     Ein neuer Filterdeskriptor wird unterhalb der **Filterdeskriptoren** Knoten.

7. Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.

8. In der **Eigenschaften** Fenster, wählen Sie die **Typ** Eigenschaft.

9. In der Liste für die **Typ** -Eigenschaft, wählen Sie das Filtermuster, die Sie möchten.

     Wählen Sie zum Erstellen eines Filters, der ein Bestelldatum verwendet, um die Anzahl der in einer Finder-Methode zurückgegebenen Aufträge zu beschränken, z. B. **Vergleich**. Ein Vergleichsfilter wird sichergestellt, dass es sich bei eine Finder-Methode nur Instanzen zurückgibt, die eine bestimmte Bedingung erfüllen. Weitere Informationen zu einzelnen Filtermustern, finden Sie unter [von BDC unterstützte Filter](http://go.microsoft.com/fwlink/?LinkId=169287).

10. In der **Eigenschaften** Fenster, wählen Sie die **zugeordnete Typdeskriptoren** Eigenschaft.

11. In der Liste für die **zugeordnete Typdeskriptoren** -Eigenschaft, wählen Sie den Typdeskriptor, die Sie zuvor in diesem Verfahren erstellt haben. Dies bezieht sich den Filter, an den Eingabeparameter der Finder-Methode.

12. Fügen Sie Code, der Finder-Methode, die Daten zurückgibt. Sie können den Eingabeparameter als Bedingung in einer select-Abfrage verwenden.

     Im folgenden Beispiel zurückgegeben, Bestellungen, die das Datum der angegebenen Reihenfolge aufweisen.

    > [!NOTE]
    >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren des Typdeskriptors für einen parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
