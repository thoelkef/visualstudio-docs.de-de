---
title: 'Vorgehensweise: Hinzufügen eines Parameters an eine Methode | Microsoft-Dokumentation'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 196ac37cc9bc4f53cfa886b92c62c7a301c3451a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756310"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Gewusst wie: Hinzufügen eines Parameters einer Methode
  Verwenden Sie einen Parameter aus, um Informationen an die Methode übergeben oder Informationen aus einer Methode zurückgegeben werden sollen. Alle Methoden müssen über mindestens einen Parameter haben. Weitere Informationen zum Entwerfen eines Parameters, den Typ der Methode zu unterstützen, die Sie erstellen möchten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Wenn Sie einen Parameter an eine Methode hinzufügen, fügt Visual Studio Parameter-Element, auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen eines Parameter-Elements finden Sie unter [Parameter](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>So fügen Sie einer Methode einen Parameter hinzu  
  
1.  Fügen Sie eine Methode mit einer Entität.  
  
2.  Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **BDC-Methodendetails** , erweitern Sie den Knoten der Methode, und erweitern Sie dann die **Parameter** Knoten.  
  
4.  In der **Hinzufügen eines Parameters** wählen **Parameter erstellen**.  
  
     Ein neuer Parameter angezeigt wird, unter dem **Parameter** Knoten.  
  
5.  Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
6.  In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen beliebigen Namen, die sinnvoll ist. Z. B. wenn die Methode Kunden zurückgibt, Sie können benennen Sie die Methode **GetCustomers**.  
  
7.  In der **BDC-Methodendetails** , öffnen Sie die Liste, die für die Richtung des Parameters angezeigt wird, und wählen Sie dann **In**, **InOut**, **Out**, oder **zurückgeben**.  
  
     Weitere Informationen über die Richtung, wählen Sie für die Typmethode, die Sie erstellen, finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Ändern Sie den Typdeskriptor des Parameters an. Weitere Informationen finden Sie unter [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Siehe auch
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
