---
title: "Freigegebene Farben für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 027e57a8d6ba4b4d317289cbdb74aa064de2ef4e
ms.contentlocale: de-de
ms.lasthandoff: 05/04/2017

---
# <a name="shared-colors-for-visual-studio"></a>Konsistente Farben für Visual Studio
Wenn Sie beim Entwerfen Benutzeroberfläche mit gängigen Visual Studio-Shell-Elementen, Sie möchten oder Ihr Benutzeroberflächenelement konsistent mit ähnlichen Features sein soll, verwenden Sie Tokennamen Paketdefinitionsdateien, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.  

In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezifische Informationen zum Zugreifen auf diese farbtoken finden Sie unter [der VSColor Dienst](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:  

-   **Verwenden Sie Tokennamen nach Funktion und nicht nach Farbe.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Die Funktionen des Kombinationsfelds und der Animation unterscheiden, und wenn das Kombinationsfeld ändert die Farbe zugeordnet ist, kann es nicht mehr sein, auf eine geeignete Farbe für Ihr Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.  

-   **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn es keine zugeordnete Textfarbe, verwenden Sie keine diese Hintergrundfarbe auf Oberflächen, auf denen erwartungsgemäß Text angezeigt. Andere Kombinationen aus Text- und Hintergrundfarben kommen die Benutzeroberfläche unlesbar.  

-   **Verwenden Sie steuerelementfarben, die für die jeweilige Position geeignet sind.** In bestimmten Status nicht einige Visual Studio-Steuerelemente auf separaten Rahmen- und Hintergrundfarben haben. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.  

> [!IMPORTANT]
> Verwenden Sie keine Token aus den Kategorien "Startseite" oder "Cider".  

## <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente

Wenn Sie die Funktion in eine Visual Studio-standardbefehlsleiste verwenden, müssen Sie den Zugriff auf formatierte Shell-Steuerelemente. Sie darf keine Vorlage neu erstellt diese gemeinsam verwendeten Steuerelemente. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.

### <a name="button-controls"></a>Schaltflächen-Steuerelemente

![Button-Steuerelement (rote Linie,)](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Schaltflächen im Dokument, das Sie in Visual Studio-Designs (hell, dunkel, Blau oder ein kontrastreiches Systemdesign) integrieren möchten. | ... für Schaltflächen, die für einen benutzerdefinierten Hintergrund angezeigt werden, die nicht Teil einer Visual Studio-Designs ist. |

**Schaltfläche: Standardstatus**

![Standard-Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Standard-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.Button` |
| Schaltflächenrahmen | `CommonControls.ButtonBorder` |

**Schaltfläche: Standardstatus**

![Standardschaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Standardschaltfläche

| Element | Tokenname: Category.color | 
| --- | --- | 
| Schaltfläche | `CommonControls.ButtonDefault` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDefault` |

**Die Taste: deaktiviert**  

![Deaktivierte Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Deaktivierte Schaltfläche  

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDisabled` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDisabled` |

**Schaltfläche: Hoverzustand**  

![Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Schaltfläche, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonHover` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderHover` |

**Schaltfläche: Zustand "gedrückt"**  

![Schaltfläche im gedrückten Zustand](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Schaltfläche im gedrückten Zustand  

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonPressed` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderPressed` |

**Schaltfläche: mit Fokus Zustand**  

![Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Schaltfläche mit Fokus  

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonFocused` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente  
![Kontrollkästchen ((rote Linie))](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Kontrollkästchen ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Kontrollkästchen-Steuerelemente auch innerhalb des Dokuments enthalten. | ... für Benutzeroberflächen, die ein Kontrollkästchen-Steuerelement enthalten ist. |

**Das Kontrollkästchen: Standardstatus**  

![Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackground` |
| Rahmen | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Das Kontrollkästchen: den deaktivierten Zustand**  

![Deaktiviertes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Deaktiviertes Kontrollkästchen  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundDisabled` |
| Rahmen | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Das Kontrollkästchen: Zeigen Sie mit Status**  

 ![Das Kontrollkästchen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Kontrollkästchen, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundHover` |
| Rahmen | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |  

**Das Kontrollkästchen: gedrückten Zustand**  

![Gedrücktes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Gedrücktes Kontrollkästchen  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Rahmen | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |  

**Das Kontrollkästchen: mit Fokus Zustand**  

![Kontrollkästchen mit Fokus](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Kontrollkästchen mit Fokus  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundFocused` |
| Rahmen | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Dropdownlisten und Kombinationsfelder Felder
![Drop-Dropdown-/Kombinationsfeld ((rote Linie))](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Drop-Dropdown-/Kombinationsfeld ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Dropdownlisten und Kombinationsfelder, die Felder im Dokument gut. | ... für Benutzeroberflächen, die ein Dropdownmenü oder ein Kombinationsfeld enthalten ist. |  
| | … for Befehlsleiste [Dropdownlisten](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) oder [Kombinationsfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Dropdownlisten und Kombinationsfelder Felder: Standardstatus**  

![Standardmäßige Drop-Dropdown-/Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Standardmäßige Drop-Dropdown-/Kombinationsfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackground` |
| Rahmen | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Trennzeichen | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackground` |

**Dropdownlisten und Kombinationsfelder Felder: den deaktivierten Zustand**  

![Deaktivierte Drop-Dropdown-/Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Deaktivierte Drop-Dropdown-/Kombinationsfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundDisabled` |
| Rahmen | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Dropdownlisten und Kombinationsfelder Felder: Zeigen Sie mit Status**  

![Drop Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundHover` |
| Rahmen | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Dropdownlisten und Kombinationsfelder Felder: gedrückten Zustand**  

![Drop Dropdown-/Kombinationsfeld, aufgerufen](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Drop Dropdown-/Kombinationsfeld, aufgerufen  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundPressed` |
| Rahmen | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Dropdownlisten und Kombinationsfelder, die Elementansicht Liste Felder: gedrückten Zustand**  

 ![Drop-Dropdown-/Kombinationsfeld gedrückt Listenansicht-Element](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Drop-Dropdown-/Kombinationsfeld gedrückt Listenansicht-Element  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund |  `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Elementtext | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Hintergrundschatten | `CommonControls.ComboBoxListBackgroundShadow` |

**Dropdownlisten und Kombinationsfelder Felder: mit Fokus Zustand**  

![Drop-Dropdown-/Kombinationsfeld mit Fokus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Drop-Dropdown-/Kombinationsfeld mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Dropdownlisten und Kombinationsfelder Felder: Eingabetext Auswahl**  

![Drop-Dropdown-/Kombinationsfeld texteingabeauswahl](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Drop-Dropdown-/Kombinationsfeld texteingabeauswahl  

| Element | Tokenname: Category.color |
| --- | --- |
| Hervorheben | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)  
Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.  

![Tabellarische Datenraster-Steuerelement ((rote Linie))](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabellarische Datenraster-Steuerelement ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für tabellarische oder Rastersteuerelemente. | ... für Benutzeroberflächen, die kein Tabellen- oder Rastersteuerelement Steuerelement ist. |

#### <a name="column-headers"></a>Spaltenheader  
Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.  

**Spaltenüberschrift: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.Default` |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Header.Glyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenüberschrift: Zeigen Sie mit Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.MouseOver` |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Header.MouseOverGlyph` |
| Rahmen | `Header.SeparatorLine` |

**Spaltenüberschrift: gedrückten Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Vordergrund (Text) | `CommonControls.CheckBoxBorderPressed` |
| Vordergrund (Glyphe) | `CommonControls.CheckBoxTextPressed` |
| Rahmen | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Listenansichtselemente  
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.  

**Liste der Elemente anzeigen: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Transparent |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Keine |

**Liste der Elemente anzeigen: Zustand "aktiv"**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActiveText` |
| Rahmen | Keine |

**Liste der Elemente anzeigen: inaktiver Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactiveText` |
| Rahmen | Keine |  

### <a name="ui-text"></a>Der Benutzeroberflächentext

#### <a name="instructional-text"></a>Hinweistext
Hinweistext bietet eine deutliche main Erklärung der Vorgehensweise in einem Dialogfeld oder Dokument.

![Standard-Anweisungstext](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Standard-Anweisungstext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundäre Anweisungstext
In der Dokumentseite mit vielen von Text und Steuerelementen verwendet einige Anweisungstext einen andere Farbe-Wert. Dies hilft, vermitteln, welche Informationen am wichtigsten ist, und verringern die gesamte Dichte Elemente der Benutzeroberfläche. (Siehe auch die im folgenden Abschnitt auf den Hinweistext.)

![Sekundäre Anweisungstext](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundäre Anweisungstext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Hinweistext
Hinweistext wird angezeigt, in ein leeres Steuerelement, das unter einem Steuerelement oder auf eine leere Dokumentoberfläche, um dem Benutzer anzuzeigen, was Sie als Nächstes tun. Sie können den Hinweistext mit Fenster- oder Steuerelement Hintergründe verwenden.

**Standard-Hinweistext**

![Standard-Hinweistext](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Standard-Hinweistext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

**Erforderliche Hinweistext**

![Erforderliche Hinweistext](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Erforderliche Hinweistext

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlRequiredHintText` |
| Hintergrund | `Environment.ControlRequiredBackground` |

**Text in Meldungsfeldern Steuerelement suchen**

> Finden Sie unter [suchen Felder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) für andere im Zusammenhang mit dem Suchsteuerelement farbtoken.

![Text in Meldungsfeldern Steuerelement suchen](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Text in Meldungsfeldern Steuerelement suchen

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Link  
Der Link ist ein Steuerelement, das ein paar Vordergrund-/Hintergrundfarbe besitzt. Verwenden Sie die Vordergrund-Linkfarbe, die auf dunklem, grauen und weißem Hintergrund ordnungsgemäß angezeigt werden, in allen Fällen. Wenn Sie nicht das farbtoken für das Linksteuerelement verwenden, sehen Sie die Standardsystemfarbe für "gedrückt", die rot blinken wird. Dies ist das Signal, dass das Steuerelement die richtige Umgebung Farbe-Token verwenden, befindet sich nicht.  

![Link ((rote Linie))](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Link ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie einen benutzerdefinierten Link erstellen müssen. | ... für Elemente, die einen Link ist nicht. |

**Link: Standardstatus**  

![Standard-hyperlink](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Standard-hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlink` |

**Hyperlink: Hoverzustand**

![Hyperlink, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hyperlink, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkHover` |

**Hyperlink: Zustand "gedrückt"**

![Gedrückte hyperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Gedrückte hyperlink  

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkPressed` |

**Hyperlink: Status "deaktiviert"**

![Deaktivierter Link](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Deaktivierter Link  

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infoleisten  
Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.  

![Infoleiste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infoleiste ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... benutzerdefinierten Infoleiste. | ... für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Infoleiste sind. |

**Infoleiste: Standardstatus**

![Standard-Infoleiste](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Standard-Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.InfoBarBackground` |
| Vordergrund (Text) | `InfoBar.InfoBar` |
| Rahmen | `InfoBar.InfoBarBorder` |

**Infoleiste schließen (&times;) Schaltfläche: Standardstatus**

![Standardmäßig schließen Infoleiste (&times;) Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Standardmäßig schließen Infoleiste (&times;) Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButton` |
| Rahmen | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Infoleiste schließen (&times;) Schaltfläche: Zeigen Sie mit Status**

![Infoleiste schließen (&times;) Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Infoleiste schließen (&times;) Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonHover` |
| Rahmen | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Infoleiste schließen (&times;) Schaltfläche: gedrückten Zustand**

![Infoleiste schließen gedrückt (&times;) Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Infoleiste schließen gedrückt (&times;) Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonDown` |
| Rahmen | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Infoleiste Hyperlink-Schaltfläche: Standardstatus**

![Infoleiste Hyperlink-Standardschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Infoleiste Hyperlink-Standardschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Infoleiste Hyperlink-Schaltfläche: Zeigen Sie mit Status**

![Infoleiste Hyperlink-Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Infoleiste Hyperlink-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit "Unterstreichen") |

**Infoleiste Hyperlink-Schaltfläche: gedrückten Zustand**

![Hyperlink-Schaltfläche gedrückt Infoleiste](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Hyperlink-Schaltfläche gedrückt Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit "Unterstreichen") |

**Infoleiste Inline Hyperlink (innerhalb eines Satzes): Standardstatus**

![Eingebettete Infoleiste Hyperlink Standardschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Eingebettete Infoleiste Hyperlink Standardschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Infoleiste Inline Hyperlink (innerhalb eines Satzes): Zeigen Sie mit Status**

![Infoleiste Inline Hyperlink-Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Infoleiste Inline Hyperlink-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit "Unterstreichen") |

**Infoleiste Inline Hyperlink (innerhalb eines Satzes): gedrückten Zustand**

![Infoleiste Inline Hyperlink-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Infoleiste Inline Hyperlink-Schaltfläche gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit "Unterstreichen") |

**Infoleiste Schaltfläche: Standardstatus**

![Infoleiste Standardschaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Infoleiste Standardschaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.Button` |
| Vordergrund (Text) | `InfoBar.Button` |
| Rahmen | `InfoBar.ButtonBorder` |

**Infoleiste Schaltfläche: Zeigen Sie mit Status**

![Infoleiste-Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Infoleiste-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseOver` |
| Vordergrund (Text) | `InfoBar.ButtonMouseOver` |
| Rahmen | `InfoBar.ButtonMouseOverBorder` |

**Infoleiste Schaltfläche: gedrückten Zustand**

![Infoleiste gedrückten Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Infoleiste gedrückten Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseDown` |
| Vordergrund (Text) | `InfoBar.ButtonMouseDown` |
| Rahmen | `InfoBar.ButtonMouseDownBorder` |

**Infoleiste Schaltfläche: den deaktivierten Zustand**

![Deaktivierte Infoleiste-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Deaktivierte Infoleiste-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonDisabled` |
| Vordergrund (Text) | `InfoBar.ButtonDisabled` |
| Rahmen | `InfoBar.ButtonDisabledBorder` |

**Infoleiste Schaltfläche: mit Fokus Zustand**

![Schaltfläche mit Fokus Infoleiste](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Schaltfläche mit Fokus Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonFocus` |
| Vordergrund (Text) | `InfoBar.ButtonFocus` |
| Rahmen | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Bildlaufleisten  
Bildlaufleisten sind von der Visual Studio-Umgebung formatiert, und Sie müssen keine Design angewendet werden muss. Sie können jedoch festlegen, dass die genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent in Bildlaufleisten angezeigt werden sollen.  

![Bildlaufleiste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Bildlaufleiste ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie Benutzeroberflächen erstellen, möchten Sie Visual Studio-Bildlaufleisten übereinstimmen. | ... für sämtliche Elemente nicht immer übereinstimmen sollen Bildlaufleisten-Benutzeroberfläche. |

**Bildlaufleiste: Standardstatus**  

![Standard-Bildlaufleiste](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Standard-Bildlaufleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbBackground` |

**Bildlaufleiste: Zeigen Sie mit Status**

![Bildlaufleiste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Bildlaufleiste, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbMouseOverBackground` |

*Bildlaufleiste: gedrückten Zustand**

![Bildlaufleiste gedrückt](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Bildlaufleiste gedrückt  

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbPressedBackground` |

**Bildlaufleiste Pfeil: Standardstatus**  

![Standard-Bildlaufpfeil-Leiste](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Standard-Bildlaufpfeil-Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowBackground`<br />(Festlegung auf dieselbe Farbe wie der Bildlaufleiste). |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyph` |

**Bildlaufleiste Pfeil: Zeigen Sie mit Status**

![Pfeil Bildlaufleiste darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Bildlaufleiste (Pfeil), wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowMouseOverBackground`<br />(Festlegung auf dieselbe Farbe wie der Bildlaufleiste). |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Bildlaufleiste Pfeil: gedrückten Zustand**  

![Pfeil Bildlaufleiste gedrückt](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Pfeil Bildlaufleiste gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowPressedBackground`<br />(Festlegung auf dieselbe Farbe wie der Bildlaufleiste). |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Suchfelder  
Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.  

Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:  

-   "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.  

-   "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.  

-   "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).  

-   "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.  

![Suchfeld ((rote Linie))](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Suchfeld ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie beim Entwerfen einer benutzerdefinierten Suchfeld. | ... für alles, was ein Suchfeld befindet sich nicht. |
| | Feld... für Elemente, die nicht immer die Suche übereinstimmen sollen UI ein. |

**Mit Fokus Eingabefeld suchen**

![Mit Fokus Eingabefeld suchen](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Mit Fokus Eingabefeld suchen  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedBackground` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | `SearchControl.FocusedBorder` |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Ohne Fokus, aktive Suche Eingabefeld**

![Eingabefeld Suche ohne Fokus](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Ohne Fokus, aktive Suche Eingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.SearchActiveBackground` |
| Vordergrund (Text) | `SearchControl.SearchActiveBackground` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Ohne Fokus, inaktive Suche Eingabefeld**

![Ohne Fokus, inaktive Suche Eingabefeld](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Ohne Fokus, inaktive Suche Eingabefeld  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Unfocused` |
| Vordergrund (Text) | `SearchControl.Unfocused` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Eingabefeld für hervorgehobene suchen (nur Text)**

![Hervorgehobene Suche Eingabefeld](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Hervorgehobene Suche Eingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Selection` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | Keine |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Eingabefeld für deaktivierte suchen**

![Eingabefeld für deaktivierte suchen](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Eingabefeld für deaktivierte suchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Disabled` |
| Vordergrund (Text) | `SearchControl.Disabled` |
| Rahmen | `SearchControl.DisabledBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Mit Fokus Suche (Aktionsschaltfläche)**

![Suche (Aktionsschaltfläche) mit Fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Mit Fokus Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Ohne Fokus Suche (Aktionsschaltfläche)**  

![Ohne Fokus Suche (Aktionsschaltfläche)](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Ohne Fokus Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | Nicht zutreffend |

**Suche (Aktionsschaltfläche) gedrückt**

![Suche (Aktionsschaltfläche) gedrückt](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Suche (Aktionsschaltfläche) gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.ActionButtonMouseDown` |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Rahmen | `SearchControl.ActionButtonMouseDownBorder` |

**Deaktivierte Suche (Aktionsschaltfläche)**

![Suche (Aktionsschaltfläche) deaktiviert](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Deaktivierte Suche (Aktionsschaltfläche)

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Rahmen | Keine |

**Dropdownschaltfläche mit Fokus suchen**

![Dropdownschaltfläche mit Fokus suchen](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Dropdownschaltfläche mit Fokus suchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.FocusedDropDownButtonBorder` |

**Ohne Fokus Suche Dropdown-Schaltfläche**

![Ohne Fokus Suche Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Ohne Fokus Suche Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.UnfocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.UnfocusedDropDownButtonBorder` |

**Aufgerufenes Dropdownelement-Schaltfläche "Suchen"**

![Aufgerufenes Dropdownelement-Schaltfläche "Suchen"](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Aufgerufenes Dropdownelement-Schaltfläche "Suchen"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.MouseDownDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Rahmen | `SearchControl.MouseDownDropDownButtonBorder` |

**Deaktiviert suchen die Dropdown Schaltfläche**

![Deaktiviert suchen die Dropdown Schaltfläche](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Deaktiviert suchen die Dropdown Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Rahmen | Keiner |

#### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld  
Die Dropdown-suchfeldmenü kann etwas komplexer als andere Dropdownmenüs in Visual Studio. Die "Empfohlene Suchbegriffe" und "Suchoptionen" können alleine oder zusammen im Menü angezeigt, und jede wird separat eingefärbt. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.  

![Die Dropdown-Suchliste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Die Dropdown-Suchliste ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie eine benutzerdefinierte Suche Dropdown-Liste erstellen. | ... für Dropdownlisten, die in anderen Kontexten angezeigt werden. |
| ... der richtigen Tokennamen für die entsprechenden Listenkomponenten. | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Dropdown-Listenelemente suchen**

| Element | Tokenname: Category.color |
| --- | --- |
| Rahmen | `SearchControl.PopupBorder` |
| Trennzeichen | `SearchControl.PopupSectionHeaderSeparator` |
| Schatten | `Environment.DropShadowBackground` |

**Sucht vorgeschlagen: Standardstatus**

![Standard empfohlene Suchbegriffe](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Standard empfohlene Suchbegriffe  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupItemText` |

**Sucht vorgeschlagen: Zeigen Sie mit Status**

![Empfohlene Suchbegriffe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Empfohlene Suchbegriffe, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupMouseOverItemText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: Standardstatus**

![Kontrollkästchen "Suche"](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Standard-Suchoptionen (Kontrollkästchen)  

![Suchoptionen](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Standard-Suchoptionen (Link)  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonText` |
| Headerhintergrund | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Headertext) | `SearchControl.PopupSectionHeaderText` |

**Suchoptionen: Zeigen Sie mit Status**

![Suchoptionen (Kontrollkästchen), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Suchoptionen (Kontrollkästchen), wenn darauf gezeigt wird  

![Suchoptionen (Link), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Suchoptionen (Link), wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: gedrückten Zustand**  

![Drücken die Suchoptionen (Kontrollkästchen)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Drücken die Suchoptionen (Kontrollkästchen)   

![Suchoptionen (Link) gedrückt](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Suchoptionen (Link) gedrückt  

| Element | Tokenname: Category.color |
| --- | --- |
| Kontrollkästchen-Hintergrund | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Linkhintergrund | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a>Strukturansichten  
Mehrere Toolfenster, einschließlich Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in gesteuert werden, die `TreeView` Kategorie. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.  

![Strukturansicht ((rote Linie))](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Strukturansicht ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... an beliebiger Stelle eine hierarchische Organisationsstruktur implementiert werden müssen. | ... für Elemente, die nicht mit einer Strukturansicht ähnlich sind. |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Strukturelement-Ansicht: Standardstatus**

![Anzeigen von Standardeintrag-Struktur](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Anzeigen von Standardeintrag-Struktur

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.Glyph` |
| Rahmen | Keine |

**Strukturelement-Ansicht: Zeigen Sie mit Status**

![Struktur-Ansichtselement, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Struktur-Ansichtselement, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |  
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.GlyphMouseOver` |
| Rahmen | Keine |

**Strukturelement-Ansicht: Ziehen Sie einen failoverstatus**

![Ziehen Sie Ansicht Strukturelement auf über](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Ziehen Sie Ansicht Strukturelement auf über  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.DragOverItem` |
| Vordergrund (Text) | `TreeView.DragOverItem` |
| Vordergrund (Glyphe) | `TreeView.DragOverItemGlyph` |
| Rahmen | Keine |

**Strukturelement-Ansicht: ausgewählt, mit Fokus Zustand**

![Element des ausgewählten und konzentriert sich Struktur anzeigen](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Element des ausgewählten und konzentriert sich Struktur anzeigen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Strukturelement-Ansicht: Zustand ausgewählten, ohne Fokus**  

![Ansichtselement Struktur ausgewählten und ohne Fokus](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Ansichtselement Struktur ausgewählten und ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Rahmen | Keine |

**Strukturelement-Ansicht: gezeigt, ausgewählt und mit Fokus Zustand**

![Struktur der ausgewählten und konzentriert sich Ansichtselement, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Struktur der ausgewählten und konzentriert sich Ansichtselement, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Strukturelement-Ansicht: darauf gezeigt wird, ausgewählt ist, und ohne Fokus Zustand**

![Ansichtselement Struktur ausgewählten und ohne Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Ansichtselement Struktur ausgewählten und ohne Fokus, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | Keine |

## <a name="shell-appearance"></a>Shell-Darstellung

### <a name="background"></a>Hintergrund  
Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Die obere und untere Hintergrundebene werden auf die gleiche Farbe in den hellen und dunklen Design festgelegt.  

![Visual Studio-Shell-Hintergrund ((rote Linie))](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio-Shell-Hintergrund ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Bereiche, die den Hintergrund der Visual Studio-Umgebung angepasst werden soll. | ... als Füllung für Bereiche, die keine hintergrundoberflächen sind. |
| | ... als Hintergrund auf vordergrundelemente platziert. |

**Untere Ebene Shell-Darstellung**

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Environment.EnvironmentBackground` |

**Obere Ebene Shell-Darstellung**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Befehlsablage  
Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.  

![Visual Studio-Befehlsablage ((rote Linie))](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio-Befehlsablage ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Bereiche, in denen Menüs oder Symbolleisten platziert. | ... für Bereiche, die nicht mit einer Befehlsablage ähnlich sind. |
|mit der richtigen Hintergrund-/Vordergrundfarbe Tokenname-Kombination. | |

**Befehl Regal-Menüleiste**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Befehl Regal Befehl Leiste **

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest-Designer  
Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Manifest-Designer ((rote Linie))](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest-Designer ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Designer, die den Manifest-Designer ähnlich sind. | ... Wenn Sie mehr als sechs Registerkarten haben. |
| anstelle allgemeiner Registerkarten-Steuerelemente am oberen Rand eines Editors innerhalb des Dokuments... ordnungsgemäß funktioniert. | ... für Benutzeroberflächen, die wie folgt den Manifest-Designer aufgebaut ist nicht. |

**Ausgewählte Registerkarte Manifest Designer: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.TabActive` |
| Rahmen | Keine |

**Beschreibung der ausgewählten Bereich der Manifest-Designers: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.DescriptionPane` |

**Manifest Designer ausgewählten Inhaltsseite: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Background` |
| Dialogfeld-Hilfetext | `ManifestDesigner.WatermarkText`<br />(Dieser Tokenname stimmt nicht seiner Funktion überein.) |

**Manifest-Designer-Registerkarte: Status deaktiviert**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Inactive` |

**Manifest-Designer-Registerkarte: Zeigen Sie mit Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Befehlsstrukturen  

###  <a name="BKMK_CommandMenus"></a>Menüs  
Menüs können an mehreren Stellen in Visual Studio auftreten: der Hauptmenüleiste, eingebettet in Dokument-oder Toolfenstern oder beim Rechtsklicken an verschiedenen Stellen der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.  

![Visual Studio-Menü ((rote Linie))](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio-Menü ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie ein benutzerdefiniertes Menü erstellen müssen.| ... als ausschließliche Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe. |
| ... Wenn Sie haben eine neue Benutzeroberflächenkomponente, die Visual Studio-Menüs abgestimmt werden sollen.| |

#### <a name="menu-titles"></a>Menütitel  
Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.  

![Menütitel ((rote Linie))](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menütitel ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie bei jedem erstellen ein benutzerdefinierten Menütitels. | ... für alles, was nicht immer den Menütitel übereinstimmen sollen. |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Menütitel: Standardstatus**

![Standard-Menütitel](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Standard-Menütitel

![Menütitel mit Glyphe, Standard](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Menütitel mit Glyphe, Standard

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuGlyph` |
| Rahmen | Keine |

**Menütitel: Zeigen Sie mit Status**  

![Menütitel, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Menütitel, wenn darauf gezeigt wird  

![Menütitel mit Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Menütitel mit Glyphe, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Rahmen | `Environment.CommandBarBorder` |

**Menütitel: gedrückten Zustand**  

![Gedrückte Menütitel](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Gedrückte Menütitel

![Menütitel mit Glyphe, gedrückt](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Menütitel mit Glyphe, gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder`<br />(Nur linken, oberen und rechten Seite.) |  

**Menütitel: den deaktivierten Zustand**  

![Deaktivierte Menütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Deaktivierte Menütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Keine |

#### <a name="menu-items"></a>Menüelemente
Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.  

![Menüelemente (rote Linie,)](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Verwenden Sie... | Empfohlen Sie nicht...  |
|---|---|
| ... für alle Dropdownlisten, die von einer Menü- oder Befehlsleiste gestartet. | ... für eine beliebige Dropdown-Liste in einem anderen Kontext. |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Menüelemente: Standardstatus**

![Standard-Menüelemente](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Standard-Menüelemente  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder` |
| Symbolkanal-Hintergrund | `Environment.CommandBarMenuIconBackground` |
| Trennzeichen | `Environment.CommandBarMenuSeparator` |
| Schatten | `Environment.DropShadowBackground` |

**Menüelemente: aktiviert und Zustände ausgewählt**  

![Menü, aktiviert](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Aktivierte Menüelement

![Menü, ausgewählt](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Ausgewählten Menüelements    

| Element | Tokenname: Category.color |
| --- | --- |
| Häkchen | `Environment.CommandBarCheckBox` |  
| Häkchenhintergrund | `Environment.CommandBarSelectedIcon` |  
| Symbolhintergrund | `Environment.CommandBarSelected` |
| Symbolrahmen | `Environment.CommandBarSelectedBorder` |

**Menüelemente: Zeigen Sie mit Status**  

![Menü gezeigt wird](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Menüelement, wenn darauf gezeigt wird

![Menü gezeigt wird überprüft](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Überprüft, Menüelement, wenn darauf gezeigt wird

![Menü Hover ausgewählt](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Ausgewählten Menüelements, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Text) | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxMouseOver` |
| Häkchenhintergrund | `Environment.CommandBarHoverOverSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarHoverOverSelected` |
| Symbolrahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menüelemente: den deaktivierten Zustand**  

![Menü, deaktiviert](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Deaktivierte Menüelement

![Menü deaktiviert (geprüft)](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Deaktivierte Menüelement mit Häkchen

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxDisabled` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Befehlsleisten  
Eine Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE, vor allem Kontrollvorgänge Befehlsablage und eingebettet in Tool- oder Dokumentfenster angezeigt werden.  

Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.  

![Befehl Befehlsleiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Befehlsleiste ((rote Linie))  

![(Rote Linie) der dokumentüberlauf-Schaltfläche](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Schaltfläche "Überlauf" ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... an Orten, in dem Sie eine eingebettete Befehlsleiste benötigen, sind aber nicht der standardmäßige Visual Studio Befehlsleisten-Standardimplementierung verwenden. | ... für Benutzeroberflächenelemente, die nicht mit einer Befehlsleiste ähnlich sind. |
| | ... für andere befehlsleistenkomponenten als, die diejenigen, für die Tokennamen festgelegt wurden. |

#### <a name="command-bar-groups"></a>Leiste Befehlsgruppen  
Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.  

![Befehlszeilengruppe (rote Linie)](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Befehlszeilengruppe ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |  
| ... an Orten, in dem Sie eine eingebettete Befehlsleiste benötigen, sind aber nicht der standardmäßige Visual Studio Befehlsleisten-Standardimplementierung verwenden. | ... für Benutzeroberflächenelemente, die nicht mit einer Befehlsleiste ähnlich sind. |
| | ... für andere befehlsleistenkomponenten als, die diejenigen, für die Tokennamen festgelegt wurden. |

**Befehlsleistengruppe: Standardstatus**  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Rahmen | `Environment.CommandBarToolBarBorder` |
| Ziehpunkt | `Environment.CommandBarDragHandle` |
| Trennzeichen | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Befehlssymbole  
![Befehlssymbol](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Symbol "Befehl" ((rote Linie))  

![Befehlssymbol mit text](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Befehlssymbol mit Text ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für alle Schaltflächen, die auf einer Befehlsleiste platziert werden. | ... für Steuerelemente, die ihren eigenen Tokennamen haben. |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Symbol "Befehl": Standardstatus**  

![Standardmäßiges Befehlssymbol](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Standardsymbol-Befehl

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Nicht zutreffend |

**Symbol "Befehl": Standardstatus, ausgewählt**

![Standardmäßig ausgewählten Befehlssymbol](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Standardmäßig ausgewählten Befehlssymbol  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextSelected` |
| Rahmen | `Environment.CommandBarSelectedBorder` |

**Symbol "Befehl": Zustand "den Fokus" oder "gezeigt wird**  

![Befehlssymbol, wenn darauf gezeigt wird oder den Fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Befehlssymbol, wenn darauf gezeigt wird oder den Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Rahmen | `Environment.CommandBarBorder` |

**Symbol "Befehl": Zustand "Hover" oder "den Fokus, ausgewählt**

![Ausgewählte Befehlssymbol Hover oder den Fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ausgewählte Befehlssymbol Hover oder den Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarHoverOverSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextHoverOverSelected` |
| Rahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Symbol "Befehl": gedrückten Zustand**  

![Gedrücktes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Gedrücktes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Rahmen | `Environment.CommandBarBorder` |

**Symbol "Befehl": Zustand deaktiviert**  

![Deaktiviertes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Deaktiviertes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |

####  <a name="BKMK_CommandComboBox"></a>Befehlsleiste-Kombinationsfelder

> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich keine enthält, verwenden Sie die farbtoken für [Dropdownlisten Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Befehlsleisten-Kombinationsfeld (rote Linie)](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Befehlsleisten-Kombinationsfeld ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Erstellung benutzerdefinierter Kombinationsfelder. | ... nur für die nicht gewünschten immer entsprechend den Befehl Befehlsleisten-Benutzeroberfläche. |
| ... für die Erstellung eines Befehlsleisten-Steuerelements, das in ein Kombinationsfeld vergleichbar ist. | ... Wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben. |

**Befehlsleiste Kombinationsfeld Eingabefeld: Standardstatus**

![Befehlsleiste Kombinationsfeld Eingabefeld](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Befehlsleiste Kombinationsfeld Eingabefeld  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxBackground` |
| Vordergrund (Text) | `Environment.ComboBoxText` |
| Rahmen | `Environment.ComboBoxBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Standardstatus**  

![Kombinationsfeld Feld Drop &#45; nach-unten-Schaltfläche](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Befehlsleisten-Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Glyphe) | `Environment.ComboBoxGlyph` |

**Befehlsleiste Dropdown-Liste: Standardstatus**

![Befehlsleiste Dropdown-Liste](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Befehlsleiste Dropdown-Liste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxPopupBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.ComboBoxPopupBorder` |

**Befehlsleiste Kombinationsfeld Eingabefeld: Zeigen Sie mit Status**  

![Befehlsleiste Kombinationsfeld Eingabefeld darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Befehlsleiste Kombinationsfeld Eingabefeld darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxMouseOverText` |
| Rahmen | `Environment.ComboBoxMouseOverBorder` |
| Trennzeichen | `Environment.ComboBoxMouseOverSeparator` |

 **Dropdown-Schaltfläche der Befehlsleiste: Zeigen Sie mit Status**  

![Befehlsleisten-Dropdown-Schaltfläche darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Befehlsleisten-Dropdown-Schaltfläche wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Befehlsleiste Dropdown-Liste: Zeigen Sie mit Status**

 ![Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Befehlsleiste Kombinationsfeld Eingabefeld: mit Fokus Zustand**  

![Mit Fokus Befehlsleiste Kombinationsfeld Eingabefeld](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Mit Fokus Befehlsleiste Kombinationsfeld Eingabefeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedBackground` |
| Vordergrund (Text) | `Environment.ComboBoxFocusedText` |
| Rahmen | `Environment.ComboBoxFocusedBorder` |
| Trennzeichen | `Environment.ComboBoxFocusedButtonSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: mit Fokus Zustand**  

![Mit Fokus Befehlsleiste Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Mit Fokus Befehlsleiste Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedButtonBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Befehlsleiste Kombinationsfeld Eingabefeld: gedrückten Zustand**  

![Befehlsleiste Kombinationsfeld Eingabefeld gedrückt](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Befehlsleiste Kombinationsfeld Eingabefeld gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseDownBackground` |
| Vordergrund (Text) | `Environment.ComboBoxMouseDownText` |
| Rahmen | `Environment.ComboBoxMouseDownBorder` |
| Trennzeichen | `Environment.ComboBoxMouseDownSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: gedrückten Zustand**

![Befehlsleiste Dropdown-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Befehlsleiste Dropdown-Schaltfläche gedrückt  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Befehlsleiste Kombinationsfeld Eingabefeld: den deaktivierten Zustand**  

![Deaktivierte Befehlsleiste Kombinationsfeld Eingabefeld](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Deaktivierte Befehlsleiste Kombinationsfeld Eingabefeld  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxDisabledBackground` |
| Vordergrund (Text) | `Environment.ComboBoxDisabledText` |
| Rahmen | `Environment.ComboBoxDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: den deaktivierten Zustand**  

![Deaktivierte Befehlsleiste Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a>Befehlsleiste Dropdowns

> [!IMPORTANT]
>  Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich enthält, verwenden Sie die farbtoken für [Kombinationsfelder Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Dropdown-Befehlsleisten ((rote Linie))](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Dropdown-Befehlsleisten ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... werden für die Erstellung benutzerdefinierter Dropdownlisten-Steuerelemente. | ... für Elemente, die ähnlich wie eine Dropdown-Liste ist nicht. |
| | ... für Kombinationsfelder oder unterteilte Schaltflächen. |   

**Befehlsleiste Dropdown-Auswahlfeld: Standardstatus**  

![Befehlsleiste Dropdownfeld Standardfelds](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Befehlsleiste Dropdownfeld Standardfelds  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownBackground` |
| Vordergrund (Text) | `DropDownText` |
| Rahmen | `DropDownBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Standardstatus**

![Standardmäßige Befehlsleisten-Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Standardmäßige Befehlsleisten-Dropdown-Schaltfläche  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.DropDownGlyph` |

**Befehlsleiste Dropdown-Liste: Standardstatus**

![Standard-Befehlsleiste Dropdown-Liste](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Standard-Befehlsleiste Dropdown-Liste  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownPopupBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.DropDownPopupBorder` |
| Schatten | `Environment.DropShadowBackground` |

**Befehlsleiste Dropdown-Auswahlfeld: Zeigen Sie mit Status**  

![Befehlsleiste Dropdownfeld Feld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Befehlsleiste Dropdownfeld Feld, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.DropDownMouseOverText` |
| Rahmen | `Environment.DropDownMouseOverBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseOverSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: Zeigen Sie mit Status**  

![Befehlsleisten-Dropdown-Schaltfläche darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Befehlsleisten-Dropdown-Schaltfläche wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseOverGlyph` |

**Befehlsleiste Dropdown-Liste: Zeigen Sie mit Status**  

![Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Befehlsleiste Dropdown-Liste, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Befehlsleiste Dropdown-Auswahlfeld: gedrückten Zustand**  

![Drop &#45; unten Auswahlfeld gedrückt](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Gedrückt Befehl Strich Dropdown-Auswahlfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseDownBackground` |
| Vordergrund (Text) | `Environment.DropDownMouseDownText` |
| Rahmen | `Environment.DropDownMouseDownBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseDownSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: gedrückten Zustand**

![Befehlsleiste Dropdown-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Befehlsleiste Dropdown-Schaltfläche gedrückt  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseDownGlyph` |

**Befehlsleiste Dropdown-Auswahlfeld: den deaktivierten Zustand**  

![Deaktivierte Befehlsleiste Dropdown-Auswahlfeld](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Auswahlfeld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownDisabledBackground` |
| Vordergrund (Text) | `Environment.DropDownDisabledText` |
| Rahmen | `Environment.DropDownDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: den deaktivierten Zustand**

![Deaktivierte Befehlsleiste Dropdown-Schaltfläche](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Deaktivierte Befehlsleiste Dropdown-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V |
| Vordergrund (Glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Befehlsleiste unterteilte Schaltflächen
Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Unterteilte Schaltfläche Dropdownlisten sind Implementierungen der [Menüs Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Trennschaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Befehlsleiste unterteilte Schaltfläche ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie beim Erstellen einer benutzerdefinierten unterteilten Schaltfläche. | für andere Arten von Schaltflächen... |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Befehlsleiste unterteilte Schaltfläche: Standardstatus**  

![Standard-Befehlsleiste unterteilte Schaltfläche](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Standard-Befehlsleiste unterteilte Schaltfläche  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keiner |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

**Befehlsleiste unterteilte Schaltfläche: Zeigen Sie mit Status**  

![Befehlsleiste unterteilte Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Befehlsleiste unterteilte Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | `Environment.CommandBarSplitButtonSeparator` |

**Befehlsleiste unterteilte Schaltfläche: gedrückten Zustand**  

![Gedrückte Befehlsleiste unterteilte Schaltfläche](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Gedrückte Befehlsleiste unterteilte Schaltfläche  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | Nicht zutreffend |

**Befehlsleiste unterteilte Schaltfläche: den deaktivierten Zustand**

![Deaktivierte Befehlsleiste unterteilte Schaltfläche](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Deaktivierte Befehlsleiste unterteilte Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Nicht zutreffend |
| Vordergrund (Text) | `Environment.ComboBoxItemTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Nicht zutreffend |
| Trennzeichen | Nicht zutreffend |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>"Weitere Optionen" und "Überlauf" Befehlsschaltflächen  
Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.  

![Befehlsleiste Schaltfläche "Weitere Optionen" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Befehlsleiste Schaltfläche "Weitere Optionen" ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für benutzerdefinierte "Weitere Optionen" oder "Überlauf" Schaltflächen. | ... für Schaltflächen, die ähnliche Funktionen zu einer "Weitere Optionen" oder "Überlauf" besitzen. |

**Befehlsleiste "Weitere Optionen" und "Überlauf" Schaltflächen: Standardstatus**  

![Optionsschaltfläche "Standard" Befehlsleiste "Weitere"](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Optionsschaltfläche "Standard" Befehlsleiste "Weitere"

![Standard Befehlsleisten-Schaltfläche "Überlauf"](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Standard Befehlsleisten-Schaltfläche "Überlauf"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsBackground` |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsGlyph` |

**Befehlsleiste "Weitere Optionen" und "Überlauf" Schaltflächen: Zeigen Sie mit Status**

![Befehlsleisten Sie "Weitere"-Optionsschaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Befehlsleisten Sie "Weitere"-Optionsschaltfläche, wenn darauf gezeigt wird  

![Befehl "Überlauf" Schaltfläche darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Befehl "Überlauf" Schaltfläche darauf gezeigt wird   

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Befehlsleiste "Weitere Optionen" und "Überlauf" Schaltflächen: gedrückten Zustand**  

![Befehlsleiste "Weitere"-Optionsschaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Befehlsleiste "Weitere"-Optionsschaltfläche gedrückt  

!["Überlauf" gedrückten](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Gedrückt Befehlsleisten-Schaltfläche "Überlauf"  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Dokumentfenster  
Besteht keine Notwendigkeit zum Replizieren von Dokumentfenstern, weil sie von Visual Studio-Umgebung bereitgestellt sind. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  

Wenn Sie Dokumentfenster-farbtoken verwenden, achten Sie darauf, dass Sie diese nur für ähnliche Elemente und immer paarweise verwenden. Wenn Sie dies tun, erhalten Sie möglicherweise unerwartete Ergebnisse auf der Benutzeroberfläche.  

### <a name="document-window-frames"></a>Dokument Fensterrahmen  
Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Bei einem Dokumentfenster außerhalb der IDE unverankert ist, sie weiterhin in einen Dokumentursprung befindet, und enthält Hintergrund, Rahmen, Text und Farben, die identisch sind, wenn er Teil der IDE ist. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.  

![Angedocktes Dokumentfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Angedocktes Dokumentfenster ((rote Linie))  

![Unverankertes Dokumentfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Unverankertes Dokumentfenster ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie das Dokumentfenster abstimmen möchten. | ... für Benutzeroberflächen, die Sie nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Dokumentfenster angedockt oder unverankert: Standardstatus**  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Hängt vom Dokumenttyp ab. |
| Vordergrund (Text) | Hängt vom Dokumenttyp ab. |
| Rahmen | `Environment.ToolWindowBorder` |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: Standardstatus**

![Standardmäßige konzentriert, Gleitkomma dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Standardmäßige konzentriert, Gleitkomma dokumentfensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Auf transparent festgelegt) |

**Ohne Fokus, Gleitkomma dokumentfensterrahmen: Standardstatus**  

![Standard ohne Fokus, Gleitkomma dokumentfensterrahmen](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Standard ohne Fokus, Gleitkomma dokumentfensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Rahmen | `Environment.MainWindowInactiveBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Auf transparent festgelegt) |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: Zeigen Sie mit Status**

![Mit Fokus, dokumentfensterrahmen Gleitkommawert, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Mit Fokus, dokumentfensterrahmen Gleitkommawert, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Ohne Fokus, Gleitkomma dokumentfensterrahmen: Zeigen Sie mit Status**  

![Ohne Fokus, Gleitkomma dokumentfensterrahmen darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Ohne Fokus, Gleitkomma dokumentfensterrahmen darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Mit Fokus, Gleitkomma dokumentfensterrahmen: gedrückten Zustand**  

![Mit Fokus, Gleitkomma dokumentfensterrahmen drücken](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Mit Fokus, Gleitkomma dokumentfensterrahmen drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Dokumentregisterkarten  
Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.  

![Dokumentieren von Registerkarten ((rote Linie))](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Dokumentieren von Registerkarten ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die auf Dokumentregisterkarten abgestimmt und Designaktualisierungen oder neue Designfarben automatisch ausgewählt werden sollen. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn die Shell einer designaktualisierung werden sollen. |

#### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten  
Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:  

-   Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.  

-   Hintergrundregisterkarten sind Dokumentregisterkarten, die nicht der aktuell ausgewählten Registerkarte entsprechen. Sobald auf die Registerkarte geklickt wird, wird sie zur ausgewählten Registerkarte, die alle Hintergrund-, Rahmen- und Textfarben von den Tokennamen übernimmt.  

![Registerkarte "Dokument öffnen" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Registerkarte "Dokument öffnen" ((rote Linie))

| Verwenden Sie...  | Empfohlen Sie nicht... |
| --- | --- |
| ... werden für die Erstellung benutzerdefinierter Dokumentregisterkarten. | ... für Registerkarten der vorläufigen (Vorschau). |
| | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Registerkarte "ausgewählte, mit Fokus Dokument"**  

![Registerkarte "ausgewählte, mit Fokus Dokument"](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Registerkarte "ausgewählte, mit Fokus Dokument"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabSelectedGradientTop`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.FileTabSelectedText` |
| Rahmen | `Environment.FileTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabDocumentBorderBackground` |

**Registerkarte "aktiviert wird, ohne Fokus Dokument"**

![Registerkarte "aktiviert wird, ohne Fokus Dokument"](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Registerkarte "aktiviert wird, ohne Fokus Dokument"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabInactiveGradientTop`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.FileTabInactiveText` |
| Rahmen | `Environment.FileTabInactiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabInactiveDocumentBorderBackground` |

**Registerkarte "Dokument" im Hintergrund: Standardstatus**  

![Registerkarte "Dokument" der Standard-Hintergrund](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Registerkarte "Dokument" der Standard-Hintergrund  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabBackground` |
| Vordergrund (Text) | `Environment.FileTabText` |
| Rahmen | `Environment.FileTabBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Registerkarte "Dokument" im Hintergrund: Zeigen Sie mit Status**  

![Registerkarte "Dokument Hintergrundvorschau"](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Registerkarte "Dokument Hintergrundvorschau"  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabHotGradientTop`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.FileTabHotText` |
| Rahmen | `Environment.FileTabHotBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

#### <a name="preview-tab"></a>Vorschauregisterkarte  
So genannte "vorläufige" Registerkarte aus. Die Vorschauregisterkarte wird auf der rechten Seite des Dokument-Registerkartenkanals angezeigt, wenn der Benutzer auf ein Element im Toolfenster des Projektmappen-Explorers klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.  

![Registerkarte "Vorschau" ((rote Linie))](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Registerkarte "Vorschau" ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... überall vorläufigen erstellen in der Vorschau anzeigen und ein Element mit die aktuellen Vorschau Registerkarte Farbe übereinstimmen soll. | ... für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau). |
| | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Registerkarte "Vorschau von fokussierten, ausgewählten"**  

![Registerkarte "Vorschau von fokussierten, ausgewählten"](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Registerkarte "Vorschau von fokussierten, ausgewählten"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedActive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Ohne Fokus, ausgewählte vorschauregisterkarte**  

![Ohne Fokus, ausgewählte vorschauregisterkarte](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Ohne Fokus, ausgewählte vorschauregisterkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Hintergrund-/ vorschauregisterkarte: Standardstatus**  

![Standardmäßige Hintergrund-/ vorschauregisterkarte](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Standardmäßige Hintergrund-/ vorschauregisterkarte  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalInactiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Hintergrund-/ vorschauregisterkarte: Zeigen Sie mit Status**  

![Registerkarte "Vorschau Hintergrundvorschau"](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Registerkarte "Vorschau Hintergrundvorschau"  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalHover` |
| Vordergrund (Text) | `Environment.FileTabProvisionalHoverForeground` |
| Rahmen | `Environment.FileTabProvisionalHoverBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

#### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche  
Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dokument Überlauf Dropdown-Menü, die mithilfe der [Menü Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) Farben, zeigt eine Liste aller geöffneten Dokumente, angezeigt und ausgeblendet, und der Überlauf-Glyphe ändert, je nachdem, ob alle geöffneten Dokumente im registerkartenkanal angezeigt werden.  

![Dokumentüberlauf-Schaltfläche ((rote Linie))](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Dokumentüberlauf-Schaltfläche ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie beim Erstellen einer benutzerdefinierten dokumentüberlauf-Schaltfläche. | ... für Benutzeroberflächen, die nicht mit einer Überlaufschaltfläche ähnlich sind. |
| | … for Überlauf Befehlsleistenschaltflächen. |

**Dokumentüberlauf-Schaltfläche: Standardstatus**  

![Standardmäßige dokumentüberlauf-Schaltfläche](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Standardmäßige dokumentüberlauf-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Rahmen | Nicht zutreffend |

**Dokumentüberlauf-Schaltfläche: Zeigen Sie mit Status**

![Dokumentüberlauf-Schaltfläche wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Dokumentüberlauf-Schaltfläche: gedrückten Zustand**  

![Dokumentüberlauf-Schaltfläche auf drücken](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Dokumentüberlauf-Schaltfläche auf drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Tagging  
Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.  

![In Visual Studio-Kennzeichnung ((rote Linie))](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />In Visual Studio-Kennzeichnung ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Benutzeroberflächen, die Tags unterstützen. | für alle anderen Arten von Benutzeroberflächenelementen... |

#### <a name="tags"></a>Tags  

**Tag: Standardstatus**

![Standard-tag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Standard-tag

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Tag.Background` |
| Vordergrund (Text) | `Tag.Background` |

**Tag: Hoverzustand**  

![Tag, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | `Tag.HoverBackground` |
| Vordergrund (Text) | `Tag.HoverBackgroundText` |

**Tag: gedrückten Zustand**

![Gedrückt tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Gedrückt tag  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.PressedBackground` |
| Vordergrund (Text) | `Tag.PressedBackgroundText` |

**Tag: ausgewählten Zustand.**

![Ausgewählte tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Ausgewählte tag  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.SelectedBackground` |
| Vordergrund (Text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Schließen (&times;) tag Glyphe

**Schließen (&times;) tag Glyphe: Standardstatus**

![Standardmäßig schließen (&times;) tag Glyphe](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Standardmäßig schließen (&times;) tag Glyphe

| Element | Tokenname: Category.color |
| --- | --- |  
| Hintergrund | N/V |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyph` |

**Schließen (&times;) tag Glyphe: Zeigen Sie mit Status**

![Schließen (&times;) Glyphe zu kennzeichnen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Schließen (&times;) Glyphe zu kennzeichnen, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphHover` |
| Rahmen | `Tag.TagHoverGlyphHoverBorder` |

**Schließen (&times;) tag Glyphe: gedrückten Zustand**

![Gedrückt schließen (&times;) tag Glyphe](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Gedrückt schließen (&times;) tag Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphPressed` |
| Rahmen | `Tag.TagHoverGlyphPressedBorder` |

**Ausgewählte Tag mit schließen (&times;) Glyphe: Standardstatus**

![Standard ausgewählte Tag mit schließen (&times;) Symbol](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Standard ausgewählte Tag mit schließen (&times;) Symbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyph` |

**Ausgewählte Tag mit schließen (&times;) Glyphe: Zeigen Sie mit Status**  

![Ausgewählte Tag mit schließen (&times;) Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Ausgewählte Tag mit schließen (&times;) Glyphe, wenn darauf gezeigt wird  


| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphHover` |
| Rahmen | `Tag.TagSelectedGlyphHoverBorder` |

**Ausgewählte Tag mit schließen (&times;) Glyphe: gedrückten Zustand**  

![Ausgewählt, die gedrückt Tag mit schließen (&times;) Symbol](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Ausgewählt, die gedrückt Tag mit schließen (&times;) Symbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphPressed` |
| Rahmen | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Toolfenster  
Besteht keine Notwendigkeit zum Replizieren der Toolfenster, weil sie von Visual Studio-Umgebung bereitgestellt sind. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  

![Toolfenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Toolfenster ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie Toolfenster abstimmen möchten. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

### <a name="tool-window-frame"></a>Toolfensterrahmen  
Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.  

![Toolfenster, Rahmen ((rote Linie))](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Toolfenster, Rahmen ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie Toolfenster abstimmen möchten. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Angedocktes Fenster**  

![Angedocktes Fenster](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Angedocktes Fenster  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.ToolWindowBorder` |

**Unverankert, mit Fokus Toolfenster**

![Unverankert, mit Fokus Toolfenster](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Unverankert, mit Fokus Toolfenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |

**Unverankert, Toolfenster ohne Fokus**  

![Unverankert, Toolfenster ohne Fokus](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Unverankert, Toolfenster ohne Fokus  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Toolbox-ähnliche windows
Die Toolbox ist eine der am häufigsten verwendeten allgemeinen Toolfenster in Visual Studio. Es ist im Wesentlichen ein Strukturansicht-Steuerelement ein bestimmtes Design und ein bestimmter Stil angewendet.  

![Toolbox-Fenster ((rote Linie))](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Toolbox-Fenster ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Wenn Sie beim Entwerfen eines Toolfensters, das immer mit der Shell-Toolbox konsistent sein sollen. | ... für Ähnlichkeit mit der Werkzeugkasten-Benutzeroberfläche nicht, oder wenn Sie nicht sicher sind, ob Ihre Benutzeroberfläche Probleme Änderung der Farben die Shell-Toolbox verfügen. |

**Toolbox-Knoten: Standardstatus**

![Standard-Toolbox übergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Standard-Toolbox übergeordneten Knoten

![Standard-Toolbox, untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Standard-Toolbox, untergeordneter Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContent`<br />(Rubriken) |
| Hintergrund | `Environment.ToolWindowBackground`<br />(Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind) |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `Environment.ToolboxContent` |
| Vordergrund (Text) | `Environment.ToolboxContent` |

**Toolbox untergeordneten Knoten: Zeigen Sie mit Status**

![Toolbox, untergeordneter Knoten darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContentMouseOver`<br />(Nur einzelne Elemente) |
| Rahmen | Keine |
| Vordergrund (Text) | `Environment.ToolboxContentMouseOver`<br />(Nur einzelne Elemente) |

**Toolbox Knoten ausgewählt: mit Fokus Zustand**

![Toolbox von fokussierten, ausgewählten übergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Toolbox von fokussierten, ausgewählten übergeordneten Knoten  

![Toolbox von fokussierten, ausgewählten untergeordneten Knoten](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Toolbox von fokussierten, ausgewählten untergeordneten Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |
| Rahmen | `TreeView.FocusVisualBorder`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |
| Vordergrund (Text) | `TreeView.SelectedItemActive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |

**Toolbox Knoten ausgewählt: ohne Fokus Zustand**

![Aktiviert wird, ohne Fokus Toolbox übergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Aktiviert wird, ohne Fokus Toolbox übergeordneter Knoten  

![Die untergeordneten Knoten ausgewählt, ohne Fokus toolbox](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Die untergeordneten Knoten ausgewählt, ohne Fokus toolbox  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |
| Vordergrund (Text) | `TreeView.SelectedItemInactive`<br />Von [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie |

### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters  
Der Rahmen der Titelleiste wird nicht echter Rahmen, es ist eine starke Linie am oberen Rand der Titelleiste. Es keinen Tokennamen für Datenbankzustands ohne Fokus.  

![Titelleiste des Toolfensters ((rote Linie))](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Titelleiste des Toolfensters ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie Toolfenster abstimmen möchten. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Titelleiste mit Fokus**

![Titelleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Titelleiste mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarActiveGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarActiveText` |
| Rahmen | `Environment.TitleBarActiveBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |
| Ziehpunkt | `Environment.TitleBarDragHandleActive` |

**Titelleiste ohne Fokus**  

![Titelleiste ohne Fokus](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Titelleiste ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarInactiveGradientBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarInactiveText` |
| Rahmen | Nicht zutreffend |
| Ziehpunkt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Tool Fenster Titelleisten-Schaltflächen  
![Schaltfläche Titelleiste ((rote Linie))](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Schaltfläche Titelleiste ((rote Linie))  

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... für Schaltflächen auf der Benutzeroberfläche, die farbtoken aus den Toolfenster-Titelleisten verwendet. | ... für Schaltflächen, die an anderer Stelle angezeigt. |
| | ... in eine beliebige andere als die angegebene Hintergrund-/Vordergrundfarbe-Kombination. |

**Mit Fokus Titelleisten-Schaltflächen: Standardstatus**

![In der Standardeinstellung fokussierte Titelleisten-Schaltflächen](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />In der Standardeinstellung fokussierte Titelleisten-Schaltflächen  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Rahmen | Nicht zutreffend |

**Ohne Fokus Titelleisten-Schaltflächen: Standardstatus**

![In der Standardeinstellung ohne Fokus Titelleisten-Schaltflächen](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />In der Standardeinstellung ohne Fokus Titelleisten-Schaltflächen    

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Rahmen | Nicht zutreffend |

**Mit Fokus Titelleisten-Schaltflächen: Zeigen Sie mit Status**  

![Mit Fokus Titelleisten-Schaltflächen darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Mit Fokus Titelleisten-Schaltflächen darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverActiveBorder` |

**Ohne Fokus Titelleisten-Schaltflächen: Zeigen Sie mit Status**  

![Ohne Fokus Titelleisten-Schaltflächen darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Ohne Fokus Titelleisten-Schaltflächen darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Mit Fokus Titelleisten-Schaltflächen: gedrückten Zustand**

![Mit Fokus Titelleisten-Schaltflächen drücken](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Mit Fokus Titelleisten-Schaltflächen drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

**Ohne Fokus Titelleisten-Schaltflächen: gedrückten Zustand**

![Ohne Fokus Titelleisten-Schaltflächen drücken](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Ohne Fokus Titelleisten-Schaltflächen drücken  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten  
![Toolfenster-Registerkarte ((rote Linie))](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Toolfenster-Registerkarte ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie Toolfenster abstimmen möchten. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Ausgewählte, fokussierte Toolfenster-Registerkarte**

![Ausgewählte, fokussierte Toolfenster-Registerkarte](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Ausgewählt, Toolfenster-Registerkarte mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedActiveText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Aktiviert wird, ohne Fokus Toolfenster-Registerkarte**  

![Aktiviert wird, ohne Fokus Toolfenster-Registerkarte](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Ausgewählt, Toolfenster-Registerkarte ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |

**Hintergrundregisterkarte im Toolfenster: Standardstatus**

![Standardmäßige Hintergrundregisterkarte im Toolfenster](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Standardmäßige Hintergrundregisterkarte im Toolfenster  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Festgelegte Farbverlaufsstopps auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabText` |
| Rahmen | `Environment.ToolWindowTabBorder` |

**Hintergrundregisterkarte im Toolfenster: Zeigen Sie mit Status**

![Hintergrundregisterkarte im Toolfenster darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Festgelegte Farbverlaufsstopps auf denselben Farbwert in Visual Studio 2013.) |
| Vordergrund (Text) | `Environment.ToolWindowTabMouseOverText` |
| Rahmen | `Environment.ToolWindowTabMouseOverBorder`<br />(Auf dieselbe Farbe wie der Hintergrund festgelegt.) |  

### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten  

![Automatisch ausgeblendete Registerkarten ((rote Linie))](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")automatisch ausgeblendete Registerkarten ((rote Linie))

| Verwenden Sie... | Empfohlen Sie nicht... |
| --- | --- |
| ... Sie an einer beliebigen Stelle erstellen Benutzeroberfläche, die Sie automatisch ausgeblendete Toolfenster-Registerkarten abstimmen möchten. | ... für Benutzeroberflächen, die nicht automatisch ändern, wenn sollen designaktualisierung der Shell ein. |

**Automatisch ausgeblendete Registerkarten: Standardstatus**  

![Automatisch ausgeblendete Registerkarte, Standard](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Automatisch ausgeblendete Registerkarte, Standard

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabText` |
| Rahmen | `Environment.AutoHideTabBorder` |

**Automatisch ausgeblendete Registerkarten: Zeigen Sie mit Status**

![Registerkarte "automatisch im Hintergrund", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird  

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Farbverlaufsstopps für dieses Token in Benutzeroberflächen mit Designs nicht verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabMouseOverText` |
| Rahmen | `Environment.AutoHideTabMouseOverBorder` |

