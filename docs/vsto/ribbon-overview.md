---
title: "&#220;bersicht &#252;ber die Multifunktionsleiste"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Benutzerdefiniertes Menüband, Mehrere Multifunktionsleisten"
  - "Anpassen des Menübands, Mehrere Multifunktionsleisten"
  - "Menüband [Office-Entwicklung in Visual Studio]"
  - "Menüband [Office-Entwicklung in Visual Studio], Informationen zur Multifunktionsleiste"
  - "Menüband [Office-Entwicklung in Visual Studio], Mehrere Multifunktionsleisten"
  - "Symbolleisten [Office-Entwicklung in Visual Studio]"
  - "Symbolleisten [Office-Entwicklung in Visual Studio], Menüband"
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# &#220;bersicht &#252;ber die Multifunktionsleiste
  Das Menüband dient zum Organisieren verwandter Befehle, damit sie leichter zu finden sind.  Befehle werden als Steuerelemente auf dem Menüband angezeigt.  Steuerelemente sind in *Gruppen* entlang einer horizontalen Leiste am oberen Rand des Anwendungsfensters organisiert.  Verwandte Gruppen sind auf Registerkarten organisiert.  
  
 Auf die meisten Features, auf die in früheren Versionen von Microsoft Office System über die Menüs und Symbolleisten zugegriffen wurde, kann jetzt über das Menüband zugegriffen werden.  Weitere Informationen finden Sie im technischen Artikel [Entwicklerübersicht der Benutzeroberfläche für 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Anpassen des Microsoft Office\-Menübands  
 Fügen Sie Ihrem Office\-Projekt zum Anpassen des Menübands eines der folgenden Menübandelemente hinzu:  
  
-   **Menüband \(Visueller Designer\)**  
  
-   **Menüband \(XML\)**  
  
 Zum Anpassen des Excel\-Menübands fügen Sie dem Excel\-VSTO\-Add\-In\-Projekt beispielsweise ein Menübandelement hinzu.  
  
### Element "Menüband \(Visueller Designer\)"  
 Das Element **Menüband \(Visueller Designer\)** verfügt über erweiterte Tools, die Ihnen den Entwurf und die Entwicklung benutzerdefinierter Menübänder erleichtern.  Verwenden Sie das Element **Menüband \(Visueller Designer\)**, um das Menüband auf folgende Weisen anzupassen:  
  
-   Fügen Sie einem Menüband benutzerdefinierte oder integrierte Registerkarten hinzu.  
  
-   Fügen Sie einer benutzerdefinierten oder integrierten Registerkarte benutzerdefinierte Gruppen hinzu.  
  
    > [!NOTE]  
    >  Eine integrierte Registerkarte oder Gruppe ist ein Element, das sich bereits auf dem Menüband einer Microsoft Office\-Anwendung befindet.  Die Registerkarte **Daten** ist z. B. eine integrierte Registerkarte in Excel.  Die Gruppe **Verbindungen** ist eine integrierte Gruppe auf der Registerkarte **Daten**.  
  
-   Fügen Sie einer benutzerdefinierten Gruppe benutzerdefinierte Steuerelemente hinzu.  
  
-   Fügen Sie der Backstage\-Ansicht benutzerdefinierte Steuerelemente hinzu.  
  
 Weitere Informationen zum Anpassen eines Menübands mithilfe des Elements **Menüband \(Visueller Designer\)** finden Sie unter [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md).  
  
### Element "Menüband \(XML\)"  
 Verwenden Sie das Element **Menüband \(XML\)**, wenn Sie das Menüband auf eine Weise anpassen möchten, die vom Element **Menüband \(Visueller Designer\)** nicht unterstützt wird.  Verwenden Sie das Element **Menüband \(XML\)**, um das Menüband auf folgende Weisen anzupassen:  
  
-   Fügen Sie einer benutzerdefinierten oder integrierten Registerkarte eigene *Gruppen* hinzu.  
  
-   Fügen Sie einer benutzerdefinierten Gruppe integrierte Steuerelemente hinzu.  
  
-   Fügen Sie benutzerdefinierten Code hinzu, um die Ereignishandler integrierter Steuerelemente zu überschreiben.  
  
-   Passen Sie die Symbolleiste für den Schnellzugriff an.  
  
-   Geben Sie eine Menübandanpassung zwischen VSTO\-Add\-Ins mithilfe einer qualifizierten ID frei.  
  
 Weitere Informationen zum Anpassen eines Menübands mithilfe des Elements **Menüband \(XML\)** finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
## Exportieren eines Menübands vom Menüband\-Designer in "Menüband \(XML\)"  
 Wenn Sie ein Menüband mithilfe des Menüband\-Designers erstellen und dann entscheiden, dass Sie das Menüband auf eine Weise anpassen möchten, die vom Element **Menüband \(Visueller Designer\)** nicht unterstützt wird, können Sie das Menüband nach XML exportieren.  
  
 Visual Studio erstellt automatisch ein Element **Menüband \(XML\)** und füllt die Datei "Menüband \(XML\)" mit Elementen und Attributen für jedes Steuerelement auf dem Menüband auf.  
  
 Nicht alle Eigenschaften im Fenster **Eigenschaften** des Menüband\-Designers werden in die Datei "Menüband \(XML\)" übertragen.  Von Visual Studio wird der Wert der **Image**\- oder **Text**\-Eigenschaft beispielsweise nicht übertragen.  Hierfür müssen Sie eine Rückrufmethode in der Menüband\-Codedatei des exportierten Projekts erstellen, um ein Bild zuzuweisen oder den Text eines Steuerelements festzulegen.  Visual Studio generiert im Rahmen des Exportvorgangs keine automatischen Rückrufmethoden.  
  
 Darüber hinaus werden alle nicht geänderten Standardeigenschaftswerte nicht in der resultierenden Menüband\-XML\-Datei angezeigt.  
  
 Weitere Informationen zum Exportieren des Menübands nach XML finden Sie unter [Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### Aktualisieren des Codes  
 Eine neue Menüband\-Codedatei wird dem **Projektmappen\-Explorer** hinzugefügt.  Diese Datei enthält die Menüband\-XML\-Klasse.  Sie müssen Rückrufmethoden im `Ribbon Callbacks`\-Bereich dieser Klasse erstellen, um Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln.  Verschieben Sie den Code aus den Ereignishandlern in die Rückrufmethoden, und ändern Sie den Code, damit er mit dem Programmmodell für die Menübanderweiterung \(RibbonX\) verwendet werden kann.  Weitere Informationen finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
 Sie müssen den Code auch den Klassen `ThisAddIn`, `ThisWorkbook` oder `ThisDocument` hinzufügen, durch die die CreateRibbonExtensibilityObject\-Methode überschrieben und die Menüband\-XML\-Klasse an die Office\-Anwendung zurückgegeben wird.  
  
 Weitere Informationen finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
## Hinzufügen mehrerer Menübandelemente zu einem Projekt  
 Sie können einem einzelnen Projekt mehrere Menübandelemente hinzufügen.  Dies ist hilfreich, wenn Sie eine der folgenden Aufgaben ausführen möchten:  
  
-   Erstellen von Menübändern für Outlook\-*Inspektoren*.  Weitere Informationen finden Sie unter [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Ein Inspektor ist ein Fenster, das geöffnet wird, wenn der Benutzer bestimmte Aufgaben ausführt, z. B. eine E\-Mail verfasst.  
  
-   Wählen Sie aus, welches Menüband zur Laufzeit angezeigt wird.  
  
### Auswählen der Menübänder, die zur Laufzeit angezeigt werden  
 Da ein Projekt mehr als ein Menüband enthalten kann, können Sie auswählen, welches Menüband zur Laufzeit angezeigt wird.  
  
 Zur Auswahl eines Menübands, das zur Laufzeit angezeigt wird, überschreiben Sie die CreateRibbonExtensibilityObject\-Methode in der Klasse `ThisAddin`, `ThisWorkbook` oder `ThisDocument` des Projekts und geben das Menüband zurück, das Sie anzeigen möchten.  Im folgenden Beispiel wird der Wert eines Felds namens `myCondition` überprüft und das entsprechende Menüband zurückgegeben.  
  
> [!NOTE]  
>  Die in diesem Beispiel verwendete Syntax gibt ein Menüband zurück, das mit dem Element **Menüband \(Visueller Designer\)** erstellt wurde.  Die Syntax für die Rückgabe eines Menübands, das mithilfe des Elements **Menüband \(XML\)** erstellt wurde, weicht geringfügig ab.  Weitere Informationen zum Zurückgeben eines Elements **Menüband \(XML\)** finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
 Fügen Sie den folgenden Code hinzu:  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
### Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)|Veranschaulicht die Anpassung des Menübands einer Microsoft Office\-Anwendung und das Hinzufügen eines **Menüband \(Visueller Designer\)**\- oder **Menüband \(XML\)**\-Elements zu einem Office\-Projekt.|  
|[Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)|Beschreibt die Verwendung des Menüband\-Designers, um dem Menüband einer Microsoft Office\-Anwendung benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzufügen.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht die Erstellung einer benutzerdefinierten Menüband\-Registerkarte mithilfe des Menüband\-Designers.  Sie können den Menüband\-Designer verwenden, um der benutzerdefinierten Registerkarte Steuerelemente hinzuzufügen und diese zu positionieren.|  
|[Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md)|Bietet eine Übersicht des Objektmodells mit starker Typisierung, das Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit verwenden können.|  
|[Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Veranschaulicht die Verwendung des Menüband\-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office\-Anwendung geladen wurde.|  
|[Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office Outlook.|  
|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office InfoPath.|  
|[Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)|Veranschaulicht das Einblenden, Ausblenden und Ändern des Menübands und wie Sie Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook\-Formularbereich ermöglichen.|  
|[Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Veranschaulicht das Ändern der Reihenfolge von Registerkarten auf einem Menüband.|  
|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|Veranschaulicht das Hinzufügen von Gruppen und Steuerelementen zu einer integrierten Registerkarte.|  
|[Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)|Veranschaulicht das Hinzufügen von Steuerelementen zum Menü, das durch Klicken auf **Datei** geöffnet wird.|  
|[Gewusst wie: Hinzufügen eines Dialogfeld-Startprogramms zu einer Multifunktionsleistengruppe](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Veranschaulicht das Hinzufügen eines Dialogfeld\-Startprogramm zu einer beliebigen Gruppe auf einem Menüband.|  
|[Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Veranschaulicht das Anpassen des Menübands auf eine innovative Weise, bei der das Menüband vom Designer in Menüband\-XML exportiert wird.|  
|[Multifunktionsleisten-XML](../vsto/ribbon-xml.md)|Erläutert die Anpassung eines Menübands durch Verwendung von Menüband\-XML.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht die Erstellung einer benutzerdefinierten Menüband\-Registerkarte mithilfe des Elements **Menüband \(XML\)**.|  
  
  