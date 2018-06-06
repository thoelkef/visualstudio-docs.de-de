---
title: 'Vorgehensweise: Hinzufügen eines Parameters einer Methode | Microsoft Docs'
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
ms.openlocfilehash: 9268fd0deb463a29c8e6d19e98ad63c86b965292
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767087"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Vorgehensweise: Hinzufügen eines Parameters einer Methode
  Verwenden Sie einen Parameter aus, um Informationen an die Methode übergeben oder zum Zurückgeben von Informationen von einer Methode. Alle Methoden müssen mindestens einen Parameter haben. Weitere Informationen zum Entwerfen eines Parameters, um den Typ der Methode zu unterstützen, die Sie erstellen möchten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Wenn Sie eine Methode einen Parameter hinzufügen, fügt Visual Studio die Parameter-Element auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen eines Parameter-Elements finden Sie unter [Parameter](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>So fügen Sie einer Methode einen Parameter hinzu  
  
1.  Fügen Sie eine Methode mit einer Entität.  
  
2.  Wählen Sie in der Menüleiste **Ansicht** > **Weitere Fenster** > **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **BDC-Methodendetails** , erweitern Sie den Knoten der Methode, und erweitern Sie dann die **Parameter** Knoten.  
  
4.  In der **Hinzufügen eines Parameters** wählen **Parameter erstellen**.  
  
     Ein neuer Parameter wird unter der **Parameter** Knoten.  
  
5.  Wählen Sie in der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
6.  In der **Eigenschaften** legen die **Namen** -Eigenschaft auf einen beliebigen Namen, die sinnvoll ist. Beispielsweise, wenn die Methode Kunden zurückgibt, nennen Sie die Methode **GetCustomers**.  
  
7.  In der **BDC-Methodendetails** , öffnen Sie die Liste, die für die Richtung des Parameters angezeigt wird, und wählen Sie dann **In**, **InOut**, **Out**, oder **zurückgeben**.  
  
     Weitere Informationen über die Richtung, wählen für die Typmethode, die Sie erstellen, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Ändern Sie den Typdeskriptor des Parameters. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Siehe auch
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
