---
title: "Vorgehensweise: hinzufügen eine Entität zu einem Modell | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2ef3885f2a290fd1d4193daf9436a08ae5588a0d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
  