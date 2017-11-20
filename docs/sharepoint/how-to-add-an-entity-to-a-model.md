---
title: "Vorgehensweise: hinzufügen eine Entität zu einem Modell | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
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
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d8cc1bf4871ef91c5b08cb77963a70e422ee3cdc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-entity-to-a-model"></a>Gewusst wie: Hinzufügen einer Entität zu einem Modell
  Um eine Entität zu erstellen, fügen Sie eine Entität-Steuerelement aus der Visual Studio **Toolbox** in den Designer für Business Data Connectivity (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Eine Entität zum Modell hinzuzufügen.  
  
1.  Erstellen Sie ein BDC-Projekt, oder öffnen Sie ein vorhandenes BDC-Projekt. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  In der **Toolbox**, aus der **BusinessDataCatalog eine** , Hinzufügen einer **Entität** -Steuerelement in den Designer.  
  
     Die neue Entität wird im Designer angezeigt. Visual Studio fügt eine `<Entity>` Element der XML-Ausgabe von der BDC-Modelldatei im Projekt. Weitere Informationen zu den Attributen eines Entity-Elements finden Sie unter [Entität](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Öffnen Sie im Designer das Kontextmenü für die Entität, wählen Sie **hinzufügen**, und wählen Sie dann **Bezeichner**.  
  
     Ein neuer Bezeichner wird für die Entität angezeigt.  
  
    > [!NOTE]  
    >  Sie können den Namen der Entität und den Bezeichner im Ändern der **Eigenschaften** Fenster.  
  
4.  Definieren Sie die Felder der Entität in einer Klasse. Sie können das Projekt eine neue Klasse hinzugefügt oder verwenden eine vorhandene Klasse, die mit anderen Tools wie z. B. den Object Relational Designer (O/R-Designer) erstellt. Das folgende Beispiel zeigt eine Entitätsklasse, wenden Sie sich an.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  