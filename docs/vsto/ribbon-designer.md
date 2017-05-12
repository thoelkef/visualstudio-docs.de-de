---
title: "Multifunktionsleisten-Designer"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Menüband"
  - "Benutzerdefiniertes Menüband"
  - "Benutzerdefiniertes Menüband, Informationen zum Multifunktionsleisten-Designer"
  - "Anpassen des Menübands"
  - "Anpassen des Menübands, Informationen zum Multifunktionsleisten-Designer"
  - "Designer [Office-Entwicklung in Visual Studio], Menüband"
  - "Schreibschutzeigenschaften"
  - "Menüband [Office-Entwicklung in Visual Studio], Allgemeine Aufgaben"
  - "Menüband [Office-Entwicklung in Visual Studio], Steuerelemente"
  - "Menüband [Office-Entwicklung in Visual Studio], Anpassen"
  - "Menüband [Office-Entwicklung in Visual Studio], Tastenkombinationen"
  - "Menüband [Office-Entwicklung in Visual Studio], Visueller Designer"
  - "Menüband-Designer [Office-Entwicklung in Visual Studio]"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# Multifunktionsleisten-Designer
  Der Menüband\-Designer ist ein visueller Entwurfzeichnungsbereich.  Mit dem Menüband\-Designer werden benutzerdefinierte Registerkarten, Gruppen und Steuerelemente des Menübands einer Microsoft Office\-Anwendung hinzugefügt.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Fügen Sie zum Öffnen des Menüband\-Designers dem Projekt ein Element von **Menüband \(Visual Designer\)** hinzu.  Anschließend können die Entwurftools für die folgenden Aufgaben verwendet werden:  
  
-   [Entwerfen des Menübandlayouts](#DesigningRibbonLayout)  
  
-   [Behandeln von Ereignissen und Festlegen der Steuerelementeigenschaften](#HandleEventsSetProperties)  
  
-   [Hinzufügen von Steuerelementen zur Backstage\-Ansicht](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Einige Aufgaben können mit dem Menüband\-Designer nicht ausgeführt werden.  Weitere Informationen zu diesen Aufgaben und zu deren Ausführung finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie im Thema zur [Verwendung des Menüband\-Designers zum Anpassen des Menübands in Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## Hinzufügen eines Elements von Menüband \(Visual Designer\) zu einem Projekt  
 Fügen Sie zum Verwenden des Menüband\-Designers dem Projekt ein neues Element von **Menüband \(Visual Designer\)** hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Beim Hinzufügen eines neuen Elements von **Menüband \(Visual Designer\)** fügt Visual Studio dem Projekt automatisch die folgenden Dateien hinzu:  
  
-   Eine Menüband\-Codedatei.  Diese Datei besitzt den Namen, den Sie im Dialogfeld **Neues Element hinzufügen** für das Element **Menüband \(Visual Designer\)** angeben.  Fügen Sie dieser Datei zum Behandeln der Menübandereignisse Code hinzu.  
  
-   Eine Codedatei des Menüband\-Designers.  Diese Datei beinhaltet vom Menüband\-Designer generierten Code und sollte nicht direkt bearbeitet werden.  
  
-   Eine Ressourcendatei.  Diese Datei beinhaltet die Eigenschaftswerte jedes Steuerelements auf dem Menüband.  
  
 Sollte bereits ein Element von **Menüband \(Visual Designer\)** aus einem anderen Projekt vorhanden sein, kann dieses im aktuellen Projekt mithilfe des Dialogfelds **Vorhandenes Element hinzufügen** wieder verwendet werden.  
  
##  <a name="DesigningRibbonLayout"></a> Entwerfen eines Menübands  
 Zum Öffnen des Menüband\-Designers stehen drei Möglichkeiten zur Verfügung:  
  
-   Doppelklicken Sie im **Projektmappen\-Explorer** auf die Menüband\-Codedatei.  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Menüband\-Codedatei, und klicken Sie danach auf **Ansicht\-Designer**.  
  
-   Wählen Sie im **Projektmappen\-Explorer** die Menüband\-Codedatei aus, und klicken Sie dann im Menü **Ansicht** auf **Designer**.  
  
 Der Menüband\-Designer beinhaltet eine Standardregisterkarte und \-gruppe.  Standardregisterkarte und \-gruppe können aus dem Menüband\-Designer entfernt werden.  Klicken Sie zum Entfernen der Standardgruppe mit der rechten Maustaste auf **Group1**, und klicken Sie anschließend auf **Löschen**.  Klicken Sie zum Entfernen der Standardregisterkarte mit der rechten Maustaste in einen leeren Bereich der Entwurfsoberfläche, und klicken Sie anschließend auf **Registerkarte für Menüband entfernen**.  
  
 Dem Menüband\-Designer können auch benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzugefügt werden.  Diese Steuerelemente befinden sich in der **Toolbox** in der Gruppe **Steuerelemente für Office\-Menübänder**.  Zum Hinzufügen von Steuerelementen von der Gruppe **Steuerelemente für Office\-Menübänder** zum Menüband\-Designer stehen drei verschiedene Möglichkeiten zur Verfügung:  
  
-   Ein Steuerelement in einen geeigneten Bereich im Menüband\-Designer ziehen.  
  
-   Auf ein Steuerelement und anschließend in einen geeigneten Bereich im Menüband\-Designer klicken.  
  
-   Geeigneten Bereich im Designer auswählen und anschließend auf ein Steuerelement in der **Toolbox** doppelklicken.  
  
### Menüband\-Entwurfworkflow  
 Führen Sie folgende grundlegende Schritte zum Entwerfen des Menübandlayouts aus:  
  
1.  [Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband](#AddTabToRibbon)  
  
2.  [Hinzufügen von Gruppen zur Registerkarte](#AddGroupsToTab)  
  
3.  [Hinzufügen von Steuerelementen zu den Gruppen](#AddControlsToGroups)  
  
 Steuerelemente können nur auf Gruppen abgelegt werden; das direkte Ziehen eines Steuerelements auf eine Registerkarte oder das Menüband ist nicht möglich.  Gruppen können nur auf Registerkarten abgelegt werden; das direkte Ziehen einer Gruppe auf ein Menüband ist nicht möglich.  
  
 Ordnen Sie Steuerelemente durch Ziehen zu den korrekten Positionen an.  Die Eigenschaften eines Steuerelements können auch im Fenster **Eigenschaften** festgelegt werden.  
  
 Steuerelemente können auf dem Menüband nicht von einer Registerkarte zur anderen gezogen werden.  Soll ein Steuerelement zu einer anderen Registerkarte verschoben werden, muss das Steuerelement mit dem Befehl **Ausschneiden** von einer Registerkarte entfernt und anschließend in eine andere Registerkarte eingefügt werden.  Wird das Steuerelement ausgeschnitten und eingefügt, wird der Ereignishandler angehalten.  Die Ausführung des Ereignishandlers kann im Fenster **Eigenschaften** fortgesetzt werden.  Weitere Informationen finden Sie unter [Eigenschaftenfenster](../ide/reference/properties-window.md).  
  
###  <a name="AddTabToRibbon"></a> Hinzufügen von benutzerdefinierten Registerkarten zum Menüband  
 Zum Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband stehen drei Möglichkeiten zur Verfügung:  
  
-   Fügen Sie von der **Toolbox** eine Registerkarte hinzu.  
  
-   Klicken Sie mit der rechten Maustaste auf den Menüband\-Designer, und klicken Sie anschließend auf **Registerkarte für Menüband hinzufügen**.  
  
-   Öffnen Sie den **Registerkartenauflistungs\-Editor**, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Wählen Sie zum Öffnen von **Registerkartenauflistungs\-Editor** im Fenster **Eigenschaften** die **Tabs**\-Eigenschaft, und klicken Sie anschließend auf die Schaltfläche mit den Auslassungszeichen ![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer").  
  
 Nach dem Hinzufügen einer Registerkarte können Gruppen mit Steuerelementen hinzugefügt werden.  
  
#### Entfernen von benutzerdefinierten Registerkarten vom Menüband  
 Zum Entfernen einer benutzerdefinierten Registerkarte vom Menüband stehen drei Möglichkeiten zur Verfügung:  
  
-   Klicken Sie mit der rechten Maustaste auf den Menüband\-Designer, und klicken Sie anschließend auf **Registerkarte für Menüband entfernen**.  
  
-   Klicken Sie im Bereich **Befehle** des Fensters **Eigenschaften** auf **Registerkarte für Menüband entfernen**.  
  
-   Öffnen Sie **Registerkartenauflistungs\-Editor**, und klicken Sie zuerst auf die Registerkarte und anschließend auf **Entfernen**.  
  
#### Ändern der Position einer Registerkarte auf dem Menüband  
 Sie können die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern.  Benutzerdefinierte Registerkarten können auch vor oder nach einer integrierten Registerkarte auf dem Menüband angeordnet werden.  Weitere Informationen finden Sie unter [Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### Anpassen der integrierten Registerkarten auf dem Menüband  
 Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office\-Anwendung befindet.  Beispielsweise handelt es sich bei der Registerkarte **Daten** um eine vordefinierte Registerkarte in Excel.  
  
 Einer integrierten Registerkarte können Gruppen und Steuerelemente hinzugefügt werden.  Standardmäßig wird eine benutzerdefinierte Gruppe als letzte Gruppe auf einer integrierten Registerkarte angezeigt, obwohl sie vor oder hinter eine integrierte Gruppe auf der Registerkarte verschoben werden kann.  
  
 Integrierte Gruppen können nicht entfernt werden.  
  
 Details zur Anpassung einer integrierten Registerkarte finden Sie unter [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Hinzufügen von Gruppen zu einer Registerkarte  
 Steuerelemente auf dem Menüband werden mithilfe von Gruppen logisch organisiert.  Fügen Sie Registerkarten Gruppen hinzu.  Fügen Sie der Gruppe alle anderen Steuerelemente hinzu.  
  
###  <a name="AddControlsToGroups"></a> Hinzufügen von Steuerelementen zu Gruppen  
 Fügen Sie einer Gruppe mindestens ein Steuerelement hinzu.  In der folgenden Tabelle wird jedes Steuerelement beschrieben.  
  
|Steuerelement|Beschreibung|  
|-------------------|------------------|  
|**Feld**|Ein Container, der Steuerelemente in einer Gruppe organisiert.  Einem Feld kann mit Ausnahme von Trennzeichen, Gruppen oder Registerkarten jedes beliebige Steuerelement hinzugefügt werden.  Ein Feld kann horizontal oder vertikal dargestellt werden.|  
|**Button**|Eine Schaltfläche, durch die eine Aktion gestartet wird.  Sie können einer Gruppe, einer Schaltflächengruppe, einer Dropdownliste, einem Katalog, einem Menü oder einer Trennschaltfläche eine Schaltfläche hinzufügen.|  
|**ButtonGroup**|Eine Gruppe, die mindestens eine Schaltfläche, eine Umschaltfläche, ein Menü, eine Trennschaltfläche und einen Katalog beinhaltet.  Einer Gruppe oder einem Menü kann eine Schaltflächengruppe oder eine Gruppe hinzugefügt werden.|  
|**CheckBox**|Ein Feld, das zum Aktivieren oder Deaktivieren einer Option aktiviert oder deaktiviert ist.|  
|**ComboBox**|Ein Bearbeitungsfeld mit einem angehängten Listenfeld.  Benutzer können ihre Auswahl entweder eingeben oder auswählen.  Im Feld wird die aktuelle Auswahl angezeigt.  Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A>\-Eigenschaft, um Elemente während der Laufzeit vor oder nach dem Laden des Menübands in die Office\-Anwendung hinzuzufügen und zu entfernen.|  
|**DropDown**|Eine Liste der Elemente, die von Benutzern ausgewählt werden können.  In eine Dropdownliste kann kein neues Element eingegeben werden.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>\-Eigenschaft Elemente hinzu.  Elemente können während der Laufzeit hinzugefügt und entfernt werden.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>\-Eigenschaft Schaltflächen hinzu.  Allerdings können Schaltflächen während der Laufzeit nicht hinzugefügt und entfernt werden, nachdem das Menüband in die Office\-Anwendung geladen wurde.|  
|**EditBox**|Ein Feld, in das der Benutzer Text eingeben kann.|  
|**Katalog**|Ein Menü mit einem visuellen Auswahlarray oder \-raster, in dem Benutzer eine Auswahl treffen können.  Das Layout der Auswahl im Menü kann gesteuert werden.  Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>\-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>\-Eigenschaft, um die Anzahl der Zeilen und Spalten anzugeben, in denen die Elemente und Schaltflächen des Katalogs angezeigt werden.|  
|**Bezeichnung**|Text, mit dem die Steuerelemente auf dem Menüband bestimmt werden können.|  
|**Menü**|Eine Dropdownliste, die sämtliche der folgenden Steuerelemente beinhalten kann:<br /><br /> -   Button<br />-   Kontrollkästchen<br />-   Katalog<br />-   Menü<br />-   Trennschaltfläche<br />-   Umschaltfläche<br />-   Trennzeichen<br /><br /> Wenn Sie einem Menü im Menüband\-Designer ein Steuerelement hinzufügen möchten, klicken Sie im Menü auf den Pfeil nach unten, um die Menüentwurfsoberfläche anzuzeigen.  Anschließend können Menübandsteuerelemente von der **Toolbox** zum Menü gezogen werden.  Ordnen Sie Steuerelemente durch Ziehen zu den gewünschten Positionen an.<br /><br /> Sollen <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> nach dem Laden des Menübands in die Office\-Anwendung Steuerelemente hinzugefügt werden, muss die <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>\-Eigenschaft vor dem Laden des Menübands auf **true** festgelegt werden.  Informationen dazu finden Sie unter [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md).|  
|**Trennzeichen**|Eine dünne Leiste zum Trennen von Elementen in einer Liste.  Beim Hinzufügen zu einer Gruppe ist die Leiste vertikal.  Beim Hinzufügen zu einem Menü ist die Leiste horizontal.|  
|**SplitButton**|Eine Schaltfläche mit einem angehängten Menü.  Eine Trennschaltfläche kann jedes der folgenden Steuerelemente beinhalten:<br /><br /> -   Button<br />-   Kontrollkästchen<br />-   Katalog<br />-   Menü<br />-   Trennschaltfläche<br />-   Umschaltfläche<br />-   Trennzeichen<br /><br /> Ebenso wie das Menü verfügt die Trennschaltfläche über eine eigene Entwurfsoberfläche.  Im Gegensatz zu einem Menü können die Elemente auf einer Trennschaltfläche nur vor dem Laden des Menübands in die Office\-Anwendung aktualisiert werden.  Weitere Informationen zum Aktualisieren der Elemente auf einer Trennschaltfläche finden Sie unter [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Eine Schaltfläche, die gedrückt oder nicht gedrückt angezeigt wird.|  
  
##  <a name="HandleEventsSetProperties"></a> Behandeln von Ereignissen und Festlegen von Eigenschaften  
 Mit dem Menüband\-Designer können Steuerelementeigenschaften während der Entwurfszeit im Fenster **Eigenschaften** festgelegt werden.  Darüber hinaus macht das Menüband ein Objektmodell mit starker Typisierung verfügbar, das zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen während der Laufzeit verwendet werden kann.  
  
 Sie können auf jedes Steuerelement im Designer doppelklicken, um einen Ereignishandler für das Standardereignis des Steuerelements zu öffnen.  Mit dem **Eigenschaftenfenster** können Sie Ereignishandler für alle anderen Steuerelementereignisse erstellen.  
  
 Menübandereignisse befinden sich im <xref:Microsoft.Office.Tools.Ribbon>\-Namespace.  Mit dem Element **Menüband \(Visual Designer\)** wird dieser Assembly im Projekt automatisch ein Verweis hinzugefügt, und die entsprechende **using**\-Anweisung oder **Imports**\-Anweisung wird am Anfang der Menüband\-Codedatei eingefügt.  
  
 Weitere Informationen zum Behandeln von Menübandereignissen und zum Festlegen der Eigenschaften von Menübandsteuerelementen während der Laufzeit finden Sie unter [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Anpassen der Backstage\-Ansicht  
 Mithilfe des Menüband\-Designers können Sie dem Menü, das beim Klicken auf die Registerkarte **Datei** geöffnet wird, Steuerelemente hinzuzufügen.  Mit diesem Menü wird die Backstage\-Ansicht aufgerufen.  
  
 Sie können mit dem Menüband\-Designer keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren.  Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage\-Ansicht angezeigt wird.  Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie ein Menüband\-XML verwenden.  Weitere Informationen zu **Menüband \(XML\)** finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  Weitere Informationen zum Anpassen der Backstage\-Ansicht finden Sie unter [Einführung in die Office 2010\-Backstage\-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188) und im Thema zum [Anpassen der Office 2010\-Backstage\-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Informationen darüber, wie Steuerelemente der Backstage\-Ansicht hinzugefügt werden, finden Sie unter [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Barrierefreiheit im Menüband\-Designer  
 Steuerelemente auf dem Menüband\-Designer können mithilfe von Tastenkombinationen verschoben werden.  Einige Tastenkombinationen gelten für alle Steuerelemente, wohingegen einige Tastenkombinationen nur für Steuerelemente mit Menüs verwendbar sind.  
  
 Die für alle Steuerelemente verwendbaren Tastenkombinationen werden in der folgenden Tabelle angezeigt.  
  
|Aktion|Tastenkombination|  
|------------|-----------------------|  
|Verschieben eines Steuerelements vor das vorherige Steuerelement in der Liste.|STRG\+NACH\-OBEN<br /><br /> STRG\+NACH\-LINKS|  
|Verschieben eines Steuerelements hinter das nächste Steuerelement in der Liste.|STRG\+NACH\-UNTEN<br /><br /> STRG\+NACH\-RECHTS|  
|Verschieben der Auswahl von einem Steuerelement zu einem anderen Steuerelement in derselben Gruppe.  Wechseln Sie in einem Dropdownbereich zwischen dem übergeordneten Steuerelement und den Steuerelementen im Dropdownbereich.|NACH\-OBEN<br /><br /> NACH\-OBEN|  
|Durchlaufen aller Steuerelemente \(vorwärts\).|TAB|  
|Durchlaufen aller Steuerelemente \(rückwärts\).|UMSCHALT\+TAB|  
|Löschen des ausgewählten Steuerelements oder eines Satzes von Steuerelementen.|ENTF|  
|Kopieren der ausgewählten Steuerelemente.|STRG\+C|  
|Ausschneiden der ausgewählten Steuerelemente.|STRG\+X|  
|Einfügen von Steuerelementen aus der Zwischenablage.|STRG\+V|  
|Auswählen der **Toolbox**.|STRG\+ALT\+X|  
|Auswählen der übergeordneten Komponente.|ESC|  
  
 Die Tastenkombinationen gelten nur für das Microsoft Office\-Menü; <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> und <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> werden in der folgenden Tabelle angezeigt.  
  
|Aktion|Tastenkombination|  
|------------|-----------------------|  
|Auswählen des übergeordneten Steuerelements, falls der Dropdownbereich geöffnet ist und im Dropdownbereich ein Steuerelement ausgewählt ist.|NACH\-LINKS|  
|Schließen des Dropdownbereichs, falls der Dropdownbereich geöffnet ist und das übergeordnete Steuerelement ausgewählt ist.|NACH\-LINKS|  
|Öffnen des Dropdownbereichs.|NACH\-RECHTS|  
|Auswählen des ersten Steuerelements im Dropdownbereich, falls der Dropdownbereich geöffnet ist.|NACH\-RECHTS|  
|Schließen eines Dropdownbereichs.|ESC|  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  