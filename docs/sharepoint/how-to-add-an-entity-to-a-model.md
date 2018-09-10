---
title: 'Vorgehensweise: hinzufügen eine Entität zu einem Modell | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 72dbebd8ff9b2e7bf7b001d540158656271c0556
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757708"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Gewusst wie: hinzufügen eine Entität zu einem Modell
  Um eine Entität zu erstellen, fügen Sie ein Steuerelement für die Entität aus der Visual Studio **Toolbox** in den Designer für Business Data Connectivity (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Um eine Entität dem Modell hinzufügen  
  
1.  Erstellen Sie ein BDC-Projekt, oder öffnen Sie ein vorhandenes BDC-Projekt. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  In der **Toolbox**, aus der **BusinessDataCatalog eine** , Hinzufügen einer **Entität** -Steuerelement in den Designer.  
  
     Die neue Entität wird im Designer angezeigt. Visual Studio fügt ein `<Entity>` Element, das XML des BDC-Modelldatei in Ihrem Projekt. Weitere Informationen zu den Attributen eines Entity-Elements finden Sie unter [Entität](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Öffnen Sie im Designer das Kontextmenü für die Entität, und wählen **hinzufügen**, und wählen Sie dann **Bezeichner**.  
  
     Ein neuer Bezeichner wird für die Entität angezeigt.  
  
    > [!NOTE]  
    >  Sie können den Namen der Entität und den Bezeichner im Ändern der **Eigenschaften** Fenster.  
  
4.  Definieren Sie die Felder der Entität in einer Klasse ein. Sie können eine neue Klasse zum Projekt hinzufügen oder verwenden Sie eine vorhandene Klasse, die mit anderen Tools wie z. B. den Object Relational Designer (O/R Designer) erstellt. Das folgende Beispiel zeigt eine Entitätsklasse, wenden Sie sich an.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Gewusst wie: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: hinzufügen eine bestimmte Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
 
