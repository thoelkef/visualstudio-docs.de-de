---
title: 'Vorgehensweise: Hinzufügen eine Entität zu einem Modell | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b269bb18580784fb08d9b081a37935c7b3f37627
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864659"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell
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
 [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)  
