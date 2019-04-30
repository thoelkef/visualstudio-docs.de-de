---
title: Erstellen. VSCT-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85e466e7ebb6294a77e89040260c16fe0043e372
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437670"
---
# <a name="authoring-vsct-files"></a>Erstellen. VSCT-Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diesem Dokument wird erläutert, wie Sie eine VSCT-Datei zum Hinzufügen von Menübefehlen, Symbolleisten und andere Elemente der Benutzeroberfläche (UI) auf der integrierten Entwicklungsumgebung (IDE) von Visual Studio zu erstellen. Verwenden Sie diese Schritte aus, wenn Sie ein Visual Studio-Paket (-VSPackage) UI-Elemente hinzufügen, die nicht bereits über eine VSCT-Datei verfügt.  
  
 Für neue Projekte empfehlen wir, dass Sie die Visual Studio-Paket-Vorlage verwenden, da es sich um eine VSCT-Datei generiert, die abhängig von Ihrer Auswahl, bereits die erforderlichen Elemente für einen Menübefehl, ein Toolfenster oder einen benutzerdefinierten Editor enthält. Sie können diese VSCT-Datei, um die Anforderungen Ihres VSPackage ändern. Weitere Informationen dazu, wie Sie eine VSCT-Datei ändern, finden Sie unter den Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Erstellung der Datei  
 Erstellen einer VSCT-Datei in den folgenden Phasen: Erstellen Sie die Struktur für Dateien und Ressourcen zu, deklarieren Sie die Elemente der Benutzeroberfläche, fügen Sie die Elemente der Benutzeroberfläche in der IDE und hinzuzufügen Sie speziellen Verhaltensweisen.  
  
### <a name="file-structure"></a>Dateistruktur  
 Die grundlegende Struktur einer VSCT-Datei ist eine [CommandTable](../../extensibility/commandtable-element.md) Stammelement, enthält eine [Befehle](../../extensibility/commands-element.md) Element und ein [Symbole](../../extensibility/symbols-element.md) Element.  
  
##### <a name="to-create-the-file-structure"></a>Beim Erstellen der Dateistruktur  
  
1. Anhand der Schritte in einer VSCT-Datei dem Projekt hinzufügen [Vorgehensweise: Erstellen Sie ein. VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Fügen Sie die erforderlichen Namespaces, die `CommandTable` Element, wie im folgenden Beispiel dargestellt.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3. In der `CommandTable` -Element, Hinzufügen einer `Commands` Element, um alle Ihre benutzerdefinierten Menüs, Symbolleisten, Befehlsgruppen und Befehle zu hosten. Damit Ihre benutzerdefinierten Elemente der Benutzeroberfläche geladen werden können, die `Commands` Element müssen die `Package` -Attributsatz auf den Namen des Pakets.  
  
     Nach der `Commands` -Element, Hinzufügen einer `Symbols` Element zu definieren, die GUIDs für das Paket und die Namen der Befehls-IDs für Ihre UI-Elemente.  
  
### <a name="including-visual-studio-resources"></a>Visual Studio-Ressourcen einschließlich  
 Verwenden der ["extern"](../../extensibility/extern-element.md) Element, das den Zugriff auf Dateien, die Visual Studio-Befehle und Menüs, die erforderlich sind, stellen Sie Ihre UI-Elemente in der IDE definieren. Wenn Sie Befehle, die außerhalb des Pakets definiert verwenden möchten, verwenden Sie die [UsedCommands](../../extensibility/usedcommands-element.md) Element, um Visual Studio zu informieren.  
  
##### <a name="to-include-visual-studio-resources"></a>Einschließen von Visual Studio-Ressourcen  
  
1. Am oberen Rand der `CommandTable` -Element, fügen Sie eine `Extern` -Element für jede externe Datei, die auf die verwiesen wird und festgelegt werden, die `href` -Attribut auf den Namen der Datei. Sie können die folgenden Headerdateien für den Zugriff auf Visual Studio-Ressourcen verweisen:  
  
    - Stdidcmd.h, definiert IDs für alle Befehle, die von Visual Studio verfügbar gemacht werden.  
  
    - Vsshlids.h, enthält die Befehls-IDs für Visual Studio-Menüs.  
  
2. Wenn Ihr Paket auf alle Befehle, die von Visual Studio oder von anderen Paketen definiert sind aufruft, fügen Sie eine `UsedCommands` Element an, nach der `Commands` Element. Füllen Sie dieses Element mit einem [UsedCommand](../../extensibility/usedcommand-element.md) -Element für jeden Befehl, die Sie aufrufen, d. h. nicht Teil des Pakets. Legen Sie die `guid` und `id` Attribute der `UsedCommand` Elementen, die die GUID und ID-Werte, der die Befehle zum Aufrufen. Weitere Informationen dazu, wie Sie die GUIDs und IDs von Visual Studio-Befehle finden Sie unter [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Verwenden Sie zum Aufrufen von Befehlen aus anderen Paketen die GUID und die ID des Befehls wie in der VSCT-Datei für diese Pakete definiert.  
  
### <a name="declaring-ui-elements"></a>Deklarieren von UI-Elemente  
 Deklarieren Sie alle Elemente der neuen Benutzeroberfläche in der `Symbols` Abschnitt der VSCT-Datei.  
  
##### <a name="to-declare-ui-elements"></a>Um UI-Elemente zu deklarieren.  
  
1. In der `Symbols` -Element, fügen Sie drei [GuidSymbol](../../extensibility/guidsymbol-element.md) Elemente. Jede `GuidSymbol` Element verfügt über eine `name` Attribut und einem `value` Attribut. Legen Sie die `name` Attribut, damit es den Verwendungszweck des Elements widerspiegelt. Die `value` Attribut nimmt eine GUID. (Zum Generieren einer GUID, die für die **Tools** Menü klicken Sie auf **GUID erstellen**, und wählen Sie dann **Registrierungsformat**.)  
  
     Die erste `GuidSymbol` Element stellt dar, das Paket, und in der Regel hat keine untergeordneten Elemente. Die zweite `GuidSymbol` -Element stellt der Befehl festgelegt und enthält alle Symbole, die Ihre Menüs, Gruppen und Befehle zu definieren. Die dritte `GuidSymbol` Element stellt Ihr imagespeicher dar und enthält Symbole für alle Symbole für Ihre Befehle. Wenn Sie keine Befehle, die Symbole zu verwenden, können Sie das dritte weglassen `GuidSymbol` Element.  
  
2. In der `GuidSymbol` -Element, das den Befehlssatz, stellt eine oder mehrere hinzufügen [IDSymbol](../../extensibility/idsymbol-element.md) Elemente. Jede dieser darstellen, ein Menü, Symbolleiste, Gruppe oder Befehl, den Sie an der Benutzeroberfläche hinzufügen.  
  
     Für jede `IDSymbol` -Element legen Sie die `name` -Attribut auf den Namen, die Sie verwenden, um auf das entsprechende Menü, Gruppe oder den Befehl zu verweisen, und legen Sie dann die `value` Element in eine hexadezimale Zahl, die die Befehls-Id darstellt. Keine zwei `IDSymbol` Elemente mit demselben übergeordneten Element können den gleichen Wert aufweisen.  
  
3. Wenn eines Ihrer Elemente der Benutzeroberfläche Symbole benötigen, fügen eine `IDSymbol` -Element für jedes Symbol, um die `GuidSymbol` Element, das Ihr Image-Speicher darstellt.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Einfügen von UI-Elemente in der IDE  
 Die [Menüs](../../extensibility/menus-element.md) Element [Gruppen](../../extensibility/groups-element.md) -Element, und [Schaltflächen](../../extensibility/buttons-element.md) -Element enthalten, die Definitionen für alle Menüs, Gruppen und Befehle, die in Ihrem Paket definiert sind. Fügen Sie diese Menüs, Gruppen und Befehle in der IDE, die entweder mit einer [übergeordneten](../../extensibility/parent-element.md) Element, das Teil der Definition des UI-Elements oder mithilfe eine [CommandPlacement](../../extensibility/commandplacement-element.md) -Element, das definiert, an anderer Stelle.  
  
 Jede `Menu`, `Group`, und `Button` Element verfügt über eine `guid` Attribut und einem `id` Attribut. Immer festgelegt der `guid` Attribut entsprechend den Namen des der `GuidSymbol` Element, das den Befehl darstellt, und festgelegt der `id` auf den Namen des Attributs der `IDSymbol` Element, das Ihre Menü, eine Gruppe oder ein Befehl in der dargestellt`Symbols`Abschnitt.  
  
##### <a name="to-define-ui-elements"></a>Um UI-Elemente zu definieren.  
  
1. Wenn Sie alle neuen Menüs, Untermenüs, Kontextmenüs oder Symbolleisten definieren, fügen Sie eine `Menus` Element der `Commands` Element. Für jedes Menü erstellt werden soll, fügen Sie dann eine [Menü](../../extensibility/menu-element.md) Element, das `Menus` Element.  
  
    Festlegen der `guid` und `id` Attribute der `Menu` -Element, und legen die `type` -Attribut auf die Art des Menüs werden sollen. Sie können auch festlegen, die `priority` Attribut zu, um die relative Position des Menüs in der übergeordneten Gruppe herzustellen.  
  
   > [!NOTE]
   > Die `priority` Attribut gelten nicht für Symbolleisten und Kontextmenüs.  
  
2. Alle Befehle in Visual Studio-IDE müssen von Befehlsgruppen gehostet werden, die die direkten untergeordneten Elemente von Menüs und Symbolleisten sind. Wenn Sie neue Menüs oder Symbolleisten der IDE hinzufügen, müssen diese neue Befehlsgruppen enthalten. Sie können auch Befehlsgruppen zu vorhandenen Menüs und Symbolleisten hinzufügen, sodass Sie Ihre Befehle visuell gruppieren können.  
  
    Wenn Sie neue Befehlsgruppen hinzufügen, müssen Sie zuerst erstellen eine `Groups` -Element, und fügen Sie hinzu eine [Gruppe](../../extensibility/group-element.md) -Element für jede Befehlsgruppe.  
  
    Legen Sie die `guid` und `id` Attribute der einzelnen `Group` -Element, und legen anschließend die `priority` Attribut zu, um die relative Position der Gruppe in der übergeordneten Menü herzustellen. Weitere Informationen finden Sie unter [Erstellen von Wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Wenn Sie der IDE neue Befehle hinzufügen, fügen Sie eine `Buttons` Element, das `Commands` Element. Fügen Sie dann für jeden Befehl, eine [Schaltfläche](../../extensibility/button-element.md) Element, das `Buttons` Element.  
  
   1. Legen Sie die `guid` und `id` Attribute der einzelnen `Button` -Element, und legen anschließend die `type` -Attribut auf die Art der gewünschte Schaltfläche. Sie können auch festlegen, die `priority` Attribut zu, um die relative Position des Befehls in der übergeordneten Gruppe herzustellen.  
  
      > [!NOTE]
      > Verwendung `type="button"` für standardmäßigen Menübefehle und Schaltflächen in Symbolleisten.  
  
   2. In der `Button` -Element, Hinzufügen einer [Zeichenfolgen](../../extensibility/strings-element.md) -Element, enthält eine [ButtonText](../../extensibility/buttontext-element.md) Element und ein [CommandName](../../extensibility/commandname-element.md) Element. Die `ButtonText` -Element stellt die textbezeichnung für ein Menüelement oder die QuickInfo für eine Symbolleisten-Schaltfläche bereit. Die `CommandName` Element enthält den Namen des Befehls, der auch im Befehl verwenden.  
  
   3. Wenn der Befehl ein Symbol verfügt, erstellen eine [Symbol](../../extensibility/icon-element.md) Element in der `Button` -Element, und legen dessen `guid` und `id` Attribute der `Bitmap` -Element für das Symbol.  
  
      > [!NOTE]
      > Symbolleisten-Schaltflächen müssen Symbole.  
  
      Weitere Informationen finden Sie unter [MenuCommands im Vergleich. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4. Wenn Ihre Befehle Symbole benötigen, fügen Sie eine [Bitmaps](../../extensibility/bitmaps-element.md) Element, das `Commands` Element. Fügen Sie dann für jedes Symbol, ein [Bitmap](../../extensibility/bitmap-element.md) Element, das `Bitmaps` Element. Dies ist in dem Sie den Speicherort der Bitmapressource angeben. Weitere Informationen finden Sie unter [Hinzufügen von Symbolen zu Menübefehlen](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Sie können die Struktur übergeordneter, um ordnungsgemäß zu platzieren. die meisten Menüs, Gruppen und Befehle verwenden. Für sehr große Befehlssätze oder wenn ein Menü, Gruppe oder den Befehl an mehreren Stellen angezeigt werden muss, empfehlen wir, dass Sie die Platzierung des Befehls angeben.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Übergeordneter Platzieren von UI-Elemente in der IDE verwenden  
  
1. Für typische übergeordneter, erstellen eine `Parent` -Element in jedem `Menu`, `Group`, und `Command` -Element, das in Ihrem Paket definiert ist.  
  
    Das Ziel der `Parent` Element ist, der im Menü oder Gruppe, die Sie im Menü enthält, oder einer Gruppe-Befehl.  
  
   1. Legen Sie die `guid` auf den Namen des Attributs der `GuidSymbol` Element, das den Befehlssatz definiert. Ist der Target-Element nicht Teil des Pakets, verwenden Sie die Guid für diese Befehl festgelegt ist, wie in der entsprechenden VSCT-Datei definiert.  
  
   2. Legen Sie die `id` Attribut entsprechend den `id` Attribut, das Menü "Ziel" oder einer Gruppe. Eine Liste der Menüs und Gruppen, die von Visual Studio verfügbar gemacht werden, finden Sie unter [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Wenn Sie eine große Anzahl von Elementen der Benutzeroberfläche in der IDE platziert haben oder wenn Sie über Elemente verfügen, die an mehreren Stellen angezeigt werden soll, definieren Sie ihre Platzierungen, in der [CommandPlacements](../../extensibility/commandplacements-element.md) Element, wie in den folgenden Schritten dargestellt.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Um die Platzierung von Befehl verwenden, um UI-Elemente in der IDE  
  
1. Nach der `Commands` -Element, Hinzufügen einer `CommandPlacements` Element.  
  
2. In der `CommandPlacements` -Element, Hinzufügen einer `CommandPlacement` -Element für jedes Menü, Gruppe oder den Befehl platzieren.  
  
    Jede `CommandPlacement` Element oder `Parent` Element ein Menü, Gruppe oder den Befehl in einem IDE-Speicherort platziert. Ein Element der Benutzeroberfläche kann nur ein übergeordnetes Element aufweisen, aber er kann mehrere befehlsplatzierungen aufweisen. Um ein Element der Benutzeroberfläche an mehreren Orten zu platzieren, Hinzufügen einer `CommandPlacement` -Element für jeden Standort.  
  
3. Legen Sie die `guid` und `id` Attribute der einzelnen `CommandPlacement` Element auf das hosting Menü oder die Gruppe, wie Sie für würden eine `Parent` Element. Sie können auch Festlegen der `priority` Attribut zu, um die relative Position des Benutzeroberflächenelements herzustellen.  
  
   Sie können die Platzierung von Überordnung und Platzierung der Befehl kombinieren. Für sehr große Befehlssätze empfehlen wir jedoch, dass Sie nur die Platzierung Befehl verwenden.  
  
### <a name="adding-specialized-behaviors"></a>Hinzufügen von spezielle Verhaltensweisen  
 Sie können [CommandFlag](../../extensibility/command-flag-element.md) Elemente, die das Verhalten von Menüs und Befehlen, z. B. zu ändern, um ihre Darstellung und die Sichtbarkeit zu ändern. Sie können auch beeinflussen, wenn ein Befehl angezeigt, mithilfe von wird [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), oder fügen Sie mithilfe von Tastenkombinationen in Visual Studio [KeyBindings](../../extensibility/keybindings-element.md). Bestimmte Arten von Menüs und Befehlen bereits haben integrierte Verhaltensweisen spezialisiert.  
  
##### <a name="to-add-specialized-behaviors"></a>Spezielle Verhaltensweisen hinzufügen  
  
1. Um ein Element der Benutzeroberfläche sichtbar machen nur in bestimmten Benutzeroberflächen-Kontexten zu, z. B. wenn eine Projektmappe geladen ist, verwenden Sie Sichtbarkeit-Einschränkungen.  
  
   1. Nach der `Commands` -Element, Hinzufügen einer `VisibilityConstraints` Element.  
  
   2. Für jedes UI-Element, eingeschränkt werden soll, Hinzufügen einer [VisibilityItem](../../extensibility/visibilityitem-element.md) Element.  
  
   3. Für jede `VisibilityItem` -Element legen Sie die `guid` und `id` Attribute auf das Menü, Gruppe oder Befehl und legen Sie dann die `context` Attribut an den Benutzeroberflächenkontext werden sollen, gemäß der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse. Weitere Informationen finden Sie unter [VisibilityItem-Element](../../extensibility/visibilityitem-element.md).  
  
2. Um die Sichtbarkeit oder die Verfügbarkeit eines UI-Elements im Code festzulegen, verwenden Sie eine oder mehrere der folgenden Befehlsflags aus:  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     Weitere Informationen finden Sie unter [Commandflag-Element](../../extensibility/command-flag-element.md).  
  
3. Verwenden Sie zum Ändern ein Elements angezeigt wird, oder seine Darstellung dynamisch ändern, eine oder mehrere der folgenden Befehlsflags aus:  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - PICT  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - TextChanges  
  
   - TextOnly  
  
     Weitere Informationen finden Sie unter [Commandflag-Element](../../extensibility/command-flag-element.md).  
  
4. Verwenden Sie zum Ändern ein Elements wie reagiert, wenn Befehle empfangen werden, eine oder mehrere der folgenden Befehlsflags aus:  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - FilterKeys  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - PostExec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     Weitere Informationen finden Sie unter [Commandflag-Element](../../extensibility/command-flag-element.md).  
  
5. Um ein Menü oder ein Element in einem Menü eine abhängige Menü-Tastenkombination anzufügen, fügen Sie ein kaufmännisches und-Zeichen ("&") in der `ButtonText` -Element für das Menü oder das Menüelement. Das Zeichen, das kaufmännische und-Zeichen folgt, ist die aktive Tastenkombination auf, wenn im übergeordneten Menü geöffnet ist.  
  
6. Verwenden Sie zum Anfügen einer unabhängigen Menü-Tastenkombination an einen Befehl [KeyBindings](../../extensibility/keybindings-element.md). Weitere Informationen finden Sie unter [KeyBinding-Element](../../extensibility/keybinding-element.md).  
  
7. Um Menütext zu lokalisieren, verwenden die `LocCanonicalName` Element. Weitere Informationen finden Sie unter [Strings-Element](../../extensibility/strings-element.md).  
  
   Einige Typen von Menüs und Schaltflächen enthalten spezielle Verhaltensweisen. In der folgende Tabelle werden einige spezielle Menü und die Schaltflächentypen beschrieben. Für andere Typen finden Sie unter der `types` Attribut Beschreibungen in [Menu Element](../../extensibility/menu-element.md), [Schaltflächenelement](../../extensibility/button-element.md), und [Combo-Element](../../extensibility/combo-element.md).  
  
   Kombinationsfeld  
   Ein Kombinationsfeld ist ein Dropdown-Liste, die auf einer Symbolleiste verwendet werden kann. Erstellen Sie zum Hinzufügen von Kombinationsfeldern an der Benutzeroberfläche eine [Combos](../../extensibility/combos-element.md) Element in der `Commands` Element. Klicken Sie dann zum Hinzufügen der `Combos` Element eine `Combo` -Element für jede im Kombinationsfeld hinzufügen. `Combo` Elemente besitzen den gleichen Attributen und untergeordneten Elemente als `Button` Elemente und zudem `DefaultWidth` und `idCommandList` Attribute. Die `DefaultWidth` -Attribut legt die Breite in Pixel und die `idCommandList` -Attribut verweist auf eine Befehls-ID, die zum Auffüllen des Kombinationsfelds verwendet wird. Weitere Informationen finden Sie unter den `Combo` Element-Dokumentation.  
  
   MenuController  
   Ein Menücontroller ist einer Schaltfläche mit einem Pfeil angezeigt. Auf den Pfeil klicken, wird eine Liste geöffnet. Um die Benutzeroberfläche ein Menücontroller hinzugefügt haben, erstellen Sie eine `Menu` Element, und legen dessen `type` Attribut **MenuController** oder **MenuControllerLatched**, je nachdem, auf das gewünschte Verhalten. Um ein Menücontroller aufzufüllen, legen Sie es als das übergeordnete Element einer `Group` Element. Der Menücontroller im werden alle untergeordneten Elemente dieser Gruppe auf die Dropdown-Liste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
