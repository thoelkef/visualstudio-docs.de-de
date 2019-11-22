---
title: 'Gewusst wie: Hinzufügen eines Parameters zu einer Methode | Microsoft-Dokumentation'
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
ms.openlocfilehash: eb1a1c1e8f11ac6daa46f9fe1468a1ff3509e135
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986238"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Gewusst wie: Hinzufügen eines Parameters zu einer Methode
  Verwenden Sie einen-Parameter, um Informationen an die-Methode zu übergeben oder um Informationen von einer Methode zurückzugeben. Alle Methoden müssen mindestens einen Parameter aufweisen. Weitere Informationen zum Entwerfen eines Parameters, der den Typ der Methode unterstützt, die Sie erstellen möchten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Wenn Sie einer Methode einen Parameter hinzufügen, fügt Visual Studio das Parameter-Element dem XML-Code der Modelldatei in Ihrem Projekt hinzu. Weitere Informationen zu den Attributen eines Parameter Elements finden Sie unter [Parameter](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>So fügen Sie einer Methode einen Parameter hinzu

1. Fügen Sie einer Entität eine Methode hinzu.

2. Wählen Sie in der Menüleiste **Ansicht** > **Weitere Windows** > **BDC-Methoden Details**aus.

     Das Fenster **BDC-Methoden Details** wird geöffnet. Weitere Informationen finden Sie unter [Übersicht über die Entwurfs Tools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).

3. Erweitern Sie im Fenster **BDC-Methoden Details** den Knoten der Methode, und erweitern Sie dann den Knoten **Parameter** .

4. Wählen Sie in der Liste **Parameter hinzufügen** die Option **Parameter erstellen**aus.

     Unterhalb des **para** meters-Knotens wird ein neuer Parameter angezeigt.

5. Wählen Sie in der Menüleiste **Ansicht** > **Eigenschaften Fenster**aus.

6. Legen Sie im **Eigenschaften** Fenster die **Name** -Eigenschaft auf einen beliebigen Namen fest, der sinnvoll ist. Wenn die Methode z. b. Kunden zurückgibt, können Sie die Methode " **GetCustomers**" benennen.

7. Öffnen Sie im Fenster **BDC-Methoden Details** die Liste, die für die Richtung des Parameters angezeigt wird, und wählen Sie dann **in**, **INOUT**, out oder **Return** **aus**.

     Weitere Informationen dazu, welche Richtung Sie für die zu Erstell Erstellungsmethode auswählen können, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Ändern Sie den Typdeskriptor des Parameters. Weitere Informationen finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
