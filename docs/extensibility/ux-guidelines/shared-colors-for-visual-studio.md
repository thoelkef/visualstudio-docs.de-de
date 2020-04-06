---
title: Freigegebene Farben für Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699928"
---
# <a name="shared-colors-for-visual-studio"></a>Freigegebene Farben für Visual Studio
Wenn Sie eine Benutzeroberfläche entwerfen, die allgemeine Visual Studio-Shellelemente verwendet, oder wenn Sie möchten, dass das Schnittstellenelement mit ähnlichen Features konsistent ist, verwenden Sie vorhandene Tokennamen in Paketdefinitionsdateien, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.

In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:

- **Verwenden Sie Tokennamen nach Funktion und nicht nach Farbe.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Die Funktionen des Kombinationsfelds und der Animation sind unterschiedlich, und wenn sich die farbe, die dem Kombinationsfeld zugeordnet ist, ändert sich möglicherweise keine geeignete Farbe mehr für das Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.

- **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn keine zugeordnete Textfarbe vorhanden ist, verwenden Sie diese Hintergrundfarbe nicht für eine Fläche, auf der Sie Text anzeigen möchten. Andere Kombinationen von Text und Hintergrundfarben können zu einer nicht lesbaren Benutzeroberfläche führen.

- **Verwenden Sie Steuerelementfarben, die für die jeweilige Position geeignet sind.** In bestimmten Zuständen verfügen einige Visual Studio-Steuerelemente nicht über separate Rahmen- und Hintergrundfarben. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.

> [!IMPORTANT]
> Verwenden Sie keine Token in den Kategorien "Startseite" oder "Cider".

## <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente

Wenn Sie eine standardmäßige Visual Studio-Befehlsleiste in Ihrem Feature verwenden, haben Sie Zugriff auf formatierte Shellsteuerelemente. Sie sollten diese allgemeinen Steuerelemente nicht erneut erstellen. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.

### <a name="button-controls"></a>Schaltflächen-Steuerelemente

![Button-Steuerelement (rote Linie)](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Schaltflächen im Dokument, die Sie in Visual Studio-Designs integrieren möchten (Light, Dark, Blue oder ein System-Design mit hohem Kontrast). | ... für Schaltflächen, die vor einem benutzerdefinierten Hintergrund angezeigt werden, der nicht Teil eines Visual Studio-Designs ist. |

**Button: Standardzustand**

![Standard-Taste](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Standard-Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.Button` |
| Schaltflächenrahmen | `CommonControls.ButtonBorder` |

**Schaltfläche: Standardzustand**

![Standardschaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Standardschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDefault` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDefault` |

**Schaltfläche: Deaktivierter Zustand**

![Deaktivierte Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Deaktivierte Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDisabled` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDisabled` |

**Button: Hover-Status**

![Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonHover` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderHover` |

**Taste: gedrückter Zustand**

![Gedrückter Knopf](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Gedrückter Knopf

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonPressed` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderPressed` |

**Button: fokussierter Zustand**

![Fokussierte Taste](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Fokussierte Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonFocused` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente
![Kontrollkästchen (rot)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Kontrollkästchen (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Kontrollkästchen-Steuerelemente, die im Dokumentbrunnen enthalten sind. | ... für jede Benutzeroberfläche, die kein Kontrollkästchen-Steuerelement ist. |

**Kontrollkästchen: Standardstatus**

![Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Standard-Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackground` |
| Rahmen | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Kontrollkästchen: Deaktivierter Status**

![Kontrollkästchen Deaktiviert](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Kontrollkästchen Deaktiviert

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundDisabled` |
| Rahmen | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Kontrollkästchen: Hover-Status**

 ![Kontrollkästchen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Kontrollkästchen, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundHover` |
| Rahmen | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Kontrollkästchen: gedrückter Zustand**

![Gedrücktes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Gedrücktes Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Rahmen | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Kontrollkästchen: fokussierter Zustand**

![Fokussiertes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Fokussiertes Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundFocused` |
| Rahmen | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Dropdowns und Combo-Boxen
![Dropdown-/Kombinationsbox (Redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Dropdown-/Kombinationsbox (Redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Dropdowns und Combo-Boxen im Dokument gut. | ... für jede Benutzeroberfläche, die keine Dropdown- oder Combobox ist. |
| | ... für [Befehlsleisten-Dropdowns](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) oder [Kombinationsfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Dropdowns und Kombinationsfelder: Standardzustand**

![Standard-Dropdown-/Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Standard-Dropdown-/Kombinationsfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackground` |
| Rahmen | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Trennzeichen | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackground` |

**Dropdowns und Combo-Boxen: deaktivierter Zustand**

![Deaktiviertes Dropdown-/Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Deaktiviertes Dropdown-/Kombinationsfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundDisabled` |
| Rahmen | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Dropdowns und Combo-Boxen: Hover-Status**

![Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundHover` |
| Rahmen | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Dropdowns und Combo-Boxen: gedrückter Zustand**

![Gedrückte Dropdown-/Combo-Box](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Gedrückte Dropdown-/Combo-Box

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundPressed` |
| Rahmen | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Dropdowns und Kombinationsfelder Listenelementansicht: gedrückter Zustand**

 ![Dropdown/Combo-Feld gedrückt Listenelementansicht](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Dropdown/Combo-Feld gedrückt Listenelementansicht

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Elementtext | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Hintergrundschatten | `CommonControls.ComboBoxListBackgroundShadow` |

**Dropdowns und Combo-Boxen: fokussierter Zustand**

![Dropdown-/Combo-Box mit Fokus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Dropdown-/Combo-Box mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Dropdowns und Kombinationsfelder: Texteingabeauswahl**

![Dropdown-/Combo-Feld-Texteingabeauswahl](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Dropdown-/Combo-Feld-Texteingabeauswahl

| Element | Tokenname: Category.color |
| --- | --- |
| Hervorheben | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)
Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.

![Tabellarische Daten-/Rastersteuerung (Rotlinie)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabellarische Daten-/Rastersteuerung (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Tabellarische oder Raster-Steuerelemente. | ... für jede Benutzeroberfläche, die kein Tabellen- oder Rastersteuerelement ist. |

#### <a name="column-headers"></a>Spaltenüberschriften
Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.

**Spaltenkopf: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.Default` |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Header.Glyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenkopf: Hover-Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.MouseOver` |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Header.MouseOverGlyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenkopf: gedrückter Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Vordergrund (Text) | `CommonControls.CheckBoxBorderPressed` |
| Vordergrund (Glyphe) | `CommonControls.CheckBoxTextPressed` |
| Rahmen | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Listenansichtselemente
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.

**Listenansichtselemente: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Transparent |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Keine |

**Listenansichtselemente: aktiver Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActiveText` |
| Rahmen | Keine |

**Listenansichtselemente: inaktiver Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactiveText` |
| Rahmen | Keine |

### <a name="ui-text"></a>UI-Text

#### <a name="instructional-text"></a>Instruktionstext
Der Instruktionstext gibt eine prominente Haupterklärung darüber, was in einem Dialog oder einer Dokumentseite zu tun ist.

![Standardanweisungstext](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Standardanweisungstext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundärer Lehrtext
In Dokumentseiten mit viel Text und Steuerelementen verwendet ein Anweisungstext einen anderen Farbwert. Dies hilft, zu vermitteln, welche Informationen am wichtigsten sind und die Gesamtdichte der UI-Elemente zu vermindern. (Siehe auch den folgenden Abschnitt zum Hinweistext.)

![Sekundärer Lehrtext](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundärer Lehrtext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Hinweistext
Hinweistext wird in einem leeren Steuerelement, unterhalb eines Steuerelements oder auf einer leeren Dokumentoberfläche angezeigt, um dem Benutzer zu zeigen, was als Nächstes zu tun ist. Sie können Hinweistext mit Fenster- oder Steuerelementhintergründen verwenden.

**Standard-Hinweistext**

![Standard-Hinweistext](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Standard-Hinweistext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

**Erforderlicher Hinweistext**

![Erforderlicher Hinweistext](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Erforderlicher Hinweistext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlRequiredHintText` |
| Hintergrund | `Environment.ControlRequiredBackground` |

**Suchfeld-Steuertext**

> Siehe [Suchfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) für andere Farbtoken im Zusammenhang mit dem Suchsteuerelement.

![Suchfeld-Steuertext](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Suchfeld-Steuertext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Link
Der Hyperlink ist ein Steuerelement, das kein Vordergrund-/Hintergrundpaar hat. Verwenden Sie in allen Fällen die Vordergrund-Hyperlinkfarbe, die auf dunklem, grauem und weißem Hintergrund korrekt angezeigt wird. Wenn Sie das Farbtoken nicht für das Hyperlinksteuerelement verwenden, wird die Standardsystemfarbe für "gedrückt" angezeigt, die rot blinkt. Das ist das Signal, dass das Steuerelement nicht das richtige Umgebungsfarbtoken verwendet.

![Hyperlink (Rote Linie)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hyperlink (Rote Linie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie einen benutzerdefinierten Hyperlink erstellen müssen. | ... für alles, was kein Hyperlink ist. |

**Hyperlink: Standardstatus**

![Standard-Hyperlink](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Standard-Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlink` |

**Hyperlink: Hover-Status**

![Hyperlink, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hyperlink, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkHover` |

**Hyperlink: gedrückter Zustand**

![Gedrückter Hyperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Gedrückter Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkPressed` |

**Hyperlink: Deaktivierter Status**

![Deaktivierter Hyperlink](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Deaktivierter Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.

![Infoleiste (rot)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infoleiste (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... beim Erstellen benutzerdefinierter Infobars. | ... für UI-Elemente, die einer Infoleiste nicht ähneln. |

**Infoleiste: Standardstatus**

![Standard-Infoleiste](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Standard-Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.InfoBarBackground` |
| Vordergrund (Text) | `InfoBar.InfoBar` |
| Rahmen | `InfoBar.InfoBarBorder` |

**Infobar Schließen&times;( ) Taste: Standardzustand**

![Standard-Infobar&times;-Schaltfläche Schließen ( )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Standard-Infobar&times;-Schaltfläche Schließen ( )

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButton` |
| Rahmen | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Infobar Schließen&times;( ) Taste: Hover-Zustand**

![Infobar Schließen&times;( ) Taste auf hover](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Infobar Schließen&times;( ) Taste auf hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonHover` |
| Rahmen | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Infobar Schließen&times;( ) Taste: gedrückter Zustand**

![Gedrückte Infobar&times;Schaltfläche Schließen ( )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Gedrückte Infobar&times;Schaltfläche Schließen ( )

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonDown` |
| Rahmen | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Infobar-Hyperlinkschaltfläche: Standardstatus**

![Standard-Infobar-Hyperlink-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Standard-Infobar-Hyperlink-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Infobar-Hyperlink-Schaltfläche: Hover-Status**

![Infobar-Hyperlink-Schaltfläche auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Infobar-Hyperlink-Schaltfläche auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit Unterstreichung) |

**Infobar-Hyperlink-Taste: Gedrückter Zustand**

![Gedrückte Infobar-Hyperlink-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Gedrückte Infobar-Hyperlink-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit Unterstreichung) |

**Infobar-Inline-Hyperlink (innerhalb eines Satzes): Standardzustand**

![Standard-Inline-Infobar-Hyperlinkschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Standard-Inline-Infobar-Hyperlinkschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Infobar-Inline-Hyperlink (innerhalb eines Satzes): Hover-Status**

![Infobar-Inline-Hyperlink-Schaltfläche auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Infobar-Inline-Hyperlink-Schaltfläche auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit Unterstreichung) |

**Infobar-Inline-Hyperlink (innerhalb eines Satzes): Gedrückter Zustand**

![Gedrückte Infobar-Inline-Hyperlinkschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Gedrückte Infobar-Inline-Hyperlinkschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit Unterstreichung) |

**Infobar-Schaltfläche: Standardstatus**

![Standard-Infoleistenschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Standard-Infoleistenschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.Button` |
| Vordergrund (Text) | `InfoBar.Button` |
| Rahmen | `InfoBar.ButtonBorder` |

**Infobar-Taste: Hover-Status**

![Infobar-Taste auf Hover](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Infobar-Taste auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseOver` |
| Vordergrund (Text) | `InfoBar.ButtonMouseOver` |
| Rahmen | `InfoBar.ButtonMouseOverBorder` |

**Infobar-Taste: gedrückter Zustand**

![Gedrückte Infobar-Taste](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Gedrückte Infobar-Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseDown` |
| Vordergrund (Text) | `InfoBar.ButtonMouseDown` |
| Rahmen | `InfoBar.ButtonMouseDownBorder` |

**Infobar-Schaltfläche: Deaktivierter Zustand**

![Deaktivierte Infobar-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Deaktivierte Infobar-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonDisabled` |
| Vordergrund (Text) | `InfoBar.ButtonDisabled` |
| Rahmen | `InfoBar.ButtonDisabledBorder` |

**Infobar-Schaltfläche: fokussierter Zustand**

![Fokussierte Infobar-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Fokussierte Infobar-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonFocus` |
| Vordergrund (Text) | `InfoBar.ButtonFocus` |
| Rahmen | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Bildlaufleisten
Bildlaufleisten werden von der Visual Studio-Umgebung formatiert und müssen nicht thematisiert werden. Sie können jedoch entscheiden, dass Sie die farben nutzen möchten, die in Bildlaufleisten verwendet werden, damit die Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent angezeigt wird.

![Scrollleiste (Rotlinie)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Scrollleiste (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie eine Benutzeroberfläche erstellen, die mit visual Studio-Bildlaufleisten übereinstimmen soll. | ... für alles, was Sie nicht immer mit der Bildlaufleisten-Benutzeroberfläche übereinstimmen möchten. |

**Bildlaufleiste: Standardzustand**

![Standard-Bildlaufleiste](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Standard-Bildlaufleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbBackground` |

**Scrollleiste: Hover-Status**

![Bildlaufleiste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Bildlaufleiste, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbMouseOverBackground` |

*Scrollleiste: gedrückter Zustand**

![Gedrückte Scrollleiste](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Gedrückte Scrollleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbPressedBackground` |

**Bildlaufleistenpfeil: Standardzustand**

![Standard-Bildlaufleistenpfeil](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Standard-Bildlaufleistenpfeil

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowBackground`<br />(Auf die gleiche Farbe wie die Bildlaufleiste eingestellt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyph` |

**Bildlaufbalkenpfeil: Hover-Status**

![Bildlaufleiste (Pfeil), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Bildlaufleiste (Pfeil), wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowMouseOverBackground`<br />(Auf die gleiche Farbe wie die Bildlaufleiste eingestellt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Bildlaufbalkenpfeil: gedrückter Zustand**

![Gedrückter Bildlaufleistenpfeil](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Gedrückter Bildlaufleistenpfeil

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowPressedBackground`<br />(Auf die gleiche Farbe wie die Bildlaufleiste eingestellt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Suchfelder
Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.

Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:

- "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.

- "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.

- "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).

- "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.

![Suchfeld (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Suchfeld (redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie ein benutzerdefiniertes Suchfeld entwerfen. | ... für alles, was kein Suchfeld ist. |
| | ... für alles, was Sie nicht immer mit der Suchfeld-Benutzeroberfläche übereinstimmen möchten. |

**Fokussiertes Sucheingabefeld**

![Fokussiertes Sucheingabefeld](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Fokussiertes Sucheingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedBackground` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | `SearchControl.FocusedBorder` |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Unkonzentriertes, aktives Sucheingabefeld**

![Suche (Eingabefeld) ohne Fokus](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Unkonzentriertes, aktives Sucheingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.SearchActiveBackground` |
| Vordergrund (Text) | `SearchControl.SearchActiveBackground` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Unkonzentriertes, inaktives Sucheingabefeld**

![Unkonzentriertes, inaktives Sucheingabefeld](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Unkonzentriertes, inaktives Sucheingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Unfocused` |
| Vordergrund (Text) | `SearchControl.Unfocused` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Hervorgehobenes Sucheingabefeld (nur Text)**

![Hervorgehobenes Sucheingabefeld](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Hervorgehobenes Sucheingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Selection` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | Keine |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Deaktiviertes Sucheingabefeld**

![Deaktiviertes Sucheingabefeld](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Deaktiviertes Sucheingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Disabled` |
| Vordergrund (Text) | `SearchControl.Disabled` |
| Rahmen | `SearchControl.DisabledBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Fokussierte Suchaktionsschaltfläche**

![Suche (Aktionsschaltfläche) mit Fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Fokussierte Suchaktionsschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Unfokussierte Suchaktionsschaltfläche**

![Unfokussierte Suchaktionsschaltfläche](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Unfokussierte Suchaktionsschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Gedrückte Suchaktionsschaltfläche**

![Gedrückte Suchaktionsschaltfläche](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Gedrückte Suchaktionsschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.ActionButtonMouseDown` |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Rahmen | `SearchControl.ActionButtonMouseDownBorder` |

**Deaktivierte Suchaktionsschaltfläche**

![Suche (Aktionsschaltfläche), deaktiviert](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Deaktivierte Suchaktionsschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Rahmen | Keine |

**Fokussierte Suche Dropdown-Taste**

![Fokussierte Suche Dropdown-Taste](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Fokussierte Suche Dropdown-Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.FocusedDropDownButtonBorder` |

**Unfokussierte Such-Dropdown-Schaltfläche**

![Unfokussierte Such-Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Unfokussierte Such-Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.UnfocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.UnfocusedDropDownButtonBorder` |

**Gedrückte Such-Dropdown-Taste**

![Gedrückte Such-Dropdown-Taste](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Gedrückte Such-Dropdown-Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.MouseDownDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Rahmen | `SearchControl.MouseDownDropDownButtonBorder` |

**Dropdown-Schaltfläche für deaktivierte Suche**

![Dropdown-Schaltfläche für deaktivierte Suche](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Dropdown-Schaltfläche für deaktivierte Suche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Rahmen | Keine |

#### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld
Das Dropdown-Menü des Suchfelds kann etwas komplexer sein als andere Dropdownmenüs in Visual Studio. Die Abschnitte "vorgeschlagene Suchen" und "Suchoptionen" können allein oder zusammen im Menü angezeigt werden, und jeder wird separat eingefärbt. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.

![Dropdown-Liste suchen (rote Linie)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Dropdown-Liste suchen (rote Linie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie eine benutzerdefinierte Such-Dropdown-Liste erstellen. | ... für Dropdown-Listen, die in anderen Kontexten angezeigt werden. |
| ... die richtigen Tokennamen für die richtigen Listenkomponenten. | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Suche Dropdown-Listenelemente**

| Element | Tokenname: Category.color |
| --- | --- |
| Rahmen | `SearchControl.PopupBorder` |
| Trennzeichen | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Vorgeschlagene Suchen: Standardstatus**

![Standard-Vorgeschlagene Suchen](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Standard-Vorgeschlagene Suchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `SearchControl.PopupItemText` |

**Vorgeschlagene Suchen: Hover-Status**

![Vorgeschlagene Suchanfragen auf Hover](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Vorgeschlagene Suchanfragen auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `SearchControl.PopupMouseOverItemText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: Standardstatus**

![Kontrollkästchen "Suche"](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Standardsuchoptionen (Kontrollkästchen)

![Suchoptionen](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Standardsuchoptionen (Link)

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonText` |
| Headerhintergrund | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Headertext) | `SearchControl.PopupSectionHeaderText` |

**Suchoptionen: Hover-Status**

![Suchoptionen (Kontrollkästchen) bei Hover](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Suchoptionen (Kontrollkästchen) bei Hover

![Suchoptionen (Link) auf Hover](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Suchoptionen (Link) auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: gedrückter Zustand**

![Gedrückte Suchoptionen (Kontrollkästchen)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Gedrückte Suchoptionen (Kontrollkästchen)

![Gedrückte Suchoptionen (Link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Gedrückte Suchoptionen (Link)

| Element | Tokenname: Category.color |
| --- | --- |
| Kontrollkästchen-Hintergrund | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Linkhintergrund | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Baumansichten
Mehrere Toolfenster, einschließlich des Projektmappen-Explorers, des Server-Explorers und der Klassenansicht, `TreeView` implementieren ein hierarchisches Organisationsschema, dessen Farben durch Farbnamen in der Kategorie gesteuert werden. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.

![Baumansicht (Rotlinie)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Baumansicht (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... überall, wo Sie eine hierarchische Organisationsansicht implementieren müssen. | ... für alles, was einer Baumansicht nicht ähnelt. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Strukturansichtselement: Standardstatus**

![Standardstrukturansichtselement](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Standardstrukturansichtselement

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.Glyph` |
| Rahmen | Keine |

**Baumansichtselement: Hover-Status**

![Baumansichtselement auf hover](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Baumansichtselement auf hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.GlyphMouseOver` |
| Rahmen | Keine |

**Baumansichtselement: Über den Zustand ziehen**

![Baumansichtselement beim Ziehen über](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Baumansichtselement beim Ziehen über

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.DragOverItem` |
| Vordergrund (Text) | `TreeView.DragOverItem` |
| Vordergrund (Glyphe) | `TreeView.DragOverItemGlyph` |
| Rahmen | Keine |

**Baumansichtselement: ausgewählter, fokussierter Zustand**

![Ausgewähltes und fokussiertes Baumansichtselement](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Ausgewähltes und fokussiertes Baumansichtselement

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Baumansichtselement: ausgewählter, unfokussierter Zustand**

![Ausgewähltes und unfokussiertes Strukturansichtselement](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Ausgewähltes und unfokussiertes Strukturansichtselement

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Rahmen | Keine |

**Strukturansichtselement: schwebender, ausgewählter und fokussierter Zustand**

![Ausgewähltes und fokussiertes Baumansichtselement auf der Mauszeiger](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Ausgewähltes und fokussiertes Baumansichtselement auf der Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Strukturansichtselement: schwebender, ausgewählter und unfokussierter Zustand**

![Ausgewähltes und unfokussiertes Baumansichtselement auf der Mauszeiger](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Ausgewähltes und unfokussiertes Baumansichtselement auf der Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | Keine |

## <a name="shell-appearance"></a>Shell-Darstellung

### <a name="background"></a>Hintergrund
Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Die oberen und unteren Hintergrundebenen werden in den Themen Licht und Dunkel auf die gleiche Farbe festgelegt.

![Hintergrund der Visual Studio-Shell (Rote Linie)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Hintergrund der Visual Studio-Shell (Rote Linie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Orte, an denen Sie dem Hintergrund der Visual Studio-Umgebung entsprechen möchten. | ... als Füllung für Orte, die keine Hintergrundflächen sind. |
| | ... als Hintergrund, auf dem Vordergrundelemente platziert werden können. |

**Aussehen der unteren Schichtschale**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackground` |

**Darstellung der obersten Schicht-Shell**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Befehlsablage
Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.

![Visual Studio-Befehlsregal (Rote Linie)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio-Befehlsregal (Rote Linie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Bereiche, in denen Sie Menüs oder Symbolleisten platzieren. | ... für Bereiche, die einem Befehlsregal nicht ähneln. |
|... mit der richtigen Hintergrund-/Vordergrundtokennamenkombination. | |

**Befehlsregal-Menüleiste**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Befehlsregal-Befehlsleiste**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest-Designer
Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest-Designer (Redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest-Designer (Redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Designer, die dem Manifest-Designer ähneln. | ... wenn Sie mehr als sechs Registerkarten haben. |
| ... anstelle der Verwendung gemeinsamer Registerkartensteuerelemente am oberen Rand eines Editors innerhalb des Dokumentbrunnens. | ... für jede Benutzeroberfläche, die nicht wie der Manifest-Designer strukturiert ist. |

**Manifest-Designer-Registerkarte: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.TabActive` |
| Rahmen | Keine |

**Manifest Designer ausgewählter Beschreibungsbereich: Standardzustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.DescriptionPane` |

**Manifest Designer ausgewählte Inhaltsseite: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Background` |
| Dialogfeld-Hilfetext | `ManifestDesigner.WatermarkText`<br />(Dieser Tokenname stimmt nicht mit seiner Funktion überein.) |

**Registerkarte Manifest-Designer: nicht ausgewählter Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Inactive` |

**Registerkarte Manifest-Designer: Hover-Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Befehlsstrukturen

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menüs
Menüs können an mehreren Stellen in Visual Studio auftreten: in der Hauptmenüleiste, eingebettet in Dokument- oder Toolfenster, oder mit der rechten Maustaste an verschiedenen Stellen in der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.

![Visual Studio-Menü (Rotlinie)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio-Menü (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie ein benutzerdefiniertes Menü erstellen müssen.| ... die Hintergrundfarbe allein. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe. |
| ... wenn Sie über eine neue UI-Komponente verfügen, die den Visual Studio-Menüs entsprechen soll.| |

#### <a name="menu-titles"></a>Menütitel
Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.

![Menütitel (Rotlinie)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menütitel (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie einen benutzerdefinierten Menütitel erstellen. | ... für alles, was Sie nicht immer mit dem Menütitel übereinstimmen möchten. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Menütitel: Standardstatus**

![Standardmenütitel](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Standardmenütitel

![Standardmenütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Standardmenütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuGlyph` |
| Rahmen | Keine |

**Menütitel: Hover-Status**

![Menütitel, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Menütitel, wenn darauf gezeigt wird

![Menütitel mit Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Menütitel mit Glyphe, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |

**Menütitel: gedrückter Zustand**

![Gedrückter Menütitel](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Gedrückter Menütitel

![Gedrückter Menütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Gedrückter Menütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder`<br />(Nur links, oben und rechts.) |

**Menütitel: deaktivierter Status**

![Deaktivierter Menütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Deaktivierter Menütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Keine |

#### <a name="menu-items"></a>Menüelemente
Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.

![Menüelemente (rote Linie)](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Verwenden... | Verwenden Sie nicht ... |
|---|---|
| ... für jede Dropdown-Liste, die über eine Menüleiste oder Befehlsleiste gestartet wird. | ... für jede Dropdown-Liste in einem anderen Kontext. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Menüelemente: Standardstatus**

![Standardmenüelemente](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Standardmenüelemente

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder` |
| Symbolkanal-Hintergrund | `Environment.CommandBarMenuIconBackground` |
| Trennzeichen | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Menüelemente: geprüfte und ausgewählte Zustände**

![Menü, aktiviert](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Geprüfter Menüpunkt

![Menü, ausgewählt](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Ausgewählter Menüpunkt

| Element | Tokenname: Category.color |
| --- | --- |
| Häkchen | `Environment.CommandBarCheckBox` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarSelected` |
| Symbolrahmen | `Environment.CommandBarSelectedBorder` |

**Menüelemente: Hover-Status**

![Menü, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Menüpunkt auf Hover

![Menü, wenn darauf gezeigt wird (aktiviert)](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Geprüfter Menüpunkt auf hover

![Menü, wenn darauf gezeigt wird (ausgewählt)](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Ausgewählter Menüpunkt auf der Maustaste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Text) | `Environment.CommandBarMenuItemMouseOverText` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxMouseOver` |
| Häkchenhintergrund | `Environment.CommandBarHoverOverSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarHoverOverSelected` |
| Symbolrahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menüelemente: deaktivierter Status**

![Menü, deaktiviert](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Deaktivierter Menüpunkt

![Menü, deaktiviert (geprüft)](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Deaktivierter Menüpunkt mit Häkchen

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxDisabled` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Befehlsleisten
Eine Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE angezeigt werden, insbesondere im Befehlsregal und eingebettet in Werkzeug- oder Dokumentfenster.

Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.

![Befehlszeile (rote Linie)](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Befehlsleiste (rot)

![Schaltfläche "Überlauf" (rote Linie)](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Überlauftaste (Redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an Orten, an denen Sie eine eingebettete Befehlsleiste benötigen, aber nicht in der Lage sind, die standardmäßige Visual Studio-Befehlsleistenimplementierung zu verwenden. | ... für UI-Elemente, die einer Befehlsleiste nicht ähneln. |
| | ... für andere Befehlsleistenkomponenten als die, für die Tokennamen angegeben sind. |

#### <a name="command-bar-groups"></a>Befehlsleistengruppen
Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.

![Befehlszeilengruppe (rote Linie)](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Befehlsleistengruppe (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an Orten, an denen Sie eine eingebettete Befehlsleiste benötigen, aber nicht in der Lage sind, die standardmäßige Visual Studio-Befehlsleistenimplementierung zu verwenden. | ... für UI-Elemente, die einer Befehlsleiste nicht ähneln. |
| | ... für andere Befehlsleistenkomponenten als die, für die Tokennamen angegeben sind. |

**Befehlsleistengruppe: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Rahmen | `Environment.CommandBarToolBarBorder` |
| Ziehpunkt | `Environment.CommandBarDragHandle` |
| Trennzeichen | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Befehlssymbole
![Rote Linie – Befehlssymbol](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Befehlssymbol (rot)

![Befehlssymbol mit Text-Redline](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Befehlssymbol mit Text (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für alle Schaltflächen, die auf einer Befehlsleiste platziert werden. | ... für Steuerelemente, die eigene Tokennamen haben. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Befehlssymbol: Standardstatus**

![Standardmäßiges Befehlssymbol](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Standardbefehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Nicht zutreffend |

**Befehlssymbol: Standardzustand, ausgewählt**

![Standardsymbol für ausgewählte Befehle](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Standardsymbol für ausgewählte Befehle

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextSelected` |
| Rahmen | `Environment.CommandBarSelectedBorder` |

**Befehlssymbol: Zeiger auf oder Fokuszustände**

![Befehlssymbol auf Hover oder Fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Befehlssymbol auf Hover oder Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehlssymbol: Zeiger auf oder Fokuszustände, ausgewählt**

![Ausgewähltes Befehlssymbol auf dem Mauszeiger oder Fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ausgewähltes Befehlssymbol auf dem Mauszeiger oder Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarHoverOverSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextHoverOverSelected` |
| Rahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Befehlssymbol: gedrückter Zustand**

![Gedrücktes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Gedrücktes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehlssymbol: Deaktivierter Status**

![Deaktiviertes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Deaktiviertes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Befehlsleisten-Kombinationsfelder

> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn Ihre Dropdownliste keinen bearbeitbaren Textbereich enthält, verwenden Sie die Farbtoken für [Dropdown-Dateien der Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Befehlsleisten-Kombinationsfeld redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Befehlsleisten-Kombinationsfeld (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... beim Erstellen benutzerdefinierter Kombinationsboxen. | ... für alles, was Sie nicht immer mit der Benutzeroberfläche der Befehlsleiste übereinstimmen möchten. |
| ... wenn Sie ein Befehlsleistensteuerelement erstellen, das einem Kombinationsfeld ähnelt. | ... wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben. |

**Eingabefeld der Befehlsleiste Combo feld: Standardzustand**

![Eingabefeld der Befehlsleisten-Kombinationsbox](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Eingabefeld der Befehlsleisten-Kombinationsbox

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxBackground` |
| Vordergrund (Text) | `Environment.ComboBoxText` |
| Rahmen | `Environment.ComboBoxBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche für die Befehlsleiste: Standardzustand**

![Combo-Box Drop-&#45;-Down-Taste](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Dropdown-Schaltfläche für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Glyphe) | `Environment.ComboBoxGlyph` |

**Dropdown-Liste der Befehlsleiste: Standardstatus**

![Dropdown-Liste der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Dropdown-Liste der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxPopupBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.ComboBoxPopupBorder` |

**Befehlsleisten-Kombinationsfeld-Eingabefeld: Hover-Status**

![Befehlsleisten-Kombinationsfeld-Eingabefeld auf Hover](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Befehlsleisten-Kombinationsfeld-Eingabefeld auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.ComboBoxMouseOverText` |
| Rahmen | `Environment.ComboBoxMouseOverBorder` |
| Trennzeichen | `Environment.ComboBoxMouseOverSeparator` |

 **Dropdown-Schaltfläche der Befehlsleiste: Hover-Status**

![Dropdown-Schaltfläche der Befehlsleiste auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Dropdown-Schaltfläche der Befehlsleiste auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Dropdown-Liste der Befehlsleiste: Hover-Status**

 ![Dropdown-Liste der Befehlsleiste auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Dropdown-Liste der Befehlsleiste auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Eingabefeld der Befehlsleiste Combo box: fokussierter Zustand**

![Fokussiertes Befehlsleisten-Kombinationsfeld-Eingabefeld](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Fokussiertes Befehlsleisten-Kombinationsfeld-Eingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedBackground` |
| Vordergrund (Text) | `Environment.ComboBoxFocusedText` |
| Rahmen | `Environment.ComboBoxFocusedBorder` |
| Trennzeichen | `Environment.ComboBoxFocusedButtonSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: fokussierter Zustand**

![Fokussierte Dropdown-Schaltfläche der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Fokussierte Dropdown-Schaltfläche der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedButtonBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Eingabefeld der Befehlsleiste Combo Box: gedrückter Zustand**

![Eingabefeld für gedrückte Befehlsleisten-Kombinationsbox](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Eingabefeld für gedrückte Befehlsleisten-Kombinationsbox

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseDownBackground` |
| Vordergrund (Text) | `Environment.ComboBoxMouseDownText` |
| Rahmen | `Environment.ComboBoxMouseDownBorder` |
| Trennzeichen | `Environment.ComboBoxMouseDownSeparator` |

**Dropdown-Taste der Befehlsleiste: gedrückter Zustand**

![Gedrückte Dropdown-Taste der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Gedrückte Dropdown-Taste der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Eingabefeld der Befehlsleiste Combo box: deaktivierter Zustand**

![Deaktiviertes Befehlsleisten-Kombinationsfeld-Eingabefeld](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Deaktiviertes Befehlsleisten-Kombinationsfeld-Eingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxDisabledBackground` |
| Vordergrund (Text) | `Environment.ComboBoxDisabledText` |
| Rahmen | `Environment.ComboBoxDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Deaktivierter Zustand**

![Dropdown-Schaltfläche für deaktivierte Befehlsleiste](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Dropdown-Schaltfläche für deaktivierte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Dropdowns der Befehlsleiste

> [!IMPORTANT]
> Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn Ihre Dropdownliste einen bearbeitbaren Textbereich enthält, verwenden Sie die Farbtoken für [Befehlsleistenkombinationsfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Dropdown der Befehlsleiste (Redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Dropdown der Befehlsleiste (Redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie benutzerdefinierte Dropdown-Listensteuerelemente erstellen. | ... für alles, was einer Dropdownliste nicht ähnelt. |
| | ... für Kombinationsfelder oder Geteilte Tasten. |

**Dropdown-Auswahlfeld der Befehlsleiste: Standardstatus**

![Standard-Dropdown-Auswahlfeld für die Befehlsleiste](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Standard-Dropdown-Auswahlfeld für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownBackground` |
| Vordergrund (Text) | `DropDownText` |
| Rahmen | `DropDownBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche für die Befehlsleiste: Standardzustand**

![Standard-Befehlsleisten-Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Standard-Befehlsleisten-Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.DropDownGlyph` |

**Dropdown-Liste der Befehlsleiste: Standardstatus**

![Dropdown-Liste der Standardbefehlsleiste](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Dropdown-Liste der Standardbefehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownPopupBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Dropdown-Auswahlfeld der Befehlsleiste: Hover-Status**

![Dropdown-Auswahlfeld für die Befehlsleiste auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Dropdown-Auswahlfeld für die Befehlsleiste auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.DropDownMouseOverText` |
| Rahmen | `Environment.DropDownMouseOverBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseOverSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: Hover-Status**

![Dropdown-Schaltfläche der Befehlsleiste auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Dropdown-Schaltfläche der Befehlsleiste auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseOverGlyph` |

**Dropdown-Liste der Befehlsleiste: Hover-Status**

![Dropdown-Liste der Befehlsleiste auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Dropdown-Liste der Befehlsleiste auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Dropdown-Auswahlfeld der Befehlsleiste: gedrückter Zustand**

![Drop&#45;-Down-Auswahlfeld gedrückt](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Gedrücktes Dropdown-Auswahlfeld für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseDownBackground` |
| Vordergrund (Text) | `Environment.DropDownMouseDownText` |
| Rahmen | `Environment.DropDownMouseDownBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseDownSeparator` |

**Dropdown-Taste der Befehlsleiste: gedrückter Zustand**

![Gedrückte Dropdown-Taste der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Gedrückte Dropdown-Taste der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseDownGlyph` |

**Dropdown-Auswahlfeld der Befehlsleiste: Deaktivierter Status**

![Deaktiviertes Dropdown-Auswahlfeld für die Befehlsleiste](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Deaktiviertes Dropdown-Auswahlfeld für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownDisabledBackground` |
| Vordergrund (Text) | `Environment.DropDownDisabledText` |
| Rahmen | `Environment.DropDownDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Deaktivierter Zustand**

![Dropdown-Schaltfläche für deaktivierte Befehlsleiste](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Dropdown-Schaltfläche für deaktivierte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Befehlsleisten-Split-Schaltflächen
Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Dropdown-Listen für geteilte Schaltflächen sind Implementierungen von [Befehlsleistenmenüs](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Trennschaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Befehlsleisten-Split-Taste (redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie eine benutzerdefinierte Split-Schaltfläche erstellen. | ... für andere Arten von Schaltflächen. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Befehlsleisten-Split-Schaltfläche: Standardzustand**

![Standard-Befehlsleisten-Split-Schaltfläche](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Standard-Befehlsleisten-Split-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

**Befehlsleiste-Split-Taste: Hover-Status**

![Befehlsleiste Split-Taste auf Hover](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Befehlsleiste Split-Taste auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | `Environment.CommandBarSplitButtonSeparator` |

**Befehlsleiste Split-Taste: gedrückter Zustand**

![Gedrückter Befehlsleisten-Split-Button](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Gedrückter Befehlsleisten-Split-Button

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | Nicht zutreffend |

**Befehlsleisten-Split-Schaltfläche: deaktivierter Status**

![Deaktivierte Befehlsleiste Split-Taste](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Deaktivierte Befehlsleiste Split-Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Text) | `Environment.ComboBoxItemTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Befehlsleiste 'Mehr Optionen' und 'Überlauf' Tasten
Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.

![Befehlsleiste 'Mehr Optionen' Taste (redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Befehlsleiste 'Mehr Optionen' Taste (redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für benutzerdefinierte Schaltflächen "Mehr Optionen" oder "Überlauf". | ... für Schaltflächen, die nicht über eine ähnliche Funktionalität wie eine Schaltfläche "Mehr Optionen" oder "Überlauf" verfügen. |

**Befehlsleiste 'Mehr Optionen' und 'Überlauf' Schaltflächen: Standardzustand**

![Standard-Befehlsleiste 'Mehr Optionen' Taste](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Standard-Befehlsleiste 'Mehr Optionen' Taste

![Standard-Befehlsleiste 'Überlauf' Taste](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Standard-Befehlsleiste 'Überlauf' Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsBackground` |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsGlyph` |

**Befehlsleiste 'Mehr Optionen' und 'Überlauf' Tasten: Hover-Status**

![Befehlsleiste 'Mehr Optionen' Taste auf Hover](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Befehlsleiste 'Mehr Optionen' Taste auf Hover

![Befehlsleiste 'Overflow' Taste auf Hover](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Befehlsleiste 'Overflow' Taste auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Befehlsleiste 'Mehr Optionen' und 'Überlauf' Tasten: gedrückter Zustand**

![Gedrückte Befehlsleiste 'Mehr Optionen' Taste](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Gedrückte Befehlsleiste 'Mehr Optionen' Taste

!["Überlauf", aufgerufen](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Gedrückte Befehlsleiste 'Overflow' Taste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Dokumentfenster
Es ist nicht erforderlich, Dokumentfenster zu replizieren, da sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

Achten Sie bei der Verwendung von Dokumentfensterfarbtoken darauf, sie nur für ähnliche Elemente und immer paarweise zu verwenden. Wenn Sie dies nicht tun, erhalten Sie möglicherweise unerwartete Ergebnisse in der Benutzeroberfläche.

### <a name="document-window-frames"></a>Dokumentfensterrahmen
Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Wenn ein Dokumentfenster außerhalb der IDE schwebt, befindet es sich immer noch in einem Dokument und verfügt über Hintergrund-, Rahmen-, Text- und Registerkartenfarben, die mit dem identisch sind, wenn es Teil der IDE ist. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.

![Angedocktes Dokumentfenster (rot)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Angedocktes Dokumentfenster (rot)

![Unverankertes Dokumentfenster (Rotlinie)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Unverankertes Dokumentfenster (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die dem Dokumentfenster entsprechen soll. | ...  für jede Benutzeroberfläche, die nicht automatisch geändert werden soll, wenn die Shell über ein Designupdate verfügt. |

**Angedocktes oder unverankertes Dokumentfenster: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Hängt vom Dokumenttyp ab. |
| Vordergrund (Text) | Hängt vom Dokumenttyp ab. |
| Rahmen | `Environment.ToolWindowBorder` |

**Fokussierter, unverankerter Dokumentfensterrahmen: Standardzustand**

![Standardfokussierter, unverankerter Dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Standardfokussierter, unverankerter Dokumentfensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Auf transparent eingestellt) |

**Unfokussierter, unverankerter Dokumentfensterrahmen: Standardzustand**

![Standard unfokussierter, unverankerter Dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Standard unfokussierter, unverankerter Dokumentfensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Rahmen | `Environment.MainWindowInactiveBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Auf transparent eingestellt) |

**Fokussierter, schwebender Dokumentfensterrahmen: Hover-Status**

![Fokussierter, schwebender Dokumentfensterrahmen auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Fokussierter, schwebender Dokumentfensterrahmen auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Unfokussierter, schwebender Dokumentfensterrahmen: Hover-Status**

![Unfokussierter, schwebender Dokumentfensterrahmen auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Unfokussierter, schwebender Dokumentfensterrahmen auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Fokussierter, schwebender Dokumentfensterrahmen: gedrückter Zustand**

![Fokussierter, schwebender Dokumentfensterrahmen auf Drücken](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Fokussierter, schwebender Dokumentfensterrahmen auf Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Dokumentregisterkarten
Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.

![Dokumentregisterkarten (rotlinie)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Dokumentregisterkarten (rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... Überall an einer Beliebigen, die Sie erstellen, können Sie Dokumentregisterkarten abgleichen und automatisch Designaktualisierungen oder neue Designfarben aufnehmen. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

#### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten
Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:

- Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.

- Hintergrundregisterkarten sind alle Dokumentregisterkarten, die nicht die aktuell ausgewählte Registerkarte sind. Sobald sie darauf geklickt haben, werden sie zur ausgewählten Registerkarte und erfassen alle Hintergrund-, Rahmen- und Textfarben aus diesen Tokennamen.

![Registerkarte Dokument öffnen (rotlinie)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Registerkarte Dokument öffnen (rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie benutzerdefinierte Dokumentregisterkarten erstellen. | ... für vorläufige (Vorschau-)Registerkarten. |
| | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Ausgewählte, fokussierte Dokumentregisterkarte**

![Ausgewählte, fokussierte Dokumentregisterkarte](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Ausgewählte, fokussierte Dokumentregisterkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabSelectedGradientTop`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.FileTabSelectedText` |
| Rahmen | `Environment.FileTabSelectedBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |
| Dokumentrahmen | `Environment.FileTabDocumentBorderBackground` |

**Ausgewählte Registerkarte für ausgewählte, unfokussierte Dokumente**

![Ausgewählte Registerkarte für ausgewählte, unfokussierte Dokumente](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Ausgewählte Registerkarte für ausgewählte, unfokussierte Dokumente

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabInactiveGradientTop`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.FileTabInactiveText` |
| Rahmen | `Environment.FileTabInactiveBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |
| Dokumentrahmen | `Environment.FileTabInactiveDocumentBorderBackground` |

**Registerkarte Hintergrunddokument: Standardzustand**

![Standard-Hintergrunddokument-Registerkarte](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Standard-Hintergrunddokument-Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabBackground` |
| Vordergrund (Text) | `Environment.FileTabText` |
| Rahmen | `Environment.FileTabBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

**Registerkarte Hintergrunddokument: Hover-Status**

![Registerkarte Hintergrunddokument auf der Mauszeiger](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Registerkarte Hintergrunddokument auf der Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabHotGradientTop`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.FileTabHotText` |
| Rahmen | `Environment.FileTabHotBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

#### <a name="preview-tab"></a>Vorschauregisterkarte
Wird auch als "vorläufige" Registerkarte bezeichnet. Die Vorschau-Registerkarte wird auf der rechten Seite des Dokumentregisterkartenkanals angezeigt, wenn der Benutzer im Werkzeugfenster Projektmappen-Explorer auf ein Element klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.

![Vorschau-Registerkarte (rot)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Vorschau-Registerkarte (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... Überall, an denen Sie eine vorläufige Vorschau erstellen und ein Element mit der aktuellen Vorschau-Registerkartenfarbe übereinstimmen soll. | ... für jede Art von Dokument oder Registerkarte, die nicht vorläufig ist (Vorschau). |
| | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Fokussierte, ausgewählte Vorschau-Registerkarte**

![Fokussierte, ausgewählte Vorschau-Registerkarte](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Fokussierte, ausgewählte Vorschau-Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedActive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Unfokussierte, ausgewählte Vorschau-Registerkarte**

![Unfokussierte, ausgewählte Vorschau-Registerkarte](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Unfokussierte, ausgewählte Vorschau-Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Registerkarte Hintergrundvorschau: Standardzustand**

![Standard-Hintergrundvorschau-Registerkarte](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Standard-Hintergrundvorschau-Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalInactiveBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

**Registerkarte Hintergrundvorschau: Hover-Status**

![Hintergrundvorschau-Registerkarte auf der Mauszeiger](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Hintergrundvorschau-Registerkarte auf der Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalHover` |
| Vordergrund (Text) | `Environment.FileTabProvisionalHoverForeground` |
| Rahmen | `Environment.FileTabProvisionalHoverBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

#### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche
Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dropdown-Menü "Dokumentüberlauf", das über die Menüfarben der [Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) gesteuert wird, zeigt eine Liste aller sichtbaren und ausgeblendeten geöffneten Dokumente an, und die Überlauf-Glyphe ändert sich, je nachdem, ob alle geöffneten Dokumente im Registerkartenkanal angezeigt werden.

![Dokumentüberlaufschaltfläche (Rote Linie)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Dokumentüberlaufschaltfläche (Rote Linie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie eine benutzerdefinierte Dokumentüberlaufschaltfläche erstellen. | ... für benutzeroberfläche, die einer Überlaufschaltfläche nicht ähnelt. |
| | ... für Befehlsleistenüberlaufschaltflächen. |

**Dokumentüberlaufschaltfläche: Standardstatus**

![Standard-Dokumentüberlaufschaltfläche](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Standard-Dokumentüberlaufschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Rahmen | Nicht zutreffend |

**Dokumentüberlaufschaltfläche: Hoverstatus**

![Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Dokumentüberlauftaste: gedrückter Zustand**

![Dokumentüberlauftaste beim Drücken](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Dokumentüberlauftaste beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Kennzeichnung (Tagging)
Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.

![Tagging in Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Tagging in Visual Studio (Redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für die Benutzeroberfläche, die Tagging unterstützt. | ... für jede andere Art von Benutzeroberfläche. |

#### <a name="tags"></a>`Tags`

**Tag: Standardstatus**

![Standard-Tag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Standard-Tag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.Background` |
| Vordergrund (Text) | `Tag.Background` |

**Tag: Hover-Status**

![Tag, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.HoverBackground` |
| Vordergrund (Text) | `Tag.HoverBackgroundText` |

**Tag: gedrückter Zustand**

![Gedrücktes Tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Gedrücktes Tag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.PressedBackground` |
| Vordergrund (Text) | `Tag.PressedBackgroundText` |

**Tag: ausgewählter Zustand**

![Ausgewähltes Tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Ausgewähltes Tag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.SelectedBackground` |
| Vordergrund (Text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Schließen&times;( ) Tag-Glyphe

**Schließen&times;( ) Tag-Glyphe: Standardzustand**

![Standard-Schließen&times;( )-Tag-Glyphe](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Standard-Schließen&times;( )-Tag-Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyph` |

**Schließen&times;( ) Tag-Glyphe: Hover-Status**

![Schließen&times;( ) Tag-Glyphe auf hover](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Schließen&times;( ) Tag-Glyphe auf hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphHover` |
| Rahmen | `Tag.TagHoverGlyphHoverBorder` |

**Schließen&times;( ) Tag-Glyphe: gedrückter Zustand**

![Gedrückt Schließen&times;( ) Tag-Glyphe](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Gedrückt Schließen&times;( ) Tag-Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphPressed` |
| Rahmen | `Tag.TagHoverGlyphPressedBorder` |

**Ausgewähltes Tag&times;mit Close ( ) Glyphe: Standardzustand**

![Standardmäßig ausgewähltes Tag&times;mit Close ( ) Glyphe](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Standardmäßig ausgewähltes Tag&times;mit Close ( ) Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyph` |

**Ausgewähltes Tag&times;mit Close ( ) Glyphe: Hover-Status**

![Ausgewähltes Tag&times;mit Close ( ) -Glyphe auf Hover](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Ausgewähltes Tag&times;mit Close ( ) -Glyphe auf Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphHover` |
| Rahmen | `Tag.TagSelectedGlyphHoverBorder` |

**Ausgewähltes Tag&times;mit Close ( ) Glyphe: gedrückter Zustand**

![Ausgewähltes, gedrücktes&times;Tag mit Close ( ) Glyphe](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Ausgewähltes, gedrücktes&times;Tag mit Close ( ) Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphPressed` |
| Rahmen | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Toolfenster
Es ist nicht erforderlich, Toolfenster zu replizieren, da sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

![Werkzeugfenster (rot)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Werkzeugfenster (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die Mitmachen von Toolfenstern angezeigt werden soll. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

### <a name="tool-window-frame"></a>Toolfensterrahmen
Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.

![Werkzeugfensterrahmen (rot)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Werkzeugfensterrahmen (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ...  an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die Mitmachen von Toolfenstern angezeigt werden soll. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Angedocktes Werkzeugfenster**

![Angedocktes Werkzeugfenster](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Angedocktes Werkzeugfenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.ToolWindowBorder` |

**Schwebendes, fokussiertes Werkzeugfenster**

![Schwebendes, fokussiertes Werkzeugfenster](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Schwebendes, fokussiertes Werkzeugfenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |

**Schwebendes, unfokussiertes Werkzeugfenster**

![Schwebendes, unfokussiertes Werkzeugfenster](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Schwebendes, unfokussiertes Werkzeugfenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Toolbox-ähnliche Fenster
Die Toolbox ist eines der am häufigsten verwendeten häufig verwendeten Toolfenster in Visual Studio. Es ist im Wesentlichen ein Baum-Steuerelement mit einem speziellen Thema und Styling angewendet.

![Toolbox-ähnliches Fenster (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Toolbox-ähnliches Fenster (redline)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... wenn Sie ein Toolfenster entwerfen, das immer mit der Shell-Toolbox konsistent sein soll. | ... für alles, was der Toolbox-Benutzeroberfläche nicht ähnelt, oder wenn Sie sich nicht sicher sind, ob ihre Benutzeroberfläche Probleme hat, wenn sich die Farben der Shell-Toolbox ändern. |

**Toolbox-Knoten: Standardstatus**

![Standardmäßiger übergeordneter Standardknoten der Toolbox](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Standardmäßiger übergeordneter Standardknoten der Toolbox

![Untergeordneter Standard-Toolboxknoten](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Untergeordneter Standard-Toolboxknoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContent`<br />(Überschriften) |
| Hintergrund | `Environment.ToolWindowBackground`<br />(Einzelne Elemente oder ganzes Fenster, wenn keine verfügbaren Steuerelemente verfügbar sind) |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `Environment.ToolboxContent` |
| Vordergrund (Text) | `Environment.ToolboxContent` |

**Toolbox-Untergeordnete Knoten: Hover-Status**

![Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContentMouseOver`<br />(Nur Einzelelemente) |
| Rahmen | Keine |
| Vordergrund (Text) | `Environment.ToolboxContentMouseOver`<br />(Nur Einzelelemente) |

**Ausgewählte Toolbox-Knoten: fokussierter Zustand**

![Fokussierter, ausgewählter parenter Toolbox-Knoten](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Fokussierter, ausgewählter parenter Toolbox-Knoten

![Fokussierter, ausgewählter untergeordneter Toolbox-Knoten](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Fokussierter, ausgewählter untergeordneter Toolbox-Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | `TreeView.FocusVisualBorder`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Ausgewählte Toolbox-Knoten: unfokussierter Zustand**

![Ausgewählter, unfokussierter übergeordneter Toolbox-Knoten](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Ausgewählter, unfokussierter übergeordneter Toolbox-Knoten

![Ausgewählter, unfokussierter untergeordneter Toolbox-Knoten](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Ausgewählter, unfokussierter untergeordneter Toolbox-Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters
Der Titelleistenrahmen ist kein echter Rahmen, er ist eine dicke Linie über der Oberseite der Titelleiste. Es hat keinen Tokennamen für seinen unfokussierten Status.

![Titelleiste des Werkzeugfensters (rot)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Titelleiste des Werkzeugfensters (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die Mitmachen von Toolfenstern angezeigt werden soll. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Titelleiste mit Fokus**

![Titelleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Titelleiste mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarActiveGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.TitleBarActiveText` |
| Rahmen | `Environment.TitleBarActiveBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |
| Ziehpunkt | `Environment.TitleBarDragHandleActive` |

**Titelleiste ohne Fokus**

![Titelleiste ohne Fokus](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Titelleiste ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarInactiveGradientBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.TitleBarInactiveText` |
| Rahmen | Nicht zutreffend |
| Ziehpunkt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Schaltflächen für die Titelleiste des Werkzeugfensters
![Titelleistenschaltfläche (Rotlinie)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Titelleistenschaltfläche (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... für Schaltflächen, die in der Benutzeroberfläche angezeigt werden, die Farbtoken aus den Titelleisten des Werkzeugfensters verwendet. | ... für Schaltflächen, die an anderen Stellen angezeigt werden. |
| | ... in einer anderen als angegebenen Hintergrund-/Vordergrundkombination. |

**Fokussierte Titelleistenschaltflächen: Standardzustand**

![Standardschaltflächen für die Titelleiste](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Standardschaltflächen für die Titelleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Rahmen | Nicht zutreffend |

**Unfokussierte Titelleistenschaltflächen: Standardzustand**

![Standardschaltflächen für unfokussierte Titelleisten](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Standardschaltflächen für unfokussierte Titelleisten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Rahmen | Nicht zutreffend |

**Fokussierte Titelleistenschaltflächen: Hover-Status**

![Fokussierte Titelleistenschaltflächen auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Fokussierte Titelleistenschaltflächen auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverActiveBorder` |

**Unfokussierte Titelleistenschaltflächen: Hover-Status**

![Unfokussierte Titelleistenschaltflächen auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Unfokussierte Titelleistenschaltflächen auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Fokussierte Titelleistentasten: Gedrückter Zustand**

![Fokussierte Titelleistentasten beim Drücken](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Fokussierte Titelleistentasten beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

**Unfokussierte Titelleistentasten: Gedrückter Zustand**

![Unkonzentrierte Titelleistentasten beim Drücken](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Unkonzentrierte Titelleistentasten beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten
![Registerkarte "Werkzeugfenster" (rot)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Registerkarte "Werkzeugfenster" (rot)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die Mitmachen von Toolfenstern angezeigt werden soll. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Ausgewählt, Toolfenster-Registerkarte mit Fokus**

![Ausgewählt, Toolfenster-Registerkarte mit Fokus](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Ausgewählt, Toolfenster-Registerkarte mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedActiveText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

**Ausgewählt, Toolfenster-Registerkarte ohne Fokus**

![Ausgewählt, Toolfenster-Registerkarte ohne Fokus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Ausgewählt, Toolfenster-Registerkarte ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

**Registerkarte "Hintergrundwerkzeugfenster": Standardzustand**

![Registerkarte des Standard-Hintergrundwerkzeugfensters](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Registerkarte des Standard-Hintergrundwerkzeugfensters

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient stoppt auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabText` |
| Rahmen | `Environment.ToolWindowTabBorder` |

**Registerkarte "Hintergrundwerkzeugfenster": Hover-Status**

![Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient stoppt auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabMouseOverText` |
| Rahmen | `Environment.ToolWindowTabMouseOverBorder`<br />(Auf die gleiche Farbe wie Hintergrund eingestellt.) |

### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten

![Automatisches Ausblenden von Registerkarten (Rotlinie)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Automatisches Ausblenden von Registerkarten (Rotlinie)

| Verwenden... | Verwenden Sie nicht ... |
| --- | --- |
| ... an einer beliebigen Stelle, an der Sie eine Benutzeroberfläche erstellen, die Sie automatisch ausgeblendeten Werkzeugfenster-Registerkarten anpassen möchten. | ... für jede Benutzeroberfläche, die Sie nicht automatisch ändern möchten, wenn die Shell über eine Designaktualisierung verfügt. |

**Automatisches Ausblenden von Registerkarten: Standardzustand**

![Automatisch ausgeblendete Registerkarte, Standard](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Automatisch ausgeblendete Registerkarte, Standard

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.AutoHideTabText` |
| Rahmen | `Environment.AutoHideTabBorder` |

**Auto-Hide-Registerkarten: Hover-Status**

![Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Gradient stopps für dieses Token, das in der thematischen Benutzeroberfläche nicht verwendet wird.) |
| Vordergrund (Text) | `Environment.AutoHideTabMouseOverText` |
| Rahmen | `Environment.AutoHideTabMouseOverBorder` |
