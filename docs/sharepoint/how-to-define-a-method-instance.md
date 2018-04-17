---
title: 'Vorgehensweise: Definieren einer Methodeninstanz | Microsoft Docs'
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
ms.openlocfilehash: 44a31af455b09db5fb359339cee8da7b3ca0c77e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-method-instance"></a>Gewusst wie: Definieren einer Methodeninstanz
  Sie müssen mindestens eine Methodeninstanz für jede Methode in Ihrem Modell definieren.  
  
 Hinzufügen eine Methodeninstanz mithilfe der **BDC-Methodendetails** Fenster. Wenn Sie die Methodeninstanz hinzufügen, fügt Visual Studio eine `<MethodInstance>` Element auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen von einem `<MethodInstance>` Element, finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Zum Definieren einer Methodeninstanz  
  
1.  In der **BDC-Methodendetails** , erweitern Sie den Knoten einer Methode, und erweitern Sie dann die **Instanzen** Knoten.  
  
2.  In der **Methodeninstanz hinzufügen** wählen **Finder-Instanz erstellen**.  
  
     Eine neue Methodeninstanz wird unter der **Instanzen** Knoten.  
  
3.  Wählen Sie in der Menüleiste **Ansicht**, wählen Sie **Fenster "Eigenschaften"**.  
  
4.  In der **Eigenschaften** die Eigenschaften der Methodeninstanz fest. Weitere Informationen zu den einzelnen Eigenschaften finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  