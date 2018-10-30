---
title: Übersicht über das Menüband
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51de8b5fbc4e21b4dabaf34f526b85f0b98623db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846358"
---
# <a name="ribbon-overview"></a>Übersicht über das Menüband
  Die Multifunktionsleiste ist eine Möglichkeit zum Organisieren verwandter Befehle, damit sie leichter zu finden sind. Befehle werden als Steuerelemente auf dem Menüband angezeigt. Steuerelemente sind in organisiert *Gruppen* entlang einer horizontalen Leiste am oberen Rand eines Anwendungsfensters. Verwandte Gruppen sind auf Registerkarten organisiert.  
  
 Die meisten Funktionen, die auf die zugegriffen wurde mithilfe von Menüs und Symbolleisten in früheren Versionen von Microsoft Office System können jetzt über das Menüband zugegriffen werden. Weitere Informationen finden Sie im technischen Artikel [Entwicklerübersicht der Benutzeroberfläche für 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customize-the-microsoft-office-ribbon"></a>Die Microsoft Office-Multifunktionsleiste anpassen  
 Fügen Sie zum Anpassen des Menübands, Office-Projekt eine der folgenden Menübandelemente hinzu:  
  
- **Menüband (visueller Designer)**  
  
- **Menüband (XML)**  
  
  Zum Anpassen des Excel-Menübands fügen Sie dem Excel-VSTO-Add-In-Projekt beispielsweise ein Menübandelement hinzu.  
  
### <a name="ribbon-visual-designer-item"></a>Element "Menüband (visueller Designer)"  
 Die **Menüband (visueller Designer)** Element verfügt über erweiterte Tools, die Sie zum Entwerfen und entwickeln eine benutzerdefinierte Multifunktionsleiste erleichtern. Verwenden der **Menüband (visueller Designer)** Element zum Anpassen des Menübands auf folgende Weise:  
  
- Fügen Sie auf einem Menüband benutzerdefinierte oder integrierte Registerkarten hinzu.  
  
- Fügen Sie einer benutzerdefinierten oder integrierten Registerkarte benutzerdefinierte Gruppen hinzu.  
  
  > [!NOTE]  
  >  Eine integrierte Registerkarte oder Gruppe ist, die auf dem Menüband einer Microsoft Office-Anwendung ist bereits vorhanden. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel. Die **Verbindungen** Gruppe ist eine integrierte Gruppe auf die **Daten** Registerkarte.  
  
- Fügen Sie einer benutzerdefinierten Gruppe benutzerdefinierte Steuerelemente hinzu.  
  
- Fügen Sie der Backstage-Ansicht benutzerdefinierte Steuerelemente hinzu.  
  
  Weitere Informationen zum Anpassen eines Menübands mithilfe der **Menüband (visueller Designer)** Element, finden Sie unter [Menüband-Designer](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Element "Menüband (XML)"  
 Verwenden der **Menüband (XML)** Element sollten Sie im Menüband auf eine Weise anpassen, die von nicht unterstützt wird die **Menüband (visueller Designer)** Element. Verwenden der **Menüband (XML)** Element zum Anpassen des Menübands auf folgende Weise:  
  
- Hinzufügen *integrierte* Gruppen zu einer benutzerdefinierten oder integrierten Registerkarte.  
  
- Fügen Sie einer benutzerdefinierten Gruppe integrierte Steuerelemente hinzu.  
  
- Fügen Sie benutzerdefinierten Code hinzu, um die Ereignishandler integrierter Steuerelemente zu überschreiben.  
  
- Passen Sie die Symbolleiste für den Schnellzugriff an.  
  
- Geben Sie eine Menübandanpassung zwischen VSTO-Add-Ins mithilfe einer qualifizierten ID frei.  
  
  Weitere Informationen zum Anpassen des Menübands mithilfe der **Menüband (XML)** Element, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportieren eines Menübands vom Menüband-Designer in Menüband-XML  
 Wenn Sie ein Menüband mithilfe des Menüband-Designers erstellen und dann entscheiden, dass Sie das Menüband auf eine Weise anpassen möchten, die die **Menüband (visueller Designer)** Element nicht unterstützt, können Sie das Menüband nach XML exportieren.  
  
 Visual Studio erstellt automatisch eine **Menüband (XML)** Element und füllt die Menüband-XML-Datei mit Elementen und Attributen für jedes Steuerelement auf dem Menüband.  
  
 Nicht alle Eigenschaften, die in der **Eigenschaften** Fenster des Menüband-Designer in der Menüband-XML-Datei übertragen werden.  Visual Studio exportiert z. B. nicht den Wert des der **Image** oder **Text** Eigenschaft. Hierfür müssen Sie eine Rückrufmethode in der Menüband-Codedatei des exportierten Projekts erstellen, um ein Bild zuzuweisen oder den Text eines Steuerelements festzulegen. Visual Studio generiert im Rahmen des Exportvorgangs keine automatischen Rückrufmethoden.  
  
 Darüber hinaus werden alle nicht geänderten Standardeigenschaftswerte nicht in der resultierenden Menüband-XML-Datei angezeigt.  
  
 Weitere Informationen dazu, wie Sie das Menüband nach XML exportieren, finden Sie unter [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="update-the-code"></a>Aktualisieren Sie den code  
 Eine neue Menüband-Codedatei hinzugefügt **Projektmappen-Explorer**. Diese Datei enthält die Menüband-XML-Klasse. Sie müssen Rückrufmethoden im `Ribbon Callbacks`-Bereich dieser Klasse erstellen, um Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln. Verschieben Sie den Code aus den Ereignishandlern in die Rückrufmethoden, und ändern Sie den Code, damit er mit dem Programmmodell für die Menübanderweiterung (RibbonX) verwendet werden kann. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Sie müssen den Code auch den Klassen `ThisAddIn`, `ThisWorkbook` oder `ThisDocument` hinzufügen, durch die die `CreateRibbonExtensibilityObject`-Methode überschrieben und die Menüband-XML-Klasse an die Office-Anwendung zurückgegeben wird.  
  
 Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="add-multiple-ribbon-items-to-a-project"></a>Fügen Sie mehrerer Menübandelemente zu einem Projekt hinzu  
 Sie können einem einzelnen Projekt mehrere Menübandelemente hinzufügen. Dies ist hilfreich, wenn Sie eine der folgenden Aufgaben ausführen möchten:  
  
-   Erstellen von Menübändern für Outlook *Inspektoren*. Weitere Informationen finden Sie unter [anpassen ein Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Ein Inspektor ist ein Fenster, das geöffnet wird, wenn der Benutzer bestimmte Aufgaben ausführt, z. B. eine E-Mail verfasst.  
  
-   Wählen Sie, welches Menüband zur Laufzeit angezeigt.  
  
### <a name="select-which-ribbons-to-display-at-runtime"></a>Wählen Sie die Laufzeit anzuzeigenden Menübänder  
 Da ein Projekt mehrere Menübänder enthalten kann, können Sie welches Menüband zur Laufzeit anzeigen auswählen.  
  
 Überschreiben, um ein Menüband zur Laufzeit auszuwählen, die `CreateRibbonExtensibilityObject` -Methode in der die `ThisAddin`, `ThisWorkbook`, oder `ThisDocument` Klasse des Projekts, und geben Sie im Menüband aus, die Sie anzeigen möchten. Das folgende Beispiel überprüft den Wert eines Felds mit dem Namen `myCondition` und das entsprechende Menüband zurückgegeben.  
  
> [!NOTE]  
>  In diesem Beispiel verwendete Syntax gibt ein Menüband, die mithilfe der **Menüband (visueller Designer)** Element. Die Syntax für die Rückgabe eines Menübands, die mit einem **Menüband (XML)** Element ist etwas anders. Weitere Informationen zur Rückgabe einer **Menüband (XML)** Element, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
 Fügen Sie den folgenden Code hinzu:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Gewusst wie: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)|Erfahren Sie, wie zum Anpassen des Menübands einer Microsoft Office-Anwendung, Hinzufügen einer **Menüband (visueller Designer)** oder **Menüband (XML)** Element, das ein Office-Projekt.|  
|[Menüband-designer](../vsto/ribbon-designer.md)|Beschreibt, wie Sie die Menüband-Designer verwenden können, um benutzerdefinierte Registerkarten, Gruppen und Steuerelemente des Menübands einer Microsoft Office-Anwendung hinzuzufügen.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht die Erstellung einer benutzerdefinierten Menüband-Registerkarte mithilfe des Menüband-Designers. Sie können den Menüband-Designer verwenden, um der benutzerdefinierten Registerkarte Steuerelemente hinzuzufügen und diese zu positionieren.|  
|[Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)|Bietet eine Übersicht über den stark typisierten Objektmodell, das Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit verwenden können.|  
|[Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Veranschaulicht die Verwendung des Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office-Anwendung geladen wurde.|  
|[Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Enthält Anweisungen zum Anpassen des Menübands in Microsoft Office Outlook.|  
|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Enthält Anweisungen zum Anpassen des Menübands in Microsoft Office InfoPath.|  
|[Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)|Veranschaulicht die anzeigen, ausblenden und Ändern des Menübands und Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formularbereich ermöglichen.|  
|[Gewusst wie: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Veranschaulicht, wie die Reihenfolge der Registerkarten auf einem Menüband ändern.|  
|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|Veranschaulicht das Hinzufügen von Gruppen und Steuerelementen zu einer integrierten Registerkarte.|  
|[Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)|Veranschaulicht das Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf die **Datei**.|  
|[Gewusst wie: Hinzufügen ein Dialogfeld-Startprogramms zu einer Menübandgruppe](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Hinzufügen ein Dialogfeld-Startprogramms zu einer Gruppe auf einem Menüband zeigt.|  
|[Gewusst wie: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Zeigt, wie zum Anpassen des Menübands auf eine innovative Weise durch Exportieren im Menüband vom Designer in Menüband-XML.|  
|[Ribbon XML](../vsto/ribbon-xml.md)|Erläutert, wie Sie ein Menüband mithilfe des Menüband-XML-anpassen können.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe der **Menüband (XML)** Element.|  
  
  