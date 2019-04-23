---
title: 'Vorgehensweise: Fügen Sie einen Parameter an eine Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a5b76e49285a629234557a973f6d4b45703f1cfd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056210"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Vorgehensweise: Fügen Sie einen Parameter einer Methode
  Verwenden Sie einen Parameter aus, um Informationen an die Methode übergeben oder Informationen aus einer Methode zurückgegeben werden sollen. Alle Methoden müssen über mindestens einen Parameter haben. Weitere Informationen zum Entwerfen eines Parameters, den Typ der Methode zu unterstützen, die Sie erstellen möchten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Wenn Sie einen Parameter an eine Methode hinzufügen, fügt Visual Studio Parameter-Element, auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen eines Parameter-Elements finden Sie unter [Parameter](http://go.microsoft.com/fwlink/?LinkId=169284).

### <a name="to-add-a-parameter-to-a-method"></a>So fügen Sie einer Methode einen Parameter hinzu

1. Fügen Sie eine Methode mit einer Entität.

2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.

     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).

3. In der **BDC-Methodendetails** , erweitern Sie den Knoten der Methode, und erweitern Sie dann die **Parameter** Knoten.

4. In der **Hinzufügen eines Parameters** wählen **Parameter erstellen**.

     Ein neuer Parameter angezeigt wird, unter dem **Parameter** Knoten.

5. Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.

6. In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen beliebigen Namen, die sinnvoll ist. Z. B. wenn die Methode Kunden zurückgibt, Sie können benennen Sie die Methode **GetCustomers**.

7. In der **BDC-Methodendetails** , öffnen Sie die Liste, die für die Richtung des Parameters angezeigt wird, und wählen Sie dann **In**, **InOut**, **Out**, oder **zurückgeben**.

     Weitere Informationen über die Richtung, wählen Sie für die Typmethode, die Sie erstellen, finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Ändern Sie den Typdeskriptor des Parameters an. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Vorgehensweise: Definieren des Typdeskriptors für einen parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
