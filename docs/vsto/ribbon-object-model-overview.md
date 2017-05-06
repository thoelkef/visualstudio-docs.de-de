---
title: "Multifunktionsleisten-Objektmodell&#252;bersicht"
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
  - "Menüband [Office-Entwicklung in Visual Studio], Objektmodell"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Multifunktionsleisten-Objektmodell&#252;bersicht
  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] macht ein Objektmodell mit starker Typisierung verfügbar, das zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen während der Laufzeit verwendet werden kann.  Beispielsweise können neue Menüsteuerelemente dynamisch ausgefüllt oder Steuerelemente kontextbezogen angezeigt und ausgeblendet werden.  Zudem besteht die Möglichkeit, einem Menüband Registerkarten, Gruppen und Steuerelemente hinzuzufügen. Dies muss jedoch vor dem Laden des Menübands durch die Office\-Anwendung erfolgen.  Informationen hierzu finden Sie unter [Festlegen von Eigenschaften, die schreibgeschützt werden](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Dieses Menüband\-Objektmodell besteht hauptsächlich aus der [Multifunktionsklasse](#RibbonClass), [Menübandereignissen](#RibbonEvents) und [Menüband\-Steuerelementklassen](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Menübandklasse  
 Wenn Sie einem Projekt ein neues Element für das **Menüband \(Visueller Designer\)** hinzufügen, fügt Visual Studio dem Projekt eine **Ribbon**\-Klasse hinzu.  Die **Ribbon**\-Klasse erbt von der <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>\-Klasse.  
  
 Diese Klasse wird als partielle Klasse angezeigt, die zwischen der Menüband\-Codedatei und der Codedatei des Menüband\-Designers aufgeteilt ist.  
  
##  <a name="RibbonEvents"></a> Menübandereignisse  
 Die **Ribbon**\-Klasse beinhaltet die folgenden drei Ereignisse:  
  
|Ereignis|Beschreibung|  
|--------------|------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wird ausgelöst, wenn die Menübandanpassung von der Office\-Anwendung geladen wird.  Der <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>\-Ereignishandler wird automatisch der Menüband\-Codedatei hinzugefügt.  Führen Sie beim Laden des Menübands mithilfe dieses Ereignishandlers benutzerdefinierten Code aus.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Ermöglicht beim Laden des Menübands die Zwischenspeicherung von Images in der Menübandanpassung.  Eine leichte Leistungsverbesserung wird erzielt, wenn zum Zwischenspeichern der Menüband\-Images in diesem Ereignishandler Code geschrieben wird.  Weitere Informationen finden Sie unter <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Wird ausgelöst, wenn die Menübandinstanz geschlossen wird.|  
  
##  <a name="RibbonControlClasses"></a> Menübandsteuerelemente  
 Der <xref:Microsoft.Office.Tools.Ribbon>\-Namespace beinhaltet einen Typ für jedes Steuerelement, das in der Gruppe **Steuerelemente für Office\-Menübänder** der **Toolbox** angezeigt wird.  
  
 In der folgenden Tabelle wird der Typ für jedes `Ribbon`\-Steuerelement angezeigt.  Eine Beschreibung jedes Steuerelements finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
|Steuerelementname|Klassenname|  
|-----------------------|-----------------|  
|**Feld**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Katalog**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Gruppe**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Bezeichnung**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Trennzeichen**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Registerkarte**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Der <xref:Microsoft.Office.Tools.Ribbon>\-Namespace verwendet für diese Typen das Ribbon\-Präfix, um einen Namenskonflikt mit den Namen der Steuerelementklassen im <xref:System.Windows.Forms>\-Namespace zu verhindern.  
  
 Beim Hinzufügen eines Steuerelements zum Menüband\-Designer deklariert der Menüband\-Designer die Klasse für dieses Steuerelement als Feld in der Codedatei des Menüband\-Designers.  
  
### Allgemeine Aufgaben mithilfe der Eigenschaften von Menübandsteuerelementen  
 Jedes `Ribbon`\-Steuerelement beinhaltet Eigenschaften, mit denen Sie verschiedene Aufgaben ausführen können, wie das Zuweisen einer Bezeichnung zu einem Steuerelement oder das Ausblenden und Anzeigen von Steuerelementen.  
  
 In einigen Fällen sind Eigenschaften schreibgeschützt, nachdem das Menüband geladen oder einem Steuerelement ein dynamisches Menü hinzugefügt wurde.  Weitere Informationen finden Sie unter [Festlegen von Eigenschaften, die schreibgeschützt werden](#SettingReadOnlyProperties).  
  
 In der folgenden Tabelle werden einige der Aufgaben beschrieben, die Sie mithilfe der Eigenschaften des `Ribbon`\-Steuerelements ausführen können.  
  
|Aufgabe:|Vorgehensweise:|  
|--------------|---------------------|  
|Aus\- oder Einblenden eines Steuerelements.|Verwenden Sie die Visible\-Eigenschaft.|  
|Aktivieren oder Deaktivieren eines Steuerelements.|Verwenden Sie die Enabled\-Eigenschaft.|  
|Festlegen der Größe eines Steuerelements.|Verwenden Sie die ControlSize\-Eigenschaft.|  
|Abrufen des Bilds, das auf einem Steuerelement angezeigt wird.|Verwenden Sie die Image\-Eigenschaft.|  
|Ändern der Bezeichnung eines Steuerelements.|Verwenden Sie die Label\-Eigenschaft.|  
|Hinzufügen von benutzerdefinierten Daten zu einem Steuerelement.|Verwenden Sie die Tag\-Eigenschaft.|  
|Abrufen der Elemente in einem <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>\-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>\-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>\-Steuerelement oder einem<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>\-Steuerelement|Verwenden Sie die Items\-Eigenschaft.|  
|Hinzufügen eines <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>\-Steuerelements, eines <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>\-Steuerelements oder eines <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>\-Steuerelements.|Verwenden Sie die Items\-Eigenschaft.|  
|Hinzufügen von Steuerelementen zu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Verwenden Sie die Items\-Eigenschaft.<br /><br /> Sollen <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> nach dem Laden des Menübands in die Office\-Anwendung Steuerelemente hinzugefügt werden, muss die <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A>\-Eigenschaft vor dem Laden des Menübands in die Office\-Anwendung auf **true** festgelegt werden.  Informationen hierzu finden Sie unter [Festlegen von Eigenschaften, die schreibgeschützt werden](#SettingReadOnlyProperties).|  
|Abrufen des ausgewählten Elements von <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Verwenden Sie die SelectedItem\-Eigenschaft.  Verwenden Sie für <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> die <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>\-Eigenschaft.|  
|Abrufen der Gruppen auf <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>\-Eigenschaft.|  
|Angeben der Anzahl der Zeilen und Spalten, die in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> angezeigt werden.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>\-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>\-Eigenschaft.|  
  
##  <a name="SettingReadOnlyProperties"></a> Festlegen von Eigenschaften, die schreibgeschützt werden  
 Einige Eigenschaften können nur vor dem Laden des Menübands festgelegt werden.  Diese Eigenschaften können an drei Orten festgelegt werden:  
  
-   Im Fenster **Eigenschaften** von Visual Studio.  
  
-   Im Konstruktor der **Ribbon**\-Klasse.  
  
-   In der CreateRibbonExtensibilityObject\-Methode der `ThisAddin`, `ThisWorkbook`\- Klasse oder `ThisDocument`\-Klasse des Projekts.  
  
 Dynamische Menüs bieten einige Ausnahmen.  Sie können neue Steuerelemente erstellen, deren Eigenschaften festlegen und sie dann während der Laufzeit einem dynamischen Menü hinzufügen, und zwar auch nach dem Laden des Menübands mit dem Menü.  
  
 Eigenschaften von Steuerelementen, die Sie einem dynamischen Menü hinzufügen, können jederzeit festgelegt werden.  
  
 Weitere Informationen finden Sie unter [Eigenschaften, die schreibgeschützt werden](#ReadOnlyProperties).  
  
### Festlegen von Eigenschaften im Konstruktor des Menübands  
 Sie können die Eigenschaften eines `Ribbon`\-Steuerelements im Konstruktor der **Ribbon**\-Klasse festlegen.  Dieser Code muss nach dem Aufruf der `InitializeComponent`\-Methode angezeigt werden.  Im folgenden Beispiel wird einer Gruppe eine neue Schaltfläche hinzugefügt, falls die aktuelle Uhrzeit 17:00 Pacific Time \(UTC\-8\) oder später ist.  
  
 Fügen Sie den folgenden Code hinzu.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 In Visual C\#\-Projekten, die Sie von Visual Studio 2008 aktualisiert haben, wird der Konstruktor in der Menüband\-Codedatei angezeigt.  
  
 In Visual Basic\-Projekten oder in Visual C\#\-Projekten, die Sie in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt haben, wird der Konstruktor in der Menüband\-Designer\-Codedatei angezeigt.  Diese Datei trägt den Namen *YourRibbonItem*.Designer.cs oder *YourRibbonItem*.Designer.vb.  Um diese Datei in Visual Basic\-Projekten anzuzeigen, müssen Sie zuerst im Projektmappen\-Explorer auf die Schaltfläche **Alle Dateien anzeigen** klicken.  
  
### Festlegen der Eigenschaften in der CreateRibbonExtensibilityObject\-Methode  
 Sie können die Eigenschaften eines `Ribbon`\-Steuerelements beim Überschreiben der CreateRibbonExtensibilityObject\-Methode in der `ThisAddin`\-, der `ThisWorkbook`\-oder der `ThisDocument`\-Klasse des Projekts festlegen.  Weitere Informationen zur CreateRibbonExtensibilityObject\-Methode finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
 Im folgenden Beispiel werden die Menübandeigenschaften in der CreateRibbonExtensibilityObject\-Methode der `ThisWorkbook`\-Klasse eines Excel\-Arbeitsmappenprojekts festgelegt.  
  
 Fügen Sie den folgenden Code hinzu.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> Eigenschaften, die schreibgeschützt werden  
 In der folgenden Tabelle werden Eigenschaften angezeigt, die nur vor dem Laden des Menübands festgelegt werden können.  
  
> [!NOTE]  
>  Sie können Sie die Eigenschaften der Steuerelemente in dynamischen Menüs jederzeit festlegen.  Diese Tabelle ist in diesem Fall nicht gültig.  
  
|Eigenschaft|Menüband\-Steuerelementklasse|  
|-----------------|-----------------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Gruppen**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabstopps**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Festlegen von Eigenschaften für in Outlook\-Inspektoren angezeigte Menübänder  
 Bei jedem Öffnen eines Inspektors, in dem das Menüband angezeigt wird, wird eine neue Instanz des Menübands erstellt.  Allerdings können die in der Tabelle oben aufgeführten Eigenschaften nur vor dem Erstellen der ersten Instanz des Menübands festgelegt werden.  Nach dem Erstellen der ersten Instanz werden diese Eigenschaften schreibgeschützt, da die erste Instanz die XML\-Datei definiert, die von Outlook zum Laden des Menübands verwendet wird.  
  
 Sofern Sie über bedingte Logik verfügen, mit der alle diese Eigenschaften auf einen anderen Wert festgelegt werden, wenn andere Instanzen des Menübands erstellt werden, bleibt dieser Code ohne Wirkung.  
  
> [!NOTE]  
>  Stellen Sie sicher, dass die **Name**\-Eigenschaft für jedes einem Outlook\-Menüband hinzugefügte Steuerelement festgelegt wird.  Wird einem Outlook\-Menüband während der Laufzeit ein Steuerelement hinzugefügt, muss diese Eigenschaft im Code festgelegt werden.  Wird einem Outlook\-Menüband während der Entwurfszeit ein Steuerelement hinzugefügt, wird die Name\-Eigenschaft automatisch festgelegt.  
  
## Menüband\-Steuerelementereignisse  
 Jede Steuerelementklasse beinhaltet mindestens ein Ereignis.  In der folgenden Tabelle werden diese Ereignisse beschrieben.  
  
|Ereignis|**Beschreibung**|  
|--------------|----------------------|  
|Click|Tritt beim Klicken auf ein Steuerelement auf.|  
|TextChanged|Tritt beim Ändern des Texts in einem Bearbeitungs\- oder Kombinationsfeld auf.|  
|ItemsLoading|Tritt auf, wenn die Items\-Auflistung des Steuerelements von Office angefordert wird.  Office nimmt eine Zwischenspeicherung der Items\-Auflistung vor, bis der Code die Eigenschaften des Steuerelements ändert oder die <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>\-Methode aufgerufen wird.|  
|ButtonClick|Tritt beim Klicken auf eine Schaltfläche in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> auf.|  
|SelectionChanged|Tritt beim Ändern der Auswahl in <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> auf.|  
|DialogLauncherClick|Tritt auf, wenn unten rechts in einer Gruppe auf das Symbol für das Dialogfeldstartprogramm geklickt wird.|  
  
 Die Ereignishandler für diese Ereignisse besitzen die folgenden zwei Parameter.  
  
|Parameter|**Beschreibung**|  
|---------------|----------------------|  
|*sender*|Ein <xref:System.Object>, das das Steuerelement darstellt, durch das das Ereignis ausgelöst wurde.|  
|*e*|Ein <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>, das ein <xref:Microsoft.Office.Core.IRibbonControl> enthält.  Greifen Sie mithilfe dieses Steuerelements auf eine beliebige Eigenschaft zu, die im von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellten Menüband\-Objektmodell nicht verfügbar ist.|  
  
## Siehe auch  
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  