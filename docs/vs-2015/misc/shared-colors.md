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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410088"
---
# <a name="shared-colors"></a>Konsistente Farben
Fügen Sie hier eine Einleitung ein.  
  
## <a name="shared-colors"></a>Konsistente Farben  
 Wenn Sie Ihre Benutzeroberfläche mit gängigen Visual Studio Shell-Elementen gestalten möchten oder Ihr Benutzeroberflächenelement konsistent mit ähnlichen Features sein soll, können Sie die Tokennamen aus den Paketdefinitionsdateien verwenden, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.  
  
 In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:  
  
- **Verwenden Sie Tokennamen, die auf der Funktion basieren, nicht auf der Farbe selbst.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Das Kombinationsfeld und die Animation erfüllen unterschiedliche Funktionen, und wenn sich die dem Kombinationsfeld zugeordnete Farbe ändert, eignet sie sich möglicherweise nicht mehr für Ihr Animationselement. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.  
  
- **Verwenden Sie Hintergrund-und Textfarben in der richtigen Kombination.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn keine zugeordnete Textfarbe vorhanden ist, sollte diese Hintergrundfarbe auf Oberflächen, auf denen erwartungsgemäß Text angezeigt wird, nicht verwendet werden. Andere Kombinationen aus Text- und Hintergrundfarbe können dazu führen, dass die Benutzeroberfläche unlesbar wird.  
  
- **Verwenden Sie Steuerelement Farben, die für Ihren Standort geeignet sind.** Für bestimmte Zustände einiger Visual Studio-Steuerelemente sind keine separaten Rahmen- und Hintergrundfarben verfügbar. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.  
  
> [!IMPORTANT]
> Verwenden Sie keine Token aus den Kategorien "Startseite" oder "Cider".  
  
### <a name="command-structures"></a>Befehlsstrukturen  
  
#### <a name="BKMK_CommandMenus"></a>Kreiert  
 Menüs können an mehreren Stellen in Visual Studio 2013 vorkommen: in der Hauptmenüleiste, eingebettet in Dokument- oder Toolfenster oder beim Rechtsklicken an verschiedenen Stellen der IDE. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.  
  
 ![Menüs (rote Linie)](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Empfohlen...  
- für die Erstellung eines benutzerdefinierten Menüs  
  
- für eine neue Benutzeroberflächenkomponente, die auf die Visual Studio-Menüs abgestimmt werden soll.  
  
Nicht empfohlen...  
als ausschließliche Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe.  
  
##### <a name="menu-title"></a>Menütitel  
 Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.  
  
 ![Menü Titel Redline](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Empfohlen...  
für die Erstellung eines benutzerdefinierten Menütitels  
  
Nicht empfohlen...  
- für Elemente, die nicht grundsätzlich auf den Menütitel abgestimmt sein sollen  
  
- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü Titel Standard](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menütitel**|Hintergrund|Keine|  
|![Menü Titel Standard](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menütitel mit Glyphe default](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuGlyph`|  
|![Menütitel mit Glyphe default](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Menütitel mit Glyphe**|Rahmen|Keine|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menütitel beim Hover](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menütitel**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menütitel beim Hover](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Menütitel mit Glyphe bei Hover](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Menütitel mit Glyphe bei Hover](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Menütitel mit Glyphe**|Rahmen|`Environment.CommandBarBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü Titel gedrückt](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menütitel**|Hintergrund|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menü Titel gedrückt](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menütitel**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menütitel mit gedrücktem Symbol](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Menütitel mit gedrücktem Symbol](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Menütitel mit Glyphe**|Rahmen|`Environment.CommandBarMenuBorder`<br /><br /> Nur linke, obere und rechte Seite|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menütitel mit deaktiviertem Symbol](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Hintergrund|Keine|  
|![Menütitel mit deaktiviertem Symbol](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Menütitel mit deaktiviertem Symbol](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Vordergrund (Glyphe)|`Environment.CommandBarTextInactive`|  
|![Menütitel mit deaktiviertem Symbol](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Menütitel mit Glyphe**|Rahmen|Keine|  
  
##### <a name="menu"></a>Menü  
 Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.  
  
 ![Menü Elemente (rote Linie)](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Empfohlen...  
 für alle Dropdownlisten, die von einer Menü- oder Befehlsleiste geöffnet werden.  
  
Nicht empfohlen...  
- für Dropdownlisten, die in einem anderen Kontext vorkommen  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Hintergrund|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Rahmen|`Environment.CommandBarMenuBorder`|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Symbolkanal-Hintergrund|`Environment.CommandBarMenuIconBackground`|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Trennzeichen|`Environment.CommandBarMenuSeparator`|  
|![Menü Standard](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Schatten|`Environment.DropShadowBackground`|  
|![Menü aktiviert](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Aktiviert**|Häkchen|`Environment.CommandBarCheckBox`|  
|![Menü aktiviert](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Aktiviert**|Häkchenhintergrund|`Environment.CommandBarSelectedIcon`|  
|![Menü ausgewählt](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Ausgewählt**|Symbolhintergrund|`Environment.CommandBarSelected`|  
|![Menü ausgewählt](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Ausgewählt**|Symbolrahmen|`Environment.CommandBarSelectedBorder`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü Hover](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Hintergrund|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü Hover](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Vordergrund (Text)|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü Hover](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menüelement**|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menü mit Mauszeiger aktiviert](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Aktiviert**|Häkchen|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menü mit Mauszeiger aktiviert](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Aktiviert**|Häkchenhintergrund|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menü Hover ausgewählt](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Ausgewählt**|Symbolhintergrund|`Environment.CommandBarHoverOverSelected`|  
|![Menü Hover ausgewählt](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Ausgewählt**|Symbolrahmen|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü deaktiviert](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menüelement|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Menü deaktiviert](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menüelement|Vordergrund (Untermenü-Glyphe)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü deaktiviert aktiviert](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Aktiviert|Häkchen|`Environment.CommandBarCheckBoxDisabled`|  
|![Menü deaktiviert aktiviert](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Aktiviert|Häkchenhintergrund|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Befehlsleiste  
 Die Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE vorkommen, vor allem in der Befehlsablage und eingebettet in Tool- oder Dokumentfenster.  
  
 Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.  
  
 ![Befehlsleiste (rote Linie)](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Überlauf Schaltfläche Redline](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  

- für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
##### <a name="command-bar-group"></a>Befehlsleistengruppe  
 Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.  
  
 ![Befehls leisten Gruppe (rote Linie)](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Empfohlen...  
 für Positionen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standardimplementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann.  
  
Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Befehlsleiste aufweisen  

- für andere Befehlsleistenkomponenten als diejenigen, für die Tokennamen festgelegt wurden  
  
  **Standard** (kein weiterer Zustand)  
  
|Element|Tokenname: Category.color|  
|-------------|--------------------------------|  
|Hintergrund|`Environment.CommandBarGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|Rahmen|`Environment.CommandBarToolBarBorder`|  
|Ziehpunkt|`Environment.CommandBarDragHandle`|  
|Trennzeichen|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Befehlssymbole  
 ![Befehls Symbol Redline](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Befehls Symbol Redline](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Empfohlen...  
 für alle Schaltflächen, die auf einer Befehlsleiste platziert werden.  
  
Nicht empfohlen...  
- für Steuerelemente, die ihren eigenen Tokennamen haben  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Befehls Symbol Standard](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Standard**|Hintergrund|N/V (erbt vom Befehlsleisten-Hintergrund)|  
|![Befehls Symbol Standard](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Standard**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Befehls Symbol Standard](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Standard**|Rahmen|N/V|  
|![Standardmäßiges Befehls Symbol ausgewählt](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Ausgewählt**|Hintergrund|`Environment.CommandBarSelected`|  
|![Standardmäßiges Befehls Symbol ausgewählt](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Ausgewählt**|Vordergrund (Text)|`Environment.CommandBarTextSelected`|  
|![Standardmäßiges Befehls Symbol ausgewählt](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Ausgewählt**|Rahmen|`Environment.CommandBarSelectedBorder`|  
  
 **Hover und Tastaturfokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Befehls Symbol Hover](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard bei Hover**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Befehls Symbol Hover](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard bei Hover**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Befehls Symbol Hover](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard bei Hover**|Rahmen|`Environment.CommandBarBorder`|  
|![Befehls Symbol, auf das gezeigt wird](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Beim Hover ausgewählt**|Hintergrund|`Environment.CommandBarHoverOverSelected`|  
|![Befehls Symbol, auf das gezeigt wird](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Beim Hover ausgewählt**|Vordergrund (Text)|`Environment.CommandBarTextHoverOverSelected`|  
|![Befehls Symbol, auf das gezeigt wird](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Beim Hover ausgewählt**|Rahmen|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Befehls Symbol gedrückt](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehls Symbol**|Hintergrund|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Befehls Symbol gedrückt](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehls Symbol**|Vordergrund (Text)|`Environment.CommandBarTextMouseDown`|  
|![Befehls Symbol gedrückt](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Gedrücktes Befehls Symbol**|Rahmen|`Environment.CommandBarBorder`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Befehls Symbol deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehls Symbol**|Hintergrund|N/V (erbt vom Befehlsleisten-Hintergrund)|  
|![Befehls Symbol deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehls Symbol**|Vordergrund (Text)|`Environment.CommandBarTextInactive`|  
|![Befehls Symbol deaktiviert](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Deaktiviertes Befehls Symbol**|Rahmen|N/V|  
  
##### <a name="BKMK_CommandComboBox"></a>Kombinations Feld  
  
> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn Ihr Dropdown keinen bearbeitbaren Textbereich enthält, verwenden Sie die unter [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown)beschriebenen Farbtoken.  
  
 ![Kombinations Feld (rote Linie)](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Empfohlen...  
- für die Erstellung benutzerdefinierter Kombinationsfelder  

- für die Erstellung eines Befehlsleisten-Steuerelements, das Ähnlichkeit mit einem Kombinationsfeld hat.  

Nicht empfohlen...  
- für Elemente, die nicht grundsätzlich auf die Befehlsleisten-Benutzeroberfläche abgestimmt sein müssen  

- wenn Sie Zugriff auf ein formatiertes Kombinationsfeld haben  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kombinations Feld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxBackground`|  
|![Kombinations Feld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxText`|  
|![Kombinations Feld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxBorder`|  
|![Kombinations Feld (Eingabefeld)](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Eingabefeld**|Trennzeichen|Kein Trennzeichen|  
|![Dropdown&#45;Schaltfläche für Kombinations Feld](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|N/V (erbt)|  
|![Dropdown&#45;Schaltfläche für Kombinations Feld](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxGlyph`|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown Liste**|Hintergrund|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown Liste**|Vordergrund (Text)|`Environment.ComboBoxItemText`|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Dropdown Liste**|Rahmen|`Environment.ComboBoxPopupBorder`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Eingabefeld für Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Eingabefeld für Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxMouseOverText`|  
|![Eingabefeld für Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxMouseOverBorder`|  
|![Eingabefeld für Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxMouseOverSeparator`|  
|![Kombinations Feld&#47;-&#45;Dropdown-Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Kombinations Feld&#47;-&#45;Dropdown-Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxMouseOverGlyph`|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste bei Hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown Liste**|Hintergrund (Menüelement)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste bei Hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown Liste**|Vordergrund (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Kombinations Feld&#47;-&#45;Dropdown Liste bei Hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Dropdown Liste**|Rahmen (Menüelement)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinations Feld-Eingabefeld mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxFocusedBackground`|  
|![Kombinations Feld-Eingabefeld mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxFocusedText`|  
|![Kombinations Feld-Eingabefeld mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxFocusedBorder`|  
|![Kombinations Feld-Eingabefeld mit Fokus](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`Environment.ComboBoxFocusedButtonBackground`|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinations Feld-Eingabefeld gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxMouseDownBackground`|  
|![Kombinations Feld-Eingabefeld gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxMouseDownText`|  
|![Kombinations Feld-Eingabefeld gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxMouseDownBorder`|  
|![Kombinations Feld-Eingabefeld gedrückt](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Eingabefeld**|Trennzeichen|`Environment.ComboBoxMouseDownSeparator`|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Kombinations Feld-Eingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Hintergrund|`Environment.ComboBoxDisabledBackground`|  
|![Kombinations Feld-Eingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`Environment.ComboBoxDisabledText`|  
|![Kombinations Feld-Eingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Rahmen|`Environment.ComboBoxDisabledBorder`|  
|![Kombinations Feld-Eingabefeld deaktiviert](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Eingabefeld**|Trennzeichen|Kein Trennzeichen|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|Keine|  
|![Dropdown&#47;&#45;Schaltfläche für Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="BKMK_CommandDropDown"></a>Dropdown  
  
> [!IMPORTANT]
> Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn Ihr Dropdown einen bearbeitbaren Textbereich enthält, verwenden Sie die unter [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox)beschriebenen Farbtoken.  
  
 ![Dropdown&#45;-rote Linie](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Empfohlen...  
 für die Erstellung benutzerdefinierter Dropdownlisten-Steuerelemente  
  
Nicht empfohlen...  
- für Elemente, die keine Ähnlichkeit mit einer Dropdownliste haben  

- für Kombinationsfelder oder unterteilte Schaltflächen  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Dropdown&#45;-Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownBackground`|  
|![Dropdown&#45;-Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`DropDownText`|  
|![Dropdown&#45;-Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Rahmen|`DropDownBorder`|  
|![Dropdown&#45;-Auswahlfeld](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Auswahlfeld**|Trennzeichen|Kein Trennzeichen|  
|![Dropdown&#45;Schaltfläche](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|Keine|  
|![Dropdown&#45;Schaltfläche](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownGlyph`|  
|![Dropdown&#45;Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown Liste**|Hintergrund|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Dropdown&#45;Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown Liste**|Vordergrund (Text)|`Environment.ComboBoxItemText`|  
|![Dropdown&#45;Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown Liste**|Rahmen|`Environment.DropDownPopupBorder`|  
|![Dropdown&#45;Liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Dropdown Liste**|Schatten|`Environment.DropShadowBackground`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Dropdown&#45;-Auswahlfeld bei Hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Dropdown&#45;-Auswahlfeld bei Hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`Environment.DropDownMouseOverText`|  
|![Dropdown&#45;-Auswahlfeld bei Hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Rahmen|`Environment.DropDownMouseOverBorder`|  
|![Dropdown&#45;-Auswahlfeld bei Hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Auswahlfeld**|Trennzeichen|`Environment.DropDownButtonMouseOverSeparator`|  
|![Dropdown&#45;-Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`Environment.DropDownButtonMouseOverBackground`|  
|![Dropdown&#45;-Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownMouseOverGlyph`|  
|![Dropdown&#45;Liste bei Hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown Liste**|Hintergrund (Menüelement)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Dropdown&#45;Liste bei Hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown Liste**|Vordergrund (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Dropdown&#45;Liste bei Hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Dropdown Liste**|Rahmen (Menüelement)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Dropdown&#45;-Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Hintergrund|`Environment.DropDownMouseDownBackground`|  
|![Dropdown&#45;-Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Vordergrund (Text)|`Environment.DropDownMouseDownText`|  
|![Dropdown&#45;-Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Rahmen|`Environment.DropDownMouseDownBorder`|  
|![Dropdown&#45;-Auswahlfeld gedrückt](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Auswahlfeld**|Trennzeichen|`Environment.DropDownButtonMouseDownSeparator`|  
|![Dropdown&#45;-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`Environment.DropDownButtonMouseDownBackground`|  
|![Dropdown&#45;-Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Dropdown&#45;-Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Hintergrund|`Environment.DropDownDisabledBackground`|  
|![Dropdown&#45;-Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Vordergrund (Text)|`Environment.DropDownDisabledText`|  
|![Dropdown&#45;-Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Rahmen|`Environment.DropDownDisabledBorder`|  
|![Dropdown&#45;-Auswahlfeld deaktiviert](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Trennzeichen|Kein Trennzeichen|  
|![Dropdown&#45;Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Hintergrund|N/V|  
|![Dropdown&#45;Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Vordergrund (Glyphe)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Trennschaltfläche  
 Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Dropdownlisten für unterteilte Schaltflächen sind Implementierungen der Befehlsleiste [Menus](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Geteilte Schaltfläche (rote Linie)](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten unterteilten Schaltfläche  
  
Nicht empfohlen...  
- für alle anderen Arten von Schaltflächen  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Trenn Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Trenn Schaltfläche (Standard)**|Hintergrund|Keine|  
|![Trenn Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Trenn Schaltfläche (Standard)**|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|![Trenn Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Trenn Schaltfläche (Standard)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonGlyph`|  
|![Trenn Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Trenn Schaltfläche (Standard)**|Rahmen|N/V|  
|![Trenn Schaltfläche](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Trenn Schaltfläche (Standard)**|Trennzeichen|N/V|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Unterteilte Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (bei hover)**|Hintergrund|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Unterteilte Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (bei hover)**|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|![Unterteilte Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (bei hover)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Unterteilte Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (bei hover)**|Rahmen|`Environment.CommandBarBorder`|  
|![Unterteilte Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Unterteilte Schaltfläche (bei hover)**|Trennzeichen|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Geteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Trenn Schaltfläche (gedrückt)**|Hintergrund|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Geteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Trenn Schaltfläche (gedrückt)**|Vordergrund (Text)|`Environment.CommandBarTextMouseDown`|  
|![Geteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Trenn Schaltfläche (gedrückt)**|Vordergrund (Glyphe)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Geteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Trenn Schaltfläche (gedrückt)**|Rahmen|`Environment.CommandBarBorder`|  
|![Geteilte Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Trenn Schaltfläche (gedrückt)**|Trennzeichen|N/V|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Trenn Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Trenn Schaltfläche (deaktiviert)**|Hintergrund|N/V|  
|![Trenn Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Trenn Schaltfläche (deaktiviert)**|Vordergrund (Text)|`Environment.ComboBoxItemTextInactive`|  
|![Trenn Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Trenn Schaltfläche (deaktiviert)**|Vordergrund (Glyphe)|`Environment.CommandBarTextInactive`|  
|![Trenn Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Trenn Schaltfläche (deaktiviert)**|Rahmen|N/V|  
|![Trenn Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Trenn Schaltfläche (deaktiviert)**|Trennzeichen|N/V|  
  
##### <a name="more-options-and-overflow-buttons"></a>Schaltflächen "Weitere Optionen" und "Überlauf"  
 Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.  
  
 ![Weitere Optionen Redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Empfohlen...  
 für die benutzerdefinierten Schaltflächen "Weitere Optionen" oder "Überlauf"  
  
 Nicht empfohlen...  
 für Schaltflächen mit einer von den Schaltflächen "Weitere Optionen" oder "Überlauf" abweichenden Funktionalität  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsBackground`|  
|![Weitere Optionen](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsGlyph`|  
|![Überlauf Schaltfläche](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Läufen**|Hintergrund|`Environment.CommandBarOptionsBackground`|  
|![Überlauf Schaltfläche](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Läufen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsGlyph`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen für den Mauszeiger](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Weitere Optionen für den Mauszeiger](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Überlauf bei Hover](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Läufen**|Hintergrund|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Überlauf bei Hover](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Läufen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Weitere Optionen gedrückt](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Weitere Optionen**|Hintergrund|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Weitere Optionen gedrückt](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Weitere Optionen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Läufen**|Hintergrund|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Läufen**|Vordergrund (Glyphe)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Dokumentfenster  
 Dokumentfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 Wenn Sie Dokumentfenster-Farbtoken verwenden, dürfen diese nur für ähnliche Elemente und paarweise verwendet werden. Andernfalls zeigen sich auf der Benutzeroberfläche unerwartete Ergebnisse.  
  
#### <a name="document-window-frame"></a>Dokumentfensterrahmen  
 Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Ein unverankertes Dokumentfenster, das sich außerhalb der IDE befindet, ist dennoch in einen Dokumentursprung eingebettet und verfügt über Hintergrund-, Rahmen-, Text- und Registerkartenfarben, die sich von den Farben der in der IDE angedockten Fenster nicht unterscheiden. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.  
  
 ![Angedocktes Dokument Fenster (rote Linie)](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Angedocktes Dokument Fenster**  
  
 ![Unverankertes Dokument Fenster Redline](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Unverankerte Dokument Fenster**  
  
 Empfohlen...  
 für alle Benutzeroberflächenelemente, die Sie auf das Dokumentfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|Dokument: angedockt oder unverankert|Hintergrund|Hängt vom Dokumenttyp ab.|  
|Dokument: angedockt oder unverankert|Vordergrund (Text)|Hängt vom Dokumenttyp ab.|  
|Dokument: angedockt oder unverankert|Rahmen|`Environment.ToolWindowBorder`|  
|![Frame Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Frame: unverankert, mit Fokus**|Hintergrund|`Environment.ToolWindowFloatingFrame`|  
|![Frame Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Frame: unverankert, mit Fokus**|Vordergrund (Text)|`Environment.ToolWindowFloatingFrame`|  
|![Frame Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Frame: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Frame Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Frame: unverankert, mit Fokus**|Rahmen|`Environment.MainWindowActiveDefaultBorder`|  
|![Frame Fokus](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Frame: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Auf transparent festgelegt|  
|![Frame ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame: unverankert, ohne Fokus**|Hintergrund|`Environment.ToolWindowFloatingFrameInactive`|  
|![Frame ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame: unverankert, ohne Fokus**|Vordergrund (Text)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Frame ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame: unverankert, ohne Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Frame ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame: unverankert, ohne Fokus**|Rahmen|`Environment.MainWindowInactiveBorder`|  
|![Frame ohne Fokus](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame: unverankert, ohne Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Auf transparent festgelegt|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Frame mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Frame: unverankert, mit Fokus**|Hintergrund (Glyphe)|`Environment.RaftedWindowButtonHoverActive`|  
|![Frame mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Frame: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Frame mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Frame: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Frame ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame: unverankert, ohne Fokus**|Hintergrund (Glyphe)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Frame ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame: unverankert, ohne Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Frame ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame: unverankert, ohne Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Frame mit Fokus gedrückt](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Frame: unverankert, mit Fokus**|Hintergrund (Glyphe)|`Environment.RaftedWindowButtonDown`|  
|![Frame mit Fokus gedrückt](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Frame: unverankert, mit Fokus**|Vordergrund (Glyphe)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Frame mit Fokus gedrückt](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Frame: unverankert, mit Fokus**|Rahmen (Glyphe)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Dokumentregisterkarten  
 Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.  
  
 ![Dokument Registerkarte (rote Linie)](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Empfohlen...  
 für jede Benutzeroberfläche, die auf Dokumentregisterkarten abgestimmt sein soll, und wenn Designaktualisierungen oder neue Designfarben automatisch ausgewählt werden sollen.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
##### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten  
 Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:  
  
- Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.  
  
- Hintergrund Registerkarten sind Dokument Registerkarten, die nicht die derzeit ausgewählte Registerkarte sind. Nachdem Sie darauf geklickt haben, werden Sie zur ausgewählten Registerkarte und erhalten alle Hintergrund-, Rahmen-und Textfarben von den Tokennamen.  
  
  ![Dokument Registerkarte rote Linie öffnen](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Empfohlen...  
  für die Erstellung benutzerdefinierter Dokumentregisterkarten  
  
  Nicht empfohlen...  
  - für vorläufige Registerkarten (Vorschau)  
  
- für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
##### <a name="selected-tab"></a>Ausgewählte Registerkarte  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokument Registerkarte, mit Fokus**|Hintergrund|`Environment.FileTabSelectedGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokument Registerkarte, mit Fokus**|Vordergrund (Text)|`Environment.FileTabSelectedText`|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokument Registerkarte, mit Fokus**|Rahmen|`Environment.FileTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Ausgewählte Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Ausgewählte Dokument Registerkarte, mit Fokus**|Dokumentrahmen|`Environment.FileTabDocumentBorderBackground`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokument Registerkarte, ohne Fokus**|Hintergrund|`Environment.FileTabInactiveGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokument Registerkarte, ohne Fokus**|Vordergrund (Text)|`Environment.FileTabInactiveText`|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokument Registerkarte, ohne Fokus**|Rahmen|`Environment.FileTabInactiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Ausgewählte Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Ausgewählte Dokument Registerkarte, ohne Fokus**|Dokumentrahmen|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Hintergrundregisterkarte  
 **Standard**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Hintergrund Registerkarte](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Standard Registerkarte für Hintergrund**|Hintergrund|`Environment.FileTabBackground`|  
|![Hintergrund Registerkarte](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Standard Registerkarte für Hintergrund**|Vordergrund (Text)|`Environment.FileTabText`|  
|![Hintergrund Registerkarte](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Standard Registerkarte für Hintergrund**|Rahmen|`Environment.FileTabBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Hintergrund" bei Hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund" bei Hover**|Hintergrund|`Environment.FileTabHotGradientTop`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Registerkarte "Hintergrund" bei Hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund" bei Hover**|Vordergrund (Text)|`Environment.FileTabHotText`|  
|![Registerkarte "Hintergrund" bei Hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Registerkarte "Hintergrund" bei Hover**|Rahmen|`Environment.FileTabHotBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
##### <a name="preview-tab"></a>Vorschauregisterkarte  
 Die Vorschauregisterkarte wird auf der rechten Seite des Dokument-Registerkartenkanals angezeigt, wenn der Benutzer auf ein Element im Toolfenster des Projektmappen-Explorers klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.  
  
 ![Vorschau Registerkarte (rote Linie)](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Empfohlen...  
 wenn Sie eine vorläufige Vorschau erstellen und Elemente mit der Farbe der aktuellen Vorschauregisterkarte übereinstimmen sollen.  
  
Nicht empfohlen...  
- für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau)  

- für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
  **Ausgewählte Vorschau Registerkarte: Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vorschau Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschau Registerkarte mit Fokus**|Hintergrund|`Environment.FileTabProvisionalSelectedActive`|  
|![Vorschau Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschau Registerkarte mit Fokus**|Vordergrund (Text)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Vorschau Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschau Registerkarte mit Fokus**|Rahmen|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Vorschau Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Vorschau Registerkarte mit Fokus**|Dokumentrahmen|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Ausgewählte Vorschau Registerkarte: ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vorschau Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Nicht fokussierte Vorschau Registerkarte**|Hintergrund|`Environment.FileTabProvisionalSelectedInactive`|  
|![Vorschau Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Nicht fokussierte Vorschau Registerkarte**|Vordergrund (Text)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Vorschau Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Nicht fokussierte Vorschau Registerkarte**|Rahmen|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Vorschau Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Nicht fokussierte Vorschau Registerkarte**|Dokumentrahmen|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Registerkarte "Hintergrund Vorschau": Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Registerkarte "Vorschau" im Hintergrund**|Hintergrund|`Environment.FileTabProvisionalInactive`|  
|![Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Registerkarte "Vorschau" im Hintergrund**|Vordergrund (Text)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Registerkarte "Vorschau"](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Registerkarte "Vorschau" im Hintergrund**|Rahmen|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Registerkarte "Hintergrund Vorschau": hover**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Vorschau" im Hintergrund](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Registerkarte "Vorschau" im Hintergrund bei Hover**|Hintergrund|`Environment.FileTabProvisionalHover`|  
|![Registerkarte "Vorschau" im Hintergrund](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Registerkarte "Vorschau" im Hintergrund bei Hover**|Vordergrund (Text)|`Environment.FileTabProvisionalHoverForeground`|  
|![Registerkarte "Vorschau" im Hintergrund](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Registerkarte "Vorschau" im Hintergrund bei Hover**|Rahmen|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
##### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche  
 Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dokumentüberlauf-Dropdownmenü, das mithilfe der **CommandBarMenu** -Farben (siehe [Menus](../misc/shared-colors.md#BKMK_CommandMenus)) gesteuert wird, zeigt eine Liste aller geöffneten Dokumente (sichtbar und unsichtbar) an. Die Überlauf-Glyphe ändert sich abhängig davon, ob alle geöffneten Dokumente im Registerkartenkanal angezeigt werden.  
  
 ![Überlauf Redline](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Empfohlen...  
für die Erstellung einer benutzerdefinierten Dokumentüberlauf-Schaltfläche  

Nicht empfohlen...  
- für Benutzeroberflächen, die keine Ähnlichkeit mit einer Überlaufschaltfläche haben  

- für Überlaufschaltflächen auf der Befehlsleiste  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Läufen](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokument Überlauf-Schaltfläche**|Hintergrund|`Environment.DocWellOverflowButtonBackground`|  
|![Läufen](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokument Überlauf-Schaltfläche**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonGlyph`|  
|![Läufen](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Dokument Überlauf-Schaltfläche**|Rahmen|N/V|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Überlauf bei Hover](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Schaltfläche "Dokument Überlauf" bei Hover**|Hintergrund|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Überlauf bei Hover](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Schaltfläche "Dokument Überlauf" bei Hover**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Überlauf bei Hover](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Schaltfläche "Dokument Überlauf" bei Hover**|Rahmen|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Schaltfläche für gedrückte Dokument Überlauf**|Hintergrund|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Schaltfläche für gedrückte Dokument Überlauf**|Vordergrund (Glyphe)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Überlauf gedrückt](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Schaltfläche für gedrückte Dokument Überlauf**|Rahmen|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Toolfenster  
 Toolfenster müssen nicht repliziert werden, weil sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.  
  
 ![Tool Fenster (rote Linie)](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
#### <a name="tool-window-frame"></a>Toolfensterrahmen  
 Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.  
  
 ![Tool Fensterrahmen (rote Linie)](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Angedockt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tool Fenster angedockt](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Tool Fenster angedockt](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Rahmen|`Environment.ToolWindowBorder`|  
  
 **Unverankert: mit Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tool Fenster mit Fokus](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Tool Fenster mit Fokus](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Rahmen|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Floating: ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tool Fenster ohne Fokus](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Hintergrund|`Environment.ToolWindowBackground`|  
|![Tool Fenster ohne Fokus](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Rahmen|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters  
 Der Rahmen der Titelleiste ist kein echter Rahmen, sondern ein dicker Strich am oberen Rand der Titelleiste. Er verfügt über keinen Tokennamen für den Zustand "Ohne Fokus".  
  
 ![Tool Fenstertitelleiste (rote Linie)](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Hintergrund|`Environment.TitleBarActiveGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Vordergrund (Text)|`Environment.TitleBarActiveText`|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Rahmen|`Environment.TitleBarActiveBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
|![Titelleiste mit Fokus](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Titelleiste mit Fokus**|Ziehpunkt|`Environment.TitleBarDragHandleActive`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Hintergrund|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Vordergrund (Text)|`Environment.TitleBarInactiveText`|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Rahmen|N/V|  
|![Titelleiste ohne Fokus](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Titelleiste ohne Fokus**|Ziehpunkt|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Titelleisten-Schaltflächen  
 ![Titelleisten Schaltfläche rote Linie](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Empfohlen...  
 für Schaltflächen auf der Benutzeroberfläche, die Farbtoken aus den Toolfenster-Titelleisten verwenden.  
  
Nicht empfohlen...  
- für Schaltflächen, die an anderer Stelle angezeigt werden  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titelleisten Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Gestellt**|Hintergrund|N/V|  
|![Titelleisten Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Gestellt**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Titelleisten Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Gestellt**|Rahmen|N/V|  
|![Titelleisten Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Hintergrund|N/V|  
|![Titelleisten Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Titelleisten Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Ohne Fokus**|Rahmen|N/V|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titelleisten Schaltfläche mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Gestellt**|Hintergrund|`Environment.ToolWindowButtonHoverActive`|  
|![Titelleisten Schaltfläche mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Gestellt**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Titelleisten Schaltfläche mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Gestellt**|Rahmen|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Titelleisten Schaltfläche ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Hintergrund|`Environment.ToolWindowButtonHoverInactive`|  
|![Titelleisten Schaltfläche ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Titelleisten Schaltfläche ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Ohne Fokus**|Rahmen|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titelleisten Schaltfläche mit Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Gestellt**|Hintergrund|`Environment.ToolWindowButtonDown`|  
|![Titelleisten Schaltfläche mit Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Gestellt**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Titelleisten Schaltfläche mit Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Gestellt**|Rahmen|`Environment.ToolWindowButtonDownBorder`|  
|![Titelleisten Schaltfläche ohne Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Hintergrund|`Environment.ToolWindowButtonDown`|  
|![Titelleisten Schaltfläche ohne Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Titelleisten Schaltfläche ohne Fokus und gedrückt](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Ohne Fokus**|Rahmen|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten  
 ![Tool Fenster Registerkarte (rote Linie)](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf die Toolfenster abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Ausgewählte Registerkarte**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tool Fenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte mit Fokus**|Hintergrund|`Environment.ToolWindowTabSelectedTab`|  
|![Tool Fenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte mit Fokus**|Vordergrund (Text)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Tool Fenster-Registerkarte mit Fokus](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte mit Fokus**|Rahmen|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tool Fenster Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte ohne Fokus**|Hintergrund|`Environment.ToolWindowTabSelectedTab`|  
|![Tool Fenster Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte ohne Fokus**|Vordergrund (Text)|`Environment.ToolWindowTabSelectedText`|  
|![Tool Fenster Registerkarte ohne Fokus](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Ausgewählt, Tool Fenster-Registerkarte ohne Fokus**|Rahmen|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
 **Hintergrund Registerkarte**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte des Tool Fenster Hintergrunds](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Registerkarte "Hintergrund Tool Fenster"**|Hintergrund|`Environment.ToolWindowTabGradientBegin`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps|  
|![Registerkarte des Tool Fenster Hintergrunds](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Registerkarte "Hintergrund Tool Fenster"**|Vordergrund (Text)|`Environment.ToolWindowTabText`|  
|![Registerkarte des Tool Fenster Hintergrunds](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Registerkarte "Hintergrund Tool Fenster"**|Rahmen|`Environment.ToolWindowTabBorder`|  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Registerkarte "Tool Fenster" im Hintergrund](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Registerkarte des Hintergrund Tool Fensters bei Hover**|Hintergrund|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> In Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps|  
|![Registerkarte "Tool Fenster" im Hintergrund](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Registerkarte des Hintergrund Tool Fensters bei Hover**|Vordergrund (Text)|`Environment.ToolWindowTabMouseOverText`|  
|![Registerkarte "Tool Fenster" im Hintergrund](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Registerkarte des Hintergrund Tool Fensters bei Hover**|Rahmen|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Auf dieselbe Farbe wie der Hintergrund festgelegt|  
  
#### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten  
 ![Automatisches&#45;Ausblenden von Redline](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Empfohlen...  
 für alle Situationen, in denen Sie Ihre Benutzeroberfläche auf automatisch ausgeblendete Toolfenster-Registerkarten abstimmen möchten.  
  
 Nicht empfohlen...  
 für Benutzeroberflächen, die bei einer Designaktualisierung der Shell nicht automatisch geändert werden sollen  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Register&#45;Karte automatisch ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Standard Registerkarte automatisch ausblenden**|Hintergrund|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Register&#45;Karte automatisch ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Standard Registerkarte automatisch ausblenden**|Vordergrund (Text)|`Environment.AutoHideTabText`|  
|![Register&#45;Karte automatisch ausblenden](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Standard Registerkarte automatisch ausblenden**|Rahmen|`Environment.AutoHideTabBorder`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Register&#45;Karte "automatisch ausblenden" bei Hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Registerkarte "automatisch ausblenden" bei Hover**|Hintergrund|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Register&#45;Karte "automatisch ausblenden" bei Hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Registerkarte "automatisch ausblenden" bei Hover**|Vordergrund (Text)|`Environment.AutoHideTabMouseOverText`|  
|![Register&#45;Karte "automatisch ausblenden" bei Hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Registerkarte "automatisch ausblenden" bei Hover**|Rahmen|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente  
 Wenn Sie für Ihr Feature eine Visual Studio-Standardbefehlsleiste verwenden, haben Sie Zugriff auf formatierte Shell-Steuerelemente. Diese gemeinsam verwendeten Steuerelemente sollten nicht von einer Vorlage neu erstellt werden. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.  
  
#### <a name="search-box"></a>Suchfeld  
 Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.  
  
 Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:  
  
- "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.  
  
- "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.  
  
- "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).  
  
- "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.  
  
  ![Suchfeld (rote Linie)](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Empfohlen...  
  für das Entwerfen eines benutzerdefinierten Suchfelds  
  
  Nicht empfohlen...  
  - für Elemente, die kein Suchfeld darstellen  
  
- für Elemente, die nicht generell auf die Suchfeld-Benutzeroberfläche abgestimmt sein sollen  
  
  **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabe Feld mit Fokus](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Hintergrund|`SearchControl.FocusedBackground`|  
|![Sucheingabe Feld mit Fokus](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`SearchControl.FocusedBackground`|  
|![Sucheingabe Feld mit Fokus](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Rahmen|`SearchControl.FocusedBorder`|  
|![Sucheingabe Feld mit Fokus](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Eingabefeld**|Trennzeichen|`SearchControl.FocusedDropDownSeparator`|  
|![Such Aktions Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Aktions Schaltfläche**|Hintergrund|Keine|  
|![Such Aktions Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Suchen")|`SearchControl.SearchGlyph`|  
|![Such Aktions Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Beenden")|`SearchControl.StopGlyph`|  
|![Such Aktions Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Löschen")|`SearchControl.ClearGlyph`|  
|![Such Aktions Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Aktions Schaltfläche**|Rahmen|N/V|  
|![Dropdown&#45;Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`SearchControl.FocusedDropDownButton`|  
|![Dropdown&#45;Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Dropdown&#45;Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Dropdown Schaltfläche**|Rahmen|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Ohne Fokus**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabe Feld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Hintergrund|`SearchControl.SearchActiveBackground`|  
|![Sucheingabe Feld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Vordergrund (Text)|`SearchControl.SearchActiveBackground`|  
|![Sucheingabe Feld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Rahmen|`SearchControl.UnfocusedBorder`|  
|![Sucheingabe Feld ohne Fokus](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktives Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Eingabefeld "nicht fokussiert" und "inaktiv" suchen](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Hintergrund|`SearchControl.Unfocused`|  
|![Eingabefeld "nicht fokussiert" und "inaktiv" suchen](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Vordergrund (Text)|`SearchControl.Unfocused`|  
|![Eingabefeld "nicht fokussiert" und "inaktiv" suchen](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Rahmen|`SearchControl.UnfocusedBorder`|  
|![Eingabefeld "nicht fokussiert" und "inaktiv" suchen](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Inaktives Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Such Aktions Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Aktions Schaltfläche**|Hintergrund|N/V|  
|![Such Aktions Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Suchen")|`SearchControl.SearchGlyph`|  
|![Such Aktions Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Beenden")|`SearchControl.StopGlyph`|  
|![Such Aktions Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe "Löschen")|`SearchControl.ClearGlyph`|  
|![Such Aktions Schaltfläche ohne Fokus](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Aktions Schaltfläche**|Rahmen|N/V|  
|![Dropdown&#45;-Schaltfläche "Suche" ohne Fokus](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`SearchControl.UnfocusedDropDownButton`|  
|![Dropdown&#45;-Schaltfläche "Suche" ohne Fokus](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Dropdown&#45;-Schaltfläche "Suche" ohne Fokus](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Dropdown Schaltfläche**|Rahmen|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche "Aktion suchen" gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Aktions Schaltfläche**|Hintergrund|`SearchControl.ActionButtonMouseDown`|  
|![Schaltfläche "Aktion suchen" gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Schaltfläche "Aktion suchen" gedrückt](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Aktions Schaltfläche**|Rahmen|`SearchControl.ActionButtonMouseDownBorder`|  
|![Dropdown&#45;-Schaltfläche für Suche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|`SearchControl.MouseDownDropDownButton`|  
|![Dropdown&#45;-Schaltfläche für Suche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Dropdown&#45;-Schaltfläche für Suche gedrückt](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Dropdown Schaltfläche**|Rahmen|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Hervorgehoben (nur Text)**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabe Feld-Hervorhebung](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem Text**|Hintergrund|`SearchControl.Selection`|  
|![Sucheingabe Feld-Hervorhebung](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem Text**|Vordergrund (Text)|`SearchControl.FocusedBackground`|  
|![Sucheingabe Feld-Hervorhebung](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem Text**|Rahmen|Keine|  
|![Sucheingabe Feld-Hervorhebung](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Eingabefeld mit hervorgehobenem Text**|Trennzeichen|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sucheingabe Feld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Hintergrund|`SearchControl.Disabled`|  
|![Sucheingabe Feld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Vordergrund (Text)|`SearchControl.Disabled`|  
|![Sucheingabe Feld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Rahmen|`SearchControl.DisabledBorder`|  
|![Sucheingabe Feld deaktiviert](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Eingabefeld**|Trennzeichen|`SearchControl.DropDownSeparator`|  
|![Such Aktions Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Aktions Schaltfläche**|Hintergrund|Keine|  
|![Such Aktions Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Aktions Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Such Aktions Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Aktions Schaltfläche**|Rahmen|Keine|  
|![Dropdown&#45;Schaltfläche für Suche deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown Schaltfläche**|Hintergrund|Keine|  
|![Dropdown&#45;Schaltfläche für Suche deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown Schaltfläche**|Vordergrund (Glyphe)|`SearchControl.DisabledDownButtonGlyph`|  
|![Dropdown&#45;Schaltfläche für Suche deaktiviert](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Dropdown Schaltfläche**|Rahmen|Keine|  
  
##### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld  
 Das Dropdownmenü im Suchfeld kann etwas komplexer sein als andere Dropdownmenüs in Visual Studio. Die Bereiche "Empfohlene Suchbegriffe" und "Suchoptionen" können alleine oder zusammen im Menü erscheinen, und jedem Bereich kann eine eigene Farbe zugeordnet sein. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.  
  
 ![Dropdown&#45;-rote Linie suchen](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Empfohlen...  
- für die Erstellung einer benutzerdefinierten Dropdownliste im Suchfeld  

- bei Verwendung der richtigen Tokennamen für die entsprechenden Listenkomponenten  

Nicht empfohlen...  
- für Dropdownlisten, die in anderen Kontexten angezeigt werden  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard (keine anderen Zustände)**  
  
|Element|Tokenname: Category.color|  
|-------------|--------------------------------|  
|Rahmen|`SearchControl.PopupBorder`|  
|Trennzeichen|`SearchControl.PopupSectionHeaderSeparator`|  
|Schatten|`Environment.DropShadowBackground`|  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Empfohlene Suchvorgänge**|Hintergrund|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Empfohlene Suchvorgänge**|Vordergrund (Text)|`SearchControl.PopupItemText`|  
|![Kontrollkästchen suchen](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Hintergrund|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Hintergrund|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kontrollkästchen suchen](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxText`|  
|![Kontrollkästchen suchen](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Linktext)|`SearchControl.PopupButtonText`|  
|![Kontrollkästchen suchen](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Headerhintergrund|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Headerhintergrund|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kontrollkästchen suchen](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Suchoptionen (Kontrollkästchen)**|Vordergrund (Headertext)|`SearchControl.PopupSectionHeaderText`|  
|![Suchoptionen](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Suchoptionen (Link)**|Vordergrund (Headertext)|`SearchControl.PopupSectionHeaderText`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Suche vorgeschlagen bei Hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Empfohlene Suchvorgänge**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suche vorgeschlagen bei Hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Empfohlene Suchvorgänge**|Vordergrund (Text)|`SearchControl.PopupMouseOverItemText`|  
|![Suche vorgeschlagen bei Hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Empfohlene Suchvorgänge**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
|![Kontrollkästchen zum Suchen nach dem Mauszeiger](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suchoptionen bei Hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Hintergrund|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Kontrollkästchen zum Suchen nach dem Mauszeiger](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Suchoptionen bei Hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Kontrollkästchen zum Suchen nach dem Mauszeiger](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Suchoptionen bei Hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Kontrollkästchen zum Suchen nach dem Mauszeiger](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
|![Suchoptionen bei Hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Suchoptionen**|Rahmen|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Gedrückte Suchoptionen](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Gedrückte Suchoptionen](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Kontrollkästchen-Hintergrund|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Gedrückte Suchoptionen](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Vordergrund (Kontrollkästchentext)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Linkhintergrund|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Gedrückte Suchoptionen](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Linkhintergrund|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Obwohl in Benutzeroberflächen mit modernen Designs nicht verwendet, gibt es Farbverlaufsstopps und -werte für diesen Hintergrund.|  
|![Suche vorgeschlagen](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Empfohlene Suchvorgänge (Kontrollkästchen)**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
|![Gedrückte Suchoptionen](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Suchoptionen**|Vordergrund (Linktext)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Link  
 Der Link ist ein Steuerelement, das keine Kombination aus Vordergrund-/Hintergrundfarbe darstellt. Sie verwenden grundsätzlich die Vordergrund-Linkfarbe, die auf dunklem, grauen und weißem Hintergrund ordnungsgemäß angezeigt wird. Wenn Sie nicht das Farbtoken für das Linksteuerelement verwenden, sehen Sie für den "gedrückten" Zustand die Standardsystemfarbe, die rot blinkend dargestellt wird. Das ist das Signal, dass das Steuerelement nicht das richtige Farbtoken für die Umgebung verwendet.  
  
 ![Hyperlink (rote Linie)](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Empfohlen...  
 für die Erstellung eines benutzerdefinierten Links  
  
 Nicht empfohlen...  
 für Elemente, die keinen Link darstellen  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink-Standard](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Vordergrund (Text)|`Environment.PanelHyperlink`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink bei Hover](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Vordergrund (Text)|`Environment.PanelHyperlinkHover`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink gedrückt](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Vordergrund (Text)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hyperlink deaktiviert](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Vordergrund (Text)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Infoleiste  
 Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.  
  
 ![Info Leiste Redline](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Empfohlen...  
 für die Erstellung einer benutzerdefinierten Infoleiste  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die keine Ähnlichkeit mit einer Infoleiste haben  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Info Leiste](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Info Leiste**|Hintergrund|`Environment.InfoBackground`|  
|![Info Leiste](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Info Leiste**|Vordergrund (Text)|`Environment.InfoText`|  
|![Info Leiste](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Info Leiste**|Rahmen|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Bildlaufleiste  
 Bildlaufleisten erhalten ihr Format von der Visual Studio-Umgebung, sodass kein Design angewendet werden muss. Sie können jedoch entscheiden, dass Sie die in Scrollleisten verwendeten Farben nutzen möchten, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent erscheint.  
  
 ![Bild Lauf Leiste (rote Linie)](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Empfohlen...  
 für die Erstellung einer Benutzeroberfläche, die auf die Visual Studio-Bildlaufleisten abgestimmt sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die nicht grundsätzlich auf die Bildlaufleisten-Benutzeroberfläche abgestimmt sein sollen  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scrollleiste](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Bild Lauf Leiste**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Scrollleiste](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Bild Lauf Leiste**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbBackground`|  
|![ScrollBar-Pfeil](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Scrollpfeil**|Hintergrund|`Environment.ScrollBarArrowBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![ScrollBar-Pfeil](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Scrollpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyph`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bild Lauf Leiste bei Hover](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Bild Lauf Leiste**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Bild Lauf Leiste bei Hover](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Bild Lauf Leiste**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![ScrollBar-Pfeil bei Hover](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Scrollpfeil**|Hintergrund|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![ScrollBar-Pfeil bei Hover](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Scrollpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bild Lauf Leiste gedrückt](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Bild Lauf Leiste**|Bildlaufleiste|`Environment.ScrollBarBackground`|  
|![Bild Lauf Leiste gedrückt](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Bild Lauf Leiste**|Vordergrund (Ziehpunkt)|`Environment.ScrollBarThumbPressedBackground`|  
|![Bild Lauf leisten Pfeil gedrückt](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Scrollpfeil**|Hintergrund|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Auf dieselbe Farbe wie die Bildlaufleiste festgelegt|  
|![Bild Lauf leisten Pfeil gedrückt](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Scrollpfeil**|Vordergrund (Glyphe)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="BKMK_TreeView"></a>Strukturansicht  
 Mehrere Toolfenster, einschließlich Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in der TreeView-Kategorie gesteuert werden. Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.  
  
 ![Strukturansicht (rote Linie)](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Empfohlen...  
 für alle Projekte zur Implementierung einer hierarchischen Organisationsstruktur  
  
Nicht empfohlen...  
- für Elemente, die keine Ähnlichkeit mit einer Strukturansicht haben  

- für eine andere als die angegebene Kombination aus Hintergrund-/Vordergrundfarbe  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Hintergrund|`TreeView.Background`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Vordergrund (Text)|`TreeView.Background`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Vordergrund (Glyphe)|`TreeView.Glyph`|  
|![Strukturansicht](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Rahmen|Keine|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht beim Hover](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Hintergrund|`TreeView.Background`|  
|![Strukturansicht beim Hover](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Vordergrund (Text)|`TreeView.Background`|  
|![Strukturansicht beim Hover](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Vordergrund (Glyphe)|`TreeView.GlyphMouseOver`|  
|![Strukturansicht beim Hover](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Rahmen|Keine|  
  
 **Per Drag & Drop**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Hintergrund|`TreeView.DragOverItem`|  
|![Strukturansicht DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Vordergrund (Text)|`TreeView.DragOverItem`|  
|![Strukturansicht DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Vordergrund (Glyphe)|`TreeView.DragOverItemGlyph`|  
|![Strukturansicht DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Rahmen|Keine|  
  
 **Ausgewählt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht fokussiert](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Gestellt**|Hintergrund|`TreeView.SelectedItemActive`|  
|![Strukturansicht fokussiert](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Gestellt**|Vordergrund (Text)|`TreeView.SelectedItemActive`|  
|![Strukturansicht fokussiert](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Gestellt**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyph`|  
|![Strukturansicht fokussiert](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Gestellt**|Rahmen|`TreeView.FocusVisualBorder`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactiveGlyph`|  
|![Strukturansicht ohne Fokus](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Ohne Fokus**|Rahmen|Keine|  
  
 **Auf "ausgewählt" zeigen**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Strukturansicht mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Gestellt**|Hintergrund|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Gestellt**|Vordergrund (Text)|`TreeView.SelectedItemActive`|  
|![Strukturansicht mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Gestellt**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Strukturansicht mit Fokus auf Hover](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Gestellt**|Rahmen|Keiner`TreeView.FocusVisualBorder`|  
|![Strukturansicht ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`|  
|![Strukturansicht ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Strukturansicht ohne Fokus auf Hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Ohne Fokus**|Rahmen|Keine|  
  
#### <a name="button-controls"></a>Schaltflächen-Steuerelemente  
 ![Schaltflächen-Steuerelement Redline](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Empfohlen...  
 für Schaltflächen im Dokument, die Sie in Visual Studio-Designs (Hell, Dunkel, Blau oder kontrastreiches Systemdesign) integrieren möchten.  
  
 Nicht empfohlen...  
 für Schaltflächen, die vor einem benutzerdefinierten Hintergrund angezeigt werden, der nicht Bestandteil eines Visual Studio-Designs ist  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Schaltfläche|`CommonControls.Button`|  
|![Schaltfläche](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Schaltflächenrahmen|`CommonControls.ButtonBorder`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Schaltfläche|`CommonControls.ButtonDisabled`|  
|![Schaltfläche deaktiviert](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Schaltflächenrahmen|`CommonControls.ButtonBorderDisabled`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Schaltfläche|`CommonControls.ButtonHover`|  
|![Schaltfläche bei Hover](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Schaltflächenrahmen|`CommonControls.ButtonBorderHover`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Schaltfläche|`CommonControls.ButtonPressed`|  
|![Schaltfläche gedrückt](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Schaltflächenrahmen|`CommonControls.ButtonBorderPressed`|  
  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Schaltfläche|`CommonControls.ButtonFocused`|  
|![Schaltfläche mit Fokus](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Schaltflächenrahmen|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente  
 ![Kontrollkästchen (rote Linie)](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Empfohlen...  
 für Kontrollkästchen-Steuerelemente im Dokumentursprung  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Kontrollkästchen-Steuerelement sind  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Hintergrund|`CommonControls.CheckBoxBackground`|  
|![Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Rahmen|`CommonControls.CheckBoxBorder`|  
|![Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Kontrollkästchen](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glyphe|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Hintergrund|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Rahmen|`CommonControls.CheckBoxBorderDisabled`|  
|![Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Kontrollkästchen deaktiviert](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glyphe|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen bei Hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Hintergrund|`CommonControls.CheckBoxBackgroundHover`|  
|![Kontrollkästchen bei Hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Rahmen|`CommonControls.CheckBoxBorderHover`|  
|![Kontrollkästchen bei Hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Kontrollkästchen bei Hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glyphe|`CommonControls.CheckBoxGlyphHover`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen gedrückt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Hintergrund|`CommonControls.CheckBoxBackgroundPressed`|  
|![Kontrollkästchen gedrückt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Rahmen|`CommonControls.CheckBoxBorderPressed`|  
|![Kontrollkästchen gedrückt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Kontrollkästchen gedrückt](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glyphe|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Hintergrund|`CommonControls.CheckBoxBackgroundFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Rahmen|`CommonControls.CheckBoxBorderFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Kontrollkästchen mit Fokus](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glyphe|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Dropdownlisten-/Kombinationsfeld-Steuerelement  
 ![&#45;Dropdown&#47;-Kombinations Feld (rote Linie)](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Empfohlen...  
für Dropdownlisten und Kombinationsfelder, die Teil des Dokumentursprungs sind.  

Nicht empfohlen...  
- für Benutzeroberflächenelemente, die keine Dropdownliste und kein Kombinationsfeld sind  

- für eine [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) oder ein [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) in der Befehlsleiste  
  
  **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Hintergrund|`CommonControls.ComboBoxBackground`|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Rahmen|`CommonControls.ComboBoxBorder`|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Trennzeichen|`CommonControls.ComboBoxSeparator`|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyphe|`CommonControls.ComboBoxGlyph`|  
|![Kombinations&#45;Feld&#47;"Dropdown"](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Hintergrund|`CommonControls.ComboBoxBackgroundDisabled`|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Rahmen|`CommonControls.ComboBoxBorderDisabled`|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Trennzeichen|`CommonControls.ComboBoxSeparatorDisabled`|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyphe|`CommonControls.ComboBoxGlyphDisabled`|  
|![&#45;Dropdown&#47;-Kombinations Feld deaktiviert](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Hintergrund|`CommonControls.ComboBoxBackgroundHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Rahmen|`CommonControls.ComboBoxBorderHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Trennzeichen|`CommonControls.ComboBoxSeparatorHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyphe|`CommonControls.ComboBoxGlyphHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld bei Hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Hintergrund|`CommonControls.ComboBoxBackgroundPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Rahmen|`CommonControls.ComboBoxBorderPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Trennzeichen|`CommonControls.ComboBoxSeparatorPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyphe|`CommonControls.ComboBoxGlyphPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld gedrückt](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Gestellt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Hintergrund|`CommonControls.ComboBoxBackgroundFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Rahmen|`CommonControls.ComboBoxBorderFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Trennzeichen|`CommonControls.ComboBoxSeparatorFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyphe|`CommonControls.ComboBoxGlyphFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld mit Fokus](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyphenhintergrund|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Text Eingabeauswahl**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Text&#45;Eingabe&#47;für Dropdown-Kombinations Feld](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Hervorheben|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Gedrückt – Listenelement Ansicht**  
  
|Komponente|Element|Tokenname: Color.category|  
|---------------|-------------|--------------------------------|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListBackground`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListBackgroundHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrund|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorder`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Rahmen|`CommonControls.ComboBoxListBorderFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemText`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextHover`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextPressed`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Elementtext|`CommonControls.ComboBoxListItemTextFocused`|  
|![&#45;Dropdown&#47;-Kombinations Feld-Listenansicht](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Hintergrundschatten|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)  
 Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.  
  
 ![Tabellendaten &#40;Raster-&#41; Steuerelement (rote Linie)](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Empfohlen...  
 für Tabellen- oder Rastersteuerelemente  
  
 Nicht empfohlen...  
 für Benutzeroberflächenelemente, die kein Tabellen- oder Rastersteuerelement sind  
  
##### <a name="column-headers"></a>Spaltenüberschriften  
 Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.  
  
|Phase|Element|Tokenname: Category.color|  
|-----------|-------------|--------------------------------|  
|Standard|Hintergrund|`Header.Default`|  
|Standard|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|Standard|Vordergrund (Glyphe)|`Header.Glyph`|  
|Standard|Rahmen|`Header.SeparatorLine`|  
|Hover|Hintergrund|`Header.MouseOver`|  
|Hover|Vordergrund (Text)|`Environment.CommandBarTextHover`|  
|Hover|Vordergrund (Glyphe)|`Header.MouseOverGlyph`|  
|Hover|Rahmen|`Header.SeparatorLine`|  
|Gedrückt|Hintergrund|`CommonControls.CheckBoxBackgroundPressed`|  
|Gedrückt|Vordergrund (Text)|`CommonControls.CheckBoxBorderPressed`|  
|Gedrückt|Vordergrund (Glyphe)|`CommonControls.CheckBoxTextPressed`|  
|Gedrückt|Rahmen|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Listenansichtselemente  
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.  
  
|Phase|Element|Tokenname: Category.color|  
|-----------|-------------|--------------------------------|  
|Standard|Hintergrund|Transparent|  
|Standard|Vordergrund (Text)|`Environment.CommandBarTextActive`|  
|Standard|Rahmen|Keine|  
|Ausgewählt (aktiv)|Hintergrund|`TreeView.SelectedItemActive`|  
|Ausgewählt (aktiv)|Vordergrund (Text)|`TreeView.SelectedItemActiveText`|  
|Ausgewählt (aktiv)|Rahmen|Keine|  
|Ausgewählt (inaktiv)|Hintergrund|`TreeView.SelectedItemInactive`|  
|Ausgewählt (inaktiv)|Vordergrund (Text)|`TreeView.SelectedItemInactiveText`|  
|Ausgewählt (inaktiv)|Rahmen|Keine|  
  
### <a name="manifest-designer"></a>Manifest-Designer  
 Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Manifest-Designer (rote Linie)](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Empfohlen...  
- für Designer, die Ähnlichkeit mit dem Manifest-Designer haben.  

- anstelle allgemeiner Registerkarten-Steuerelemente, die im oberen Bereich eines Editors im Dokumentursprung angezeigt werden.  

Nicht empfohlen...  
- bei Verwendung von mehr als sechs Registerkarten  

- für Benutzeroberflächenelemente, die nicht wie der Manifest-Designer aufgebaut sind  
  
|Phase|Komponente|Element|Tokenname: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Standard (ausgewählt)|Registerkarte|Hintergrund|`ManifestDesigner.TabActive`|  
|Standard (ausgewählt)|Registerkarte|Rahmen|Keine|  
|Standard (ausgewählt)|Beschreibungsbereich|Hintergrund|`ManifestDesigner.DescriptionPane`|  
|Standard (ausgewählt)|Inhaltsseite|Hintergrund|`ManifestDesigner.Background`|  
|Standard (ausgewählt)|Inhaltsseite|Dialogfeld-Hilfetext|`ManifestDesigner.WatermarkText`<br /><br /> Dieser Tokenname stimmt nicht mit seiner Funktion überein.|  
|Nicht ausgewählt|Registerkarte|Hintergrund|`ManifestDesigner.Tab.Inactive`|  
|Hover|Registerkarte|Hintergrund|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Kennzeichnung (Tagging)  
 Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.  
  
 ![Tagging Redline](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Empfohlen...  
 für Benutzeroberflächen, die Tags unterstützen.  
  
 Nicht empfohlen...  
 für andere Arten von Benutzeroberflächenelementen  
  
#### <a name="tag"></a>Tag  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Standard**|Hintergrund|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Standard**|Vordergrund (Text)|`Tag.Background`|  
|![Markierung bei Hover](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hocker**|Hintergrund|`Tag.HoverBackground`|  
|![Markierung bei Hover](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hocker**|Vordergrund (Text)|`Tag.HoverBackgroundText`|  
|![Gedrücktes Tag](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Drückt**|Hintergrund|`Tag.PressedBackground`|  
|![Gedrücktes Tag](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Drückt**|Vordergrund (Text)|`Tag.PressedBackgroundText`|  
|![Tag ausgewählt](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Ausgewählt**|Hintergrund|`Tag.SelectedBackground`|  
|![Tag ausgewählt](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Ausgewählt**|Vordergrund (Text)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glyphe (Schließsymbol)  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tagglyphe &#40;&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Standard (tagstandard)**|Hintergrund|N/V|  
|![Tagglyphe &#40;&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Standard (tagstandard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyph`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tagsymbol &#40;&#41; bei Hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (tagstandard)**|Hintergrund|`Tag.TagHoverGlyphHoverBackground`|  
|![Tagsymbol &#40;&#41; bei Hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (tagstandard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyphHover`|  
|![Tagsymbol &#40;&#41; bei Hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (tagstandard)**|Rahmen|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Drückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#40;Tagglyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (tagstandard)**|Hintergrund|`Tag.TagHoverGlyphPressedBackground`|  
|![&#40;Tagglyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (tagstandard)**|Vordergrund (Glyphe)|`Tag.TagHoverGlyphPressed`|  
|![&#40;Tagglyphe&#41; gedrückt](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Gedrückt (tagstandard)**|Rahmen|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Tag ausgewählt/Glyphe Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag ausgewählt](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Standard (Tag ausgewählt)**|Hintergrund|N/V|  
|![Tag ausgewählt](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Standard (Tag ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyph`|  
  
 **Tag ausgewählt/Glyphe Hover**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag ausgewählt bei Hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (Tag ausgewählt)**|Hintergrund|`Tag.TagSelectedGlyphHoverBackground`|  
|![Tag ausgewählt bei Hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (Tag ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyphHover`|  
|![Tag ausgewählt bei Hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (Tag ausgewählt)**|Rahmen|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Tag ausgewählt/Glyphe gedrückt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag ausgewählt (gedrückt)](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag ausgewählt)**|Hintergrund|`Tag.TagSelectedGlyphPressedBackground`|  
|![Tag ausgewählt (gedrückt)](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag ausgewählt)**|Vordergrund (Glyphe)|`Tag.TagSelectedGlyphPressed`|  
|![Tag ausgewählt (gedrückt)](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Gedrückt (Tag ausgewählt)**|Rahmen|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Shell  
  
#### <a name="background"></a>Hintergrund  
 Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Ab Visual Studio 2013 werden die obere und untere Hintergrundebene im dunklen und hellen Design auf dieselbe Farbe festgelegt.  
  
 ![Shellhintergrund (rote Linie)](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Empfohlen...  
 für Bereiche, die an den Hintergrund der Visual Studio-Umgebung angepasst werden sollen.  
  
Nicht empfohlen...  
- als Füllung für Bereiche, die keine Hintergrundoberflächen sind  

- als Hintergrund, auf dem Vordergrundelemente platziert werden sollen  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|Untere Ebene|Hintergrund|`Environment.EnvironmentBackground`|  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Obere Ebene|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Befehlsablage  
 Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.  
  
 ![Befehls Regal (rote Linie)](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Empfohlen...  
- für Bereiche, in denen Menüs oder Symbolleisten platziert werden.  

- mit der richtigen Kombination aus Hintergrund-/vordergrundtokenname.  
  
  Nicht empfohlen...  
  für Bereiche, die keine Ähnlichkeit mit einer Befehlsablage aufweisen  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Menüleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Befehlsleiste|Hintergrund<br /><br /> *Farbverlaufs Stopps werden in Visual Studio 2013 hellen und dunklen Designs auf denselben Farbwert festgelegt.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Toolbox  
 Der Werkzeugkasten ist eines der allgemeinen Toolfenster, die am häufigsten in Visual Studio verwendet werden. Es handelt sich um ein Struktursteuerelement, auf das ein bestimmtes Design und ein bestimmter Stil angewendet wurde.  
  
 ![Toolbox (rote Linie)](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Empfohlen...  
 für den Entwurf eines Toolfensters, das immer mit dem Shell-Werkzeugkasten konsistent sein soll.  
  
 Nicht empfohlen...  
 für Elemente, die keine Ähnlichkeit mit der Werkzeugkasten-Benutzeroberfläche haben, oder wenn Sie nicht sicher sind, ob Ihre Benutzeroberfläche bei Änderung der Farben des Shell-Werkzeugkastens Probleme verursacht  
  
 **Standard**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Toolbox übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Hintergrund|`Environment.ToolboxContent`<br /><br /> Kopfzeilen<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind.|  
|![Untergeordneter Toolbox-Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneter Knoten**|Hintergrund|`Environment.ToolboxContent`<br /><br /> Kopfzeilen<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Einzelne Elemente oder das gesamte Fenster, wenn keine Steuerelemente verfügbar sind.|  
|![Toolbox übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Rahmen|Keine|  
|![Untergeordneter Toolbox-Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneter Knoten**|Rahmen|Keine|  
|![Toolbox übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Vordergrund (Glyphe)|`Environment.ToolboxContent`|  
|![Untergeordneter Toolbox-Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneter Knoten**|Vordergrund (Glyphe)|`Environment.ToolboxContent`|  
|![Toolbox übergeordneter Knoten](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Übergeordneter Knoten**|Vordergrund (Text)|`Environment.ToolboxContent`|  
|![Untergeordneter Toolbox-Knoten](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Untergeordneter Knoten**|Vordergrund (Text)|`Environment.ToolboxContent`|  
  
 **Hocker**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Toolbox untergeordneter Knoten bei Hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Toolbox Hover auf untergeordneten Knoten**|Hintergrund|`Environment.ToolboxContentMouseOver`<br /><br /> Nur einzelne Elemente|  
|![Toolbox untergeordneter Knoten bei Hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Toolbox Hover auf untergeordneten Knoten**|Rahmen|Keine|  
|![Toolbox untergeordneter Knoten bei Hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Toolbox Hover auf untergeordneten Knoten**|Vordergrund (Text)|`Environment.ToolboxContentMouseOver`<br /><br /> Nur einzelne Elemente|  
  
 **Ausgewählt**  
  
|Komponente|Element|Tokenname: Category.color|  
|---------------|-------------|--------------------------------|  
|![Toolbox übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Hintergrund|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Rahmen|`TreeView.FocusVisualBorder`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Rahmen|`TreeView.FocusVisualBorder`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Übergeordneter Knoten mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten mit Fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Untergeordneter Knoten mit Fokus**|Vordergrund (Text)|`TreeView.SelectedItemActive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Hintergrund|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Rahmen|Keine|  
|![Toolbox untergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Rahmen|Keine|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Vordergrund (Glyphe)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox übergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Übergeordneter Knoten ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Toolbox untergeordneter Knoten ohne Fokus](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Untergeordneter Knoten ohne Fokus**|Vordergrund (Text)|`TreeView.SelectedItemInactive`<br /><br /> Aus Kategorie [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Farbwertverweis  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Komponente|-Komponente|Element|Phase|Hell|Dunkel|Blau|Hoher Kontrast|  
|Trennlinien|||Standard|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Expander-Glyphe||Vordergrund|Standard|||||  
|Expander-Glyphe||Vordergrund|Hover|||||  
|Expander-Glyphe||Hintergrund|Standard|||||  
|Expander-Glyphe||Hintergrund|Hover|||||  
|Expander-Glyphe||Rahmen|Standard|||||  
|Expander-Glyphe||Rahmen|Hover|||||