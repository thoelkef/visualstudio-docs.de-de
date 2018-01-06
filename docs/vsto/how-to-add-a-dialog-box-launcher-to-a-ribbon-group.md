---
title: "Vorgehensweise: Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f9b9b3500b833b8ecf56d66d036f8284484b6600
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Gewusst wie: Hinzufügen eines Dialogfeld-Startprogramms zu einer Multifunktionsleistengruppe
  Sie können eine beliebige Gruppe auf einem Menüband ein Dialogfeld-Startprogramms hinzufügen. Ein Dialogfeld-Startprogramm ist ein kleines Symbol, das in einer Gruppe angezeigt wird. Benutzer klicken Sie auf dieses Symbol zum Öffnen der zugehörigen Dialogfeldern oder Aufgabenbereiche, die mehr Optionen angeben, die auf die Gruppe beziehen.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe  
  
1.  Wählen Sie in der Menüband-Codedatei (VB- oder CS-Datei) **Projektmappen-Explorer**.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Designer**.  
  
3.  In der Menüband-Designer mit der rechten Maustaste in eine beliebige Gruppe, und klicken Sie dann auf **DialogBoxLauncher hinzufügen**.  
  
     Hinzufügen von Code für die <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> -Ereignis für die Gruppe zu einer benutzerdefinierten oder integrierten Dialogfeld zu öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Vorgehensweise: Ändern der Position einer Registerkarte auf dem Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Vorgehensweise: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  