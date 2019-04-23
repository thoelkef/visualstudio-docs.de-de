---
title: Übersicht über das Menüband-Objektmodell
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5958eb6fb8fd14dd510fa87d900efa76cb6f6a87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040715"
---
# <a name="ribbon-object-model-overview"></a>Übersicht über das Menüband-Objektmodell
  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ein stark typisierten Objektmodell, mit denen Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit zur Verfügung. Beispielsweise können neue Menüsteuerelemente dynamisch ausgefüllt oder Steuerelemente kontextbezogen angezeigt und ausgeblendet werden. Zudem besteht die Möglichkeit, einem Menüband Registerkarten, Gruppen und Steuerelemente hinzuzufügen. Dies muss jedoch vor dem Laden des Menübands durch die Office-Anwendung erfolgen. Weitere Informationen finden Sie unter [legen fest, die schreibgeschützt werden](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Dieses Menüband-Objektmodell besteht hauptsächlich aus der [Multifunktionsleistenklasse](#RibbonClass), [Multifunktionsleisten-Ereignisse](#RibbonEvents), und [Menüband-Steuerelementklassen](#RibbonControlClasses).

## <a name="RibbonClass"></a> Ribbon-Klasse
 Beim Hinzufügen einer neuen **Menüband (visueller Designer)** Element zu einem Projekt, fügt Visual Studio eine **Menüband** Ihrem Projekt. Die **Menüband** Klasse erbt von der <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> Klasse.

 Diese Klasse wird als partielle Klasse angezeigt, die zwischen der Menüband-Codedatei und der Codedatei des Menüband-Designers aufgeteilt ist.

## <a name="RibbonEvents"></a> Menübandereignisse
 Die **Menüband** Klasse enthält die folgenden drei Ereignisse:

|event|Beschreibung|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wird ausgelöst, wenn die Multifunktionsleisten-Anpassung die Office-Anwendung geladen wird. Die <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> -Ereignishandler wird automatisch der Menüband-Codedatei hinzugefügt. Führen Sie beim Laden des Menübands mithilfe dieses Ereignishandlers benutzerdefinierten Code aus.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Sie können Zwischenspeicherung von Images in die Anpassung der Multifunktionsleiste beim Laden des Menübands. Sie können eine leichte leistungsverbesserung abrufen, wenn Sie Code zum Zwischenspeichern der Menüband-Images in diesem Ereignishandler schreiben. Weitere Informationen finden Sie unter <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Wird ausgelöst, wenn die Menübandinstanz geschlossen wird.|

## <a name="RibbonControlClasses"></a> Menübandsteuerelemente
 Die <xref:Microsoft.Office.Tools.Ribbon> -Namespace enthält einen Typ für jedes Steuerelement, das Sie in finden Sie unter den **Steuerelemente für Office-Menübänder** Gruppe der **Toolbox**.

 In der folgenden Tabelle wird der Typ für jedes `Ribbon`-Steuerelement angezeigt. Eine Beschreibung der einzelnen Steuerelemente, finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

|Steuerelementname|Klassenname|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button** (Schaltfläche)|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Katalog**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Gruppieren**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Bezeichnung**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Trennzeichen**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**TAB**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Der <xref:Microsoft.Office.Tools.Ribbon>-Namespace verwendet für diese Typen das Ribbon-Präfix, um einen Namenskonflikt mit den Namen der Steuerelementklassen im <xref:System.Windows.Forms>-Namespace zu verhindern.

 Beim Hinzufügen eines Steuerelements zum Menüband-Designer deklariert der Menüband-Designer die Klasse für dieses Steuerelement als Feld in der Codedatei des Menüband-Designers.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Allgemeine Aufgaben, die mit den Eigenschaften von Menübandsteuerelementen
 Jedes `Ribbon`-Steuerelement beinhaltet Eigenschaften, mit denen Sie verschiedene Aufgaben ausführen können, wie das Zuweisen einer Bezeichnung zu einem Steuerelement oder das Ausblenden und Anzeigen von Steuerelementen.

 In einigen Fällen sind Eigenschaften schreibgeschützt, nach dem Laden des Menübands oder nachdem ein Steuerelement ein dynamisches Menü hinzugefügt wurde. Weitere Informationen finden Sie unter [legen fest, die schreibgeschützt werden](#SettingReadOnlyProperties).

 In der folgenden Tabelle werden einige der Aufgaben beschrieben, die Sie mithilfe der Eigenschaften des `Ribbon`-Steuerelements ausführen können.

|Aufgabe:|Vorgehensweise:|
|--------------------|--------------|
|Aus- oder Einblenden eines Steuerelements.|Verwenden Sie die Visible-Eigenschaft.|
|Aktivieren oder Deaktivieren eines Steuerelements.|Verwenden Sie die Enabled-Eigenschaft.|
|Festlegen der Größe eines Steuerelements.|Verwenden Sie die ControlSize-Eigenschaft.|
|Abrufen des Bilds, das auf einem Steuerelement angezeigt wird.|Verwenden Sie die Image-Eigenschaft.|
|Ändern der Bezeichnung eines Steuerelements.|Verwenden Sie die Label-Eigenschaft.|
|Hinzufügen von benutzerdefinierten Daten zu einem Steuerelement.|Verwenden Sie die Tag-Eigenschaft.|
|Abrufen der Elemente in einem <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>-Steuerelement oder einem<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>-Steuerelement|Verwenden der Items-Eigenschaft.|
|Hinzufügen eines <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>-Steuerelements, eines <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>-Steuerelements oder eines <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>-Steuerelements.|Verwenden der Items-Eigenschaft.|
|Hinzufügen von Steuerelementen zu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Verwenden der Items-Eigenschaft.<br /><br /> Zum Hinzufügen von Steuerelementen, die <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> , nachdem das Menüband in der Office-Anwendung geladen wird, müssen Sie festlegen der <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> Eigenschaft **"true"** vor dem Laden des Menübands in die Office-Anwendung. Weitere Informationen finden Sie unter [legen fest, die schreibgeschützt werden](#SettingReadOnlyProperties).|
|Abrufen des ausgewählten Elements von <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Verwenden Sie die SelectedItem-Eigenschaft. Verwenden Sie für <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> die <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>-Eigenschaft.|
|Abrufen der Gruppen auf <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>-Eigenschaft.|
|Angeben der Anzahl der Zeilen und Spalten, die in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> angezeigt werden.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>-Eigenschaft.|

## <a name="SettingReadOnlyProperties"></a> Festlegen von Eigenschaften, die schreibgeschützt werden
 Einige Eigenschaften können nur vor dem Laden des Menübands festgelegt werden. Diese Eigenschaften können an drei Orten festgelegt werden:

- In der Visual Studio **Eigenschaften** Fenster.

- Im Konstruktor der **Menüband** Klasse.

- In der `CreateRibbonExtensibilityObject`-Methode der `ThisAddin`, `ThisWorkbook`- Klasse oder `ThisDocument`-Klasse des Projekts.

  Dynamische Menüs bieten einige Ausnahmen. Sie können neue Steuerelemente erstellen, ihre Eigenschaften festlegen und dann zur Laufzeit einem dynamischen Menü auch nach dem Laden des Menübands mit dem Menü hinzufügen.

  Eigenschaften von Steuerelementen, die Sie einem dynamischen Menü hinzufügen, können jederzeit festgelegt werden.

  Weitere Informationen finden Sie unter [Eigenschaften, die schreibgeschützt werden](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Festlegen von Eigenschaften im Konstruktor des Menübands
 Sie können die Eigenschaften festlegen einer `Ribbon` Steuerelement im Konstruktor des der **Menüband** Klasse. Dieser Code muss nach dem Aufruf der `InitializeComponent`-Methode angezeigt werden. Im folgenden Beispiel wird einer Gruppe eine neue Schaltfläche hinzugefügt, falls die aktuelle Uhrzeit 17:00 Pacific Time (UTC-8) oder später ist.

 Fügen Sie den folgenden Code hinzu.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 In visuellen C# Projekte, die Sie von Visual Studio 2008 aktualisiert haben, der Konstruktor wird angezeigt, in der Menüband-Codedatei.

 In Visual Basic-Projekten oder in Visual C#-Projekten, die Sie in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt haben, wird der Konstruktor in der Menüband-Designer-Codedatei angezeigt. Diese Datei heißt *YourRibbonItem*. "Designer.cs" oder *YourRibbonItem*. Designer.vb. Um diese Datei in Visual Basic-Projekten zu anzuzeigen, klicken Sie zunächst auf die **alle Dateien anzeigen** Schaltfläche im Projektmappen-Explorer.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Festlegen von Eigenschaften in der CreateRibbonExtensibilityObject-Methode
 Sie können die Eigenschaften eines `Ribbon`-Steuerelements beim Überschreiben der `CreateRibbonExtensibilityObject`-Methode in der `ThisAddin`-, der `ThisWorkbook`-oder der `ThisDocument`-Klasse des Projekts festlegen. Weitere Informationen zu den `CreateRibbonExtensibilityObject` -Methode finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

 Im folgenden Beispiel wird die Menüband-Eigenschaften der `CreateRibbonExtensibilityObject` Methode der `ThisWorkbook` Klasse von einer Excel-Workbook-Projekt.

 Fügen Sie den folgenden Code hinzu.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="ReadOnlyProperties"></a> Eigenschaften, die schreibgeschützt werden
 Die folgende Tabelle zeigt die Eigenschaften, die nur vor dem Laden des Menübands festgelegt werden können.

> [!NOTE]
>  Sie können Sie die Eigenschaften der Steuerelemente in dynamischen Menüs jederzeit festlegen. Diese Tabelle ist in diesem Fall nicht gültig.

|Eigenschaft|Menüband-Steuerelementklasse|
|--------------|--------------------------|
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
|**Tabs**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Titel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Festlegen von Eigenschaften für die Bänder, die in Outlook-Inspektoren angezeigt werden.
 Bei jedem Öffnen eines Inspektors, in dem das Menüband angezeigt wird, wird eine neue Instanz des Menübands erstellt. Allerdings können die in der Tabelle oben aufgeführten Eigenschaften nur vor dem Erstellen der ersten Instanz des Menübands festgelegt werden. Nach dem Erstellen der ersten Instanz werden diese Eigenschaften schreibgeschützt, da die erste Instanz die XML-Datei definiert, die von Outlook zum Laden des Menübands verwendet wird.

 Sofern Sie über bedingte Logik verfügen, mit der alle diese Eigenschaften auf einen anderen Wert festgelegt werden, wenn andere Instanzen des Menübands erstellt werden, bleibt dieser Code ohne Wirkung.

> [!NOTE]
>  Sicherstellen, dass die **Namen** -Eigenschaft für jedes Steuerelement, das Sie einem Outlook-Menüband hinzufügen festgelegt ist. Wenn Sie einem Outlook-Menüband zur Laufzeit ein Steuerelement hinzugefügt haben, müssen Sie diese Eigenschaft im Code festlegen. Wenn Sie ein Steuerelement zu einem Outlook-Menüband zur Entwurfszeit hinzufügen, wird die Name-Eigenschaft automatisch festgelegt.

## <a name="ribbon-control-events"></a>Menüband-Steuerelementereignisse
 Jede Steuerelementklasse beinhaltet mindestens ein Ereignis. In der folgenden Tabelle werden diese Ereignisse beschrieben.

|event|Beschreibung|
|-----------|-----------------|
|Klicken|Tritt beim Klicken auf ein Steuerelement auf.|
|TextChanged|Tritt beim Ändern des Texts in einem Bearbeitungs- oder Kombinationsfeld auf.|
|ItemsLoading|Tritt auf, wenn die Auflistung der Elemente des Steuerelements von Office angefordert wird. Office speichert die Items-Auflistung, bis Ihr Code die Eigenschaften des Steuerelements geändert wird, oder Sie rufen die <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> Methode.|
|ButtonClick|Tritt beim Klicken auf eine Schaltfläche in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> auf.|
|SelectionChanged|Tritt beim Ändern der Auswahl in <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> auf.|
|DialogLauncherClick|Tritt auf, wenn unten rechts in einer Gruppe auf das Symbol für das Dialogfeldstartprogramm geklickt wird.|

 Die Ereignishandler für diese Ereignisse besitzen die folgenden zwei Parameter.

|Parameter|Beschreibung|
|---------------|-----------------|
|*sender*|Ein <xref:System.Object>, das das Steuerelement darstellt, durch das das Ereignis ausgelöst wurde.|
|*e*|Ein <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>, das ein <xref:Microsoft.Office.Core.IRibbonControl> enthält. Greifen Sie mithilfe dieses Steuerelements auf eine beliebige Eigenschaft zu, die im von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellten Menüband-Objektmodell nicht verfügbar ist.|

## <a name="see-also"></a>Siehe auch
- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md)
