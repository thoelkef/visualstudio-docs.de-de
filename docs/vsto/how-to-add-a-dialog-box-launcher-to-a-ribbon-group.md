---
title: 'Vorgehensweise: Hinzufügen eines Dialogfeld-Startprogramms zu einer Menübandgruppe'
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6ec94b8fc170f195b00a6c093605860c97048ed
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648696"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Vorgehensweise: Hinzufügen eines Dialogfeld-Startprogramms zu einer Menübandgruppe
  Sie können ein Dialogfeld-Startprogramms zu einer Gruppe auf einem Menüband hinzufügen. Ein Dialogfeld-Startprogramm ist ein kleines Symbol, das in einer Gruppe angezeigt wird. Benutzer klicken Sie auf dieses Symbol, um den zugehörigen Dialogfeldern oder Aufgabenbereiche, die weitere Optionen angeben, die im Zusammenhang mit der Gruppe zu öffnen.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe  
  
1.  Wählen Sie die Menüband-Codedatei (*vb* oder *cs* Datei) in **Projektmappen-Explorer**.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Designer**.  
  
3.  Mit der rechten Maustaste in einer beliebigen Gruppe im Menüband-Designer, und klicken Sie dann auf **DialogBoxLauncher hinzufügen**.  
  
     Fügen Sie Code in die <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> Ereignis der Gruppe, die einen benutzerdefinierten oder integrierten Dialogfeld zu öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Menüband-designer](../vsto/ribbon-designer.md)   
 [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Vorgehensweise: Hinzufügen von Steuerelementen zur backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  