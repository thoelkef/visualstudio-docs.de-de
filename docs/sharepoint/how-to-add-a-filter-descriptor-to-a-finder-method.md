---
title: 'Vorgehensweise: Hinzufügen ein Filterdeskriptors zu einer Finder-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63374f4d96c86ea3eafbd4c6fa3fbe3d1f5a5899
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755598"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Gewusst wie: Hinzufügen ein Filterdeskriptors zu einer Finder-Methode
  Filterdeskriptoren ermöglichen Consumern des Modells, um Werte an Methoden übergeben werden, bevor sie ausgeführt werden. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Ein häufiges Szenario ist, dass Benutzer in SharePoint soll, um Instanzen von einem externen Inhaltstyp abzurufen, die bestimmte Kriterien erfüllen. Sie können dieses Szenario unterstützen, durch das Hinzufügen eines Filterdeskriptors zu einer Finder-Methode.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Hinzufügen ein Filterdeskriptors zu einer Finder-Methode  
  
1.  In der **BDC-Methodendetails** Fenster, erweitern Sie den Knoten einer Finder-Methode, erweitern Sie die **Parameter** Knoten, und fügen Sie dann einen Eingabeparameter hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Parameters an eine Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  In der **Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters.  
  
3.  Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
4.  In der **Eigenschaften** legen die **Typnamen** Eigenschaft in einen Datentyp, der für den Filter geeignet ist.  
  
     Z. B. möglicherweise einen Filter ein Bestelldatum verwenden, um die Anzahl der von der Methode zurückgegebenen Aufträge zu beschränken. Um den Filter, unterstützen die **Typnamen** Eigenschaft des Typdeskriptors muss festgelegt werden, um **System.DateTime**.  
  
5.  In der **Methodendetails** Fenster, erweitern Sie die **Filterdeskriptoren** Knoten.  
  
6.  In **Hinzufügen eines Filterdeskriptors** wählen **Filterdeskriptor erstellen**.  
  
     Ein neuer Filterdeskriptor wird unterhalb der **Filterdeskriptoren** Knoten.  
  
7.  Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
8.  In der **Eigenschaften** Fenster, wählen Sie die **Typ** Eigenschaft.  
  
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
 [Gewusst wie: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: hinzufügen eine bestimmte Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
