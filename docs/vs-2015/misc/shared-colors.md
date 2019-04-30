---
title: Freigegebene Farben | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436574"
---
# <a name="shared-colors"></a>Konsistente Farben
Fügen Sie hier eine Einleitung ein.  
  
## <a name="shared-colors"></a>Konsistente Farben  
 Wenn Sie Ihre Benutzeroberfläche mit gängigen Visual Studio Shell-Elementen gestalten möchten oder Ihr Benutzeroberflächenelement konsistent mit ähnlichen Features sein soll, können Sie die Tokennamen aus den Paketdefinitionsdateien verwenden, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.  
  
 In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:  
  
- **Verwenden Sie Tokennamen nach Funktion und nicht nach Farbe.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Das Kombinationsfeld und die Animation erfüllen unterschiedliche Funktionen, und wenn sich die dem Kombinationsfeld zugeordnete Farbe ändert, eignet sie sich möglicherweise nicht mehr für Ihr Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.  
  
- **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination aus.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn keine zugeordnete Textfarbe vorhanden ist, sollte diese Hintergrundfarbe auf Oberflächen, auf denen erwartungsgemäß Text angezeigt wird, nicht verwendet werden. Andere Kombinationen aus Text- und Hintergrundfarbe können dazu führen, dass die Benutzeroberfläche unlesbar wird.  
  
- **Verwenden Sie steuerelementfarben, die für die jeweilige Position geeignet sind.** Für bestimmte Zustände einiger Visual Studio-Steuerelemente sind keine separaten Rahmen- und Hintergrundfarben verfügbar. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.  
  
> [!IMPORTANT]
> Verwenden Sie keine Token aus den Kategorien "Startseite" oder "Cider".  
  
### <a name="command-structures"></a>Befehlsstrukturen  
  
#### <a name="BKMK_CommandMenus"></a> Menüs  
 Menüs können an mehreren Stellen in Visual Studio 2013 vorkommen: in der Hauptmenüleiste, eingebettet in Dokument- oder Toolfenster oder beim Rechtsklicken an verschiedenen Stellen der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.  
  
 ![(Rote Linie) der Menüs](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Empfohlen...  
- für die Erstellung eines benutzerdefinierten Menüs  
  
- für eine neue Benutzeroberflächenkomponente, die auf die Visual Studio-Menüs abgestimmt werden soll.  
  
Nicht empfohlen...  
als ausschließliche Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe.  
  
##### <a name="menu-title"></a>Menütitel  
 Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.  
  
 ![Menütitel (rote Linie,)](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Empfohlen...  
für die Erstellung eines benutzerdefinierten Menütitels  
  
Nicht empfohlen...  
- für Elemente, die nicht grundsätzlich auf den Menütitel abgestimmt sein sollen  
  
- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Standard für Menütitel](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menütitel**|Hintergrund|Keiner|  
|![Standard für Menütitel](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menütitel mit Standardglyphe](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuGlyph`|  
|![Menütitel mit Standardglyphe](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Menütitel mit Glyphe**|Rahmen|Keiner|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menütitel, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menütitel**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menütitel, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Menütitel mit Glyphe, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Menütitel mit Glyphe, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Menütitel mit Glyphe**|Rahmen|`Environment.CommandBarBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menütitel, aufgerufen](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menütitel**|Hintergrund|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menütitel, aufgerufen](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menütitel mit Glyphe, gedrückt](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Menütitel mit Glyphe, gedrückt](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Menütitel mit Glyphe**|Rahmen|`Environment.CommandBarMenuBorder`<br /><br /> Nur linke, obere und rechte Seite|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menütitel mit Standardglyphe in deaktiviertem Zustand](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Hintergrund|Keiner|  
|![Menütitel mit Standardglyphe in deaktiviertem Zustand](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Menütitel mit Standardglyphe in deaktiviertem Zustand](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarTextInactive`|  
|![Menütitel mit Standardglyphe in deaktiviertem Zustand](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Rahmen|Keiner|  
  
##### <a name="menu"></a>Menü  
 Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.  
  
 ![(Rote Linie) der Menüelemente](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Empfohlen...  
 für alle Dropdownlisten, die von einer Menü- oder Befehlsleiste geöffnet werden.  
  
Nicht empfohlen...  
- für Dropdownlisten, die in einem anderen Kontext vorkommen  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Hintergrund|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Rahmen|`Environment.CommandBarMenuBorder`|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Symbolkanal-Hintergrund|`Environment.CommandBarMenuIconBackground`|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Trennzeichen|`Environment.CommandBarMenuSeparator`|  
|![Menüstandard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Schatten|`Environment.DropShadowBackground`|  
|![Im Menü](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Aktiviert**|Häkchen|`Environment.CommandBarCheckBox`|  
|![Im Menü](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Aktiviert**|Häkchenhintergrund|`Environment.CommandBarSelectedIcon`|  
|![Ausgewählte Menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **ausgewählt**|Symbolhintergrund|`Environment.CommandBarSelected`|  
|![Ausgewählte Menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **ausgewählt**|Symbolrahmen|`Environment.CommandBarSelectedBorder`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Zeigen Sie die im Menü](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Hintergrund|`Environment.CommandBarMenuItemMouseOver`|  
|![Zeigen Sie die im Menü](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Vordergrund (Text)|`Environment.CommandBarMenuItemMouseOver`|  
|![Zeigen Sie die im Menü](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menü "Wenn darauf gezeigt wird überprüft,](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Aktiviert**|Häkchen|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menü "Wenn darauf gezeigt wird überprüft,](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Aktiviert**|Häkchenhintergrund|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menü zeigen Sie ausgewählte](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **ausgewählt**|Symbolhintergrund|`Environment.CommandBarHoverOverSelected`|  
|![Menü zeigen Sie ausgewählte](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **ausgewählt**|Symbolrahmen|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menü, deaktiviert](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menüelement|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Menü, deaktiviert](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menüelement|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü, deaktiviert (geprüft)](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Aktiviert|Häkchen|`Environment.CommandBarCheckBoxDisabled`|  
|![Menü, deaktiviert (geprüft)](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Aktiviert|Häkchenhintergrund|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Befehlsleiste  
 Die Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE vorkommen, vor allem in der Befehlsablage und eingebettet in Tool- oder Dokumentfenster.  
  
 Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.  
  
 ![(Rote Linie) der Befehlsleiste](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![(Rote Linie) der Schaltfläche "Überlauf"](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  

- für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
##### <a name="command-bar-group"></a>Befehlsleistengruppe  
 Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.  
  
 ![Befehlszeilengruppe (rote Linie,)](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  

- für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
  **Standard** (kein weiterer Zustand)  
  
|Element|Tokenname: Category.Color|  
|-------------|--------------------------------|  
|Hintergrund|`Environment.CommandBarGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|Rahmen|`Environment.CommandBarToolBarBorder`|  
|Ziehpunkt|`Environment.CommandBarDragHandle`|  
|Trennzeichen|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Befehlssymbole  
 ![Befehlssymbol](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Befehlssymbol](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Empfohlen...  
 für alle Schaltflächen, die auf einer Befehlsleiste platziert werden.  
  
Nicht empfohlen...  
- für Steuerelemente, die ihren eigenen Tokennamen haben  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Standardmäßiges Befehlssymbol Befehl](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Default**|Hintergrund|N/V (erbt vom Befehlsleisten-Hintergrund)|  
|![Standardmäßiges Befehlssymbol Befehl](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Default**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Standardmäßiges Befehlssymbol Befehl](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Default**|Rahmen|Nicht zutreffend|  
|![Standardmäßiges Befehlssymbol ausgewählt Befehl](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **ausgewählt**|Hintergrund|`Environment.CommandBarSelected`|  
|![Standardmäßiges Befehlssymbol ausgewählt Befehl](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **ausgewählt**|Vordergrund (Text)|`Environment.CommandBarTextSelected`|  
|![Standardmäßiges Befehlssymbol ausgewählt Befehl](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **ausgewählt**|Rahmen|`Environment.CommandBarSelectedBorder`|  
  
 **Hover- und Tastaturfokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Zeigen Sie das Symbol der Befehl](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard, wenn darauf gezeigt wird**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Zeigen Sie das Symbol der Befehl](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard, wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Zeigen Sie das Symbol der Befehl](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard, wenn darauf gezeigt wird**|Rahmen|`Environment.CommandBarBorder`|  
|![Symbol gezeigt wird, die ausgewählten Befehl](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Ausgewählt, wenn darauf gezeigt wird**|Hintergrund|`Environment.CommandBarHoverOverSelected`|  
|![Symbol gezeigt wird, die ausgewählten Befehl](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Ausgewählt, wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.CommandBarTextHoverOverSelected`|  
|![Symbol gezeigt wird, die ausgewählten Befehl](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Ausgewählt, wenn darauf gezeigt wird**|Rahmen|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Befehlssymbol, aufgerufen](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehlssymbol**|Hintergrund|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Befehlssymbol, aufgerufen](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehlssymbol**|Vordergrund (Text)|`Environment.CommandBarTextMouseDown`|  
|![Befehlssymbol, aufgerufen](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehlssymbol**|Rahmen|`Environment.CommandBarBorder`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Befehlssymbol, deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehlssymbol**|Hintergrund|N/V (erbt vom Befehlsleisten-Hintergrund)|  
|![Befehlssymbol, deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehlssymbol**|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Befehlssymbol, deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehlssymbol**|Rahmen|Nicht zutreffend|  
  
##### <a name="BKMK_CommandComboBox"></a> Kombinationsfeld  
  
> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn Ihr Dropdown keinen bearbeitbaren Textbereich enthält, verwenden Sie die unter [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown)beschriebenen Farbtoken.  
  
 ![Kombinationsfeld (rote Linie,)](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Empfohlen...  
- für die Erstellung benutzerdefinierter Kombinationsfelder  

- für die Erstellung eines Befehlsleisten-Steuerelements, das Ähnlichkeit mit einem Kombinationsfeld hat.  

Nicht empfohlen...  
- für Elemente, die nicht grundsätzlich auf die Befehlsleisten-Benutzeroberfläche abgestimmt sein müssen  

- wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Kombinationsfeld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxBackground`|  
|![Kombinationsfeld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxText`|  
|![Kombinationsfeld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxBorder`|  
|![Kombinationsfeld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Trennzeichen|Kein Trennzeichen|  
|![Kombinationsfeld-Dropdown&#45;gedrückt](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|N/V (erbt)|  
|![Kombinationsfeld-Dropdown&#45;gedrückt](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxGlyph`|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown-Liste**|Hintergrund|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown-Liste**|Vordergrund (Text)|`Environment.ComboBoxItemText`|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown-Liste**|Rahmen|`Environment.ComboBoxPopupBorder`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Kombinationsfeld (Eingabefeld) bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kombinationsfeld (Eingabefeld) bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxMouseOverText`|  
|![Kombinationsfeld (Eingabefeld) bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxMouseOverBorder`|  
|![Kombinationsfeld (Eingabefeld) bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxMouseOverSeparator`|  
|![Das Kombinationsfeld&#47;löschen&#45;gedrückt, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Das Kombinationsfeld&#47;löschen&#45;gedrückt, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxMouseOverGlyph`|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown-Liste**|Hintergrund (Menüelement)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown-Liste**|Vordergrund (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Das Kombinationsfeld&#47;löschen&#45;-Liste bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown-Liste**|Rahmen (Menüelement)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinationsfeld (Eingabefeld) mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxFocusedBackground`|  
|![Kombinationsfeld (Eingabefeld) mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxFocusedText`|  
|![Kombinationsfeld (Eingabefeld) mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxFocusedBorder`|  
|![Kombinationsfeld (Eingabefeld) mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Das Kombinationsfeld&#47;löschen&#45;ab-Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`Environment.ComboBoxFocusedButtonBackground`|  
|![Das Kombinationsfeld&#47;löschen&#45;ab-Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinationsfeld (Eingabefeld) gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxMouseDownBackground`|  
|![Kombinationsfeld (Eingabefeld) gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxMouseDownText`|  
|![Kombinationsfeld (Eingabefeld) gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxMouseDownBorder`|  
|![Kombinationsfeld (Eingabefeld) gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxMouseDownSeparator`|  
|![Das Kombinationsfeld&#47;löschen&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Das Kombinationsfeld&#47;löschen&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinationsfeld (Eingabefeld) deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxDisabledBackground`|  
|![Kombinationsfeld (Eingabefeld) deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxDisabledText`|  
|![Kombinationsfeld (Eingabefeld) deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxDisabledBorder`|  
|![Kombinationsfeld (Eingabefeld) deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Trennzeichen|Kein Trennzeichen|  
|![Das Kombinationsfeld&#47;löschen&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|Keiner|  
|![Das Kombinationsfeld&#47;löschen&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="BKMK_CommandDropDown"></a> Dropdown-Liste  
  
> [!IMPORTANT]
> Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich enthält, verwenden Sie die unter [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox)beschriebenen Farbtoken.  
  
 ![Drop&#45;nach unten (rote Linie)](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Empfohlen...  
 für die Erstellung benutzerdefinierter Dropdownlisten-Steuerelemente  
  
Nicht empfohlen...  
- für Elemente, die keine Ähnlichkeit mit einer Dropdownliste haben  

- für Kombinationsfelder oder unterteilte Schaltflächen  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownBackground`|  
|![Drop&#45;unten Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`DropDownText`|  
|![Drop&#45;unten Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Rahmen|`DropDownBorder`|  
|![Drop&#45;unten Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Trennzeichen|Kein Trennzeichen|  
|![Drop&#45;gedrückt](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|Keiner|  
|![Drop&#45;gedrückt](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownGlyph`|  
|![Drop&#45;-Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown-Liste**|Hintergrund|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Drop&#45;-Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown-Liste**|Vordergrund (Text)|`Environment.ComboBoxItemText`|  
|![Drop&#45;-Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown-Liste**|Rahmen|`Environment.DropDownPopupBorder`|  
|![Drop&#45;-Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown-Liste**|Schatten|`Environment.DropShadowBackground`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten Auswahlfeld bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Drop&#45;unten Auswahlfeld bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`Environment.DropDownMouseOverText`|  
|![Drop&#45;unten Auswahlfeld bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Rahmen|`Environment.DropDownMouseOverBorder`|  
|![Drop&#45;unten Auswahlfeld bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Trennzeichen|`Environment.DropDownButtonMouseOverSeparator`|  
|![Drop&#45;gedrückt, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`Environment.DropDownButtonMouseOverBackground`|  
|![Drop&#45;gedrückt, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownMouseOverGlyph`|  
|![Drop&#45;down list on hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown-Liste**|Hintergrund (Menüelement)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Drop&#45;down list on hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown-Liste**|Vordergrund (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Drop&#45;down list on hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown-Liste**|Rahmen (Menüelement)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownMouseDownBackground`|  
|![Drop&#45;unten Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`Environment.DropDownMouseDownText`|  
|![Drop&#45;unten Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Rahmen|`Environment.DropDownMouseDownBorder`|  
|![Drop&#45;unten Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Trennzeichen|`Environment.DropDownButtonMouseDownSeparator`|  
|![Drop&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`Environment.DropDownButtonMouseDownBackground`|  
|![Drop&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Hintergrund|`Environment.DropDownDisabledBackground`|  
|![Drop&#45;unten Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Vordergrund (Text)|`Environment.DropDownDisabledText`|  
|![Drop&#45;unten Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Rahmen|`Environment.DropDownDisabledBorder`|  
|![Drop&#45;unten Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Trennzeichen|Kein Trennzeichen|  
|![Drop&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Hintergrund|Nicht zutreffend|  
|![Drop&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Vordergrund (Glyphe)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Trennschaltfläche  
 Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Dropdownlisten für unterteilte Schaltflächen sind Implementierungen der Befehlsleiste [Menus](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Trennschaltfläche (rote Linie,)](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten unterteilten Schaltfläche  
  
Nicht empfohlen...  
- für alle anderen Arten von Schaltflächen  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Unterteilte Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Unterteilte Schaltfläche (Standard)**|Hintergrund|Keiner|  
|![Unterteilte Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Unterteilte Schaltfläche (Standard)**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Unterteilte Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Unterteilte Schaltfläche (Standard)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonGlyph`|  
|![Unterteilte Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Unterteilte Schaltfläche (Standard)**|Rahmen|Nicht zutreffend|  
|![Unterteilte Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Unterteilte Schaltfläche (Standard)**|Trennzeichen|Nicht zutreffend|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (wenn darauf gezeigt wird)**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (wenn darauf gezeigt wird)**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (wenn darauf gezeigt wird)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (wenn darauf gezeigt wird)**|Rahmen|`Environment.CommandBarBorder`|  
|![Unterteilte Schaltfläche, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (wenn darauf gezeigt wird)**|Trennzeichen|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Unterteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Unterteilte Schaltfläche (gedrückt)**|Hintergrund|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Unterteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Unterteilte Schaltfläche (gedrückt)**|Vordergrund (Text)|`Environment.CommandBarTextMouseDown`|  
|![Unterteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Unterteilte Schaltfläche (gedrückt)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Unterteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Unterteilte Schaltfläche (gedrückt)**|Rahmen|`Environment.CommandBarBorder`|  
|![Unterteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Unterteilte Schaltfläche (gedrückt)**|Trennzeichen|Nicht zutreffend|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Unterteilte Schaltfläche, deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Unterteilte Schaltfläche (deaktiviert)**|Hintergrund|Nicht zutreffend|  
|![Unterteilte Schaltfläche, deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Unterteilte Schaltfläche (deaktiviert)**|Vordergrund (Text)|`Environment.ComboBoxItemTextInactive`|  
|![Unterteilte Schaltfläche, deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Unterteilte Schaltfläche (deaktiviert)**|Vordergrund (Glyphe)|`Environment.CommandBarTextInactive`|  
|![Unterteilte Schaltfläche, deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Unterteilte Schaltfläche (deaktiviert)**|Rahmen|Nicht zutreffend|  
|![Unterteilte Schaltfläche, deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Unterteilte Schaltfläche (deaktiviert)**|Trennzeichen|Nicht zutreffend|  
  
##### <a name="more-options-and-overflow-buttons"></a>Schaltflächen "Weitere Optionen" und "Überlauf"  
 Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.  
  
 ![Weitere Optionen (rote Linie,)](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Empfohlen...  
 für die benutzerdefinierten Schaltflächen "Weitere Optionen" oder "Überlauf"  
  
 Nicht empfohlen...  
 für Schaltflächen mit einer von den Schaltflächen "Weitere Optionen" oder "Überlauf" abweichenden Funktionalität  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsBackground`|  
|![Weitere Optionen](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsGlyph`|  
|![Schaltfläche "Überlauf"](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Overflow**|Hintergrund|`Environment.CommandBarOptionsBackground`|  
|![Schaltfläche "Überlauf"](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Overflow**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsGlyph`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Weitere Optionen bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Bei einer mauszeigerbewegung über Overflow](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Overflow**|Hintergrund|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Bei einer mauszeigerbewegung über Overflow](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Overflow**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen gedrückt](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Weitere Optionen gedrückt](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Overflow**|Hintergrund|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Overflow**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Dokumentfenster  
 Dokumentfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 Wenn Sie Dokumentfenster-Farbtoken verwenden, dürfen diese nur für ähnliche Elemente und paarweise verwendet werden. Andernfalls zeigen sich auf der Benutzeroberfläche unerwartete Ergebnisse.  
  
#### <a name="document-window-frame"></a>Dokumentfensterrahmen  
 Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Ein unverankertes Dokumentfenster, das sich außerhalb der IDE befindet, ist dennoch in einen Dokumentursprung eingebettet und verfügt über Hintergrund-, Rahmen-, Text- und Registerkartenfarben, die sich von den Farben der in der IDE angedockten Fenster nicht unterscheiden. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.  
  
 ![Angedocktes Dokumentfenster (rote Linie,)](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Angedocktes Dokumentfenster**  
  
 ![Unverankertes Dokumentfenster (rote Linie)](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Unverankertes Dokumentfenster**  
  
 Empfohlen...  
 für alle Benutzeroberflächenelemente, die Sie auf das Dokumentfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|Dokument: angedockt oder unverankert|Hintergrund|Hängt vom Dokumenttyp ab.|  
|Dokument: angedockt oder unverankert|Vordergrund (Text)|Hängt vom Dokumenttyp ab.|  
|Dokument: angedockt oder unverankert|Rahmen|`Environment.ToolWindowBorder`|  
|![Rahmen mit Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rahmen: unverankert, mit Fokus**|Hintergrund|`Environment.ToolWindowFloatingFrame`|  
|![Rahmen mit Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rahmen: unverankert, mit Fokus**|Vordergrund (Text)|`Environment.ToolWindowFloatingFrame`|  
|![Rahmen mit Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rahmen: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Rahmen mit Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rahmen: unverankert, mit Fokus**|Rahmen|`Environment.MainWindowActiveDefaultBorder`|  
|![Rahmen mit Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rahmen: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Auf transparent festgelegt|  
|![Rahmen ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Hintergrund|`Environment.ToolWindowFloatingFrameInactive`|  
|![Rahmen ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Vordergrund (Text)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Rahmen ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Rahmen ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Rahmen|`Environment.MainWindowInactiveBorder`|  
|![Rahmen ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Auf transparent festgelegt|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Rahmen mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rahmen: unverankert, mit Fokus**|Hintergrund (Glyphe)|`Environment.RaftedWindowButtonHoverActive`|  
|![Rahmen mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rahmen: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Rahmen mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rahmen: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Rahmen ohne Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Hintergrund (Glyphe)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Rahmen ohne Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Rahmen ohne Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rahmen: unverankert, ohne Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Rahmen mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rahmen: unverankert, mit Fokus**|Hintergrund (Glyphe)|`Environment.RaftedWindowButtonDown`|  
|![Rahmen mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rahmen: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Rahmen mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rahmen: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Dokumentregisterkarten  
 Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.  
  
 ![(Rote Linie) der Registerkarte "Dokument"](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Empfohlen...  
 für jede Benutzeroberfläche, die auf Dokumentregisterkarten abgestimmt sein soll, und wenn Designaktualisierungen oder neue Designfarben automatisch ausgewählt werden sollen.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
##### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten  
 Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:  
  
- Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.  
  
- Hintergrundregisterkarten sind Dokumentregisterkarten, die nicht der aktuell ausgewählten Registerkarte entsprechen. Sobald auf die Registerkarte geklickt wird, wird sie zur ausgewählten Registerkarte, die alle Hintergrund-, Rahmen- und Textfarben von den Tokennamen übernimmt.  
  
  ![(Rote Linie) der Registerkarte "Dokument öffnen"](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Empfohlen...  
  für die Erstellung benutzerdefinierter Dokumentregisterkarten  
  
  Nicht empfohlen...  
  - für vorläufige Registerkarten (Vorschau)  
  
- für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
##### <a name="selected-tab"></a>Ausgewählte Registerkarte  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, mit Fokus**|Hintergrund|`Environment.FileTabSelectedGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, mit Fokus**|Vordergrund (Text)|`Environment.FileTabSelectedText`|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, mit Fokus**|Rahmen|`Environment.FileTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, mit Fokus**|Dokumentrahmen|`Environment.FileTabDocumentBorderBackground`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, ohne Fokus**|Hintergrund|`Environment.FileTabInactiveGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, ohne Fokus**|Vordergrund (Text)|`Environment.FileTabInactiveText`|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, ohne Fokus**|Rahmen|`Environment.FileTabInactiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokumentregisterkarte, ohne Fokus**|Dokumentrahmen|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Hintergrundregisterkarte  
 **Default**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Hintergrund"](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Hintergrundregisterkarte, Standard**|Hintergrund|`Environment.FileTabBackground`|  
|![Registerkarte "Hintergrund"](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Hintergrundregisterkarte, Standard**|Vordergrund (Text)|`Environment.FileTabText`|  
|![Registerkarte "Hintergrund"](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Hintergrundregisterkarte, Standard**|Rahmen|`Environment.FileTabBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund", wenn darauf gezeigt wird**|Hintergrund|`Environment.FileTabHotGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund", wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.FileTabHotText`|  
|![Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund", wenn darauf gezeigt wird**|Rahmen|`Environment.FileTabHotBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
##### <a name="preview-tab"></a>Vorschauregisterkarte  
 Die Vorschauregisterkarte wird auf der rechten Seite des Dokument-Registerkartenkanals angezeigt, wenn der Benutzer auf ein Element im Toolfenster des Projektmappen-Explorers klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.  
  
 ![(Rote Linie) der Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Empfohlen...  
 wenn Sie eine vorläufige Vorschau erstellen und Elemente mit der Farbe der aktuellen Vorschauregisterkarte übereinstimmen sollen.  
  
Nicht empfohlen...  
- für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau)  

- für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
  **Ausgewählte vorschauregisterkarte: Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Vorschauregisterkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschauregisterkarte mit Fokus**|Hintergrund|`Environment.FileTabProvisionalSelectedActive`|  
|![Vorschauregisterkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschauregisterkarte mit Fokus**|Vordergrund (Text)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Vorschauregisterkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschauregisterkarte mit Fokus**|Rahmen|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Vorschauregisterkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschauregisterkarte mit Fokus**|Dokumentrahmen|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Ausgewählte vorschauregisterkarte: Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Vorschau" ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Vorschauregisterkarte**|Hintergrund|`Environment.FileTabProvisionalSelectedInactive`|  
|![Registerkarte "Vorschau" ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Vorschauregisterkarte**|Vordergrund (Text)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Registerkarte "Vorschau" ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Vorschauregisterkarte**|Rahmen|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Registerkarte "Vorschau" ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Vorschauregisterkarte**|Dokumentrahmen|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Registerkarte "Vorschau" Hintergrund: Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hintergrund-Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Vorschau-/ Hintergrundregisterkarte**|Hintergrund|`Environment.FileTabProvisionalInactive`|  
|![Hintergrund-Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Vorschau-/ Hintergrundregisterkarte**|Vordergrund (Text)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Hintergrund-Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Vorschau-/ Hintergrundregisterkarte**|Rahmen|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Registerkarte "Vorschau" Hintergrund: Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Vorschau Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Vorschau-/ Hintergrundregisterkarte wenn darauf gezeigt wird**|Hintergrund|`Environment.FileTabProvisionalHover`|  
|![Registerkarte "Vorschau Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Vorschau-/ Hintergrundregisterkarte wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.FileTabProvisionalHoverForeground`|  
|![Registerkarte "Vorschau Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Vorschau-/ Hintergrundregisterkarte wenn darauf gezeigt wird**|Rahmen|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
##### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche  
 Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dokumentüberlauf-Dropdownmenü, das mithilfe der **CommandBarMenu** -Farben (siehe [Menus](../misc/shared-colors.md#BKMK_CommandMenus)) gesteuert wird, zeigt eine Liste aller geöffneten Dokumente (sichtbar und unsichtbar) an. Die Überlauf-Glyphe ändert sich abhängig davon, ob alle geöffneten Dokumente im Registerkartenkanal angezeigt werden.  
  
 ![Overflow redline](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Empfohlen...  
für die Erstellung einer benutzerdefinierten Dokumentüberlauf-Schaltfläche  

Nicht empfohlen...  
- für Benutzeroberflächen, die keine Ähnlichkeit mit einer Überlaufschaltfläche haben  

- für Überlaufschaltflächen auf der Befehlsleiste  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokumentüberlauf-Schaltfläche**|Hintergrund|`Environment.DocWellOverflowButtonBackground`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokumentüberlauf-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonGlyph`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokumentüberlauf-Schaltfläche**|Rahmen|Nicht zutreffend|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bei einer mauszeigerbewegung über Overflow](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Dokumentüberlauf-Schaltfläche wenn darauf gezeigt wird**|Hintergrund|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Bei einer mauszeigerbewegung über Overflow](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Dokumentüberlauf-Schaltfläche wenn darauf gezeigt wird**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Bei einer mauszeigerbewegung über Overflow](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Dokumentüberlauf-Schaltfläche wenn darauf gezeigt wird**|Rahmen|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Gedrückte dokumentüberlauf-Schaltfläche**|Hintergrund|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Gedrückte dokumentüberlauf-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Gedrückte dokumentüberlauf-Schaltfläche**|Rahmen|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Toolfenster  
 Toolfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 ![Toolfenster (rote Linie,)](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
#### <a name="tool-window-frame"></a>Toolfensterrahmen  
 Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.  
  
 ![(Rote Linie) der Toolfensterrahmen](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Angedockt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolfenster angedockt](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Toolfenster angedockt](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Rahmen|`Environment.ToolWindowBorder`|  
  
 **Gleitkommawert: mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolfenster mit Fokus](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Toolfenster mit Fokus](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Rahmen|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Gleitkommawert: ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolfenster ohne Fokus](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Toolfenster ohne Fokus](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Rahmen|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters  
 Der Rahmen der Titelleiste ist kein echter Rahmen, sondern ein dicker Strich am oberen Rand der Titelleiste. Er verfügt über keinen Tokennamen für den Zustand "Ohne Fokus".  
  
 ![(Rote Linie) der Titelleiste des Toolfensters](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Hintergrund|`Environment.TitleBarActiveGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Vordergrund (Text)|`Environment.TitleBarActiveText`|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Rahmen|`Environment.TitleBarActiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Ziehpunkt|`Environment.TitleBarDragHandleActive`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Hintergrund|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Vordergrund (Text)|`Environment.TitleBarInactiveText`|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Rahmen|Nicht zutreffend|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Ziehpunkt|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Titelleisten-Schaltflächen  
 ![Titelleistenschaltfläche (rote Linie,)](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Empfohlen...  
 für Schaltflächen auf der Benutzeroberfläche, die Farbtoken aus den Toolfenster-Titelleisten verwenden.  
  
Nicht empfohlen...  
- für Schaltflächen, die an anderer Stelle angezeigt werden  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste mit Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Mit Fokus**|Hintergrund|Nicht zutreffend|  
|![Titelleiste mit Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Mit Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Titelleiste mit Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Mit Fokus**|Rahmen|Nicht zutreffend|  
|![Titelleiste ohne Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Hintergrund|Nicht zutreffend|  
|![Titelleiste ohne Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Titelleiste ohne Fokus Schaltfläche](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Rahmen|Nicht zutreffend|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Titelleistenschaltfläche mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Mit Fokus**|Hintergrund|`Environment.ToolWindowButtonHoverActive`|  
|![Titelleistenschaltfläche mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Mit Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Titelleistenschaltfläche mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Mit Fokus**|Rahmen|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Titelleiste ohne Fokus, wenn darauf gezeigt wird Schaltfläche](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Hintergrund|`Environment.ToolWindowButtonHoverInactive`|  
|![Titelleiste ohne Fokus, wenn darauf gezeigt wird Schaltfläche](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Titelleiste ohne Fokus, wenn darauf gezeigt wird Schaltfläche](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Rahmen|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste auf die Schaltfläche mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Mit Fokus**|Hintergrund|`Environment.ToolWindowButtonDown`|  
|![Titelleiste auf die Schaltfläche mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Mit Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Titelleiste auf die Schaltfläche mit Fokus, aufgerufen](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Mit Fokus**|Rahmen|`Environment.ToolWindowButtonDownBorder`|  
|![Titelleiste ohne Fokus und gedrückten zu Schaltfläche](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Hintergrund|`Environment.ToolWindowButtonDown`|  
|![Titelleiste ohne Fokus und gedrückten zu Schaltfläche](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Titelleiste ohne Fokus und gedrückten zu Schaltfläche](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Rahmen|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten  
 ![(Rote Linie) der Toolfenster-Registerkarte](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Ausgewählte Registerkarte**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Der Toolfenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählte, fokussierte Toolfenster-Registerkarte**|Hintergrund|`Environment.ToolWindowTabSelectedTab`|  
|![Der Toolfenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählte, fokussierte Toolfenster-Registerkarte**|Vordergrund (Text)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Der Toolfenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählte, fokussierte Toolfenster-Registerkarte**|Rahmen|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolfenster-Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählte, ohne Fokus Toolfenster-Registerkarte**|Hintergrund|`Environment.ToolWindowTabSelectedTab`|  
|![Toolfenster-Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählte, ohne Fokus Toolfenster-Registerkarte**|Vordergrund (Text)|`Environment.ToolWindowTabSelectedText`|  
|![Toolfenster-Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählte, ohne Fokus Toolfenster-Registerkarte**|Rahmen|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Registerkarte "Hintergrund"**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hintergrund der Toolfenster-Registerkarte](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Hintergrundregisterkarte im Toolfenster**|Hintergrund|`Environment.ToolWindowTabGradientBegin`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps|  
|![Hintergrund der Toolfenster-Registerkarte](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Hintergrundregisterkarte im Toolfenster**|Vordergrund (Text)|`Environment.ToolWindowTabText`|  
|![Hintergrund der Toolfenster-Registerkarte](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Hintergrundregisterkarte im Toolfenster**|Rahmen|`Environment.ToolWindowTabBorder`|  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tool-Fenster Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hintergrundregisterkarte im Toolfenster wenn darauf gezeigt wird**|Hintergrund|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps|  
|![Tool-Fenster Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hintergrundregisterkarte im Toolfenster wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.ToolWindowTabMouseOverText`|  
|![Tool-Fenster Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hintergrundregisterkarte im Toolfenster wenn darauf gezeigt wird**|Rahmen|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
#### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten  
 ![Automatische&#45;(rote Linie) der ausblenden](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf automatisch ausgeblendete Toolfenster-Registerkarten abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Automatische&#45;Registerkarte ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Automatisch ausgeblendete Registerkarte, Standard**|Hintergrund|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Automatische&#45;Registerkarte ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Automatisch ausgeblendete Registerkarte, Standard**|Vordergrund (Text)|`Environment.AutoHideTabText`|  
|![Automatische&#45;Registerkarte ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Automatisch ausgeblendete Registerkarte, Standard**|Rahmen|`Environment.AutoHideTabBorder`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Automatische&#45;blenden Sie die Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird**|Hintergrund|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Automatische&#45;blenden Sie die Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird**|Vordergrund (Text)|`Environment.AutoHideTabMouseOverText`|  
|![Automatische&#45;blenden Sie die Registerkarte "Hintergrundvorschau"](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird**|Rahmen|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente  
 Wenn Sie für Ihr Feature eine Visual Studio-Standardbefehlsleiste verwenden, haben Sie Zugriff auf formatierte Shell-Steuerelemente. Diese gemeinsam verwendeten Steuerelemente sollten nicht von einer Vorlage neu erstellt werden. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.  
  
#### <a name="search-box"></a>Suchfeld  
 Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.  
  
 Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:  
  
- "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.  
  
- "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.  
  
- "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).  
  
- "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.  
  
  ![Search box redline](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Empfohlen...  
  für das Entwerfen eines benutzerdefinierten Suchfelds  
  
  Nicht empfohlen...  
  - für Elemente, die kein Suchfeld darstellen  
  
- für Elemente, die nicht generell auf die Suchfeld-Benutzeroberfläche abgestimmt sein sollen  
  
  **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Schwerpunkt sucheingabefeld](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Hintergrund|`SearchControl.FocusedBackground`|  
|![Schwerpunkt sucheingabefeld](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`SearchControl.FocusedBackground`|  
|![Schwerpunkt sucheingabefeld](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Rahmen|`SearchControl.FocusedBorder`|  
|![Schwerpunkt sucheingabefeld](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Trennzeichen|`SearchControl.FocusedDropDownSeparator`|  
|![Suche (Aktionsschaltfläche) mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Schaltfläche "Aktion"**|Hintergrund|Keiner|  
|![Suche (Aktionsschaltfläche) mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Suchen")|`SearchControl.SearchGlyph`|  
|![Suche (Aktionsschaltfläche) mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Beenden")|`SearchControl.StopGlyph`|  
|![Suche (Aktionsschaltfläche) mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Löschen")|`SearchControl.ClearGlyph`|  
|![Suche (Aktionsschaltfläche) mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Schaltfläche "Aktion"**|Rahmen|Nicht zutreffend|  
|![Suche&#45;ab-Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`SearchControl.FocusedDropDownButton`|  
|![Suche&#45;ab-Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Suche&#45;ab-Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown-Schaltfläche**|Rahmen|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabefeld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Hintergrund|`SearchControl.SearchActiveBackground`|  
|![Sucheingabefeld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Vordergrund (Text)|`SearchControl.SearchActiveBackground`|  
|![Sucheingabefeld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Rahmen|`SearchControl.UnfocusedBorder`|  
|![Sucheingabefeld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Sucheingabefeld ohne Fokus und inaktiv](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Hintergrund|`SearchControl.Unfocused`|  
|![Sucheingabefeld ohne Fokus und inaktiv](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Vordergrund (Text)|`SearchControl.Unfocused`|  
|![Sucheingabefeld ohne Fokus und inaktiv](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Rahmen|`SearchControl.UnfocusedBorder`|  
|![Sucheingabefeld ohne Fokus und inaktiv](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Suche (Aktionsschaltfläche) ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Schaltfläche "Aktion"**|Hintergrund|Nicht zutreffend|  
|![Suche (Aktionsschaltfläche) ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Suchen")|`SearchControl.SearchGlyph`|  
|![Suche (Aktionsschaltfläche) ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Beenden")|`SearchControl.StopGlyph`|  
|![Suche (Aktionsschaltfläche) ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe "Löschen")|`SearchControl.ClearGlyph`|  
|![Suche (Aktionsschaltfläche) ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Schaltfläche "Aktion"**|Rahmen|Nicht zutreffend|  
|![Suche&#45;ohne Fokus gedrückt](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`SearchControl.UnfocusedDropDownButton`|  
|![Suche&#45;ohne Fokus gedrückt](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Suche&#45;ohne Fokus gedrückt](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown-Schaltfläche**|Rahmen|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Suche (Aktionsschaltfläche) gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Schaltfläche "Aktion"**|Hintergrund|`SearchControl.ActionButtonMouseDown`|  
|![Suche (Aktionsschaltfläche) gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Suche (Aktionsschaltfläche) gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Schaltfläche "Aktion"**|Rahmen|`SearchControl.ActionButtonMouseDownBorder`|  
|![Suche&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|`SearchControl.MouseDownDropDownButton`|  
|![Suche&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Suche&#45;ab-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown-Schaltfläche**|Rahmen|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Hervorgehoben (nur Text)**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Search input field highlight](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem text**|Hintergrund|`SearchControl.Selection`|  
|![Search input field highlight](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem text**|Vordergrund (Text)|`SearchControl.FocusedBackground`|  
|![Search input field highlight](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem text**|Rahmen|Keiner|  
|![Search input field highlight](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem text**|Trennzeichen|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Hintergrund|`SearchControl.Disabled`|  
|![Sucheingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`SearchControl.Disabled`|  
|![Sucheingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Rahmen|`SearchControl.DisabledBorder`|  
|![Sucheingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Suche (Aktionsschaltfläche) deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Schaltfläche "Aktion"**|Hintergrund|Keiner|  
|![Suche (Aktionsschaltfläche) deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Schaltfläche "Aktion"**|Vordergrund (Glyphe)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Suche (Aktionsschaltfläche) deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Schaltfläche "Aktion"**|Rahmen|Keiner|  
|![Suche&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown-Schaltfläche**|Hintergrund|Keiner|  
|![Suche&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown-Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.DisabledDownButtonGlyph`|  
|![Suche&#45;gedrückt deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown-Schaltfläche**|Rahmen|Keiner|  
  
##### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld  
 Das Dropdownmenü im Suchfeld kann etwas komplexer sein als andere Dropdownmenüs in Visual Studio. Die Bereiche "Empfohlene Suchbegriffe" und "Suchoptionen" können alleine oder zusammen im Menü erscheinen, und jedem Bereich kann eine eigene Farbe zugeordnet sein. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.  
  
 ![Suche&#45;nach unten (rote Linie)](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Empfohlen...  
- für die Erstellung einer benutzerdefinierten Dropdownliste im Suchfeld  

- bei Verwendung der richtigen Tokennamen für die entsprechenden Listenkomponenten  

Nicht empfohlen...  
- für Dropdownlisten, die in anderen Kontexten angezeigt werden  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard (kein weiterer Zustand)**  
  
|Element|Tokenname: Category.Color|  
|-------------|--------------------------------|  
|Rahmen|`SearchControl.PopupBorder`|  
|Trennzeichen|`SearchControl.PopupSectionHeaderSeparator`|  
|Schatten|`Environment.DropShadowBackground`|  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Suchvorschlag](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Vorschläge für Suchen**|Hintergrund|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchvorschlag](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Vorschläge für Suchen**|Vordergrund (Text)|`SearchControl.PopupItemText`|  
|![Kontrollkästchen "Suche"](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Hintergrund|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Hintergrund|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kontrollkästchen "Suche"](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxText`|  
|![Kontrollkästchen "Suche"](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Linktext)|`SearchControl.PopupButtonText`|  
|![Kontrollkästchen "Suche"](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Headerhintergrund|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Headerhintergrund|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kontrollkästchen "Suche"](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Headertext)|`SearchControl.PopupSectionHeaderText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Headertext)|`SearchControl.PopupSectionHeaderText`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bei einer mauszeigerbewegung über suchvorschlag](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Vorschläge für Suchen**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Bei einer mauszeigerbewegung über suchvorschlag](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Vorschläge für Suchen**|Vordergrund (Text)|`SearchControl.PopupMouseOverItemText`|  
|![Bei einer mauszeigerbewegung über suchvorschlag](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Vorschläge für Suchen**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
|![Search-Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Bei einer mauszeigerbewegung über die Suchoptionen](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Search-Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Bei einer mauszeigerbewegung über die Suchoptionen](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Search-Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Bei einer mauszeigerbewegung über die Suchoptionen](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Search-Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
|![Bei einer mauszeigerbewegung über die Suchoptionen](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Suchvorschlag gedrückt](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen gedrückt](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchvorschlag gedrückt](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen gedrückt](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchvorschlag gedrückt](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Suchoptionen gedrückt](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Suchvorschlag gedrückt](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Linkhintergrund|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen gedrückt](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Linkhintergrund|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchvorschlag gedrückt](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchbegriffe (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Suchoptionen gedrückt](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Link  
 Der Link ist ein Steuerelement, das keine Kombination aus Vordergrund-/Hintergrundfarbe darstellt. Sie verwenden grundsätzlich die Vordergrund-Linkfarbe, die auf dunklem, grauen und weißem Hintergrund ordnungsgemäß angezeigt wird. Wenn Sie nicht das Farbtoken für das Linksteuerelement verwenden, sehen Sie für den "gedrückten" Zustand die Standardsystemfarbe, die rot blinkend dargestellt wird. Das ist das Signal, dass das Steuerelement nicht das richtige Farbtoken für die Umgebung verwendet.  
  
 ![Hyperlink redline](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Empfohlen...  
 für die Erstellung eines benutzerdefinierten Links  
  
 Nicht empfohlen...  
 für Elemente, die keinen Link darstellen  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink, Standard](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Vordergrund (Text)|`Environment.PanelHyperlink`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Link bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Vordergrund (Text)|`Environment.PanelHyperlinkHover`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Link – gedrückt](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Vordergrund (Text)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink, deaktiviert](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Vordergrund (Text)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Infoleiste  
 Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.  
  
 ![Infobar redline](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten Infoleiste  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Infoleiste haben  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Infobar](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Infobar**|Hintergrund|`Environment.InfoBackground`|  
|![Infobar](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Infobar**|Vordergrund (Text)|`Environment.InfoText`|  
|![Infobar](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Infobar**|Rahmen|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Bildlaufleiste  
 Bildlaufleisten erhalten ihr Format von der Visual Studio-Umgebung, sodass kein Design angewendet werden muss. Möglicherweise möchten jedoch, dass Sie für die Farben, die in Bildlaufleisten verwendet werden, sodass Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent nutzen möchten.  
  
 ![(Rote Linie) der Bildlaufleiste](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Empfohlen...  
 für die Erstellung einer Benutzeroberfläche, die auf die Visual Studio-Bildlaufleisten abgestimmt sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die nicht grundsätzlich auf die Bildlaufleisten-Benutzeroberfläche abgestimmt sein sollen  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bildlaufleiste](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Bildlaufleiste](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbBackground`|  
|![Bildlaufleiste Pfeil](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Bildlaufpfeil**|Hintergrund|`Environment.ScrollBarArrowBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![Bildlaufleiste Pfeil](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Bildlaufpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyph`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bildlaufleiste, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Bildlaufleiste, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Bildlaufleisten-Taste bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Bildlaufpfeil**|Hintergrund|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![Bildlaufleisten-Taste bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Bildlaufpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bildlaufleiste geklickt](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Bildlaufleiste geklickt](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbPressedBackground`|  
|![Bildlaufleisten-Taste gedrückt](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Bildlaufpfeil**|Hintergrund|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![Bildlaufleisten-Taste gedrückt](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Bildlaufpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="BKMK_TreeView"></a> Strukturansicht  
 Mehrere Toolfenster, einschließlich Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in der TreeView-Kategorie gesteuert werden. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.  
  
 ![Tree view redline](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Empfohlen...  
 für alle Projekte zur Implementierung einer hierarchischen Organisationsstruktur  
  
Nicht empfohlen...  
- für Elemente, die keine Ähnlichkeit mit einer Strukturansicht haben  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Hintergrund|`TreeView.Background`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Vordergrund (Text)|`TreeView.Background`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Vordergrund (Glyphe)|`TreeView.Glyph`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Rahmen|Keiner|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Bei einer mauszeigerbewegung über die Strukturansicht](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Hintergrund|`TreeView.Background`|  
|![Bei einer mauszeigerbewegung über die Strukturansicht](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Vordergrund (Text)|`TreeView.Background`|  
|![Bei einer mauszeigerbewegung über die Strukturansicht](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Vordergrund (Glyphe)|`TreeView.GlyphMouseOver`|  
|![Bei einer mauszeigerbewegung über die Strukturansicht](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Rahmen|Keiner|  
  
 **Ziehen Sie auf**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Struktur anzeigen "DragOver"](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Hintergrund|`TreeView.DragOverItem`|  
|![Struktur anzeigen "DragOver"](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Vordergrund (Text)|`TreeView.DragOverItem`|  
|![Struktur anzeigen "DragOver"](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Vordergrund (Glyphe)|`TreeView.DragOverItemGlyph`|  
|![Struktur anzeigen "DragOver"](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Rahmen|Keiner|  
  
 **ausgewählt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht mit Fokus](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyph`|  
|![Strukturansicht mit Fokus](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Mit Fokus**|Rahmen|`TreeView.FocusVisualBorder`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactiveGlyph`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Rahmen|Keiner|  
  
 **Ausgewähltes Element zeigen**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Strukturansicht mit Fokus, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Mit Fokus**|Rahmen|Keiner`TreeView.FocusVisualBorder`|  
|![Strukturansicht ohne Fokus bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Strukturansicht ohne Fokus bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Rahmen|Keiner|  
  
#### <a name="button-controls"></a>Schaltflächen-Steuerelemente  
 ![(Rote Linie) der Schaltflächen-Steuerelement](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Empfohlen...  
 für Schaltflächen im Dokument, die Sie in Visual Studio-Designs (Hell, Dunkel, Blau oder kontrastreiches Systemdesign) integrieren möchten.  
  
 Nicht empfohlen...  
 für Schaltflächen, die vor einem benutzerdefinierten Hintergrund angezeigt werden, der nicht Bestandteil eines Visual Studio-Designs ist  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Schaltfläche|`CommonControls.Button`|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Schaltflächenrahmen|`CommonControls.ButtonBorder`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Schaltfläche|`CommonControls.ButtonDisabled`|  
|![Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Schaltflächenrahmen|`CommonControls.ButtonBorderDisabled`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche ", wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Schaltfläche|`CommonControls.ButtonHover`|  
|![Schaltfläche ", wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Schaltflächenrahmen|`CommonControls.ButtonBorderHover`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Gedrückte Taste](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Schaltfläche|`CommonControls.ButtonPressed`|  
|![Gedrückte Taste](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Schaltflächenrahmen|`CommonControls.ButtonBorderPressed`|  
  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Schaltfläche|`CommonControls.ButtonFocused`|  
|![Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Schaltflächenrahmen|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente  
 ![Aktivieren Sie das Kontrollkästchen (rote Linie,)](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Empfohlen...  
 für Kontrollkästchen-Steuerelemente im Dokumentursprung  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Kontrollkästchen-Steuerelement sind  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Aktivieren Sie das Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Hintergrund|`CommonControls.CheckBoxBackground`|  
|![Aktivieren Sie das Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Rahmen|`CommonControls.CheckBoxBorder`|  
|![Aktivieren Sie das Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Aktivieren Sie das Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glyphe|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Aktivieren Sie das Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Hintergrund|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Aktivieren Sie das Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Rahmen|`CommonControls.CheckBoxBorderDisabled`|  
|![Aktivieren Sie das Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Aktivieren Sie das Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glyphe|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Das Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Hintergrund|`CommonControls.CheckBoxBackgroundHover`|  
|![Das Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Rahmen|`CommonControls.CheckBoxBorderHover`|  
|![Das Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Das Kontrollkästchen, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glyphe|`CommonControls.CheckBoxGlyphHover`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Aktivieren Sie das Kontrollkästchen geklickt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Hintergrund|`CommonControls.CheckBoxBackgroundPressed`|  
|![Aktivieren Sie das Kontrollkästchen geklickt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Rahmen|`CommonControls.CheckBoxBorderPressed`|  
|![Aktivieren Sie das Kontrollkästchen geklickt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Aktivieren Sie das Kontrollkästchen geklickt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glyphe|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Hintergrund|`CommonControls.CheckBoxBackgroundFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Rahmen|`CommonControls.CheckBoxBorderFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glyphe|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Dropdownlisten-/Kombinationsfeld-Steuerelement  
 ![Drop&#45;unten&#47;(rote Linie) der im Kombinationsfeld](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Empfohlen...  
für Dropdownlisten und Kombinationsfelder, die Teil des Dokumentursprungs sind.  

Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Dropdownliste und kein Kombinationsfeld sind  

- für eine [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) oder ein [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) in der Befehlsleiste  
  
  **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Hintergrund|`CommonControls.ComboBoxBackground`|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Rahmen|`CommonControls.ComboBoxBorder`|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Trennzeichen|`CommonControls.ComboBoxSeparator`|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyphe|`CommonControls.ComboBoxGlyph`|  
|![Drop&#45;unten&#47;Kombinationsfeld](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled** (deaktiviert)  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Hintergrund|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Rahmen|`CommonControls.ComboBoxBorderDisabled`|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Trennzeichen|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyphe|`CommonControls.ComboBoxGlyphDisabled`|  
|![Drop&#45;unten&#47;Kombinationsfeld, deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Hintergrund|`CommonControls.ComboBoxBackgroundHover`|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Rahmen|`CommonControls.ComboBoxBorderHover`|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Trennzeichen|`CommonControls.ComboBoxSeparatorHover`|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyphe|`CommonControls.ComboBoxGlyphHover`|  
|![Drop&#45;unten&#47;im Kombinationsfeld, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Hintergrund|`CommonControls.ComboBoxBackgroundPressed`|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Rahmen|`CommonControls.ComboBoxBorderPressed`|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Trennzeichen|`CommonControls.ComboBoxSeparatorPressed`|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyphe|`CommonControls.ComboBoxGlyphPressed`|  
|![Drop&#45;unten&#47;gedrückten Kombinationsfelds](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Mit Fokus**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Hintergrund|`CommonControls.ComboBoxBackgroundFocused`|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Rahmen|`CommonControls.ComboBoxBorderFocused`|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Trennzeichen|`CommonControls.ComboBoxSeparatorFocused`|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyphe|`CommonControls.ComboBoxGlyphFocused`|  
|![Drop&#45;unten&#47;Kombinationsfeld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Texteingabeauswahl**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;Combo Box Texteingabe](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Hervorheben|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Gedrückt – Listenelementansicht**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListBackground`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListBackgroundHover`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorder`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderHover`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderPressed`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderFocused`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemText`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextHover`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextPressed`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextFocused`|  
|![Drop&#45;unten&#47;Combo Box-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrundschatten|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)  
 Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.  
  
 ![Tabellendaten &#40;Rastersteuerelement&#41; (rote Linie)](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Empfohlen...  
 für Tabellen- oder Rastersteuerelemente  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Tabellen- oder Rastersteuerelement sind  
  
##### <a name="column-headers"></a>Spaltenheader  
 Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.  
  
|Zustand|Element|Tokenname: Category.Color|  
|-----------|-------------|--------------------------------|  
|Standard|Hintergrund|`Header.Default`|  
|Standard|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|Standard|Vordergrund (Glyphe)|`Header.Glyph`|  
|Standard|Rahmen|`Header.SeparatorLine`|  
|Darauf zeigen (Hover)|Hintergrund|`Header.MouseOver`|  
|Darauf zeigen (Hover)|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|Darauf zeigen (Hover)|Vordergrund (Glyphe)|`Header.MouseOverGlyph`|  
|Darauf zeigen (Hover)|Rahmen|`Header.SeparatorLine`|  
|Gedrückt|Hintergrund|`CommonControls.CheckBoxBackgroundPressed`|  
|Gedrückt|Vordergrund (Text)|`CommonControls.CheckBoxBorderPressed`|  
|Gedrückt|Vordergrund (Glyphe)|`CommonControls.CheckBoxTextPressed`|  
|Gedrückt|Rahmen|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Listenansichtselemente  
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.  
  
|Zustand|Element|Tokenname: Category.Color|  
|-----------|-------------|--------------------------------|  
|Standard|Hintergrund|Transparent|  
|Standard|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|Standard|Rahmen|Keiner|  
|Ausgewählt (aktiv)|Hintergrund|`TreeView.SelectedItemActive`|  
|Ausgewählt (aktiv)|Vordergrund (Text)|`TreeView.SelectedItemActiveText`|  
|Ausgewählt (aktiv)|Rahmen|Keiner|  
|Ausgewählt (inaktiv)|Hintergrund|`TreeView.SelectedItemInactive`|  
|Ausgewählt (inaktiv)|Vordergrund (Text)|`TreeView.SelectedItemInactiveText`|  
|Ausgewählt (inaktiv)|Rahmen|Keiner|  
  
### <a name="manifest-designer"></a>Manifest-Designer  
 Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![(Rote Linie) der Manifest-Designer](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Empfohlen...  
- für Designer, die Ähnlichkeit mit dem Manifest-Designer haben.  

- anstelle allgemeiner Registerkarten-Steuerelemente, die im oberen Bereich eines Editors im Dokumentursprung angezeigt werden.  

Nicht empfohlen...  
- bei Verwendung von mehr als sechs Registerkarten  

- für Benutzeroberflächenelemente, die nicht wie der Manifest-Designer aufgebaut sind  
  
|Zustand|Komponente|Element|Tokenname: Category.Color|  
|-----------|---------------|-------------|--------------------------------|  
|Standard (ausgewählt)|Registerkarte|Hintergrund|`ManifestDesigner.TabActive`|  
|Standard (ausgewählt)|Registerkarte|Rahmen|Keiner|  
|Standard (ausgewählt)|Beschreibungsbereich|Hintergrund|`ManifestDesigner.DescriptionPane`|  
|Standard (ausgewählt)|Inhaltsseite|Hintergrund|`ManifestDesigner.Background`|  
|Standard (ausgewählt)|Inhaltsseite|Dialogfeld-Hilfetext|`ManifestDesigner.WatermarkText`<br /><br /> Dieser Tokenname stimmt nicht mit seiner Funktion überein.|  
|Nicht ausgewählt|Registerkarte|Hintergrund|`ManifestDesigner.Tab.Inactive`|  
|Darauf zeigen (Hover)|Registerkarte|Hintergrund|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Tagging  
 Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.  
  
 ![Tagging (rote Linie)](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Empfohlen...  
 für Benutzeroberflächen, die Tags unterstützen.  
  
 Nicht empfohlen...  
 für andere Arten von Benutzeroberflächenelementen  
  
#### <a name="tag"></a>Tag  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Default**|Hintergrund|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Default**|Vordergrund (Text)|`Tag.Background`|  
|![Markieren Sie bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Hintergrund|`Tag.HoverBackground`|  
|![Markieren Sie bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Vordergrund (Text)|`Tag.HoverBackgroundText`|  
|![Tag, aufgerufen](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Gedrückt**|Hintergrund|`Tag.PressedBackground`|  
|![Tag, aufgerufen](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Gedrückt**|Vordergrund (Text)|`Tag.PressedBackgroundText`|  
|![Tag, ausgewählt](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **ausgewählt**|Hintergrund|`Tag.SelectedBackground`|  
|![Tag, ausgewählt](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **ausgewählt**|Vordergrund (Text)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glyphe (Schließsymbol)  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;Glyphe&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Standard (Tag, Standard)**|Hintergrund|Nicht zutreffend|  
|![Tag &#40;Glyphe&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Standard (Tag, Standard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyph`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;Glyphe&#41; bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wenn darauf gezeigt wird (Tag, Standard)**|Hintergrund|`Tag.TagHoverGlyphHoverBackground`|  
|![Tag &#40;Glyphe&#41; bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wenn darauf gezeigt wird (Tag, Standard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyphHover`|  
|![Tag &#40;Glyphe&#41; bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wenn darauf gezeigt wird (Tag, Standard)**|Rahmen|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;Glyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (Tag, Standard)**|Hintergrund|`Tag.TagHoverGlyphPressedBackground`|  
|![Tag &#40;Glyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (Tag, Standard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyphPressed`|  
|![Tag &#40;Glyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (Tag, Standard)**|Rahmen|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Tag ausgewählt/Glyphe, Standard**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag, ausgewählt](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Standard (Tag, ausgewählt)**|Hintergrund|Nicht zutreffend|  
|![Tag, ausgewählt](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Standard (Tag, ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyph`|  
  
 **Tag ausgewählt/Glyphe, Hoverzustand**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag, ausgewählt werden, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hoverzustand (Tag, ausgewählt)**|Hintergrund|`Tag.TagSelectedGlyphHoverBackground`|  
|![Tag, ausgewählt werden, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hoverzustand (Tag, ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyphHover`|  
|![Tag, ausgewählt werden, wenn darauf gezeigt wird](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hoverzustand (Tag, ausgewählt)**|Rahmen|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Tag-ausgewählt/Glyphe, die gedrückt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag, ausgewählt gedrückt](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag, ausgewählt)**|Hintergrund|`Tag.TagSelectedGlyphPressedBackground`|  
|![Tag, ausgewählt gedrückt](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag, ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyphPressed`|  
|![Tag, ausgewählt gedrückt](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag, ausgewählt)**|Rahmen|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Shell  
  
#### <a name="background"></a>Hintergrund  
 Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Ab Visual Studio 2013 werden die obere und untere Hintergrundebene im dunklen und hellen Design auf dieselbe Farbe festgelegt.  
  
 ![Shell-Hintergrund (rote Linie,)](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Empfohlen...  
 für Bereiche, die an den Hintergrund der Visual Studio-Umgebung angepasst werden sollen.  
  
Nicht empfohlen...  
- als Füllung für Bereiche, die keine Hintergrundoberflächen sind  

- als Hintergrund, auf dem Vordergrundelemente platziert werden sollen  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|Untere Ebene|Hintergrund|`Environment.EnvironmentBackground`|  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Befehlsablage  
 Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.  
  
 ![(Rote Linie) der Befehlsablage](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Empfohlen...  
- für Bereiche, in denen Menüs oder Symbolleisten platziert werden.  

- mit dem richtigen Hintergrund / Vordergrund token Kombination aus.  
  
  Nicht empfohlen...  
  für Bereiche, die keine Ähnlichkeit mit einer Befehlsablage aufweisen  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufstopps auf denselben Farbwert in Visual Studio 2013 im hellen und dunklen Designs festgelegt ist.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Werkzeugkasten  
 Der Werkzeugkasten ist eines der allgemeinen Toolfenster, die am häufigsten in Visual Studio verwendet werden. Es handelt sich um ein Struktursteuerelement, auf das ein bestimmtes Design und ein bestimmter Stil angewendet wurde.  
  
 ![(Rote Linie) der Toolbox](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Empfohlen...  
 für den Entwurf eines Toolfensters, das immer mit dem Shell-Werkzeugkasten konsistent sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die keine Ähnlichkeit mit der Werkzeugkasten-Benutzeroberfläche haben, oder wenn Sie nicht sicher sind, ob Ihre Benutzeroberfläche bei Änderung der Farben des Shell-Werkzeugkastens Probleme verursacht  
  
 **Default**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolbox, übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Hintergrund|`Environment.ToolboxContent`<br /><br /> Kopfzeilen<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind.|  
|![Toolbox, untergeordneter Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneten Knoten**|Hintergrund|`Environment.ToolboxContent`<br /><br /> Kopfzeilen<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind.|  
|![Toolbox, übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Rahmen|Keiner|  
|![Toolbox, untergeordneter Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneten Knoten**|Rahmen|Keiner|  
|![Toolbox, übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Vordergrund (Glyphe)|`Environment.ToolboxContent`|  
|![Toolbox, untergeordneter Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneten Knoten**|Vordergrund (Glyphe)|`Environment.ToolboxContent`|  
|![Toolbox, übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Vordergrund (Text)|`Environment.ToolboxContent`|  
|![Toolbox, untergeordneter Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneten Knoten**|Vordergrund (Text)|`Environment.ToolboxContent`|  
  
 **Hover**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolbox, untergeordneter Knoten bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Werkzeugkasten, zeigen auf untergeordneten Knoten**|Hintergrund|`Environment.ToolboxContentMouseOver`<br /><br /> Nur einzelne Elemente|  
|![Toolbox, untergeordneter Knoten bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Werkzeugkasten, zeigen auf untergeordneten Knoten**|Rahmen|Keiner|  
|![Toolbox, untergeordneter Knoten bei einer mauszeigerbewegung über](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Werkzeugkasten, zeigen auf untergeordneten Knoten**|Vordergrund (Text)|`Environment.ToolboxContentMouseOver`<br /><br /> Nur einzelne Elemente|  
  
 **ausgewählt**  
  
|Komponente|Element|Tokenname: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Toolbox, übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Rahmen|`TreeView.FocusVisualBorder`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Rahmen|`TreeView.FocusVisualBorder`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox, untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox (untergeordneter Knoten) ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Rahmen|Keiner|  
|![Toolbox (untergeordneter Knoten) ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Rahmen|Keiner|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox (untergeordneter Knoten) ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox (untergeordneter Knoten) ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Farbwertverweis  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Komponente|Segment|Element|Zustand|Hell|Dunkel|Blau|Hoher Kontrast|  
|Trennlinien|||Standard|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Expander-Glyphe||Vordergrund|Standard|||||  
|Expander-Glyphe||Vordergrund|Darauf zeigen (Hover)|||||  
|Expander-Glyphe||Hintergrund|Standard|||||  
|Expander-Glyphe||Hintergrund|Darauf zeigen (Hover)|||||  
|Expander-Glyphe||Rahmen|Standard|||||  
|Expander-Glyphe||Rahmen|Darauf zeigen (Hover)|||||