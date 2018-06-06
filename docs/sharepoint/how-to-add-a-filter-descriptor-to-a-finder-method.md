---
title: 'Vorgehensweise: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode | Microsoft Docs'
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
ms.openlocfilehash: 307759881c6795d33dfb5a1c1425402aece05efb
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766613"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Vorgehensweise: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode
  Filterdeskriptoren ermöglichen Consumern des Modells, Werte an Methoden übergeben werden, bevor sie ausgeführt werden. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Ein häufiges Szenario ist, dass Benutzer in SharePoint beim Abrufen von Instanzen von einem externen Inhaltstyp, die bestimmte Kriterien erfüllen. Hinzufügen eines Filterdeskriptors zu einer Finder-Methode, um dieses Szenario zu unterstützen.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Hinzufügen ein Filterdeskriptors zu einer Finder-Methode  
  
1.  In der **BDC-Methodendetails** Fenster, erweitern Sie den Knoten einer Finder-Methode und die **Parameter** Knoten, und fügen Sie einen Eingabeparameter hinzu. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  In der **Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
4.  In der **Eigenschaften** legen die **Typnamen** Eigenschaft in einen Datentyp, der für den Filter geeignet ist.  
  
     Ein Filter möglicherweise z. B. ein Bestelldatum verwendet, um die Anzahl der von der Methode zurückgegebenen Aufträge zu beschränken. Um den Filter unterstützen die **Typnamen** Eigenschaft des Typdeskriptors muss festgelegt werden, um **System.DateTime**.  
  
5.  In der **Methodendetails** Fenster, erweitern Sie die **Filterdeskriptoren** Knoten.  
  
6.  In **Hinzufügen eines Filterdeskriptors** wählen **Filterdeskriptors erstellen**.  
  
     Eine neue Filterdeskriptors wird unterhalb der **Filterdeskriptoren** Knoten.  
  
7.  Wählen Sie in der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
8.  In der **Eigenschaften** Fenster, wählen Sie die **Typ** Eigenschaft.  
  
9. In der Liste, die für die **Typ** -Eigenschaft, wählen Sie das Filtermuster, die Sie möchten.  
  
     Wählen Sie zum Erstellen eines Filters, der ein Bestelldatum verwendet, um die Anzahl der in einer Finder-Methode zurückgegebenen Aufträge zu beschränken, z. B. **Vergleich**. Ein Vergleichsfilter wird sichergestellt, dass es sich bei eine Finder-Methode nur Instanzen zurückgegeben, die eine bestimmte Bedingung erfüllen. Weitere Informationen zu jeder Filtermuster, finden Sie unter [von BDC unterstützte Filter](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. In der **Eigenschaften** Fenster, wählen Sie die **zugeordnete Typdeskriptoren** Eigenschaft.  
  
11. In der Liste, die für die **zugeordnete Typdeskriptoren** -Eigenschaft, wählen Sie den Typdeskriptor, die Sie zuvor in dieser Prozedur erstellt haben. Diese Metrik bezieht sich den Filter für die Eingabeparameter der Finder-Methode.  
  
12. Fügen Sie Code, der Finder-Methode, die Daten zurückgibt. Sie können den Eingabeparameter als Bedingung in einer select-Abfrage verwenden.  
  
     Im folgende Beispiel werden Aufträge, die den angegebenen Bestelldatum zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  