---
title: "Menüband (Übersicht) | Microsoft Docs"
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
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fcf026af4877ee2aefe17551763752d385b63493
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ribbon-overview"></a>Übersicht über die Multifunktionsleiste
  Das Menüband dient zum Organisieren verwandter Befehle, damit sie leichter zu finden sind. Befehle werden als Steuerelemente auf dem Menüband angezeigt. Steuerelemente sind in organisiert *Gruppen* entlang einer horizontalen Leiste am oberen Rand des Anwendungsfensters. Verwandte Gruppen sind auf Registerkarten organisiert.  
  
 Auf die meisten Funktionen, auf die in früheren Versionen von Microsoft Office System über die Menüs und Symbolleisten zugegriffen wurde, kann jetzt über das Menüband zugegriffen werden. Weitere Informationen finden Sie im technischen Artikel [Entwicklerübersicht der Benutzeroberfläche für 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>Anpassen des Microsoft Office-Menübands  
 Fügen Sie Ihrem Office-Projekt zum Anpassen des Menübands eines der folgenden Menübandelemente hinzu:  
  
-   **Menüband (visueller Designer)**  
  
-   **Menüband (XML)**  
  
 Zum Anpassen des Excel-Menübands fügen Sie dem Excel-VSTO-Add-In-Projekt beispielsweise ein Menübandelement hinzu.  
  
### <a name="ribbon-visual-designer-item"></a>Element "Menüband (Visueller Designer)"  
 Die **Menüband (visueller Designer)** Element verfügt über erweiterte Tools, die Ihnen das Entwerfen und Entwickeln eines benutzerdefinierten Menübands erleichtern. Verwenden der **Menüband (visueller Designer)** Element zum Anpassen des Menübands auf folgende Weise:  
  
-   Fügen Sie einem Menüband benutzerdefinierte oder integrierte Registerkarten hinzu.  
  
-   Fügen Sie einer benutzerdefinierten oder integrierten Registerkarte benutzerdefinierte Gruppen hinzu.  
  
    > [!NOTE]  
    >  Eine integrierte Registerkarte oder Gruppe ist ein Element, das sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel. Die **Verbindungen** Gruppe ist eine integrierte Gruppe auf die **Daten** Registerkarte.  
  
-   Fügen Sie einer benutzerdefinierten Gruppe benutzerdefinierte Steuerelemente hinzu.  
  
-   Fügen Sie der Backstage-Ansicht benutzerdefinierte Steuerelemente hinzu.  
  
 Weitere Informationen zum Anpassen eines Menübands mithilfe der **Menüband (visueller Designer)** Element, finden Sie unter [Menüband-Designer](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Element "Menüband (XML)"  
 Verwenden der **Menüband (XML)** Element Wunsch Anpassen des Menübands auf eine Weise, die von nicht unterstützt wird die **Menüband (visueller Designer)** Element. Verwenden der **Menüband (XML)** Element zum Anpassen des Menübands auf folgende Weise:  
  
-   Hinzufügen *integrierte* Gruppen aus, um einen benutzerdefinierten oder integrierten Registerkarte.  
  
-   Fügen Sie einer benutzerdefinierten Gruppe integrierte Steuerelemente hinzu.  
  
-   Fügen Sie benutzerdefinierten Code hinzu, um die Ereignishandler integrierter Steuerelemente zu überschreiben.  
  
-   Passen Sie die Symbolleiste für den Schnellzugriff an.  
  
-   Geben Sie eine Menübandanpassung zwischen VSTO-Add-Ins mithilfe einer qualifizierten ID frei.  
  
 Weitere Informationen zum Anpassen des Menübands mithilfe der **Menüband (XML)** Element, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportieren eines Menübands vom Menüband-Designer in "Menüband (XML)"  
 Wenn Sie ein Menüband mithilfe des Menüband-Designers erstellen und dann entscheiden, dass Sie das Menüband auf eine Weise anpassen möchten, die die **Menüband (visueller Designer)** Element nicht unterstützt, können Sie das Menüband nach XML exportieren.  
  
 Visual Studio erstellt automatisch eine **Menüband (XML)** Element und füllt die Menüband-XML-Datei mit Elementen und Attributen für jedes Steuerelement auf dem Menüband.  
  
 Nicht alle Eigenschaften, die in der **Eigenschaften** Fenster des Menüband-Designer in der Menüband-XML-Datei übertragen werden.  Visual Studio exportiert z. B. nicht den Wert der **Image** oder **Text** Eigenschaft. Hierfür müssen Sie eine Rückrufmethode in der Menüband-Codedatei des exportierten Projekts erstellen, um ein Bild zuzuweisen oder den Text eines Steuerelements festzulegen. Visual Studio generiert im Rahmen des Exportvorgangs keine automatischen Rückrufmethoden.  
  
 Darüber hinaus werden alle nicht geänderten Standardeigenschaftswerte nicht in der resultierenden Menüband-XML-Datei angezeigt.  
  
 Weitere Informationen zum Exportieren des Menübands nach XML finden Sie unter [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="updating-the-code"></a>Aktualisieren des Codes  
 Eine neue Menüband-Codedatei hinzugefügt **Projektmappen-Explorer**. Diese Datei enthält die Menüband-XML-Klasse. Sie müssen Rückrufmethoden im `Ribbon Callbacks`-Bereich dieser Klasse erstellen, um Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln. Verschieben Sie den Code aus den Ereignishandlern in die Rückrufmethoden, und ändern Sie den Code, damit er mit dem Programmmodell für die Menübanderweiterung (RibbonX) verwendet werden kann. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Außerdem müssen Sie Code zum Hinzufügen der `ThisAddIn`, `ThisWorkbook`, oder `ThisDocument` -Klasse, überschreibt die CreateRibbonExtensibilityObject-Methode und die Office-Anwendung die Menüband-XML-Klasse zurückgegeben.  
  
 Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>Hinzufügen mehrerer Menübandelemente zu einem Projekt  
 Sie können einem einzelnen Projekt mehrere Menübandelemente hinzufügen. Dies ist hilfreich, wenn Sie eine der folgenden Aufgaben ausführen möchten:  
  
-   Erstellen von Menübändern für Outlook *Inspektoren*. Weitere Informationen finden Sie unter [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Ein Inspektor ist ein Fenster, das geöffnet wird, wenn der Benutzer bestimmte Aufgaben ausführt, z. B. eine E-Mail verfasst.  
  
-   Wählen Sie aus, welches Menüband zur Laufzeit angezeigt wird.  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>Auswählen der Menübänder, die zur Laufzeit angezeigt werden  
 Da ein Projekt mehr als ein Menüband enthalten kann, können Sie auswählen, welches Menüband zur Laufzeit angezeigt wird.  
  
 Markieren Sie ein Menüband zur Laufzeit außer Kraft setzen die CreateRibbonExtensibilityObject-Methode in der `ThisAddin`, `ThisWorkbook`, oder `ThisDocument` -Klasse des Projekts, und geben Sie im Menüband, die Sie anzeigen möchten. Im folgenden Beispiel wird der Wert eines Felds namens `myCondition` überprüft und das entsprechende Menüband zurückgegeben.  
  
> [!NOTE]  
>  In diesem Beispiel verwendete Syntax gibt ein Menüband, das erstellt wurde die **Menüband (visueller Designer)** Element. Die Syntax für die Rückgabe eines Menübands, das erstellt wird eine **Menüband (XML)** Element ist etwas anders. Weitere Informationen zum Zurückgeben einer **Menüband (XML)** Element, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
 Fügen Sie den folgenden Code hinzu:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)|Veranschaulicht das Anpassen des Menübands einer Microsoft Office-Anwendung, Hinzufügen einer **Menüband (visueller Designer)** oder **Menüband (XML)** Element aus, um ein Office-Projekt.|  
|[Menüband-Designer](../vsto/ribbon-designer.md)|Beschreibt die Verwendung des Menüband-Designers, um dem Menüband einer Microsoft Office-Anwendung benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzufügen.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht die Erstellung einer benutzerdefinierten Menüband-Registerkarte mithilfe des Menüband-Designers. Sie können den Menüband-Designer verwenden, um der benutzerdefinierten Registerkarte Steuerelemente hinzuzufügen und diese zu positionieren.|  
|[Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)|Bietet eine Übersicht des Objektmodells mit starker Typisierung, das Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit verwenden können.|  
|[Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Veranschaulicht die Verwendung des Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office-Anwendung geladen wurde.|  
|[Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office Outlook.|  
|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office InfoPath.|  
|[Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)|Veranschaulicht das Einblenden, Ausblenden und Ändern des Menübands und wie Sie Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formularbereich ermöglichen.|  
|[Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Veranschaulicht das Ändern der Reihenfolge von Registerkarten auf einem Menüband.|  
|[Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|Veranschaulicht das Hinzufügen von Gruppen und Steuerelementen zu einer integrierten Registerkarte.|  
|[Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)|Veranschaulicht das Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf die **Datei**.|  
|[Vorgehensweise: Hinzufügen eines Dialogfeld-Startprogramms zu einer Menübandgruppe](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Veranschaulicht das Hinzufügen eines Dialogfeld-Startprogramm zu einer beliebigen Gruppe auf einem Menüband.|  
|[Vorgehensweise: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Veranschaulicht das Anpassen des Menübands auf eine innovative Weise, bei der das Menüband vom Designer in Menüband-XML exportiert wird.|  
|[Menüband-XML](../vsto/ribbon-xml.md)|Erläutert die Anpassung eines Menübands durch Verwendung von Menüband-XML.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe der **Menüband (XML)** Element.|  
  
  