---
title: 'Vorgehensweise: Hinzufügen eines Dialogfeld-Startprogramms zu einer Menübandgruppe'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d831cb629665e641394d011bd11eb74481c4f94
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087182"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Vorgehensweise: Hinzufügen eines Dialogfeld-Startprogramms zu einer Menübandgruppe
  Sie können ein Dialogfeld-Startprogramms zu einer Gruppe auf einem Menüband hinzufügen. Ein Dialogfeld-Startprogramm ist ein kleines Symbol, das in einer Gruppe angezeigt wird. Benutzer klicken Sie auf dieses Symbol, um den zugehörigen Dialogfeldern oder Aufgabenbereiche, die weitere Optionen angeben, die im Zusammenhang mit der Gruppe zu öffnen.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe

1. Wählen Sie die Menüband-Codedatei (*vb* oder *cs* Datei) in **Projektmappen-Explorer**.

2. Auf der **Ansicht** Menü klicken Sie auf **Designer**.

3. Mit der rechten Maustaste in einer beliebigen Gruppe im Menüband-Designer, und klicken Sie dann auf **DialogBoxLauncher hinzufügen**.

     Fügen Sie Code in die <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> Ereignis der Gruppe, die einen benutzerdefinierten oder integrierten Dialogfeld zu öffnen.

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Menüband-designer](../vsto/ribbon-designer.md)
- [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Vorgehensweise: Hinzufügen von Steuerelementen zur backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
