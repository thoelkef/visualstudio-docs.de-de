---
title: 'Vorgehensweise: Definieren einer Methodeninstanz | Microsoft-Dokumentation'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e6dd6c0d7676c6b3c2071f0fcb07e8073313633
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118851"
---
# <a name="how-to-define-a-method-instance"></a>Gewusst wie: Definieren einer Methodeninstanz
  Sie müssen mindestens eine Methodeninstanz für jede Methode in Ihrem Modell definieren.  
  
 Methodeninstanz hinzufügen, mit der **BDC-Methodendetails** Fenster. Wenn Sie die Methodeninstanz hinzufügen, fügt Visual Studio eine `<MethodInstance>` Element auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen von einem `<MethodInstance>` Element finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Zum Definieren einer Methodeninstanz  
  
1.  In der **BDC-Methodendetails** , erweitern Sie den Knoten einer Methode, und erweitern Sie dann die **Instanzen** Knoten.  
  
2.  In der **Methodeninstanz hinzufügen** wählen **Finder-Instanz erstellen**.  
  
     Eine neue Methodeninstanz angezeigt wird, unter dem **Instanzen** Knoten.  
  
3.  Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.  
  
4.  In der **Eigenschaften** legen die Eigenschaften der Instanz. Weitere Informationen zu den einzelnen Eigenschaften finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Siehe auch
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Gewusst wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
