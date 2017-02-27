---
title: "Freigegebene Farben f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Freigegebene Farben f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie Ihre Benutzeroberfläche mit gängigen Visual Studio Shell-Elementen gestalten möchten oder Ihr Benutzeroberflächenelement konsistent mit ähnlichen Features sein soll, können Sie die Tokennamen aus den Paketdefinitionsdateien verwenden, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.  
  
 In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:  
  
-   **Verwenden Sie token basierend auf der Funktion, nicht auf die Farbe an sich.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Das Kombinationsfeld und die Animation erfüllen unterschiedliche Funktionen, und wenn sich die dem Kombinationsfeld zugeordnete Farbe ändert, eignet sie sich möglicherweise nicht mehr für Ihr Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.  
  
-   **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination aus.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn keine zugeordnete Textfarbe vorhanden ist, sollte diese Hintergrundfarbe auf Oberflächen, auf denen erwartungsgemäß Text angezeigt wird, nicht verwendet werden. Andere Kombinationen aus Text- und Hintergrundfarbe können dazu führen, dass die Benutzeroberfläche unlesbar wird.  
  
-   **Verwenden Sie die Steuerelement-Farben, die für ihren Standort geeignet sind.** Für bestimmte Zustände einiger Visual Studio-Steuerelemente sind keine separaten Rahmen- und Hintergrundfarben verfügbar. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.  
  
> [!IMPORTANT]
>  Verwenden Sie keine Token finden Sie in den Kategorien "Startseite" oder "Cider".  
  
## <a name="command-structures"></a>Befehlsstrukturen  
  
###  <a name="a-namebkmkcommandmenusa-menus"></a><a name="BKMK_CommandMenus"></a> Menüs  
 Menüs können an mehreren Stellen in Visual Studio auftreten: der Hauptmenüleiste eingebettet im Dokument oder Tool Windows oder auf mit der rechten Maustaste an verschiedenen Stellen in der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.  
  
 ![Menü (rote Linie)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")  
  
 Empfohlen...  
 -   für die Erstellung eines benutzerdefinierten Menüs  
  
-   für eine neue Benutzeroberflächenkomponente, die auf die Visual Studio-Menüs abgestimmt werden soll.  
  
 Nicht empfohlen...  
 als ausschließliche Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe.  
  
#### <a name="menu-title"></a>Menütitel  
 Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.  
  
 ![Menütitel (rote Linie)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")  
  
 Empfohlen...  
 für die Erstellung eines benutzerdefinierten Menütitels  
  
 Nicht empfohlen...  
 -   für Elemente, die nicht grundsätzlich auf den Menütitel abgestimmt sein sollen  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Standard für Menütitel](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")  
  
 **Menütitel**  
  
 Hintergrund  
  
 Keiner  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 ![Menütitel mit Standardglyphe](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")  
  
 **Menütitel mit Glyphe**  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarMenuGlyph`  
  
 Rahmen  
  
 Keine  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menütitel, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")  
  
 **Menütitel**  
  
 Hintergrund  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextHover`  
  
 ![Menütitel mit Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")  
  
 **Menütitel mit Glyphe**  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarMenuMouseOverGlyph`  
  
 Rahmen  
  
 `Environment.CommandBarBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menütitel, aufgerufen](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")  
  
 **Menütitel**  
  
 Hintergrund  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 ![Menütitel mit Glyphe, aufgerufen](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")  
  
 **Menütitel mit Glyphe**  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarMenuMouseDownGlyph`  
  
 Rahmen  
  
 `Environment.CommandBarMenuBorder`  
  
 Nur linke, obere und rechte Seite  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menütitel mit Standardglyphe in deaktiviertem Zustand](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")  
  
 **Menütitel mit Glyphe**  
  
 Hintergrund  
  
 Keiner  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextInactive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarTextInactive`  
  
 Rahmen  
  
 Keiner  
  
#### <a name="menu"></a>Menü  
 Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.  
  
 ![Menüelemente (rote Linie)](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")  
  
 Empfohlen...  
 für alle Dropdownlisten, die von einer Menü- oder Befehlsleiste geöffnet werden.  
  
 Nicht empfohlen...  
 -   für Dropdownlisten, die in einem anderen Kontext vorkommen  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menüstandard](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")  
  
 **Im Menü**  
  
 Hintergrund  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 Vordergrund (Untermenü-Glyphe)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 Rahmen  
  
 `Environment.CommandBarMenuBorder`  
  
 Symbolkanal-Hintergrund  
  
 `Environment.CommandBarMenuIconBackground`  
  
 Trennzeichen  
  
 `Environment.CommandBarMenuSeparator`  
  
 Schatten  
  
 `Environment.DropShadowBackground`  
  
 ![Menü, aktiviert](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")  
  
 **Aktiviert**  
  
 Häkchen  
  
 `Environment.CommandBarCheckBox`  
  
 Häkchenhintergrund  
  
 `Environment.CommandBarSelectedIcon`  
  
 ![Menü, ausgewählt](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")  
  
 **Ausgewählt**  
  
 Symbolhintergrund  
  
 `Environment.CommandBarSelected`  
  
 Symbolrahmen  
  
 `Environment.CommandBarSelectedBorder`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menü, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")  
  
 **Menüelement**  
  
 Hintergrund  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Vordergrund (Untermenü-Glyphe)  
  
 `Environment.CommandBarMenuMouseOverSubmenuGlyph`  
  
 ![Menü, wenn darauf gezeigt wird (aktiviert)](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")  
  
 **Aktiviert**  
  
 Häkchen  
  
 `Environment.CommandBarCheckBoxMouseOver`  
  
 Häkchenhintergrund  
  
 `Environment.CommandBarHoverOverSelectedIcon`  
  
 ![Menü, wenn darauf gezeigt wird (ausgewählt)](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")  
  
 **Ausgewählt**  
  
 Symbolhintergrund  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Symbolrahmen  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Menü, deaktiviert](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")  
  
 Menüelement  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextInactive`  
  
 Vordergrund (Untermenü-Glyphe)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 ![Menü, deaktiviert (geprüft)](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")  
  
 Aktiviert  
  
 Häkchen  
  
 `Environment.CommandBarCheckBoxDisabled`  
  
 Häkchenhintergrund  
  
 `Environment.CommandBarSelectedIconDisabled`  
  
### <a name="command-bar"></a>Befehlsleiste  
 Die Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE vorkommen, vor allem in der Befehlsablage und eingebettet in Tool- oder Dokumentfenster.  
  
 Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.  
  
 ![Befehlszeile (rote Linie)](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Schaltfläche "Überlauf" (rote Linie)](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
 Nicht empfohlen...  
 -   für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  
  
-   für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
#### <a name="command-bar-group"></a>Befehlsleistengruppe  
 Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.  
  
 ![Befehlszeilengruppe (rote Linie)](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
 Nicht empfohlen...  
 -   für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  
  
-   für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
 **Standard** (kein weiterer Zustand)  
  
 Element  
  
 Tokenname: Category.color  
  
 Hintergrund  
  
 `Environment.CommandBarGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Rahmen  
  
 `Environment.CommandBarToolBarBorder`  
  
 Ziehpunkt  
  
 `Environment.CommandBarDragHandle`  
  
 Trennzeichen  
  
 `Environment.CommandBarToolBarSeparator`  
  
 `Environment.CommandBarToolBarSeparatorHighlight`  
  
#### <a name="command-icons"></a>Befehlssymbole  
 ![Rote Linie – Befehlssymbol](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Rote Linie – Befehlssymbol](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Empfohlen...  
 für alle Schaltflächen, die auf einer Befehlsleiste platziert werden.  
  
 Nicht empfohlen...  
 -   für Steuerelemente, die ihren eigenen Tokennamen haben  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Standardmäßiges Befehlssymbol](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")  
  
 **Default**  
  
 Hintergrund  
  
 N/V (erbt vom Befehlsleisten-Hintergrund)  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 ![Standardmäßiges Befehlssymbol ausgewählt](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")  
  
 **Ausgewählt**  
  
 Hintergrund  
  
 `Environment.CommandBarSelected`  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextSelected`  
  
 Rahmen  
  
 `Environment.CommandBarSelectedBorder`  
  
 **Gezeigt wird und den Tastaturfokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Befehlssymbol, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")  
  
 **Standard, wenn darauf gezeigt wird**  
  
 Hintergrund  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextHover`  
  
 Rahmen  
  
 `Environment.CommandBarBorder`  
  
 ![Befehlssymbol, wenn darauf gezeigt wird (ausgewählt)](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")  
  
 **Aktiviert, wenn darauf gezeigt wird**  
  
 Hintergrund  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextHoverOverSelected`  
  
 Rahmen  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Befehlssymbol, aufgerufen](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")  
  
 **Gedrückten Befehlssymbol**  
  
 Hintergrund  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Rahmen  
  
 `Environment.CommandBarBorder`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Befehlssymbol, deaktiviert](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")  
  
 **Deaktivierte Befehlssymbol**  
  
 Hintergrund  
  
 N/V (erbt vom Befehlsleisten-Hintergrund)  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextInactive`  
  
 Rahmen  
  
 Nicht zutreffend  
  
####  <a name="a-namebkmkcommandcomboboxa-combo-box"></a><a name="BKMK_CommandComboBox"></a> Kombinationsfeld  
  
> [!IMPORTANT]
>  Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn der Dropdown-Liste eine Region bearbeitbaren Text nicht enthalten ist, verwenden Sie die Color-Token finden Sie unter [Dropdown-](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  
  
 ![Kombinationsfeld (rote Linie)](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")  
  
 Empfohlen...  
 -   für die Erstellung benutzerdefinierter Kombinationsfelder  
  
-   für die Erstellung eines Befehlsleisten-Steuerelements, das Ähnlichkeit mit einem Kombinationsfeld hat.  
  
 Nicht empfohlen...  
 -   für Elemente, die nicht grundsätzlich auf die Befehlsleisten-Benutzeroberfläche abgestimmt sein müssen  
  
-   wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kombinationsfeld (Eingabefeld)](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `Environment.ComboBoxBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxText`  
  
 Rahmen  
  
 `Environment.ComboBoxBorder`  
  
 Trennzeichen  
  
 Kein Trennzeichen  
  
 ![Kombinationsfeld Feld Drop &#45; nach-unten-Schaltfläche](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 N/V (erbt)  
  
 Vordergrund (Glyphe)  
  
 `Environment.ComboBoxGlyph`  
  
 ![Kombinationsfeld &#47; Drop &#45;-Liste](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")  
  
 **Dropdown-Liste**  
  
 Hintergrund  
  
 `Environment.ComboBoxPopupBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxItemText`  
  
 Rahmen  
  
 `Environment.ComboBoxPopupBorder`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kombinationsfeld (Eingabefeld), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `Environment.ComboBoxMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxMouseOverText`  
  
 Rahmen  
  
 `Environment.ComboBoxMouseOverBorder`  
  
 Trennzeichen  
  
 `Environment.ComboBoxMouseOverSeparator`  
  
 ![Kombinationsfeld &#47; Drop &#45; Sie gedrückt, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `Environment.ComboBoxButtonMouseOverBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ComboBoxMouseOverGlyph`  
  
 ![Kombinationsfeld &#47; Drop &#45;-Liste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")  
  
 **Dropdown-Liste**  
  
 Hintergrund (Menüelement)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Rahmen (Menüelement)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Color.category  
  
 ![Kombinationsfeld (Eingabefeld) mit Fokus](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `Environment.ComboBoxFocusedBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxFocusedText`  
  
 Rahmen  
  
 `Environment.ComboBoxFocusedBorder`  
  
 Trennzeichen  
  
 `Environment.ComboBoxFocusedButtonSeparator`  
  
 ![Kombinationsfeld &#47; Drop &#45; ab-Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `Environment.ComboBoxFocusedButtonBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ComboBoxFocusedGlyph`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Color.category  
  
 ![Kombinationsfeld (Eingabefeld) im gedrückten Zustand](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `Environment.ComboBoxMouseDownBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxMouseDownText`  
  
 Rahmen  
  
 `Environment.ComboBoxMouseDownBorder`  
  
 Trennzeichen  
  
 `Environment.ComboBoxMouseDownSeparator`  
  
 ![Kombinationsfeld &#47; Drop &#45; Sie die Maustaste gedrückt wurde.](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `Environment.ComboBoxButtonMouseDownBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ComboBoxMouseDownGlyph`  
  
 **Deaktiviert**  
  
 ![Kombinationsfeld (Eingabefeld), deaktiviert](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `Environment.ComboBoxDisabledBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxDisabledText`  
  
 Rahmen  
  
 `Environment.ComboBoxDisabledBorder`  
  
 Trennzeichen  
  
 Kein Trennzeichen  
  
 ![Kombinationsfeld &#47; Drop &#45; gedrückt deaktiviert](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `Environment.ComboBoxDisabledGlyph`  
  
####  <a name="a-namebkmkcommanddropdowna-drop-down"></a><a name="BKMK_CommandDropDown"></a> Dropdown-Liste  
  
> [!IMPORTANT]
>  Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn der Dropdown-Liste eine Region bearbeitbaren Text enthält, verwenden Sie die Color-Token finden Sie unter [im Kombinationsfeld](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  
  
 ![Drop &#45; nach unten (rote Linie)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")  
  
 Empfohlen...  
 für die Erstellung benutzerdefinierter Dropdownlisten-Steuerelemente  
  
 Nicht empfohlen...  
 -   für Elemente, die keine Ähnlichkeit mit einer Dropdownliste haben  
  
-   für Kombinationsfelder oder unterteilte Schaltflächen  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; Sie Auswahlfeld](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")  
  
 **Auswahlfeld**  
  
 Hintergrund  
  
 `Environment.DropDownBackground`  
  
 Vordergrund (Text)  
  
 `DropDownText`  
  
 Rahmen  
  
 `DropDownBorder`  
  
 Trennzeichen  
  
 Kein Trennzeichen  
  
 ![Drop &#45; gedrückt](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `Environment.DropDownGlyph`  
  
 ![Drop &#45;-Liste](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")  
  
 **Dropdown-Liste**  
  
 Hintergrund  
  
 `Environment.DropDownPopupBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxItemText`  
  
 Rahmen  
  
 `Environment.DropDownPopupBorder`  
  
 Schatten  
  
 `Environment.DropShadowBackground`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; Sie Auswahlfeld darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")  
  
 **Auswahlfeld**  
  
 Hintergrund  
  
 `Environment.DropDownMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.DropDownMouseOverText`  
  
 Rahmen  
  
 `Environment.DropDownMouseOverBorder`  
  
 Trennzeichen  
  
 `Environment.DropDownButtonMouseOverSeparator`  
  
 ![Drop &#45; Sie gedrückt, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `Environment.DropDownButtonMouseOverBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.DropDownMouseOverGlyph`  
  
 ![Drop &#45;-Liste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")  
  
 **Dropdown-Liste**  
  
 Hintergrund (Menüelement)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Rahmen (Menüelement)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; Sie Auswahlfeld gedrückt](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")  
  
 **Auswahlfeld**  
  
 Hintergrund  
  
 `Environment.DropDownMouseDownBackground`  
  
 Vordergrund (Text)  
  
 `Environment.DropDownMouseDownText`  
  
 Rahmen  
  
 `Environment.DropDownMouseDownBorder`  
  
 Trennzeichen  
  
 `Environment.DropDownButtonMouseDownSeparator`  
  
 ![Drop &#45; Sie die Maustaste gedrückt wurde.](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `Environment.DropDownButtonMouseDownBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.DropDownMouseDownGlyph`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; Sie Auswahlfeld deaktiviert](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")  
  
 Hintergrund  
  
 `Environment.DropDownDisabledBackground`  
  
 Vordergrund (Text)  
  
 `Environment.DropDownDisabledText`  
  
 Rahmen  
  
 `Environment.DropDownDisabledBorder`  
  
 Trennzeichen  
  
 Kein Trennzeichen  
  
 ![Drop &#45; gedrückt deaktiviert](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")  
  
 Hintergrund  
  
 N/V  
  
 Vordergrund (Glyphe)  
  
 `Environment.DropDownDisabledGlyph`  
  
#### <a name="split-button"></a>Unterteilte Schaltfläche  
 Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Split Schaltfläche Dropdown-Listen sind Implementierungen der Befehlsleiste [Menüs](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  
  
 ![Trennschaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten unterteilten Schaltfläche  
  
 Nicht empfohlen...  
 -   für alle anderen Arten von Schaltflächen  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Unterteilte Schaltfläche](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")  
  
 **Trennschaltfläche (Standard)**  
  
 Hintergrund  
  
 Keiner  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarSplitButtonGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 Trennzeichen  
  
 Nicht zutreffend  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")  
  
 **Trennschaltfläche (wenn darauf gezeigt wird)**  
  
 Hintergrund  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextHover`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarSplitButtonMouseOverGlyph`  
  
 Rahmen  
  
 `Environment.CommandBarBorder`  
  
 Trennzeichen  
  
 `Environment.CommandBarSplitButtonSeparator`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Unterteilte Schaltfläche, aufgerufen](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")  
  
 **Trennschaltfläche (gedrückt)**  
  
 Hintergrund  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarSplitButtonMouseDownGlyph`  
  
 Rahmen  
  
 `Environment.CommandBarBorder`  
  
 Trennzeichen  
  
 Nicht zutreffend  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Unterteilte Schaltfläche, deaktiviert](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")  
  
 **Trennschaltfläche (deaktiviert)**  
  
 Hintergrund  
  
 Nicht zutreffend  
  
 Vordergrund (Text)  
  
 `Environment.ComboBoxItemTextInactive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarTextInactive`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 Trennzeichen  
  
 N/V  
  
#### <a name="more-options-and-overflow-buttons"></a>Schaltflächen "Weitere Optionen" und "Überlauf"  
 Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.  
  
 ![Weitere Optionen (rote Linie)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Empfohlen...  
 für die benutzerdefinierten Schaltflächen "Weitere Optionen" oder "Überlauf"  
  
 Nicht empfohlen...  
 für Schaltflächen mit einer von den Schaltflächen "Weitere Optionen" oder "Überlauf" abweichenden Funktionalität  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Weitere Optionen](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")  
  
 **Weitere Optionen**  
  
 ![Schaltfläche "Überlauf"](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")  
  
 **Überlauf**  
  
 Hintergrund  
  
 `Environment.CommandBarOptionsBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarOptionsGlyph`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Weitere Optionen", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")  
  
 **Weitere Optionen**  
  
 !["Überlauf", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")  
  
 **Überlauf**  
  
 Hintergrund  
  
 `Environment.CommandBarOptionsMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Weitere Optionen", aufgerufen](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")  
  
 **Weitere Optionen**  
  
 !["Überlauf", aufgerufen](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")  
  
 **Überlauf**  
  
 Hintergrund  
  
 `Environment.CommandBarOptionsMouseDownBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Glyphe)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
## <a name="document-windows"></a>Dokumentfenster  
 Dokumentfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 Wenn Sie Dokumentfenster-Farbtoken verwenden, dürfen diese nur für ähnliche Elemente und paarweise verwendet werden. Andernfalls zeigen sich auf der Benutzeroberfläche unerwartete Ergebnisse.  
  
### <a name="document-window-frame"></a>Dokumentfensterrahmen  
 Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Ein unverankertes Dokumentfenster, das sich außerhalb der IDE befindet, ist dennoch in einen Dokumentursprung eingebettet und verfügt über Hintergrund-, Rahmen-, Text- und Registerkartenfarben, die sich von den Farben der in der IDE angedockten Fenster nicht unterscheiden. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.  
  
 ![Angedocktes Dokumentfenster (rote Linie)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Angedocktes Dokumentfenster**  
  
 ![Unverankertes Dokumentfenster (rote Linie)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Unverankertes Dokumentfenster**  
  
 Empfohlen...  
 für alle Benutzeroberflächenelemente, die Sie auf das Dokumentfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 Dokument: angedockt oder unverankert  
  
 Hintergrund  
  
 Hängt vom Dokumenttyp ab.  
  
 Vordergrund (Text)  
  
 Hängt vom Dokumenttyp ab.  
  
 Rahmen  
  
 `Environment.ToolWindowBorder`  
  
 ![Rahmen mit Fokus](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")  
  
 **Rahmen: verankert, mit Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Vordergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonActiveGlyph`  
  
 Rahmen  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 Rahmen (Glyphe)  
  
 `Environment.RaftedWindowButtonActiveBorder`  
  
 Auf transparent festgelegt  
  
 ![Rahmen ohne Fokus](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")  
  
 **Rahmen: verankert, ohne Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonInactiveGlyph`  
  
 Rahmen  
  
 `Environment.MainWindowInactiveBorder`  
  
 Rahmen (Glyphe)  
  
 `Environment.RaftedWindowButtonInactiveBorder`  
  
 Auf transparent festgelegt  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Rahmen mit Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")  
  
 **Rahmen: verankert, mit Fokus**  
  
 Hintergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonHoverActive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonHoverActiveGlyph`  
  
 Rahmen (Glyphe)  
  
 `Environment.RaftedWindowButtonHoverActiveBorder`  
  
 ![Rahmen ohne Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")  
  
 **Rahmen: verankert, ohne Fokus**  
  
 Hintergrund (Glyphe)  
  
 `EnvironmentRaftedWindowButtonHoverInactive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonHoverInactiveGlyph`  
  
 Rahmen (Glyphe)  
  
 `Environment.RaftedWindowButtonHoverInactiveBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Rahmen mit Fokus, aufgerufen](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")  
  
 **Rahmen: verankert, mit Fokus**  
  
 Hintergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonDown`  
  
 Vordergrund (Glyphe)  
  
 `Environment.RaftedWindowButtonDownGlyph`  
  
 Rahmen (Glyphe)  
  
 `Environment.RaftedWindowButtonDownBorder`  
  
### <a name="document-tabs"></a>Dokumentregisterkarten  
 Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.  
  
 ![Registerkarte "Dokument" (rote Linie)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Empfohlen...  
 für jede Benutzeroberfläche, die auf Dokumentregisterkarten abgestimmt sein soll, und wenn Designaktualisierungen oder neue Designfarben automatisch ausgewählt werden sollen.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
#### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten  
 Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:  
  
-   Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.  
  
-   Hintergrundregisterkarten sind Dokumentregisterkarten, die nicht der aktuell ausgewählten Registerkarte entsprechen. Sobald auf die Registerkarte geklickt wird, wird sie zur ausgewählten Registerkarte, die alle Hintergrund-, Rahmen- und Textfarben von den Tokennamen übernimmt.  
  
 ![Registerkarte "Dokument öffnen" (rote Linie)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
 Empfohlen...  
 für die Erstellung benutzerdefinierter Dokumentregisterkarten  
  
 Nicht empfohlen...  
 -   für vorläufige Registerkarten (Vorschau)  
  
-   für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
#### <a name="selected-tab"></a>Ausgewählte Registerkarte  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Ausgewählte Registerkarte mit Fokus](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")  
  
 **Ausgewählte Dokumentregisterkarte mit Fokus**  
  
 Hintergrund  
  
 `Environment.FileTabSelectedGradientTop`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.FileTabSelectedText`  
  
 Rahmen  
  
 `Environment.FileTabSelectedBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 Dokumentrahmen  
  
 `Environment.FileTabDocumentBorderBackground`  
  
 **Ohne Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Ausgewählte Registerkarte ohne Fokus](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")  
  
 **Ausgewählte Dokumentregisterkarte ohne Fokus**  
  
 Hintergrund  
  
 `Environment.FileTabInactiveGradientTop`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.FileTabInactiveText`  
  
 Rahmen  
  
 `Environment.FileTabInactiveBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 Dokumentrahmen  
  
 `Environment.FileTabInactiveDocumentBorderBackground`  
  
#### <a name="background-tab"></a>Hintergrundregisterkarte  
 **Default**  
  
 ![Hintergrundregisterkarte](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")  
  
 **Hintergrund Registerkarte Standard**  
  
 Hintergrund  
  
 `Environment.FileTabBackground`  
  
 Vordergrund (Text)  
  
 `Environment.FileTabText`  
  
 Rahmen  
  
 `Environment.FileTabBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 **Gezeigt wird**  
  
 ![Hintergrundregisterkarte, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")  
  
 **Registerkarte "Hintergrundvorschau"**  
  
 Hintergrund  
  
 `Environment.FileTabHotGradientTop`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.FileTabHotText`  
  
 Rahmen  
  
 `Environment.FileTabHotBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
#### <a name="preview-tab"></a>Vorschauregisterkarte  
 Die Vorschauregisterkarte wird auf der rechten Seite des Dokument-Registerkartenkanals angezeigt, wenn der Benutzer auf ein Element im Toolfenster des Projektmappen-Explorers klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.  
  
 ![Registerkarte "Vorschau" (rote Linie)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Empfohlen...  
 wenn Sie eine vorläufige Vorschau erstellen und Elemente mit der Farbe der aktuellen Vorschauregisterkarte übereinstimmen sollen.  
  
 Nicht empfohlen...  
 -   für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau)  
  
-   für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Der ausgewählten vorschauregisterkarte: mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Vorschau" mit Fokus](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")  
  
 **Registerkarte mit Fokus Vorschau**  
  
 Hintergrund  
  
 `Environment.FileTabProvisionalSelectedActive`  
  
 Vordergrund (Text)  
  
 `Environment.FileTabProvisionalSelectedActiveForeground`  
  
 Rahmen  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 Dokumentrahmen  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 **Der ausgewählten vorschauregisterkarte: ohne Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Vorschau" ohne Fokus](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")  
  
 **Registerkarte ohne Fokus Vorschau**  
  
 Hintergrund  
  
 `Environment.FileTabProvisionalSelectedInactive`  
  
 Vordergrund (Text)  
  
 `Environment.FileTabProvisionalSelectedInactiveForeground`  
  
 Rahmen  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 Dokumentrahmen  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 **Registerkarte "Vorschau" Hintergrund: Standard**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Hintergrund"](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")  
  
 **Registerkarte "Hintergrund" der Preview-Registerkarte**  
  
 Hintergrund  
  
 `Environment.FileTabProvisionalInactive`  
  
 Vordergrund (Text)  
  
 `Environment.FileTabProvisionalInactiveForeground`  
  
 Rahmen  
  
 `Environment.FileTabProvisionalInactiveBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 **Registerkarte "Vorschau" Hintergrund: bewegen**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Hintergrundvorschau", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")  
  
 **Vorschau Registerkarte Registerkarte "Hintergrundvorschau"**  
  
 Hintergrund  
  
 `Environment.FileTabProvisionalHover`  
  
 Vordergrund (Text)  
  
 `Environment.FileTabProvisionalHoverForeground`  
  
 Rahmen  
  
 `Environment.FileTabProvisionalHoverBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
#### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche  
 Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dokumentüberlauf-Dropdownmenü, das mithilfe der **CommandBarMenu** -Farben (siehe [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)) gesteuert wird, zeigt eine Liste aller geöffneten Dokumente (sichtbar und unsichtbar) an. Die Überlauf-Glyphe ändert sich abhängig davon, ob alle geöffneten Dokumente im Registerkartenkanal angezeigt werden.  
  
 !["Überlauf" (rote Linie)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten Dokumentüberlauf-Schaltfläche  
  
 Nicht empfohlen...  
 -   für Benutzeroberflächen, die keine Ähnlichkeit mit einer Überlaufschaltfläche haben  
  
-   für Überlaufschaltflächen auf der Befehlsleiste  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Überlauf](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")  
  
 **Schaltfläche "Überlauf" Dokument**  
  
 Hintergrund  
  
 `Environment.DocWellOverflowButtonBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.DocWellOverflowButtonGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Überlauf", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")  
  
 **Dokument Überlaufschaltfläche darauf gezeigt wird**  
  
 Hintergrund  
  
 `Environment.DocWellOverflowButtonMouseOverBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.DocWellOverflowButtonMouseOverGlyph`  
  
 Rahmen  
  
 `Environment.DocWellOverflowButtonMouseOverBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Überlauf", aufgerufen](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")  
  
 **Dokument-Überlauf gedrückt**  
  
 Hintergrund  
  
 `Environment.DocWellOverflowButtonMouseDownBackground`  
  
 Vordergrund (Glyphe)  
  
 `Environment.DocWellOverflowButtonMouseDownGlyph`  
  
 Rahmen  
  
 `Environment.DocWellOverflowButtonMouseDownBorder`  
  
## <a name="tool-windows"></a>Toolfenster  
 Toolfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 ![Toolfenster (rote Linie)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
### <a name="tool-window-frame"></a>Toolfensterrahmen  
 Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.  
  
 ![Toolfenster, Rahmen (rote Linie)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **In der Dockingstation**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolfenster, angedockt](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")  
  
 Hintergrund  
  
 `Environment.ToolWindowBackground`  
  
 Rahmen  
  
 `Environment.ToolWindowBorder`  
  
 **Gleitkommawert: mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolfenster mit Fokus](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")  
  
 Hintergrund  
  
 `Environment.ToolWindowBackground`  
  
 Rahmen  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 **Gleitkommawert: ohne Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolfenster ohne Fokus](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")  
  
 Hintergrund  
  
 `Environment.ToolWindowBackground`  
  
 Rahmen  
  
 `Environment.MainWindowInactiveBorder`  
  
### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters  
 Der Rahmen der Titelleiste ist kein echter Rahmen, sondern ein dicker Strich am oberen Rand der Titelleiste. Er verfügt über keinen Tokennamen für den Zustand "Ohne Fokus".  
  
 ![Toolfenster, Titelleiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Titelleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")  
  
 **Titelleiste mit Fokus**  
  
 Hintergrund  
  
 `Environment.TitleBarActiveGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.TitleBarActiveText`  
  
 Rahmen  
  
 `Environment.TitleBarActiveBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 Ziehpunkt  
  
 `Environment.TitleBarDragHandleActive`  
  
 **Ohne Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Titelleiste ohne Fokus](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")  
  
 **Titelleiste ohne Fokus**  
  
 Hintergrund  
  
 `Environment.TitleBarInactiveGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.TitleBarInactiveText`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 Ziehpunkt  
  
 `Environment.TitleBarDragHandle`  
  
#### <a name="title-bar-buttons"></a>Titelleisten-Schaltflächen  
 ![Titelleistenschaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Empfohlen...  
 für Schaltflächen auf der Benutzeroberfläche, die Farbtoken aus den Toolfenster-Titelleisten verwenden.  
  
 Nicht empfohlen...  
 -   für Schaltflächen, die an anderer Stelle angezeigt werden  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Titelleistenschaltfläche mit Fokus](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")  
  
 **Mit Fokus**  
  
 Hintergrund  
  
 N/V  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonActiveGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 ![Titelleistenschaltfläche ohne Fokus](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")  
  
 **Ohne Fokus**  
  
 Hintergrund  
  
 N/V  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonInactiveGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Titelleistenschaltfläche mit Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")  
  
 **Mit Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowButtonHoverActive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonHoverActiveGlyph`  
  
 Rahmen  
  
 `Environment.ToolWindowButtonHoverActiveBorder`  
  
 ![Titelleistenschaltfläche ohne Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")  
  
 **Ohne Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowButtonHoverInactive`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonHoverInactiveGlyph`  
  
 Rahmen  
  
 `Environment.ToolWindowButtonHoverInactiveBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Titelleistenschaltfläche mit Fokus, aufgerufen](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")  
  
 **Mit Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowButtonDown`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonDownActiveGlyph`  
  
 Rahmen  
  
 `Environment.ToolWindowButtonDownBorder`  
  
 ![Titelleistenschaltfläche ohne Fokus, aufgerufen](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")  
  
 **Ohne Fokus**  
  
 Hintergrund  
  
 `Environment.ToolWindowButtonDown`  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolWindowButtonDownInactiveGlyph`  
  
 Rahmen  
  
 `Environment.ToolWindowButtonDownBorder`  
  
### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten  
 ![Registerkarte "Toolfenster" (rote Linie)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Ausgewählte Registerkarte**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Toolfenster" mit Fokus](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")  
  
 **Ausgewählte fokussierte Tool-Fenster (Registerkarte)**  
  
 Hintergrund  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowTabSelectedActiveText`  
  
 Rahmen  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Registerkarte "Toolfenster" ohne Fokus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")  
  
 **Ausgewählten, ohne Fokus Tool-Fenster (Registerkarte)**  
  
 Hintergrund  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowTabSelectedText`  
  
 Rahmen  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
 **Registerkarte "Hintergrund"**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolfenster, Registerkarte "Hintergrund"](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")  
  
 **Registerkarte "Hintergrund Tool-Fenster"**  
  
 Hintergrund  
  
 `Environment.ToolWindowTabGradientBegin`  
  
 In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps  
  
 `Environment.ToolWindowTabGradientEnd`  
  
 In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowTabText`  
  
 Rahmen  
  
 `Environment.ToolWindowTabBorder`  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolfenster, Registerkarte "Hintergrund", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")  
  
 **Tool-Fenster Registerkarte "Hintergrundvorschau"**  
  
 Hintergrund  
  
 `Environment.ToolWindowTabMouseOverBackgroundBegin`  
  
 In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps  
  
 `Environment.ToolWindowTabMouseOverBackgroundEnd`  
  
 In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps  
  
 Vordergrund (Text)  
  
 `Environment.ToolWindowTabMouseOverText`  
  
 Rahmen  
  
 `Environment.ToolWindowTabMouseOverBorder`  
  
 Auf dieselbe Farbe wie der Hintergrund festgelegt  
  
### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten  
 ![Auto &#45; ausblenden (rote Linie)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf automatisch ausgeblendete Toolfenster-Registerkarten abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Auto &#45; Registerkarte "Hintergrund"](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")  
  
 **Standardregisterkarte automatisch im Hintergrund**  
  
 Hintergrund  
  
 `Environment.AutoHideTabBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.AutoHideTabText`  
  
 Rahmen  
  
 `Environment.AutoHideTabBorder`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Auto &#45; Registerkarte "Hintergrund", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")  
  
 **Registerkarte "Hintergrundvorschau" automatisch ausblenden**  
  
 Hintergrund  
  
 `Environment.AutoHideTabMouseOverBackgroundBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `Environment.AutoHideTabMouseOverText`  
  
 Rahmen  
  
 `Environment.AutoHideTabMouseOverBorder`  
  
## <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente  
 Wenn Sie für Ihr Feature eine Visual Studio-Standardbefehlsleiste verwenden, haben Sie Zugriff auf formatierte Shell-Steuerelemente. Diese gemeinsam verwendeten Steuerelemente sollten nicht von einer Vorlage neu erstellt werden. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.  
  
### <a name="search-box"></a>Suchfeld  
 Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.  
  
 Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:  
  
-   "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.  
  
-   "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.  
  
-   "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).  
  
-   "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.  
  
 ![Suchfeld (rote Linie)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")  
  
 Empfohlen...  
 für das Entwerfen eines benutzerdefinierten Suchfelds  
  
 Nicht empfohlen...  
 -   für Elemente, die kein Suchfeld darstellen  
  
-   für Elemente, die nicht generell auf die Suchfeld-Benutzeroberfläche abgestimmt sein sollen  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suche (Eingabefeld) mit Fokus](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `SearchControl.FocusedBackground`  
  
 Vordergrund (Text)  
  
 `SearchControl.FocusedBackground`  
  
 Rahmen  
  
 `SearchControl.FocusedBorder`  
  
 Trennzeichen  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 ![Suche (Aktionsschaltfläche) mit Fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")  
  
 **Schaltfläche "Aktion"**  
  
 Hintergrund  
  
 Keine  
  
 Vordergrund (Glyphe "Suchen")  
  
 `SearchControl.SearchGlyph`  
  
 Vordergrund (Glyphe "Beenden")  
  
 `SearchControl.StopGlyph`  
  
 Vordergrund (Glyphe "Löschen")  
  
 `SearchControl.ClearGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 ![Suchen Sie Drop & #45 zu, die nach-unten Sie-Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `SearchControl.FocusedDropDownButton`  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.FocusedDropDownButtonGlyph`  
  
 Rahmen  
  
 `SearchControl.FocusedDropDownButtonBorder`  
  
 **Ohne Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suche (Eingabefeld) ohne Fokus](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")  
  
 **Aktive Eingabefeld**  
  
 Hintergrund  
  
 `SearchControl.SearchActiveBackground`  
  
 Vordergrund (Text)  
  
 `SearchControl.SearchActiveBackground`  
  
 Rahmen  
  
 `SearchControl.UnfocusedBorder`  
  
 Trennzeichen  
  
 `SearchControl.DropDownSeparator`  
  
 ![Suche (Eingabefeld) ohne Fokus und inaktiv](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")  
  
 **Inaktive Eingabefeld**  
  
 Hintergrund  
  
 `SearchControl.Unfocused`  
  
 Vordergrund (Text)  
  
 `SearchControl.Unfocused`  
  
 Rahmen  
  
 `SearchControl.UnfocusedBorder`  
  
 Trennzeichen  
  
 `SearchControl.DropDownSeparator`  
  
 ![Suche (Aktionsschaltfläche) ohne Fokus](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")  
  
 **Schaltfläche "Aktion"**  
  
 Hintergrund  
  
 Nicht zutreffend  
  
 Vordergrund (Glyphe "Suchen")  
  
 `SearchControl.SearchGlyph`  
  
 Vordergrund (Glyphe "Beenden")  
  
 `SearchControl.StopGlyph`  
  
 Vordergrund (Glyphe "Löschen")  
  
 `SearchControl.ClearGlyph`  
  
 Rahmen  
  
 Nicht zutreffend  
  
 ![Durchsuchen Sie Drop & #45, die nach-unten Sie-Schaltfläche ohne Fokus](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `SearchControl.UnfocusedDropDownButton`  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.UnfocusedDropDownButtonGlyph`  
  
 Rahmen  
  
 `SearchControl.UnfocusedDropDownButtonBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suche (Aktionsschaltfläche), aufgerufen](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")  
  
 **Schaltfläche "Aktion"**  
  
 Hintergrund  
  
 `SearchControl.ActionButtonMouseDown`  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.ActionButtonMouseDownGlyph`  
  
 Rahmen  
  
 `SearchControl.ActionButtonMouseDownBorder`  
  
 ![Suchen Sie Drop & #45 zu, nach-unten Sie-Schaltfläche gedrückt](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 `SearchControl.MouseDownDropDownButton`  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.MouseDownDropDownButtonGlyph`  
  
 Rahmen  
  
 `SearchControl.MouseDownDropDownButtonBorder`  
  
 **Hervorgehobene (nur Text)**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suche (Eingabefeld), hervorgehoben](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")  
  
 **Eingabefeld mit hervorgehobenem text**  
  
 Hintergrund  
  
 `SearchControl.Selection`  
  
 Vordergrund (Text)  
  
 `SearchControl.FocusedBackground`  
  
 Rahmen  
  
 Keine  
  
 Trennzeichen  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suche (Eingabefeld), deaktiviert](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")  
  
 **Eingabefeld**  
  
 Hintergrund  
  
 `SearchControl.Disabled`  
  
 Vordergrund (Text)  
  
 `SearchControl.Disabled`  
  
 Rahmen  
  
 `SearchControl.DisabledBorder`  
  
 Trennzeichen  
  
 `SearchControl.DropDownSeparator`  
  
 ![Suche (Aktionsschaltfläche), deaktiviert](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")  
  
 **Schaltfläche "Aktion"**  
  
 Hintergrund  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.ActionButtonDisabledGlyph`  
  
 Rahmen  
  
 Keine  
  
 ![Suchen Sie Drop & #45 zu, die nach-unten Sie-Schaltfläche, deaktiviert](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")  
  
 **Dropdown-Schaltfläche**  
  
 Hintergrund  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `SearchControl.DisabledDownButtonGlyph`  
  
 Rahmen  
  
 Keiner  
  
#### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld  
 Das Dropdownmenü im Suchfeld kann etwas komplexer sein als andere Dropdownmenüs in Visual Studio. Die Bereiche "Empfohlene Suchbegriffe" und "Suchoptionen" können alleine oder zusammen im Menü erscheinen, und jedem Bereich kann eine eigene Farbe zugeordnet sein. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.  
  
 ![Drop & #45 durchsuchen; nach unten (rote Linie)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
 Empfohlen...  
 -   für die Erstellung einer benutzerdefinierten Dropdownliste im Suchfeld  
  
-   bei Verwendung der richtigen Tokennamen für die entsprechenden Listenkomponenten  
  
 Nicht empfohlen...  
 -   für Dropdownlisten, die in anderen Kontexten angezeigt werden  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Standardwert (keine weiteren Status)**  
  
 Element  
  
 Tokenname: Category.color  
  
 Rahmen  
  
 `SearchControl.PopupBorder`  
  
 Trennzeichen  
  
 `SearchControl.PopupSectionHeaderSeparator`  
  
 Schatten  
  
 `Environment.DropShadowBackground`  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Suchvorschlag](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")  
  
 **Suchvorschläge**  
  
 Hintergrund  
  
 `SearchControl.PopupItemsListBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `SearchControl.PopupItemText`  
  
 ![Kontrollkästchen "Suche"](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")  
  
 **Suchoptionen (Kontrollkästchen)**  
  
 ![Suchoptionen](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")  
  
 **Optionen (Link)**  
  
 Hintergrund  
  
 `SearchControl.PopupSectionBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Kontrollkästchentext)  
  
 `SearchControl.PopupCheckboxText`  
  
 Vordergrund (Linktext)  
  
 `SearchControl.PopupButtonText`  
  
 Headerhintergrund  
  
 `SearchControl.PopupSectionHeaderGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Headertext)  
  
 `SearchControl.PopupSectionHeaderText`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Suchvorschlag", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")  
  
 **Suchvorschläge**  
  
 Hintergrund  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Text)  
  
 `SearchControl.PopupMouseOverItemText`  
  
 Rahmen  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 ![Kontrollkästchen "Suche", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")  
  
 **Suchvorschläge (Kontrollkästchen)**  
  
 !["Suchoptionen", wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")  
  
 **Suchoptionen**  
  
 Hintergrund  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Kontrollkästchentext)  
  
 `SearchControl.PopupCheckboxMouseDownText`  
  
 Vordergrund (Linktext)  
  
 `SearchControl.PopupButtonMouseDownText`  
  
 Rahmen  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 !["Suchvorschlag" im gedrückten Zustand](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")  
  
 **Suchvorschläge (Kontrollkästchen)**  
  
 !["Suchoptionen" im gedrückten Zustand](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")  
  
 **Suchoptionen**  
  
 Kontrollkästchen-Hintergrund  
  
 `SearchControl.PopupControlMouseDownBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 `SearchControl.PopupControlMouseDownBackgroundGradientEnd`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Kontrollkästchentext)  
  
 `SearchControl.PopupCheckboxMouseDownText`  
  
 Linkhintergrund  
  
 `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`  
  
 Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.  
  
 Vordergrund (Linktext)  
  
 `SearchControl.PopupButtonMouseDownText`  
  
### <a name="hyperlink"></a>Link  
 Der Link ist ein Steuerelement, das keine Kombination aus Vordergrund-/Hintergrundfarbe darstellt. Sie verwenden grundsätzlich die Vordergrund-Linkfarbe, die auf dunklem, grauen und weißem Hintergrund ordnungsgemäß angezeigt wird. Wenn Sie nicht das Farbtoken für das Linksteuerelement verwenden, sehen Sie für den "gedrückten" Zustand die Standardsystemfarbe, die rot blinkend dargestellt wird. Das ist das Signal, dass das Steuerelement nicht das richtige Farbtoken für die Umgebung verwendet.  
  
 ![Hyperlink (rote Linie)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Empfohlen...  
 für die Erstellung eines benutzerdefinierten Links  
  
 Nicht empfohlen...  
 für Elemente, die keinen Link darstellen  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Hyperlink, Standard](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")  
  
 Vordergrund (Text)  
  
 `Environment.PanelHyperlink`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Hyperlink, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")  
  
 Vordergrund (Text)  
  
 `Environment.PanelHyperlinkHover`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Hyperlink, aufgerufen](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")  
  
 Vordergrund (Text)  
  
 `Environment.PanelHyperlinkPressed`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Hyperlink, deaktiviert](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")  
  
 Vordergrund (Text)  
  
 `Environment.PanelHyperlinkDisabled`  
  
### <a name="infobar"></a>Infoleiste  
 Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.  
  
 ![Infoleiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten Infoleiste  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Infoleiste haben  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Infoleiste](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")  
  
 **Infoleiste**  
  
 Hintergrund  
  
 `Environment.InfoBackground`  
  
 Vordergrund (Text)  
  
 `Environment.InfoText`  
  
 Rahmen  
  
 `Environment.ToolWindowBorder`  
  
### <a name="scroll-bar"></a>Bildlaufleiste  
 Bildlaufleisten erhalten ihr Format von der Visual Studio-Umgebung, sodass kein Design angewendet werden muss. Sie können jedoch festlegen, dass die in Bildlaufleisten genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 ![Bildlaufleiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Empfohlen...  
 für die Erstellung einer Benutzeroberfläche, die auf die Visual Studio-Bildlaufleisten abgestimmt sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die nicht grundsätzlich auf die Bildlaufleisten-Benutzeroberfläche abgestimmt sein sollen  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Bildlaufleiste](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")  
  
 **Bildlaufleiste**  
  
 Bildlaufleiste  
  
 `Environment.ScrollBarBackground`  
  
 Vordergrund (Ziehpunkt)  
  
 `Environment.ScrollBarThumbBackground`  
  
 ![Bildlaufleiste, Pfeil](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")  
  
 **Bildlaufpfeil**  
  
 Hintergrund  
  
 `Environment.ScrollBarArrowBackground`  
  
 Auf dieselbe Farbe wie die Bildlaufleiste festgelegt  
  
 Vordergrund (Glyphe)  
  
 `Environment.ScrollBarArrowGlyph`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Bildlaufleiste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")  
  
 **Bildlaufleiste**  
  
 Bildlaufleiste  
  
 `Environment.ScrollBarBackground`  
  
 Vordergrund (Ziehpunkt)  
  
 `Environment.ScrollBarThumbMouseOverBackground`  
  
 ![Bildlaufleiste (Pfeil), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")  
  
 **Bildlaufpfeil**  
  
 Hintergrund  
  
 `Environment.ScrollBarArrowMouseOverBackground`  
  
 Auf dieselbe Farbe wie die Bildlaufleiste festgelegt  
  
 Vordergrund (Glyphe)  
  
 `Environment.ScrollBarArrowGlyphMouseOver`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Bildlaufleiste, aufgerufen](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")  
  
 **Bildlaufleiste**  
  
 Bildlaufleiste  
  
 `Environment.ScrollBarBackground`  
  
 Vordergrund (Ziehpunkt)  
  
 `Environment.ScrollBarThumbPressedBackground`  
  
 ![Bildlaufleiste (Pfeil), aufgerufen](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")  
  
 **Bildlaufpfeil**  
  
 Hintergrund  
  
 `Environment.ScrollBarArrowPressedBackground`  
  
 Auf dieselbe Farbe wie die Bildlaufleiste festgelegt  
  
 Vordergrund (Glyphe)  
  
 `Environment.ScrollBarArrowGlyphPressed`  
  
###  <a name="a-namebkmktreeviewa-tree-view"></a><a name="BKMK_TreeView"></a> Strukturansicht  
 Mehrere Toolfenster, einschließlich Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in der TreeView-Kategorie gesteuert werden. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.  
  
 ![Strukturansicht (rote Linie)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")  
  
 Empfohlen...  
 für alle Projekte zur Implementierung einer hierarchischen Organisationsstruktur  
  
 Nicht empfohlen...  
 -   für Elemente, die keine Ähnlichkeit mit einer Strukturansicht haben  
  
-   für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Strukturansicht](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")  
  
 Hintergrund  
  
 `TreeView.Background`  
  
 Vordergrund (Text)  
  
 `TreeView.Background`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.Glyph`  
  
 Rahmen  
  
 Keine  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Strukturansicht, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")  
  
 Hintergrund  
  
 `TreeView.Background`  
  
 Vordergrund (Text)  
  
 `TreeView.Background`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.GlyphMouseOver`  
  
 Rahmen  
  
 Keine  
  
 **Ziehen Sie über**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Strukturansicht, wenn Element darüber gezogen wird](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")  
  
 Hintergrund  
  
 `TreeView.DragOverItem`  
  
 Vordergrund (Text)  
  
 `TreeView.DragOverItem`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.DragOverItemGlyph`  
  
 Rahmen  
  
 Keine  
  
 **Ausgewählt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Strukturansicht mit Fokus](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")  
  
 **Mit Fokus**  
  
 Hintergrund  
  
 `TreeView.SelectedItemActive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemActive`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemActiveGlyph`  
  
 Rahmen  
  
 `TreeView.FocusVisualBorder`  
  
 ![Strukturansicht ohne Fokus](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")  
  
 **Ohne Fokus**  
  
 Hintergrund  
  
 `TreeView.SelectedItemInactive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemInactive`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemInactiveGlyph`  
  
 Rahmen  
  
 Keine  
  
 **Zeigen Sie auf ausgewählt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Strukturansicht mit Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")  
  
 **Mit Fokus**  
  
 Hintergrund  
  
 `TreeView.SelectedItemActive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemActive`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Rahmen  
  
 Keine`TreeView.FocusVisualBorder`  
  
 ![Strukturansicht ohne Fokus, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")  
  
 **Ohne Fokus**  
  
 Hintergrund  
  
 `TreeView.SelectedItemInactive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemInactive`  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Rahmen  
  
 Keiner  
  
### <a name="button-controls"></a>Schaltflächen-Steuerelemente  
 ![Button-Steuerelement (rote Linie)](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Empfohlen...  
 für Schaltflächen im Dokument, die Sie in Visual Studio-Designs (Hell, Dunkel, Blau oder kontrastreiches Systemdesign) integrieren möchten.  
  
 Nicht empfohlen...  
 für Schaltflächen, die vor einem benutzerdefinierten Hintergrund angezeigt werden, der nicht Bestandteil eines Visual Studio-Designs ist  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Schaltfläche](../../extensibility/ux-guidelines/media/0303-156_button.png "0303-156_Button")  
  
 Schaltfläche  
  
 `CommonControls.Button`  
  
 Schaltflächenrahmen  
  
 `CommonControls.ButtonBorder`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Schaltfläche, deaktiviert](../../extensibility/ux-guidelines/media/0303-157_buttondisabled.png "0303-157_ButtonDisabled")  
  
 Schaltfläche  
  
 `CommonControls.ButtonDisabled`  
  
 Schaltflächenrahmen  
  
 `CommonControls.ButtonBorderDisabled`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-158_buttonhover.png "0303-158_ButtonHover")  
  
 Schaltfläche  
  
 `CommonControls.ButtonHover`  
  
 Schaltflächenrahmen  
  
 `CommonControls.ButtonBorderHover`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Schaltfläche, aufgerufen](../../extensibility/ux-guidelines/media/0303-159_buttonpressed.png "0303-159_ButtonPressed")  
  
 Schaltfläche  
  
 `CommonControls.ButtonPressed`  
  
 Schaltflächenrahmen  
  
 `CommonControls.ButtonBorderPressed`  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/0303-160_buttonfocused.png "0303-160_ButtonFocused")  
  
 Schaltfläche  
  
 `CommonControls.ButtonFocused`  
  
 Schaltflächenrahmen  
  
 `CommonControls.ButtonBorderFocused`  
  
### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente  
 ![Kontrollkästchen (rote Linie)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")  
  
 Empfohlen...  
 für Kontrollkästchen-Steuerelemente im Dokumentursprung  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Kontrollkästchen-Steuerelement sind  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackground`  
  
 Rahmen  
  
 `CommonControls.CheckBoxBorder`  
  
 Text  
  
 `CommonControls.CheckBoxText`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyph`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kontrollkästchen, deaktiviert](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackgroundDisabled`  
  
 Rahmen  
  
 `CommonControls.CheckBoxBorderDisabled`  
  
 Text  
  
 `CommonControls.CheckBoxTextDisabled`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphDisabled`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kontrollkästchen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackgroundHover`  
  
 Rahmen  
  
 `CommonControls.CheckBoxBorderHover`  
  
 Text  
  
 `CommonControls.CheckBoxTextHover`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphHover`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kontrollkästchen, aufgerufen](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Rahmen  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Text  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Kontrollkästchen mit Fokus](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackgroundFocused`  
  
 Rahmen  
  
 `CommonControls.CheckBoxBorderFocused`  
  
 Text  
  
 `CommonControls.CheckBoxTextFocused`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphFocused`  
  
### <a name="drop-boxcombo-box-controls"></a>Dropdownlisten-/Kombinationsfeld-Steuerelement  
 ![Drop &#45; ab &#47; Kombinationsfeld (rote Linie)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
 Empfohlen...  
 für Dropdownlisten und Kombinationsfelder, die Teil des Dokumentursprungs sind.  
  
 Nicht empfohlen...  
 -   für Benutzeroberflächenelemente, die keine Dropdownliste und kein Kombinationsfeld sind  
  
-   für eine [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) oder ein [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) in der Befehlsleiste  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; Kombinationsfeld](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxBackground`  
  
 Rahmen  
  
 `CommonControls.ComboBoxBorder`  
  
 Text  
  
 `CommonControls.ComboBoxText`  
  
 Trennzeichen  
  
 `CommonControls.ComboBoxSeparator`  
  
 Glyphe  
  
 `CommonControls.ComboBoxGlyph`  
  
 Glyphenhintergrund  
  
 `CommonControls.ComboBoxGlyphBackground`  
  
 **Deaktiviert**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; Kombinationsfeld, deaktiviert](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxBackgroundDisabled`  
  
 Rahmen  
  
 `CommonControls.ComboBoxBorderDisabled`  
  
 Text  
  
 `CommonControls.ComboBoxTextDisabled`  
  
 Trennzeichen  
  
 `CommonControls.ComboBoxSeparatorDisabled`  
  
 Glyphe  
  
 `CommonControls.ComboBoxGlyphDisabled`  
  
 Glyphenhintergrund  
  
 `CommonControls.ComboBoxGlyphBackgroundDisabled`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; im Kombinationsfeld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxBackgroundHover`  
  
 Rahmen  
  
 `CommonControls.ComboBoxBorderHover`  
  
 Text  
  
 `CommonControls.ComboBoxTextHover`  
  
 Trennzeichen  
  
 `CommonControls.ComboBoxSeparatorHover`  
  
 Glyphe  
  
 `CommonControls.ComboBoxGlyphHover`  
  
 Glyphenhintergrund  
  
 `CommonControls.ComboBoxGlyphBackgroundHover`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; Kombinationsfeld gedrückt](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxBackgroundPressed`  
  
 Rahmen  
  
 `CommonControls.ComboBoxBorderPressed`  
  
 Text  
  
 `CommonControls.ComboBoxTextPressed`  
  
 Trennzeichen  
  
 `CommonControls.ComboBoxSeparatorPressed`  
  
 Glyphe  
  
 `CommonControls.ComboBoxGlyphPressed`  
  
 Glyphenhintergrund  
  
 `CommonControls.ComboBoxGlyphBackgroundPressed`  
  
 **Mit Fokus**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; Kombinationsfeld mit Fokus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxBackgroundFocused`  
  
 Rahmen  
  
 `CommonControls.ComboBoxBorderFocused`  
  
 Text  
  
 `CommonControls.ComboBoxTextFocused`  
  
 Trennzeichen  
  
 `CommonControls.ComboBoxSeparatorFocused`  
  
 Glyphe  
  
 `CommonControls.ComboBoxGlyphFocused`  
  
 Glyphenhintergrund  
  
 `CommonControls.ComboBoxGlyphBackgroundFocused`  
  
 **Eingabe Textauswahl**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Drop &#45; ab &#47; Kombinationsfeld Feld Texteingabe](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")  
  
 Hervorheben  
  
 `CommonControls.ComboBoxTextInputSelection`  
  
 **Elementansicht gedrückt-Liste**  
  
 ![Drop &#45; ab &#47; Kombinationsfeld Feld Listenansicht](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")  
  
 Hintergrund  
  
 `CommonControls.ComboBoxListBackground`  
  
 `CommonControls.ComboBoxListBackgroundHover`  
  
 `CommonControls.ComboBoxListItemBackgroundPressed`  
  
 `CommonControls.ComboBoxListItemBackgroundFocused`  
  
 Rahmen  
  
 `CommonControls.ComboBoxListBorder`  
  
 `CommonControls.ComboBoxListBorderHover`  
  
 `CommonControls.ComboBoxListBorderPressed`  
  
 `CommonControls.ComboBoxListBorderFocused`  
  
 Elementtext  
  
 `CommonControls.ComboBoxListItemText`  
  
 `CommonControls.ComboBoxListItemTextHover`  
  
 `CommonControls.ComboBoxListItemTextPressed`  
  
 `CommonControls.ComboBoxListItemTextFocused`  
  
 Hintergrundschatten  
  
 `CommonControls.ComboBoxListBackgroundShadow`  
  
### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)  
 Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.  
  
 ![Tabellarische Daten &#40; Rastersteuerelement &#41; (rote Linie)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Empfohlen...  
 für Tabellen- oder Rastersteuerelemente  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Tabellen- oder Rastersteuerelement sind  
  
#### <a name="column-headers"></a>Spaltenheader  
 Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.  
  
 Zustand  
  
 Element  
  
 Tokenname: Category.color  
  
 Standard  
  
 Hintergrund  
  
 `Header.Default`  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 Vordergrund (Glyphe)  
  
 `Header.Glyph`  
  
 Rahmen  
  
 `Header.SeparatorLine`  
  
 Darauf zeigen (Hover)  
  
 Hintergrund  
  
 `Header.MouseOver`  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextHover`  
  
 Vordergrund (Glyphe)  
  
 `Header.MouseOverGlyph`  
  
 Rahmen  
  
 `Header.SeparatorLine`  
  
 Gedrückt  
  
 Hintergrund  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Vordergrund (Text)  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Vordergrund (Glyphe)  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Rahmen  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
#### <a name="list-view-items"></a>Listenansichtselemente  
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.  
  
 Zustand  
  
 Element  
  
 Tokenname: Category.color  
  
 Standard  
  
 Hintergrund  
  
 Transparent  
  
 Vordergrund (Text)  
  
 `Environment.CommandBarTextActive`  
  
 Rahmen  
  
 Keiner  
  
 Ausgewählt (aktiv)  
  
 Hintergrund  
  
 `TreeView.SelectedItemActive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemActiveText`  
  
 Rahmen  
  
 Keiner  
  
 Ausgewählt (inaktiv)  
  
 Hintergrund  
  
 `TreeView.SelectedItemInactive`  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemInactiveText`  
  
 Rahmen  
  
 Keiner  
  
## <a name="manifest-designer"></a>Manifest-Designer  
 Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Manifest-Designer (rote Linie)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
 Empfohlen...  
 -   für Designer, die Ähnlichkeit mit dem Manifest-Designer haben.  
  
-   anstelle allgemeiner Registerkarten-Steuerelemente, die im oberen Bereich eines Editors im Dokumentursprung angezeigt werden.  
  
 Nicht empfohlen...  
 -   bei Verwendung von mehr als sechs Registerkarten  
  
-   für Benutzeroberflächenelemente, die nicht wie der Manifest-Designer aufgebaut sind  
  
 Zustand  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 Standard (ausgewählt)  
  
 Registerkarte  
  
 Hintergrund  
  
 `ManifestDesigner.TabActive`  
  
 Rahmen  
  
 Keine  
  
 Beschreibungsbereich  
  
 Hintergrund  
  
 `ManifestDesigner.DescriptionPane`  
  
 Inhaltsseite  
  
 Hintergrund  
  
 `ManifestDesigner.Background`  
  
 Dialogfeld-Hilfetext  
  
 `ManifestDesigner.WatermarkText`  
  
 Dieser Tokenname stimmt nicht mit seiner Funktion überein.  
  
 Nicht ausgewählt  
  
 Registerkarte  
  
 Hintergrund  
  
 `ManifestDesigner.Tab.Inactive`  
  
 Darauf zeigen (Hover)  
  
 Registerkarte  
  
 Hintergrund  
  
 `ManifestDesigner.Tab.Mouseover`  
  
## <a name="tagging"></a>Tagging  
 Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.  
  
 ![Tagging (rote Linie)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")  
  
 Empfohlen...  
 für Benutzeroberflächen, die Tags unterstützen.  
  
 Nicht empfohlen...  
 für andere Arten von Benutzeroberflächenelementen  
  
### <a name="tag"></a>Tag  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")  
  
 **Default**  
  
 Hintergrund  
  
 `Tag.Background`  
  
 Vordergrund (Text)  
  
 `Tag.Background`  
  
 ![Tag, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")  
  
 **Gezeigt wird**  
  
 Hintergrund  
  
 `Tag.HoverBackground`  
  
 Vordergrund (Text)  
  
 `Tag.HoverBackgroundText`  
  
 ![Tag, aufgerufen](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")  
  
 **Gedrückt**  
  
 Hintergrund  
  
 `Tag.PressedBackground`  
  
 Vordergrund (Text)  
  
 `Tag.PressedBackgroundText`  
  
 ![Tag, ausgewählt](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")  
  
 **Ausgewählt**  
  
 Hintergrund  
  
 `Tag.SelectedBackground`  
  
 Vordergrund (Text)  
  
 `Tag.SelectedBackgroundText`  
  
### <a name="glyph-close-icon"></a>Glyphe (Schließsymbol)  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag &#40; Symbol &#41;](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")  
  
 **Standard (Tag Standard)**  
  
 Hintergrund  
  
 N/V  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagHoverGlyph`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag &#40; Symbol &#41; Wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")  
  
 **Gezeigt wird (Standard Tag)**  
  
 Hintergrund  
  
 `Tag.TagHoverGlyphHoverBackground`  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagHoverGlyphHover`  
  
 Rahmen  
  
 `Tag.TagHoverGlyphHoverBorder`  
  
 **Gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag &#40; Symbol &#41; gedrückt](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")  
  
 **Gedrückt (Tag Standard)**  
  
 Hintergrund  
  
 `Tag.TagHoverGlyphPressedBackground`  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagHoverGlyphPressed`  
  
 Rahmen  
  
 `Tag.TagHoverGlyphPressedBorder`  
  
 **Tag ausgewählt/Standardglyphe**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag, ausgewählt](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")  
  
 **Standard (Tag ausgewählt)**  
  
 Hintergrund  
  
 N/V  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagSelectedGlyph`  
  
 **Tag ausgewählt/Symbols gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag (ausgewählt), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")  
  
 **Gezeigt wird (Tag ausgewählt)**  
  
 Hintergrund  
  
 `Tag.TagSelectedGlyphHoverBackground`  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagSelectedGlyphHover`  
  
 Rahmen  
  
 `Tag.TagSelectedGlyphHoverBorder`  
  
 **Tag-ausgewählt/Symbols gedrückt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Tag (ausgewählt), aufgerufen](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")  
  
 **Gedrückt (Tag, ausgewählt)**  
  
 Hintergrund  
  
 `Tag.TagSelectedGlyphPressedBackground`  
  
 Vordergrund (Glyphe)  
  
 `Tag.TagSelectedGlyphPressed`  
  
 Rahmen  
  
 `Tag.TagSelectedGlyphPressedBorder`  
  
## <a name="shell"></a>Shell  
  
### <a name="background"></a>Hintergrund  
 Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Ab Visual Studio 2013 werden die obere und untere Hintergrundebene im dunklen und hellen Design auf dieselbe Farbe festgelegt.  
  
 ![Shell-Hintergrund (rote Linie)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Empfohlen...  
 für Bereiche, die an den Hintergrund der Visual Studio-Umgebung angepasst werden sollen.  
  
 Nicht empfohlen...  
 -   als Füllung für Bereiche, die keine Hintergrundoberflächen sind  
  
-   als Hintergrund, auf dem Vordergrundelemente platziert werden sollen  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 Untere Ebene  
  
 Hintergrund  
  
 `Environment.EnvironmentBackground`  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 Obere Ebene  
  
 Hintergrund  
  
 *Farbverlaufstopps auf den gleichen Farbwert in Visual Studio 2013 Licht und Dunkeln Designs festgelegt.*  
  
 `Environment.EnvironmentBackgroundGradientBegin`  
  
 `Environment.EnvironmentBackgroundGradientEnd`  
  
 `Environment.EnvironmentBackgroundGradientMiddle1`  
  
 `Environment.EnvironmentBackgroundGradientMiddle2`  
  
### <a name="command-shelf"></a>Befehlsablage  
 Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.  
  
 ![Befehlsleiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")  
  
 Empfohlen...  
 -   für Bereiche, in denen Menüs oder Symbolleisten platziert werden.  
  
-   mit dem richtigen Hintergrund /? token Foreground-Kombination.  
  
 Nicht empfohlen...  
 für Bereiche, die keine Ähnlichkeit mit einer Befehlsablage aufweisen  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 Menüleiste  
  
 Hintergrund  
  
 *Farbverlaufstopps auf den gleichen Farbwert in Visual Studio 2013 Licht und Dunkeln Designs festgelegt.*  
  
 `Environment.CommandShelfHighlightGradientBegin`  
  
 `Environment.CommandShelfHighlightGradientMiddle`  
  
 `Environment.CommandShelfHighlightGradientEnd`  
  
 Befehlsleiste  
  
 Hintergrund  
  
 *Farbverlaufstopps auf den gleichen Farbwert in Visual Studio 2013 Licht und Dunkeln Designs festgelegt.*  
  
 `Environment.CommandShelfBackgroundGradientBegin`  
  
 `Environment.CommandShelfBackgroundGradientMiddle`  
  
 `Environment.CommandShelfBackgroundGradientEnd`  
  
## <a name="toolbox"></a>Werkzeugkasten  
 Der Werkzeugkasten ist eines der allgemeinen Toolfenster, die am häufigsten in Visual Studio verwendet werden. Es handelt sich um ein Struktursteuerelement, auf das ein bestimmtes Design und ein bestimmter Stil angewendet wurde.  
  
 ![Toolbox (rote Linie)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")  
  
 Empfohlen...  
 für den Entwurf eines Toolfensters, das immer mit dem Shell-Werkzeugkasten konsistent sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die keine Ähnlichkeit mit der Werkzeugkasten-Benutzeroberfläche haben, oder wenn Sie nicht sicher sind, ob Ihre Benutzeroberfläche bei Änderung der Farben des Shell-Werkzeugkastens Probleme verursacht  
  
 **Default**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolbox, übergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")  
  
 **Übergeordneter Knoten**  
  
 ![Toolbox, untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")  
  
 **Untergeordnete Knoten**  
  
 Hintergrund  
  
 `Environment.ToolboxContent`  
  
 Kopfzeilen  
  
 `Environment.ToolWindowBackground`  
  
 Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind.  
  
 Rahmen  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `Environment.ToolboxContent`  
  
 Vordergrund (Text)  
  
 `Environment.ToolboxContent`  
  
 **Gezeigt wird**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")  
  
 **Toolbox Hover in untergeordneten Knoten**  
  
 Hintergrund  
  
 `Environment.ToolboxContentMouseOver`  
  
 Nur einzelne Elemente  
  
 Rahmen  
  
 Keine  
  
 Vordergrund (Text)  
  
 `Environment.ToolboxContentMouseOver`  
  
 Nur einzelne Elemente  
  
 **Ausgewählt**  
  
 Komponente  
  
 Element  
  
 Tokenname: Category.color  
  
 ![Toolbox (übergeordneter Knoten) mit Fokus](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")  
  
 **Fokussierte übergeordneter Knoten**  
  
 ![Toolbox (untergeordneter Knoten) mit Fokus](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")  
  
 **Fokussierte untergeordnete Knoten**  
  
 Hintergrund  
  
 `TreeView.SelectedItemActive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 Rahmen  
  
 `TreeView.FocusVisualBorder`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemActive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemActive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 ![Toolbox (übergeordneter Knoten) ohne Fokus](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")  
  
 **Ohne Fokus übergeordneter Knoten**  
  
 ![Toolbox (untergeordneter Knoten) ohne Fokus](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")  
  
 **Ohne Fokus untergeordneter Knoten**  
  
 Hintergrund  
  
 `TreeView.SelectedItemInactive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 Rahmen  
  
 Keine  
  
 Vordergrund (Glyphe)  
  
 `TreeView.SelectedItemInactive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie  
  
 Vordergrund (Text)  
  
 `TreeView.SelectedItemInactive`  
  
 Aus [Strukturansicht](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) Kategorie