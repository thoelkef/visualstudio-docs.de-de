---
title: Multifunktionsleisten-Designer
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cc47445f9d2024f5d8a83c8f376bc0299b8ea4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103640"
---
# <a name="ribbon-designer"></a>Multifunktionsleisten-Designer
  Der Menüband-Designer ist ein visueller Entwurfzeichnungsbereich. Verwenden Sie die Menüband-Designer, um benutzerdefinierte Registerkarten, Gruppen und Steuerelemente des Menübands einer Microsoft Office-Anwendung hinzuzufügen.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Fügen Sie zum Öffnen des Menüband-Designers eine **Menüband (visueller Designer)** Element zu Ihrem Projekt. Anschließend können die Entwurftools für die folgenden Aufgaben verwendet werden:

- [Entwerfen des Menübandlayouts](#DesigningRibbonLayout)

- [Verarbeiten von Ereignissen und Festlegen von Steuerelementeigenschaften](#HandleEventsSetProperties)

- [Hinzufügen von Steuerelementen zur Backstage-Ansicht](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
>  Einige Aufgaben können mit dem Menüband-Designer nicht ausgeführt werden. Weitere Informationen zu diesen Aufgaben und wie Sie sie ausführen können, finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden des Menüband-Designers zum Anpassen des Menübands in Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Hinzufügen eines Elements von Menüband (visueller Designer) zu einem Projekt
 Um dem Menüband-Designer zu verwenden, fügen Sie ein neues **Menüband (visueller Designer)** Element zu Ihrem Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Beim Hinzufügen einer neuen **Menüband (visueller Designer)** , Visual Studio automatisch fügt die folgenden Dateien zu Ihrem Projekt:

- Eine Menüband-Codedatei. Diese Datei enthält den Namen, den Sie, für angeben die **Menüband (visueller Designer)** Element in der **neues Element hinzufügen** Dialogfeld. Fügen Sie dieser Datei zum Behandeln der Menübandereignisse Code hinzu.

- Eine Codedatei des Menüband-Designers. Diese Datei beinhaltet vom Menüband-Designer generierten Code und sollte nicht direkt bearbeitet werden.

- Eine Ressourcendatei. Diese Datei enthält die Eigenschaftswerte jedes Steuerelements auf dem Menüband.

  Wenn Sie bereits haben eine **Menüband (visueller Designer)** Element aus einem anderen Projekt können Sie diesen wiederverwenden in Ihrem aktuellen Projekt mithilfe der **vorhandenes Element hinzufügen** Dialogfeld.

## <a name="DesigningRibbonLayout"></a> Entwerfen eines Menübands
 Zum Öffnen des Menüband-Designers stehen drei Möglichkeiten zur Verfügung:

- In **Projektmappen-Explorer**, doppelklicken Sie auf dem Menüband-Codedatei.

- In **Projektmappen-Explorer**mit der rechten Maustaste auf die Menüband-Codedatei, und klicken Sie dann auf **Ansicht-Designer**.

- In **Projektmappen-Explorer**, wählen Sie die Menüband-Codedatei, und klicken Sie dann auf **Designer** auf die **Ansicht** Menü.

  Der Menüband-Designer beinhaltet eine Standardregisterkarte und -gruppe. Standardregisterkarte und -gruppe können aus dem Menüband-Designer entfernt werden. Zum Entfernen der Standardgruppe Maustaste **Group1**, und klicken Sie dann auf **löschen**. Klicken Sie zum Entfernen der Standardregisterkarte mit der rechten Maustaste in eines leeren Bereichs der Entwurfsoberfläche, und klicken Sie dann auf **Registerkarte für Menüband entfernen**.

  Dem Menüband-Designer können auch benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzugefügt werden. Sie finden diese Steuerelemente in der **Toolbox**in die **Steuerelemente für Office-Menübänder** Gruppe. Es gibt drei Möglichkeiten zum Hinzufügen von Steuerelementen aus der **Steuerelemente für Office-Menübänder** Gruppe zum Menüband-Designer:

- Ein Steuerelement in einen geeigneten Bereich im Menüband-Designer ziehen.

- Auf ein Steuerelement und anschließend in einen geeigneten Bereich im Menüband-Designer klicken.

- Wählen Sie einen geeigneten Bereich im Designer, und doppelklicken Sie dann auf ein Steuerelement in der **Toolbox**.

### <a name="ribbon-design-workflow"></a>Menüband-entwurfworkflow
 Führen Sie folgende grundlegende Schritte zum Entwerfen des Menübandlayouts aus:

1. [Hinzufügen eine benutzerdefinierte Registerkarte zum Menüband](#AddTabToRibbon).

2. [Fügen Sie Gruppen hinzu, auf die Registerkarte](#AddGroupsToTab).

3. [Hinzufügen von Steuerelementen zu Gruppen](#AddControlsToGroups).

   Steuerelemente können nur auf Gruppen gelöscht werden: Sie können nicht direkt auf einer Registerkarte oder das Menüband ein Steuerelement ziehen. Gruppen können nur auf Registerkarten abgelegt werden; Sie Ziehen einer Gruppe können nicht direkt auf einem Menüband.

   Ordnen Sie Steuerelemente durch Ziehen zu den korrekten Positionen an. Sie können die Eigenschaften eines Steuerelements festlegen, mit der **Eigenschaften** Fenster.

   Steuerelemente kann nicht auf dem Menüband nicht von einer Registerkarte zur anderen gezogen werden. Wenn Sie ein Steuerelement in eine andere Registerkarte verschieben möchten, müssen Sie verwenden die **Ausschneiden** Befehl für entfernen Sie das Steuerelement von einer Registerkarte, und klicken Sie dann in eine andere Registerkarte eingefügt. Wird das Steuerelement ausgeschnitten und eingefügt, wird der Ereignishandler angehalten. Sie können die Ereignishandler im Wiederherstellen der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Fenster "Eigenschaften"](../ide/reference/properties-window.md).

### <a name="AddTabToRibbon"></a> Hinzufügen von benutzerdefinierten Registerkarten zum Menüband
 Es gibt drei Möglichkeiten zum Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband:

- Hinzufügen einer Registerkarte aus der **Toolbox**.

- Mit der rechten Maustaste in der Menüband-Designer, und klicken Sie dann auf **Registerkarte für Menüband hinzufügen**.

- Öffnen der **Registerkartenauflistungs-Editor**, und klicken Sie dann auf **hinzufügen**.

   Zu öffnen der **Registerkartenauflistungs-Editor**in die **Eigenschaften** wählen Sie im Fenster der **Registerkarten** -Eigenschaft, und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten ![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse").

  Nach dem Hinzufügen einer Registerkarte können Gruppen mit Steuerelementen hinzugefügt werden.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Entfernen von benutzerdefinierten Registerkarten vom Menüband
 Es gibt drei Möglichkeiten zum Entfernen einer benutzerdefinierten Registerkarte vom Menüband aus:

- Mit der rechten Maustaste in des Designers, und klicken Sie dann auf **Registerkarte für Menüband entfernen**.

- In der **Befehle** im Bereich der **Eigenschaften** Fenster, klicken Sie auf **Registerkarte für Menüband entfernen**.

- Öffnen der **Registerkartenauflistungs-Editor**, wählen Sie die Registerkarte, und klicken Sie dann auf **entfernen**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Ändern der Position einer Registerkarte des Menübands
 Sie können die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern. Sie können auch benutzerdefinierte Registerkarten vor oder nach einer integrierten Registerkarte auf dem Menüband positionieren. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Anpassen der integrierten Registerkarten auf dem Menüband
 Eine integrierte Registerkarte ist eine Registerkarte, die bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel.

 Einer integrierten Registerkarte können Gruppen und Steuerelemente hinzugefügt werden. Standardmäßig wird eine benutzerdefinierte Gruppe als letzte Gruppe auf einer integrierten Registerkarte angezeigt, obwohl sie vor oder hinter eine integrierte Gruppe auf der Registerkarte verschoben werden kann.

 Integrierte Gruppen können nicht entfernt werden.

 Ausführliche Informationen zum Anpassen einer integrierten Registerkarte finden Sie unter [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="AddGroupsToTab"></a> Hinzufügen von Gruppen zu einer Registerkarte
 Steuerelemente auf dem Menüband werden mithilfe von Gruppen logisch organisiert. Fügen Sie Registerkarten Gruppen hinzu. Fügen Sie der Gruppe alle anderen Steuerelemente hinzu.

### <a name="AddControlsToGroups"></a> Hinzufügen von Steuerelementen zu Gruppen
 Fügen Sie einer Gruppe mindestens ein Steuerelement hinzu. In der folgenden Tabelle wird jedes Steuerelement beschrieben.

|Steuerelement|Beschreibung|
|-------------|-----------------|
|**Box**|Ein Container, der Steuerelemente in einer Gruppe organisiert. Einem Feld kann mit Ausnahme von Trennzeichen, Gruppen oder Registerkarten jedes beliebige Steuerelement hinzugefügt werden. Ein Feld kann horizontal oder vertikal dargestellt werden.|
|**Button** (Schaltfläche)|Eine Schaltfläche, durch die eine Aktion gestartet wird. Sie können einer Gruppe, einer Schaltflächengruppe, einer Dropdownliste, einem Katalog, einem Menü oder einer Trennschaltfläche eine Schaltfläche hinzufügen.|
|**ButtonGroup**|Eine Gruppe, die mindestens eine Schaltfläche, eine Umschaltfläche, ein Menü, eine Trennschaltfläche und einen Katalog beinhaltet. Einer Gruppe oder einem Menü kann eine Schaltflächengruppe oder eine Gruppe hinzugefügt werden.|
|**CheckBox**|Ein Feld, das zum Aktivieren oder Deaktivieren einer Option aktiviert oder deaktiviert ist.|
|**ComboBox**|Ein Bearbeitungsfeld mit einem angehängten Listenfeld. Benutzer können ihre Auswahl entweder eingeben oder auswählen. Im Feld wird die aktuelle Auswahl angezeigt. Verwenden der <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> Eigenschaft hinzufügen und Entfernen von Elementen zur Laufzeit vor oder nach dem Laden des Menübands in die Office-Anwendung.|
|**DropDown**|Eine Liste der Elemente, die von Benutzern ausgewählt werden können. In eine Dropdownliste kann kein neues Element eingegeben werden.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>-Eigenschaft Elemente hinzu. Sie können die hinzufügen und Entfernen von Elementen zur Laufzeit.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>-Eigenschaft Schaltflächen hinzu. Sie können keine jedoch hinzufügen und entfernen Schaltflächen, zur Laufzeit, nachdem das Menüband in der Office-Anwendung geladen wird.|
|**EditBox**|Ein Feld, in das der Benutzer Text eingeben kann.|
|**Katalog**|Ein Menü mit einem visuellen Auswahlarray oder -raster, in dem Benutzer eine Auswahl treffen können. Das Layout der Auswahl im Menü kann gesteuert werden. Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>-Eigenschaft, um die Anzahl der Zeilen und Spalten anzugeben, in denen die Elemente und Schaltflächen des Katalogs angezeigt werden.|
|**Bezeichnung**|Text, die Sie verwenden können, um Steuerelemente auf dem Menüband zu identifizieren.|
|**Menü**|Eine Dropdownliste, die sämtliche der folgenden Steuerelemente beinhalten kann:<br /><br /> -Schaltfläche ""<br />-Kontrollkästchen<br />-Katalog<br />-Menü<br />-Die unterteilte Schaltfläche<br />-Aus-Schaltfläche<br />-Trennzeichen<br /><br /> Wenn Sie einem Menü im Menüband-Designer ein Steuerelement hinzufügen möchten, klicken Sie im Menü auf den Pfeil nach unten, um die Menüentwurfsoberfläche anzuzeigen. Sie können Menübandsteuerelemente von der **Toolbox** zum Menü gezogen. Ordnen Sie Steuerelemente durch Ziehen zu den gewünschten Positionen an.<br /><br /> Zum Hinzufügen von Steuerelementen, die <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> , nachdem das Menüband in der Office-Anwendung geladen wird, müssen Sie festlegen der <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> Eigenschaft **"true"** vor dem Laden des Menübands. Informationen hierzu finden Sie unter [Multifunktionsleisten-objektmodellübersicht](../vsto/ribbon-object-model-overview.md).|
|**Trennzeichen**|Eine dünne Leiste zum Trennen von Elementen in einer Liste. Beim Hinzufügen zu einer Gruppe ist die Leiste vertikal. Beim Hinzufügen zu einem Menü ist die Leiste horizontal.|
|**SplitButton**|Eine Schaltfläche mit einem angehängten Menü. Eine Trennschaltfläche kann jedes der folgenden Steuerelemente beinhalten:<br /><br /> -Schaltfläche ""<br />-Kontrollkästchen<br />-Katalog<br />-Menü<br />-Die unterteilte Schaltfläche<br />-Aus-Schaltfläche<br />-Trennzeichen<br /><br /> Ebenso wie das Menü verfügt die Trennschaltfläche über eine eigene Entwurfsoberfläche. Allerdings können im Gegensatz zu einem Menü, Sie nur die Elemente aktualisiert auf einer Trennschaltfläche vor dem Laden des Menübands in die Office-Anwendung. Weitere Informationen zum Aktualisieren der Elemente auf einer Trennschaltfläche finden Sie unter [Multifunktionsleisten-objektmodellübersicht](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Eine Schaltfläche, die gedrückt oder nicht gedrückt angezeigt wird.|

## <a name="HandleEventsSetProperties"></a> Behandeln von Ereignissen und Festlegen von Eigenschaften
 Menüband-Designer können Sie zum Festlegen von Steuerelementeigenschaften zur Entwurfszeit mithilfe der **Eigenschaften** Fenster. Darüber hinaus macht das Menüband ein stark typisiertes Objektmodell, mit denen Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit verfügbar.

 Sie können auf jedes Steuerelement im Designer doppelklicken, um einen Ereignishandler für das Standardereignis des Steuerelements zu öffnen. Sie können Ereignishandler für alle anderen Steuerelementereignisse erstellen, mit der **Eigenschaften** Fenster.

 Menübandereignisse befinden sich im <xref:Microsoft.Office.Tools.Ribbon>-Namespace. Die **Menüband (visueller Designer)** Element fügt automatisch einen Verweis auf diese Assembly im Projekt und fügt die entsprechende **mit** oder **Importe** -Anweisung am Anfang der Menüband-Codedatei.

 Informationen zum Behandeln von Menübandereignissen und zum Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit finden Sie unter [Multifunktionsleisten-objektmodellübersicht](../vsto/ribbon-object-model-overview.md).

## <a name="CustomizingMicrosoftOfficeButton"></a> Anpassen der Backstage-Ansicht
 Können Sie zum Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf dem Menüband-Designer die **Datei** Registerkarte. Mit diesem Menü wird die Backstage-Ansicht aufgerufen.

 Sie können mit dem Menüband-Designer keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren. Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage-Ansicht angezeigt wird. Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie ein Menüband-XML verwenden. Weitere Informationen zu **Menüband (XML)**, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md). Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189) und [anpassen die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Weitere Informationen zur Vorgehensweise beim Hinzufügen von Steuerelementen zur Backstage-Ansicht finden Sie unter [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="Accessibility"></a> Barrierefreiheit im Menüband-Designer
 Steuerelemente auf dem Menüband-Designer können mithilfe von Tastenkombinationen verschoben werden. Einige Tastenkombinationen gelten für alle Steuerelemente, wohingegen einige Tastenkombinationen nur für Steuerelemente mit Menüs verwendbar sind.

 Die für alle Steuerelemente verwendbaren Tastenkombinationen werden in der folgenden Tabelle angezeigt.

|Aktion|Tastenkombination|
|------------|-----------------------|
|Verschieben eines Steuerelements vor das vorherige Steuerelement in der Liste.|**STRG**+**einrichten**<br /><br /> **STRG**+**links**|
|Verschieben eines Steuerelements hinter das nächste Steuerelement in der Liste.|**STRG**+**nach unten**<br /><br /> **Ctrl**+**Right**|
|Verschieben der Auswahl von einem Steuerelement zu einem anderen Steuerelement in derselben Gruppe. Wechseln Sie in einem Dropdownbereich zwischen dem übergeordneten Steuerelement und den Steuerelementen im Dropdownbereich.|**Nach-oben**<br /><br /> **Nach unten**|
|Durchlaufen aller Steuerelemente (vorwärts).|**TAB**|
|Durchlaufen aller Steuerelemente (rückwärts).|**UMSCHALT**+**Tab**|
|Löschen des ausgewählten Steuerelements oder eines Satzes von Steuerelementen.|**Löschen**|
|Kopieren der ausgewählten Steuerelemente.|**STRG**+**C**|
|Ausschneiden der ausgewählten Steuerelemente.|**STRG**+**X**|
|Einfügen von Steuerelementen aus der Zwischenablage.|**STRG**+**V**|
|Wählen Sie die **Toolbox**.|**Ctrl**+**Alt**+**X**|
|Auswählen der übergeordneten Komponente.|**ESC**|

 Die Tastenkombinationen gelten nur für das Microsoft Office-Menü; <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> und <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> werden in der folgenden Tabelle angezeigt.

|Aktion|Tastenkombination|
|------------|-----------------------|
|Auswählen des übergeordneten Steuerelements, falls der Dropdownbereich geöffnet ist und im Dropdownbereich ein Steuerelement ausgewählt ist.|**Links**|
|Schließen des Dropdownbereichs, falls der Dropdownbereich geöffnet ist und das übergeordnete Steuerelement ausgewählt ist.|**Links**|
|Öffnen des Dropdownbereichs.|**Rechts**|
|Auswählen des ersten Steuerelements im Dropdownbereich, falls der Dropdownbereich geöffnet ist.|**Rechts**|
|Schließen eines Dropdownbereichs.|**ESC**|

## <a name="see-also"></a>Siehe auch

- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
