---
title: Freigegebene Farben für Visual Studio | Microsoft-Dokumentation
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b36b7c123f4da9ca3ab7a6f33a972345cdf70e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310779"
---
# <a name="shared-colors-for-visual-studio"></a>Konsistente Farben für Visual Studio
Wenn Sie beim Entwerfen, Benutzeroberfläche, die allgemeine Visual Studio Shell-Elementen oder Ihr Benutzeroberflächenelement konsistent mit ähnlichen Features sein soll, verwenden Sie Tokennamen in Paketdefinitionsdateien, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.

In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:

- **Verwenden Sie Tokennamen nach Funktion und nicht nach Farbe.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Die Funktionen des Kombinationsfelds und der Animation sind unterschiedlich, und wenn das Kombinationsfeld ändert die Farbe zugeordnet ist, kann es nicht mehr sein, auf eine geeignete Farbe für Ihr Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.

- **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination aus.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn nicht die zugeordnete Textfarbe vorhanden ist, verwenden Sie nicht diese Hintergrundfarbe auf Oberflächen, auf denen erwartungsgemäß Text angezeigt. Andere Kombinationen von Text- und Hintergrundfarben können die Benutzeroberfläche unlesbar führen.

- **Verwenden Sie steuerelementfarben, die für die jeweilige Position geeignet sind.** Für bestimmte Zustände nicht einige Visual Studio-Steuerelemente auf separaten Rahmen- und Hintergrundfarben haben. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.

> [!IMPORTANT]
> Verwenden Sie keine Token gefunden, die in den Kategorien "Startseite" oder "Cider".

## <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente

Wenn Sie eine standardmäßige Visual Studio-Befehlsleiste in Ihrer Funktion verwenden, müssen Sie den Zugriff auf formatierte Shell-Steuerelemente. Sie sollten nicht Re-Vorlage diese gemeinsam verwendeten Steuerelemente. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.

### <a name="button-controls"></a>Schaltflächen-Steuerelemente

![(Rote Linie) der Schaltflächen-Steuerelement](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Schaltflächen im Dokument, das Sie in Visual Studio-Designs (hell, dunkel, Blau oder Design mit hohem Kontrast System) integrieren möchten. | ... für Schaltflächen, die für einen benutzerdefinierten Hintergrund angezeigt werden, die nicht Teil eines Visual Studio-Designs ist. |

**Schaltfläche: standard-Status**

![Schaltfläche "Standard"](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Schaltfläche "Standard"

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.Button` |
| Schaltflächenrahmen | `CommonControls.ButtonBorder` |

**Button: Standardzustand**

![Schaltfläche "Standard"](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Schaltfläche "Standard"

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDefault` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDefault` |

**Schaltfläche: deaktiviert**

![Deaktivierte Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Deaktivierte Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDisabled` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDisabled` |

**Schaltfläche: Hover-Zustand**

![Schaltfläche ", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonHover` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderHover` |

**Schaltfläche: gedrückten Zustand**

![Schaltfläche im gedrückten Zustand](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Schaltfläche im gedrückten Zustand

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonPressed` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderPressed` |

**Schaltfläche: fokussierte Zustand**

![Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Schaltfläche mit Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonFocused` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente
![Aktivieren Sie das Kontrollkästchen ((rote Linie))](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Aktivieren Sie das Kontrollkästchen ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Kontrollkästchen-Steuerelemente, die auch im Dokument enthaltenen. | ... für Benutzeroberflächen, die nicht von einem Kontrollkästchen-Steuerelement. |

**Aktivieren Sie das Kontrollkästchen: Status**

![Aktivieren Sie das Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Standard-Kontrollkästchen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackground` |
| Rahmen | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Aktivieren Sie das Kontrollkästchen: Status "deaktiviert"**

![Deaktiviertes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Deaktiviertes Kontrollkästchen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundDisabled` |
| Rahmen | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Aktivieren Sie das Kontrollkästchen: Zeigen Sie mit Status**

 ![Das Kontrollkästchen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Kontrollkästchen, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundHover` |
| Rahmen | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Aktivieren Sie das Kontrollkästchen: gedrückt-Status**

![Gedrücktes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Gedrücktes Kontrollkästchen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Rahmen | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Aktivieren Sie das Kontrollkästchen: mit Fokus Zustand**

![Aktivieren Sie das Kontrollkästchen mit Fokus](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Aktivieren Sie das Kontrollkästchen mit Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundFocused` |
| Rahmen | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Dropdownlisten und Kombinationsfelder Felder
![Drop-down/combo box (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Drop-/ Kombinationsfeld ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Dropdownlisten und Kombinationsfelder Feldern im Dokument gut. | ... für Benutzeroberflächen, die ein Dropdown-Liste oder ein Kombinationsfeld-Feld nicht. |
| | für die Befehlsleiste... [Dropdownlisten](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) oder [Kombinationsfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Dropdownlisten und Kombinationsfelder Felder: Status**

![Standard & Drop-/ Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Standard & Drop-/ Kombinationsfeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackground` |
| Rahmen | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Trennzeichen | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackground` |

**Dropdownlisten und Kombinationsfelder Felder: Status "deaktiviert"**

![Deaktivierte & Drop-/ Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Deaktivierte & Drop-/ Kombinationsfeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundDisabled` |
| Rahmen | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Dropdownlisten und Kombinationsfelder Felder: bewegen Sie den Mauszeiger Zustand**

![Drop-/ Kombinationsfeld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundHover` |
| Rahmen | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Dropdownlisten und Kombinationsfelder Felder: gedrückt-Status**

![Drücken die Drop-/ Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Drop-/ Kombinationsfeld, aufgerufen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundPressed` |
| Rahmen | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Dropdownlisten und Kombinationsfelder Felder Element Listenansicht: gedrückt-Status**

 ![Drop-/ Kombinationsfeld, Listenansicht-Element gedrückt](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Drop-/ Kombinationsfeld, Listenansicht-Element gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Elementtext | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Hintergrundschatten | `CommonControls.ComboBoxListBackgroundShadow` |

**Dropdownlisten und Kombinationsfelder Felder: mit Fokus Zustand**

![Drop-/ Kombinationsfeld mit Fokus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Drop-/ Kombinationsfeld mit Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Dropdownlisten und Kombinationsfelder Felder: Auswahl für Eingabetext**

![Auswahl der Drop-/ Kombinationsfeld-Eingabetext](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Drop-/ Kombinationsfeld texteingabeauswahl

| Element | Tokenname: Category.Color |
| --- | --- |
| Hervorheben | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)
Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.

![Tabellarische Daten/Grid-Steuerelement ((rote Linie))](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabellarische Daten/Grid-Steuerelement ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für tabellarische oder Rastersteuerelemente. | ... für Benutzeroberflächenelemente, die kein Tabellen- oder Rastersteuerelement Steuerelement ist. |

#### <a name="column-headers"></a>Spaltenheader
Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.

**Spaltenüberschrift: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Header.Default` |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Header.Glyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenüberschrift: Zeigen Sie mit Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Header.MouseOver` |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Header.MouseOverGlyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenüberschrift: gedrückt-Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Vordergrund (Text) | `CommonControls.CheckBoxBorderPressed` |
| Vordergrund (Glyphe) | `CommonControls.CheckBoxTextPressed` |
| Rahmen | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Listenansichtselemente
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.

**Liste der Elemente anzeigen: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Transparent |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Keiner |

**Liste der Elemente anzeigen: Zustand "aktiv"**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActiveText` |
| Rahmen | Keiner |

**Liste der Elemente anzeigen: inaktiver Zustand**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactiveText` |
| Rahmen | Keiner |

### <a name="ui-text"></a>Benutzeroberflächentext

#### <a name="instructional-text"></a>Hinweistext
Anweisungstext bietet eine deutliche main Erklärung der Vorgehensweise in einem Dialogfeld oder Dokument.

![Default instructional text](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Standard-Anweisungstext

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundäre Anweisungstext
Einige Anweisungstext verwendet Seiten des Dokuments mit vielen von Text und Steuerelementen einen andere Farbe-Wert. Dadurch wird die vermitteln, welche Informationen am wichtigsten ist, und verringern die gesamte Dichte der Elemente der Benutzeroberfläche. (Siehe auch die im folgenden Abschnitt auf den Hinweistext.)

![Secondary instructional text](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundäre Anweisungstext

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Hinweistext
Hinweistext angezeigt wird, in ein leeres Steuerelement, das unterhalb eines Steuerelements oder auf ein leeres Dokument-Oberfläche, die dem Benutzer angezeigt wird, was Sie als Nächstes tun. Sie können den Hinweistext mit entweder Fensters oder Steuerelements Hintergründen verwenden.

**Standard-Hinweistext**

![Default hint text](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Standard-Hinweistext

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

**Erforderliche Hinweistext**

![Required hint text](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Erforderliche Hinweistext

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlRequiredHintText` |
| Hintergrund | `Environment.ControlRequiredBackground` |

**Suchtext für Kontrollkästchen-Steuerelement**

> Finden Sie unter [suchen Felder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) für andere Farbe-Token, die im Zusammenhang mit der das Suchsteuerelement.

![Suchen von Text in Meldungsfeldern Steuerelement](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Suchtext für Kontrollkästchen-Steuerelement

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Link
Der Link ist ein Steuerelement, das nicht über ein paar Vordergrund-/Hintergrundfarbe verfügt. Verwenden Sie in allen Fällen die Vordergrund-Linkfarbe, die auf dunklem, grauen und weißem Hintergrund ordnungsgemäß angezeigt wird. Wenn Sie nicht das farbtoken für das Linksteuerelement verwenden, sehen Sie die Standardsystemfarbe für "gedrückt", die rot blinken wird. Dies ist das Signal, dass das Steuerelement die richtige Umgebung-farbtoken verwenden, ist nicht.

![Hyperlink (redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hyperlink ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie einen benutzerdefinierten Link erstellen müssen. | ... für alle Elemente, die einen Link nicht. |

**Link: Standardzustand**

![Standard-Hyperlink](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Standard-hyperlink

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlink` |

**Link: Hover-Zustand**

![Link bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hyperlink, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkHover` |

**Link: gedrückten Zustand**

![Gedrückte Hyperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Gedrückte hyperlink

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkPressed` |

**Link: deaktiviert**

![Deaktivierte Hyperlink](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Deaktivierte hyperlink

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infoleisten
Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.

![Infobar (redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infoleiste ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... bei der Erstellung einer benutzerdefinierten Infoleiste. | ... von UI-Elementen, die keine Ähnlichkeit mit einer Infoleiste sind. |

**Infoleiste: Standardzustand**

![Standard Infoleiste](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Standard-Infoleiste

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.InfoBarBackground` |
| Vordergrund (Text) | `InfoBar.InfoBar` |
| Rahmen | `InfoBar.InfoBarBorder` |

**Infoleiste schließen (&times;) Schaltfläche: Status**

![Standardmäßig schließen Infoleiste (&times;) Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Standardmäßig schließen Infoleiste (&times;) Schaltfläche "

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButton` |
| Rahmen | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Infoleiste schließen (&times;) Schaltfläche: Zeigen Sie mit Status**

![Infoleiste schließen (&times;) Schaltfläche ", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Infoleiste schließen (&times;) Schaltfläche ", wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonHover` |
| Rahmen | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Infoleiste schließen (&times;) Schaltfläche: gedrückt-Status**

![Infoleiste Schließen geklickt (&times;) Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Infoleiste Schließen geklickt (&times;) Schaltfläche "

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonDown` |
| Rahmen | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Infoleiste Linkschaltfläche: Status**

![Default infobar hyperlink button](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Schaltfläche "Standard Infoleiste Hyperlink"

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Infoleiste Linkschaltfläche: Zeigen Sie mit Status**

![Infobar hyperlink button on hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Infoleiste Hyperlink-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit "Unterstreichen") |

**Infoleiste Linkschaltfläche: gedrückt-Status**

![Pressed infobar hyperlink button](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Hyperlink-Schaltfläche gedrückt Infoleiste

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit "Unterstreichen") |

**Inline-Link (innerhalb eines Satzes) Infoleiste: Status**

![Schaltfläche "Standard Inline Infoleiste Hyperlink"](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Schaltfläche "Standard Inline Infoleiste Hyperlink"

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Inline-Link (innerhalb eines Satzes) Infoleiste: Zeigen Sie mit Status**

![Infobar inline hyperlink button on hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Infoleiste Inline Hyperlink-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit "Unterstreichen") |

**Inline-Link (innerhalb eines Satzes) Infoleiste: gedrückt-Status**

![Pressed infobar inline hyperlink button](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Infoleiste Inline Hyperlink geklickt

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit "Unterstreichen") |

**Infoleiste Schaltfläche: Status**

![Default infobar button](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Infoleiste-Schaltfläche "Standard"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.Button` |
| Vordergrund (Text) | `InfoBar.Button` |
| Rahmen | `InfoBar.ButtonBorder` |

**Infoleiste Schaltfläche: Zeigen Sie mit Status**

![Infobar button on hover](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Infoleiste-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseOver` |
| Vordergrund (Text) | `InfoBar.ButtonMouseOver` |
| Rahmen | `InfoBar.ButtonMouseOverBorder` |

**Infoleiste Schaltfläche: gedrückt-Status**

![Pressed infobar button](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Schaltfläche "gedrückten Infoleiste"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseDown` |
| Vordergrund (Text) | `InfoBar.ButtonMouseDown` |
| Rahmen | `InfoBar.ButtonMouseDownBorder` |

**Infoleiste Schaltfläche: Status "deaktiviert"**

![Disabled infobar button](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Deaktivierte Infoleiste-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonDisabled` |
| Vordergrund (Text) | `InfoBar.ButtonDisabled` |
| Rahmen | `InfoBar.ButtonDisabledBorder` |

**Infoleiste Schaltfläche: mit Fokus Zustand**

![Focused infobar button](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Schaltfläche "mit Fokus Infoleiste"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonFocus` |
| Vordergrund (Text) | `InfoBar.ButtonFocus` |
| Rahmen | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Bildlaufleisten
Bildlaufleisten erhalten Ihr Format von Visual Studio-Umgebung, und Sie müssen nicht mit Design versehen werden. Möglicherweise möchten jedoch, dass Sie für die Farben, die in Bildlaufleisten verwendet werden, sodass Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent nutzen möchten.

![Bildlaufleiste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Bildlaufleiste ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie Benutzeroberflächen erstellen, möchten Sie Visual Studio-Bildlaufleisten übereinstimmen. | Alles was Sie nicht immer überein möchten... für Bildlaufleisten-Benutzeroberfläche. |

**Bildlaufleiste: Status**

![Standard-Bildlaufleiste](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Standard-Bildlaufleiste

| Element | Tokenname: Category.Color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbBackground` |

**Bildlaufleiste: Zeigen Sie mit Status**

![Bildlaufleiste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Bildlaufleiste, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbMouseOverBackground` |

*Bildlaufleiste: gedrückt-Status**

![Gedrückten Bildlaufleiste](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Drücken die Bildlaufleiste.

| Element | Tokenname: Category.Color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbPressedBackground` |

**Bildlaufleiste Pfeil: Status**

![Bildlaufleiste (Pfeil) standardmäßig](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Bildlaufleiste (Pfeil) Standard

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowBackground`<br />(Auf dieselbe Farbe wie die Bildlaufleiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyph` |

**Bildlaufleiste Pfeil: Zeigen Sie mit Status**

![Bildlaufleisten-Taste bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Bildlaufleiste (Pfeil), wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowMouseOverBackground`<br />(Auf dieselbe Farbe wie die Bildlaufleiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Bildlaufleiste Pfeil: gedrückt-Status**

![Gedrückten Bildlaufleiste (Pfeil)](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Drücken die Bildlaufleiste (Pfeil)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowPressedBackground`<br />(Auf dieselbe Farbe wie die Bildlaufleiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Suchfelder
Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.

Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:

- "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.

- "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.

- "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).

- "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.

![Suchfeld ((rote Linie))](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Suchfeld ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie beim Entwerfen eines benutzerdefinierten Suchfelds. | ... für alles, was ein Suchfeld nicht ist. |
| | Feld... für Elemente, die nicht immer die Suche übereinstimmen sollen UI ein. |

**Schwerpunkt sucheingabefeld**

![Eingabefeld für zielgerichtete Suche in](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Schwerpunkt sucheingabefeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedBackground` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | `SearchControl.FocusedBorder` |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Ohne Fokus, aktive sucheingabefeld**

![Sucheingabefeld ohne Fokus](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Ohne Fokus, aktive sucheingabefeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.SearchActiveBackground` |
| Vordergrund (Text) | `SearchControl.SearchActiveBackground` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Ohne Fokus, inaktive sucheingabefeld**

![Ohne Fokus, inaktive sucheingabefeld](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Ohne Fokus, inaktive sucheingabefeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.Unfocused` |
| Vordergrund (Text) | `SearchControl.Unfocused` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Hervorgehobene sucheingabefeld (nur Text)**

![Highlighted search input field](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Hervorgehobene sucheingabefeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.Selection` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | Keiner |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Deaktivierte sucheingabefeld**

![Deaktiviert suchen Eingabefeld](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Deaktivierte sucheingabefeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.Disabled` |
| Vordergrund (Text) | `SearchControl.Disabled` |
| Rahmen | `SearchControl.DisabledBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Fokussierte Suche (Aktionsschaltfläche)**

![Suche (Aktionsschaltfläche) mit Fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Fokussierte Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Ohne Fokus Suche (Aktionsschaltfläche)**

![Ohne Fokus Suche (Aktionsschaltfläche)](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Ohne Fokus Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Suche (Aktionsschaltfläche) gedrückt**

![Gedrückten Suche (Aktionsschaltfläche)](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Suche (Aktionsschaltfläche) gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.ActionButtonMouseDown` |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Rahmen | `SearchControl.ActionButtonMouseDownBorder` |

**Deaktivierte Suche (Aktionsschaltfläche)**

![Suche (Aktionsschaltfläche) deaktiviert](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Deaktivierte Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Rahmen | Keiner |

**Zielgerichtete Suche in Dropdown-Schaltfläche**

![Zielgerichtete Suche in Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Zielgerichtete Suche in Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.FocusedDropDownButtonBorder` |

**Ohne Fokus Suche Dropdown-Schaltfläche**

![Die Dropdown-Schaltfläche ohne Fokus Suche](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Ohne Fokus Suche Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.UnfocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.UnfocusedDropDownButtonBorder` |

**Die Dropdown-Suchschaltfläche geklickt**

![Die Dropdown-Schaltfläche gedrückt Suche](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Die Dropdown-Suchschaltfläche geklickt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.MouseDownDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Rahmen | `SearchControl.MouseDownDropDownButtonBorder` |

**Deaktiviert Dropdown-Schaltfläche "Suchen"**

![Deaktiviert Dropdown-Schaltfläche "Suchen"](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Deaktiviert Dropdown-Schaltfläche "Suchen"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Rahmen | Keiner |

#### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld
Die Dropdown-suchfeldmenü kann etwas komplexer als andere Dropdownmenüs in Visual Studio sein. Die "Empfohlene Suchbegriffe" und die Abschnitte "Suchoptionen" können alleine oder zusammen im Menü angezeigt, und jede Bereiche. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.

![Die Dropdown-Suchliste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Die Dropdown-Suchliste ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie eine benutzerdefinierte Suche Dropdown-Liste erstellen. | ... für Dropdownlisten, die in anderen Kontexten angezeigt werden. |
| ... die richtigen Tokennamen für die entsprechenden Listenkomponenten. | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Dropdown-Listenfeld Elemente suchen**

| Element | Tokenname: Category.Color |
| --- | --- |
| Rahmen | `SearchControl.PopupBorder` |
| Trennzeichen | `SearchControl.PopupSectionHeaderSeparator` |
| Schatten | `Environment.DropShadowBackground` |

**Empfohlene Suchvorgänge: Status**

![Standard empfohlene Suchbegriffe](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Standard empfohlene Suchbegriffe

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupItemText` |

**Empfohlene Suchvorgänge: Zeigen Sie mit Status**

![Empfohlene Suchvorgänge, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Empfohlene Suchbegriffe, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupMouseOverItemText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: Status**

![Kontrollkästchen "Suche"](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Standard-Suchoptionen (Kontrollkästchen)

![Suchoptionen](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Standard-Suchoptionen (Link)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonText` |
| Headerhintergrund | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Headertext) | `SearchControl.PopupSectionHeaderText` |

**Suchoptionen: Zeigen Sie mit Status**

![Suchoptionen (Kontrollkästchen) bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Suchoptionen (Kontrollkästchen), wenn darauf gezeigt wird

![Suchoptionen (Link) bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Suchoptionen (Link), wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: gedrückt-Status**

![Suchoptionen (Kontrollkästchen) gedrückt](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Drücken die Suchoptionen (Kontrollkästchen)

![Suchoptionen (Link) gedrückt](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Suchoptionen (Link) gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Kontrollkästchen-Hintergrund | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Linkhintergrund | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |

### <a name="BKMK_TreeView"></a> Strukturansichten
Mehrere Toolfenster, einschließlich der Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in gesteuert werden, die `TreeView` Kategorie. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.

![Strukturansicht ((rote Linie))](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Strukturansicht ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... eine beliebige Stelle eine hierarchische Organisationsstruktur implementiert werden müssen. | ... für Elemente, die sich nicht um eine Strukturansicht ähnlich ist. |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Strukturansichtselement: Status**

![Standard-Strukturansichtselement](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Standard-Strukturansichtselement

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.Glyph` |
| Rahmen | Keiner |

**Strukturansichtselement: Zeigen Sie mit Status**

![Strukturansichtselement bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Strukturansichtselement, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.GlyphMouseOver` |
| Rahmen | Keiner |

**Strukturansichtselement: Ziehen Sie über den Status**

![Struktur auf ziehen Sie das Ansichtselement über](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Ziehen Strukturansichtselement auf über

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.DragOverItem` |
| Vordergrund (Text) | `TreeView.DragOverItem` |
| Vordergrund (Glyphe) | `TreeView.DragOverItemGlyph` |
| Rahmen | Keiner |

**Strukturansichtselement: ausgewählt wird, konzentriert sich der Zustand**

![Ausgewählt, und konzentrieren uns Strukturansichtselement](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Ausgewählte und fokussierte Strukturansichtselement

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Strukturansichtselement: ausgewählten Zustand ohne Fokus**

![Ausgewählte und ohne Fokus Strukturansichtselement](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Ausgewählte und ohne Fokus Strukturansichtselement

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Rahmen | Keiner |

**Strukturansichtselement: gezeigt, ausgewählt und konzentriert sich der Zustand**

![Ausgewählt, und konzentrieren uns Strukturansichtselement bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Ausgewählte und fokussierte Strukturansichtselement wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Strukturansichtselement: gezeigt wird, ohne Fokus und ausgewählten Zustand**

![Ausgewählte und ohne Fokus Strukturansichtselement bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Ausgewählte und ohne Fokus Strukturansichtselement wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | Keiner |

## <a name="shell-appearance"></a>Shell-Darstellung

### <a name="background"></a>Hintergrund
Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Die obere und untere Hintergrundebene werden auf dieselbe Farbe die hellen und dunklen Design festgelegt.

![Visual Studio-Shell-Hintergrund ((rote Linie))](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio-Shell-Hintergrund ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... nach stellen, die auf den Hintergrund der Visual Studio-Umgebung angepasst werden sollen. | ... als Füllung für Bereiche, die keine hintergrundoberflächen sind. |
| | ... als Hintergrund auf vordergrundelemente platziert. |

**Untere Ebene Shell Darstellung**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackground` |

**Darstellung der obersten Ebene-shell**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Befehlsablage
Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.

![Visual Studio-Befehlsablage ((rote Linie))](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio-Befehlsablage ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Bereiche, in dem Sie Menüs oder Symbolleisten platziert. | ... für Bereiche, die nicht mit einer Befehlsablage ähnlich sind. |
|… with die Kombination des richtigen Hintergrund-/Vordergrundfarbe-token-Namen. | |

**Befehl-Shell-Menüleiste**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Befehlsleiste Shelf-Befehl**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest-Designer
Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest-Designer ((rote Linie))](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest-Designer ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Designer ähneln, die vom Manifest-Designer. | ... Wenn Sie über mehr als sechs Registerkarten verfügen. |
| anstelle allgemeiner Registerkarten-Steuerelemente am oberen Rand eines Editors innerhalb des Dokuments... gut ist. | ... für Benutzeroberflächenelemente, die wie der Manifest-Designer strukturiert sind. |

**Ausgewählte Registerkarte Manifest Designer: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `ManifestDesigner.TabActive` |
| Rahmen | Keiner |

**Beschreibung der ausgewählten Bereich der Manifest-Designers: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `ManifestDesigner.DescriptionPane` |

**Manifest Designer ausgewählten Inhaltsseite: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Background` |
| Dialogfeld-Hilfetext | `ManifestDesigner.WatermarkText`<br />(Dieser Tokenname stimmt nicht seine Funktion überein.) |

**Manifest-Designer-Registerkarte: nicht markierten Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Inactive` |

**Manifest-Designer-Registerkarte: Zeigen Sie mit Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Befehlsstrukturen

### <a name="BKMK_CommandMenus"></a> Menüs
Menüs können an mehreren Stellen in Visual Studio auftreten: der Hauptmenüleiste, eingebettet in Dokument-oder Toolfenster oder beim Rechtsklicken an verschiedenen Stellen der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.

![Visual Studio-Menü ((rote Linie))](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio-Menü ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie ein benutzerdefiniertes Menü erstellen müssen.| ... als ausschließliche Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe. |
| ... Wenn Sie haben eine neue UI-Komponente, die die Visual Studio-Menüs abgestimmt werden sollen.| |

#### <a name="menu-titles"></a>Menütitel
Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.

![Menütitel ((rote Linie))](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menütitel ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie einen benutzerdefinierten Menütitels erstellen. | ... für alles, was nicht immer den Menütitel übereinstimmen sollen. |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Menütitel: Status**

![Menütitel Standard](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Standard-Menütitel

![Menütitel mit Glyphe, Standard](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Standard-Menütitel mit Glyphe

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuGlyph` |
| Rahmen | Keiner |

**Menütitel: Zeigen Sie mit Status**

![Menütitel, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Menütitel, wenn darauf gezeigt wird

![Menütitel mit Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Menütitel mit Glyphe, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |

**Menütitel: gedrückt-Status**

![Menütitel gedrückt](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Gedrückten Menütitel

![Menütitel mit Glyphe, gedrückt](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Menütitel mit Glyphe, gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder`<br />(Nur linken, oberen und rechten Seite.) |

**Menütitel: Status "deaktiviert"**

![Menütitel mit Glyphe deaktiviert](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Deaktivierte Menütitel mit Glyphe

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Keiner |

#### <a name="menu-items"></a>Menüelemente
Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.

![(Rote Linie) der Menüelemente](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Verwenden Sie... | Verwenden Sie keine... |
|---|---|
| ... für alle Dropdown-Liste, die von einer Menü- oder Befehlsleiste gestartet wird. | ... für alle Dropdown-Liste in einem anderen Kontext. |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Menüelemente: Status**

![Standard-Menüelemente](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Standard-Menüelemente

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder` |
| Symbolkanal-Hintergrund | `Environment.CommandBarMenuIconBackground` |
| Trennzeichen | `Environment.CommandBarMenuSeparator` |
| Schatten | `Environment.DropShadowBackground` |

**Menüelemente: aktiviert und Zustände ausgewählt**

![Im Menü](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Aktiviert Menüelement

![Ausgewählte Menü](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Ausgewählte Menüelement

| Element | Tokenname: Category.Color |
| --- | --- |
| Häkchen | `Environment.CommandBarCheckBox` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarSelected` |
| Symbolrahmen | `Environment.CommandBarSelectedBorder` |

**Menüelemente: Zeigen Sie mit Status**

![Zeigen Sie die im Menü](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Menüelement, wenn darauf gezeigt wird

![Menü "Wenn darauf gezeigt wird überprüft,](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Überprüft, Menüelement, wenn darauf gezeigt wird

![Menü zeigen Sie ausgewählte](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Ausgewählte Menüelement aus, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Text) | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxMouseOver` |
| Häkchenhintergrund | `Environment.CommandBarHoverOverSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarHoverOverSelected` |
| Symbolrahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menüelemente: Status "deaktiviert"**

![Menü, deaktiviert](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Menüelement deaktiviert

![Menü, deaktiviert (geprüft)](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Deaktivierte Menüelemente mit Häkchen

| Element | Tokenname: Category.Color |
| --- | --- |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxDisabled` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Befehlsleisten
Eine Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE, insbesondere Befehlsablage und eingebettet in Tool- oder Dokumentfenster angezeigt werden.

Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.

![(Rote Linie) der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Befehlsleiste ((rote Linie))

![(Rote Linie) der Schaltfläche "Überlauf"](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Schaltfläche "Überlauf" ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... an Orten, in dem Sie eine eingebettete Befehlsleiste benötigen, sind aber nicht der standardmäßige Visual Studio Befehlsleisten-Standardimplementierung verwenden. | ... von UI-Elementen, die nicht mit einer Befehlsleiste ähnlich sind. |
| | ... für andere befehlsleistenkomponenten als, die diejenigen, für die Tokennamen festgelegt wurden. |

#### <a name="command-bar-groups"></a>Befehlsgruppen-Leiste
Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.

![Befehlszeilengruppe (rote Linie,)](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Befehlszeilengruppe ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... an Orten, in dem Sie eine eingebettete Befehlsleiste benötigen, sind aber nicht der standardmäßige Visual Studio Befehlsleisten-Standardimplementierung verwenden. | ... von UI-Elementen, die nicht mit einer Befehlsleiste ähnlich sind. |
| | ... für andere befehlsleistenkomponenten als, die diejenigen, für die Tokennamen festgelegt wurden. |

**Befehlsleistengruppe: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Rahmen | `Environment.CommandBarToolBarBorder` |
| Ziehpunkt | `Environment.CommandBarDragHandle` |
| Trennzeichen | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Befehlssymbole
![Befehlssymbol](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Befehlssymbol ((rote Linie))

![Befehlssymbol, mit dem Text](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Befehlssymbol, mit dem Text ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für alle Schaltflächen, die auf einer Befehlsleiste platziert werden. | ... für Steuerelemente, die ihren eigenen Tokennamen haben. |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Befehlssymbol: Status**

![Standardmäßiges Befehlssymbol Befehl](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Standard-Befehlssymbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Nicht zutreffend |

**Befehlssymbol: Status, ausgewählt**

![Standard, ausgewählte Befehlssymbol](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Standard, ausgewählte Befehlssymbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextSelected` |
| Rahmen | `Environment.CommandBarSelectedBorder` |

**Befehlssymbol: Zeigen Sie bzw. den Fokus Zustände**

![Befehlssymbol, wenn darauf gezeigt wird oder den Fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Befehlssymbol, wenn darauf gezeigt wird oder den Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehlssymbol: Zeigen Sie bzw. den Fokus Zustände ausgewählt**

![Befehlssymbol, wenn darauf gezeigt wird oder den Fokus ausgewählt](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Symbol für ausgewählten Befehl gezeigt wird, oder den Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarHoverOverSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextHoverOverSelected` |
| Rahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Befehlssymbol: gedrückt-Status**

![Befehlssymbol gedrückt](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Gedrücktes Befehlssymbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehlssymbol: Status "deaktiviert"**

![Deaktiviertes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Deaktiviertes Befehlssymbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |

#### <a name="BKMK_CommandComboBox"></a> Kombinationsfeldern für Befehle Balken

> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich nicht umfasst, verwenden Sie die farbtoken für [Dropdownlisten Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![(Rote Linie) der Befehlsleiste im Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Befehlsleisten-Kombinationsfeld ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Erstellung benutzerdefinierter Kombinationsfelder. | ... für alles was Sie nicht möchten immer entsprechen den Befehl Befehlsleisten-Benutzeroberfläche. |
| ... wenn ein Befehlsleisten-Steuerelement zu erstellen, die an ein Kombinationsfeld ähnlich ist. | ... Wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben. |

**Befehlsleiste Kombinationsfeld (Eingabefeld): Status**

![Befehlsleiste Kombinationsfeld (Eingabefeld)](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Befehlsleiste Kombinationsfeld (Eingabefeld)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxBackground` |
| Vordergrund (Text) | `Environment.ComboBoxText` |
| Rahmen | `Environment.ComboBoxBorder` |
| Trennzeichen | Kein Trennzeichen |

**Befehlsleisten-Dropdown-Schaltfläche: Status**

![Kombinationsfeld-Dropdown&#45;gedrückt](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Befehlsleisten-Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Glyphe) | `Environment.ComboBoxGlyph` |

**Befehlsleiste Dropdown-Liste: Status**

![Befehlsleiste Dropdown-Listenfeld](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Befehlsleiste Dropdown-Liste

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxPopupBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.ComboBoxPopupBorder` |

**Befehlsleiste Kombinationsfeld (Eingabefeld): Zeigen Sie mit Status**

![Befehlsleiste Kombinationsfeld (Eingabefeld) bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Befehlsleiste Kombinationsfeld (Eingabefeld) Wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxMouseOverText` |
| Rahmen | `Environment.ComboBoxMouseOverBorder` |
| Trennzeichen | `Environment.ComboBoxMouseOverSeparator` |

 **Befehlsleisten-Dropdown-Schaltfläche: Zeigen Sie mit Status**

![Befehlsleisten-Dropdown-Schaltfläche bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Befehlsleisten-Dropdown-Schaltfläche wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Befehlsleiste Dropdown-Liste: Zeigen Sie mit Status**

 ![Befehlsleiste Dropdown-Liste bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Befehlsleiste Kombinationsfeld (Eingabefeld): mit Fokus Zustand**

![Konzentriert die Befehlsleiste Kombinationsfeld (Eingabefeld)](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Schwerpunkt Befehlsleiste Kombinationsfeld (Eingabefeld)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedBackground` |
| Vordergrund (Text) | `Environment.ComboBoxFocusedText` |
| Rahmen | `Environment.ComboBoxFocusedBorder` |
| Trennzeichen | `Environment.ComboBoxFocusedButtonSeparator` |

**Befehlsleisten-Dropdown-Schaltfläche: mit Fokus Zustand**

![Konzentriert die Befehlsleiste Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Dropdown-Schaltfläche mit Fokus der Befehlsleiste

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedButtonBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Befehlsleiste Kombinationsfeld (Eingabefeld): gedrückt-Status**

![Befehl Leiste Kombinationsfeld (Eingabefeld) gedrückt](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Befehlsleiste Kombinationsfeld (Eingabefeld) gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseDownBackground` |
| Vordergrund (Text) | `Environment.ComboBoxMouseDownText` |
| Rahmen | `Environment.ComboBoxMouseDownBorder` |
| Trennzeichen | `Environment.ComboBoxMouseDownSeparator` |

**Befehlsleisten-Dropdown-Schaltfläche: gedrückt-Status**

![Befehlsleiste Dropdown-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Befehlsleiste Dropdown-Schaltfläche gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Befehlsleiste Kombinationsfeld (Eingabefeld): Status "deaktiviert"**

![Kombinationsfeld (Eingabefeld) der Befehlsleiste deaktiviert](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Deaktivierte Befehlsleiste Kombinationsfeld (Eingabefeld)

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxDisabledBackground` |
| Vordergrund (Text) | `Environment.ComboBoxDisabledText` |
| Rahmen | `Environment.ComboBoxDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Befehlsleisten-Dropdown-Schaltfläche: Status "deaktiviert"**

![Deaktiviert die Dropdown-Schaltfläche der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="BKMK_CommandDropDown"></a> Befehlsleiste Dropdown-Elemente

> [!IMPORTANT]
> Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich enthält, verwenden Sie die farbtoken für [Kombinationsfelder Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Leiste Dropdown-Befehl ((rote Linie))](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Leiste Dropdown-Befehl ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie benutzerdefinierte Dropdownlisten-Steuerelemente erstellen. | ... für alle Elemente, die ähnlich wie eine Dropdown-Liste enthalten ist. |
| | ... für Kombinationsfelder oder unterteilte Schaltflächen. |

**Befehlsleiste Dropdown-Auswahlfeld: Status**

![Standard-Befehlsleiste Dropdown-Auswahlfeld](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Standard-Befehlsleiste-Dropdown-Auswahlfeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownBackground` |
| Vordergrund (Text) | `DropDownText` |
| Rahmen | `DropDownBorder` |
| Trennzeichen | Kein Trennzeichen |

**Befehlsleisten-Dropdown-Schaltfläche: Status**

![Befehlsleiste Dropdown-Schaltfläche Standard](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Standardmäßige Befehlsleisten-Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Glyphe) | `Environment.DropDownGlyph` |

**Befehlsleiste Dropdown-Liste: Status**

![Standard-Befehlsleiste Dropdown-Listenfeld](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Standard-Befehlsleiste Dropdown-Liste

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownPopupBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.DropDownPopupBorder` |
| Schatten | `Environment.DropShadowBackground` |

**Befehlsleiste Dropdown-Auswahlfeld: Zeigen Sie mit Status**

![Befehlsleiste-Dropdown-Auswahlfeld bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Befehlsleiste-Dropdown-Auswahlfeld wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.DropDownMouseOverText` |
| Rahmen | `Environment.DropDownMouseOverBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseOverSeparator` |

**Befehlsleisten-Dropdown-Schaltfläche: Zeigen Sie mit Status**

![Befehlsleisten-Dropdown-Schaltfläche bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Befehlsleisten-Dropdown-Schaltfläche wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseOverGlyph` |

**Befehlsleiste Dropdown-Liste: Zeigen Sie mit Status**

![Befehlsleiste Dropdown-Liste bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Befehlsleiste Dropdown-Auswahlfeld: gedrückt-Status**

![Drop&#45;unten Auswahlfeld gedrückt](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Befehl Leiste Dropdown-Auswahlfeld gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseDownBackground` |
| Vordergrund (Text) | `Environment.DropDownMouseDownText` |
| Rahmen | `Environment.DropDownMouseDownBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseDownSeparator` |

**Befehlsleisten-Dropdown-Schaltfläche: gedrückt-Status**

![Befehlsleiste Dropdown-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Befehlsleiste Dropdown-Schaltfläche gedrückt

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseDownGlyph` |

**Befehlsleiste Dropdown-Auswahlfeld: Status "deaktiviert"**

![Deaktiviert die Befehlsleiste Dropdown-Auswahlfeld](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Auswahlfeld

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DropDownDisabledBackground` |
| Vordergrund (Text) | `Environment.DropDownDisabledText` |
| Rahmen | `Environment.DropDownDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Befehlsleisten-Dropdown-Schaltfläche: Status "deaktiviert"**

![Deaktiviert die Dropdown-Schaltfläche der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Befehlsleiste unterteilte Schaltflächen
Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Split Schaltfläche Dropdownlisten sind Implementierungen der [Menüs Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Trennschaltfläche (rote Linie,)](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Befehlsleiste unterteilte Schaltfläche ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Sie beim Erstellen einer benutzerdefinierten unterteilten Schaltfläche. | für andere Arten von Schaltflächen... |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Befehlsleiste unterteilte Schaltfläche: Status**

![Standard-Befehl Leiste unterteilte Schaltfläche](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Standard-Befehlsleiste unterteilte Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

**Befehlsleiste unterteilte Schaltfläche: Zeigen Sie mit Status**

![Befehlsleiste unterteilte Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Befehlsleiste unterteilte Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | `Environment.CommandBarSplitButtonSeparator` |

**Befehlsleiste unterteilte Schaltfläche: gedrückt-Status**

![Befehl Leiste unterteilte Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Gedrückten Befehlsleiste unterteilte Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | Nicht zutreffend |

**Befehlsleiste unterteilte Schaltfläche: Status "deaktiviert"**

![Befehl Leiste unterteilte Schaltfläche deaktiviert](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Deaktivierte Befehlsleiste unterteilte Schaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Text) | `Environment.ComboBoxItemTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>"Weitere Optionen" und "Überlauf" Befehlsschaltflächen
Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.

![Schaltfläche "Weitere Optionen" der Befehlsleiste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Schaltfläche "Weitere Optionen" der Befehlsleiste ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für benutzerdefinierte "Weitere Optionen" oder "Überlauf" Schaltflächen. | ... für Schaltflächen, die keine ähnliche Funktionalität wie eine "Weitere Optionen" oder "Überlauf" haben. |

**"Weitere Optionen" und "Überlauf" Schaltflächen der Befehlsleiste: Status**

![Befehlsleiste "Weitere Optionen"-Schaltfläche Standard](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Schaltfläche "Standard" Befehlsleiste "Weitere Optionen"

![Schaltfläche "Überlauf" der Befehlsleiste Standard](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Standard Befehlsleisten-Schaltfläche "Überlauf"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsBackground` |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsGlyph` |

**"Weitere Optionen" und "Überlauf" Schaltflächen der Befehlsleiste: Zeigen Sie mit Status**

![Schaltfläche "Weitere Optionen", wenn darauf gezeigt wird der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Befehl Leiste die Schaltfläche "Weitere Optionen", wenn darauf gezeigt wird

!["Überlauf" Befehlsleistenschaltfläche bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />"Überlauf" Befehlsleistenschaltfläche wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**"Weitere Optionen" und "Überlauf" Schaltflächen der Befehlsleiste: gedrückt-Status**

![Befehlsleiste "Weitere Optionen"-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Befehlsleiste "Weitere Optionen"-Schaltfläche gedrückt

![Überlauf gedrückt](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Drücken die Befehlsleisten-Schaltfläche "Überlauf"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Dokumentfenster
Besteht keine Notwendigkeit zum Replizieren von Dokumentfenstern, weil sie von Visual Studio-Umgebung bereitgestellt sind. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

Wenn Sie Dokumentfenster-farbtoken verwenden zu können, achten Sie darauf, dass sie nur für ähnliche Elemente und paarweise verwendet wird. Wenn Sie dies nicht tun, erhalten Sie möglicherweise unerwartete Ergebnisse auf der Benutzeroberfläche.

### <a name="document-window-frames"></a>Dokument Fensterrahmen
Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Wenn ein Dokumentfenster außerhalb der IDE unverankert ist, es immer noch befindet sich in einen Dokumentursprung und Hintergrund, Rahmen, Text- und registerkartenfarben, die identisch sind, wenn es Teil der IDE ist verfügt. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.

![Angedocktes Dokumentfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Angedocktes Dokumentfenster ((rote Linie))

![Unverankertes Dokumentfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Unverankertes Dokumentfenster ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Sie das Dokumentfenster abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Dokumentfenster angedockt oder unverankert: Status**

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Hängt vom Dokumenttyp ab. |
| Vordergrund (Text) | Hängt vom Dokumenttyp ab. |
| Rahmen | `Environment.ToolWindowBorder` |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: Status**

![Standardmäßig konzentrieren, Gleitkomma dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Standardmäßige konzentrieren, Gleitkomma dokumentfensterrahmen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Auf transparent festgelegt) |

**Rahmen ohne Fokus, unverankertes Dokument-Fenster: Status**

![Standardmäßig ohne Fokus, unverankerte dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Standardmäßig ohne Fokus, unverankerte dokumentfensterrahmen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Rahmen | `Environment.MainWindowInactiveBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Auf transparent festgelegt) |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: Zeigen Sie mit Status**

![Mit Fokus, Gleitkomma dokumentfensterrahmen bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Mit Fokus, Gleitkomma dokumentfensterrahmen, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Rahmen ohne Fokus, unverankertes Dokument-Fenster: Zeigen Sie mit Status**

![Ohne Fokus, unverankerte dokumentfensterrahmen bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Ohne Fokus, unverankertes dokumentfensterrahmen, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund (Glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: gedrückt-Status**

![Mit Fokus, Gleitkomma dokumentfensterrahmen beim Klicken](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Mit Fokus, Gleitkomma dokumentfensterrahmen beim Klicken

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Dokumentregisterkarten
Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.

![Dokumentregisterkarten ((rote Linie))](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Dokumentregisterkarten ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die auf Dokumentregisterkarten abgestimmt und Designaktualisierungen oder neue Designfarben automatisch ausgewählt werden sollen. | ... für Benutzeroberflächenelemente, die Sie nicht automatisch geändert wird, wenn die Shell einer designaktualisierung möchten. |

#### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten
Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:

- Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.

- Hintergrundregisterkarten sind Dokumentregisterkarten, die nicht der aktuell ausgewählten Registerkarte entsprechen. Sobald auf die Registerkarte geklickt wird, wird sie zur ausgewählten Registerkarte, die alle Hintergrund-, Rahmen- und Textfarben von den Tokennamen übernimmt.

![Registerkarte "Dokument öffnen" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Registerkarte "Dokument öffnen" ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Sie beim Erstellen benutzerdefinierter Dokumentregisterkarten. | ... für Registerkarten für vorläufige (Vorschau). |
| | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Registerkarte "ausgewählte, fokussierte Dokument"**

![Ausgewählt, konzentriert sich die Registerkarte "Dokument"](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Registerkarte "ausgewählte, fokussierte Dokument"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabSelectedGradientTop`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabSelectedText` |
| Rahmen | `Environment.FileTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabDocumentBorderBackground` |

**Registerkarte "aktiviert wird, ohne Fokus Dokument"**

![Aktiviert wird, ohne Fokus Dokumentregisterkarte](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Registerkarte "aktiviert wird, ohne Fokus Dokument"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabInactiveGradientTop`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabInactiveText` |
| Rahmen | `Environment.FileTabInactiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabInactiveDocumentBorderBackground` |

**Dokument-Registerkarte "Hintergrund": Status**

![Registerkarte "Dokument" der Standard-Hintergrund](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Registerkarte "Dokument" der Standard-Hintergrund

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabBackground` |
| Vordergrund (Text) | `Environment.FileTabText` |
| Rahmen | `Environment.FileTabBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Dokument-Registerkarte "Hintergrund": Zeigen Sie mit Status**

![Registerkarte "Dokument Hintergrundvorschau"](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Registerkarte "Dokument Hintergrundvorschau"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabHotGradientTop`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabHotText` |
| Rahmen | `Environment.FileTabHotBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

#### <a name="preview-tab"></a>Vorschauregisterkarte
Wird aufgerufen, auch eine "provisional"-Registerkarte. Die Vorschauregisterkarte wird auf der rechten Seite des Dokument-Registerkartenkanals angezeigt, wenn der Benutzer auf ein Element im Toolfenster des Projektmappen-Explorers klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.

![Registerkarte "Vorschau" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Registerkarte "Vorschau" ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... überall Sie vorläufige erstellen Vorschau, und möchten von einem Element, entsprechend der aktuellen Vorschau der Farbe. | ... für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau). |
| | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Registerkarte "Vorschau von fokussierten, ausgewählten"**

![Registerkarte "Vorschau von fokussierten, ausgewählten"](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Registerkarte "Vorschau von fokussierten, ausgewählten"

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedActive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Unfocused, ausgewählte Vorschau**

![Vorschauregisterkarte ohne Fokus, ausgewählten](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Unfocused, ausgewählte Vorschau

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Registerkarte Vorschau Hintergrund: Standard Zustand**

![Standardmäßigen Hintergrund-/ vorschauregisterkarte](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Standardregisterkarte für Hintergrund-Vorschau

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalInactiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Registerkarte Vorschau Hintergrund: hover-Zustand**

![Registerkarte "Vorschau Hintergrundvorschau"](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Registerkarte Vorschau Hintergrund bewegen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalHover` |
| Vordergrund (Text) | `Environment.FileTabProvisionalHoverForeground` |
| Rahmen | `Environment.FileTabProvisionalHoverBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

#### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche
Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Der Überlauf Dropdown-Menü Dokument die gesteuert wird der [Menü Befehlsleisten](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) Farben, listet alle geöffneten Dokumente angezeigt und ausgeblendet sowie die Überlauf Symbol ändert sich je nachdem, ob alle geöffneten Dokumente in der Registerkarte Kanal angezeigt.

![Dokumentüberlauf-Schaltfläche ((rote Linie))](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Dokument Überlaufschaltfläche (redline)

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie eine benutzerdefinierte Überlaufschaltfläche erstellen. | ... für die Benutzeroberfläche nicht wie eine Überlaufschaltfläche. |
| | für den Überlauf Befehlsleistenschaltflächen. |

**Dokument Überlaufschaltfläche: Standard-Zustand**

![Dokumentüberlauf-Standardschaltfläche](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Standardmäßige Dokument Überlaufschaltfläche

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Rahmen | Nicht zutreffend |

**Dokument Überlaufschaltfläche: hover-Zustand**

![Dokumentüberlauf-Schaltfläche bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Dokument Überlaufschaltfläche: Status**

![Dokumentüberlauf-Schaltfläche auf Press](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Dokument Überlaufschaltfläche drücken

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Tagging
Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.

![Für Tags in Visual Studio ((rote Linie))](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Kennzeichnung in Visual Studio (redline)

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| für Benutzeroberflächen, die Tags unterstützt. | ... für jede andere Art von Benutzeroberfläche. |

#### <a name="tags"></a>Tags

**Tag: Standardzustand**

![Standardtag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Standard-tag

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.Background` |
| Vordergrund (Text) | `Tag.Background` |

**Tag: Hover-Zustand**

![Markieren Sie bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.HoverBackground` |
| Vordergrund (Text) | `Tag.HoverBackgroundText` |

**Tag: gedrückt-Status**

![Tag gedrückt](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Gedrückten tag

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.PressedBackground` |
| Vordergrund (Text) | `Tag.PressedBackgroundText` |

**Tag: Auswahlzustand**

![Ausgewählte Tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Ausgewählte tag

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.SelectedBackground` |
| Vordergrund (Text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Schließen (&times;) tag-Symbol

**Schließen (&times;) tag-Symbol: Status**

![Standardmäßig schließen (&times;) tag Glyph](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Standardmäßig schließen (&times;) tag-Symbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyph` |

**Schließen (&times;) tag-Symbol: Zeigen Sie mit Status**

![Schließen (&times;) tag-Symbol bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Schließen (&times;) Symbol markieren, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphHover` |
| Rahmen | `Tag.TagHoverGlyphHoverBorder` |

**Schließen (&times;) tag-Symbol: gedrückt-Status**

![Gedrückt schließen (&times;) tag Glyph](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Gedrückt schließen (&times;) tag-Symbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphPressed` |
| Rahmen | `Tag.TagHoverGlyphPressedBorder` |

**Ausgewählte Tag mit schließen (&times;) Symbol: Status**

![Standardmäßig ausgewählte Tag mit schließen (&times;) Symbol](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Standardmäßig ausgewählte Tag mit schließen (&times;) Symbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyph` |

**Ausgewählte Tag mit schließen (&times;) Symbol: Zeigen Sie mit Status**

![Ausgewählte Tag mit schließen (&times;) Symbol bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Ausgewählte Tag mit schließen (&times;) Symbol, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphHover` |
| Rahmen | `Tag.TagSelectedGlyphHoverBorder` |

**Ausgewählte Tag mit schließen (&times;) Symbol: gedrückt-Status**

![Ausgewählt, die gedrückt-Tag mit schließen (&times;) Symbol](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Ausgewählt, die gedrückt-Tag mit schließen (&times;) Symbol

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphPressed` |
| Rahmen | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Toolfenster
Besteht keine Notwendigkeit zum Replizieren von Toolfenstern, weil sie von Visual Studio-Umgebung bereitgestellt sind. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

![Toolfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Toolfenster ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Toolfenster abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

### <a name="tool-window-frame"></a>Toolfensterrahmen
Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.

![Toolfenster, Rahmen ((rote Linie))](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Toolfenster, Rahmen ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Toolfenster abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Angedocktes Toolfenster**

![Angedocktes Toolfenster](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Angedocktes Toolfenster

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.ToolWindowBorder` |

**Unverankert, mit Fokus in Toolfenster**

![Unverankert, mit Toolfenster Fokus](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Unverankert, mit Fokus in Toolfenster

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |

**Unverankert, Toolfenster ohne Fokus**

![Fenster unverankert, ohne Fokus](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Unverankert, Toolfenster ohne Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Toolbox ähnelte windows
Der Werkzeugkasten ist eines der am häufigsten verwendeten allgemeinen Toolfenster in Visual Studio. Es ist im Wesentlichen ein Strukturansicht-Steuerelement mit der ein bestimmtes Design und Stil angewendet.

![Fenster "Toolbox ähnelte" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Fenster "Toolbox ähnelte" ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... Wenn Sie beim Entwerfen eines Toolfensters, das immer mit dem Shell-Werkzeugkasten konsistent sein sollen. | ... für Ähnlichkeit mit der Werkzeugkasten-Benutzeroberfläche nicht, oder wenn Sie nicht sicher sind, ob die Benutzeroberfläche problematisch sein, wenn die Änderung der Farben des Shell-werkzeugkastens. |

**Toolbox-Knoten: Status**

![Standard-Toolbox übergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Standard-Toolbox übergeordneten Knoten

![Standard-Toolbox, untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Standard-Toolbox, untergeordneter Knoten

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContent`<br />(Rubriken) |
| Hintergrund | `Environment.ToolWindowBackground`<br />(Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind) |
| Rahmen | Keiner |
| Vordergrund (Glyphe) | `Environment.ToolboxContent` |
| Vordergrund (Text) | `Environment.ToolboxContent` |

**Toolbox-Unterknoten: hover-Zustand**

![Toolbox, untergeordneter Knoten bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContentMouseOver`<br />(Nur für einzelne Elemente) |
| Rahmen | Keiner |
| Vordergrund (Text) | `Environment.ToolboxContentMouseOver`<br />(Nur für einzelne Elemente) |

**Ausgewählte Toolbox Knoten: mit Fokus Zustand**

![Toolbox von fokussierten, ausgewählten übergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Toolbox von fokussierten, ausgewählten übergeordneten Knoten

![Toolbox von fokussierten, ausgewählten untergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Toolbox von fokussierten, ausgewählten untergeordneten Knoten

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | `TreeView.FocusVisualBorder`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Ausgewählte Toolbox Knoten: ohne Fokus Zustand**

![Die übergeordneten Knoten aktiviert wird, ohne Fokus Toolbox](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Aktiviert wird, ohne Fokus Toolbox, übergeordneter Knoten

![Die untergeordneten Knoten aktiviert wird, ohne Fokus Toolbox](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Die untergeordneten Knoten aktiviert wird, ohne Fokus toolbox

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | Keiner |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters
Der Rahmen der Titelleiste wird nicht echter Rahmen, sondern eine starke Linie am oberen Rand der Titelleiste. Es muss keine Tokennamen für den Zustand ohne Fokus.

![Titelleiste des Toolfensters ((rote Linie))](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Titelleiste des Toolfensters ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Toolfenster abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Titelleiste mit Fokus**

![Titelleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Titelleiste mit Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.TitleBarActiveGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarActiveText` |
| Rahmen | `Environment.TitleBarActiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Ziehpunkt | `Environment.TitleBarDragHandleActive` |

**Titelleiste ohne Fokus**

![Titelleiste ohne Fokus](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Titelleiste ohne Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.TitleBarInactiveGradientBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarInactiveText` |
| Rahmen | Nicht zutreffend |
| Ziehpunkt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Tool-Fenster Titelleisten-Schaltflächen
![Title bar Schaltfläche ((rote Linie))](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Title bar Schaltfläche ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... für Schaltflächen auf der Benutzeroberfläche, die farbtoken aus den Toolfenster-Titelleisten verwendet. | ... für Schaltflächen, die an anderer Stelle angezeigt. |
| | erfüllt... in eine beliebige Hintergrund-/Vordergrundfarbe-Kombination als angegeben. |

**Titelleisten-Schaltflächen konzentriert: Status**

![Standard, konzentriert sich Titelleisten-Schaltflächen](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Standard, fokussierte Titelleisten-Schaltflächen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Rahmen | Nicht zutreffend |

**Ohne Fokus Titelleisten-Schaltflächen: Status**

![Standard, ohne Fokus Titelleisten-Schaltflächen](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Standard, ohne Fokus Titelleisten-Schaltflächen

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Rahmen | Nicht zutreffend |

**Titelleisten-Schaltflächen konzentriert: Zeigen Sie mit Status**

![Titelleisten-Schaltflächen bei einer mauszeigerbewegung über konzentriert](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Fokussierte Titelleisten-Schaltflächen wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverActiveBorder` |

**Ohne Fokus Titelleisten-Schaltflächen: Zeigen Sie mit Status**

![Ohne Fokus Titelleisten-Schaltflächen bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Ohne Fokus Titelleisten-Schaltflächen wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Titelleisten-Schaltflächen konzentriert: gedrückt-Status**

![Klicken Sie mit dem Titelleisten-Schaltflächen Schwerpunkt](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Fokussierte Titelleisten-Schaltflächen beim Klicken

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

**Ohne Fokus Titelleisten-Schaltflächen: gedrückt-Status**

![Ohne Fokus Titelleisten-Schaltflächen beim Klicken](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Ohne Fokus Titelleisten-Schaltflächen beim Klicken

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten
![Der Toolfenster-Registerkarte ((rote Linie))](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Der Toolfenster-Registerkarte ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Toolfenster abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Ausgewählte, fokussierte Toolfenster-Registerkarte**

![Ausgewählt, Toolfenster-Registerkarte konzentriert](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Ausgewählt, Toolfenster-Registerkarte mit Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedActiveText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Ausgewählte, ohne Fokus Toolfenster-Registerkarte**

![Ausgewählte, ohne Fokus Toolfenster-Registerkarte](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Ausgewählt, Toolfenster-Registerkarte ohne Fokus

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Hintergrundregisterkarte im Toolfenster: Status**

![Standardmäßige Hintergrundregisterkarte im Toolfenster](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Standardmäßige Hintergrundregisterkarte im Toolfenster

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Festgelegte Farbverlaufsstopps auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabText` |
| Rahmen | `Environment.ToolWindowTabBorder` |

**Hintergrundregisterkarte im Toolfenster: Zeigen Sie mit Status**

![Hintergrundregisterkarte im Toolfenster bei einer mauszeigerbewegung über](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Festgelegte Farbverlaufsstopps auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabMouseOverText` |
| Rahmen | `Environment.ToolWindowTabMouseOverBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten

![Automatisch ausgeblendete Registerkarten ((rote Linie))](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline")automatisch ausgeblendete Registerkarten ((rote Linie))

| Verwenden Sie... | Verwenden Sie keine... |
| --- | --- |
| ... erstellen Sie eine beliebige Stelle Benutzeroberfläche, die Sie automatisch ausgeblendete Toolfenster-Registerkarten abstimmen möchten. | ... für Benutzeroberflächenelemente, die Sie nicht, automatisch ändern, wenn möchten designaktualisierung die Shell ein. |

**Automatisch ausgeblendete Registerkarten: Status**

![Automatisch ausgeblendete Registerkarte, Standard](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Automatisch ausgeblendete Registerkarte, Standard

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabText` |
| Rahmen | `Environment.AutoHideTabBorder` |

**Automatisch ausgeblendete Registerkarten: Zeigen Sie mit Status**

![Automatisch ausgeblendete Registerkarte "Hintergrundvorschau"](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird

| Element | Tokenname: Category.Color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token, die nicht mit Design der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabMouseOverText` |
| Rahmen | `Environment.AutoHideTabMouseOverBorder` |
