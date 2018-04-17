---
title: 'Vorgehensweise: Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d71124d0a3843053ad7558e0e1038b8d6626b5e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  