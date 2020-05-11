---
title: Authoring. Vsct-Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710000"
---
# <a name="author-vsct-files"></a>Author .vsct-Dateien
In diesem Dokument wird gezeigt, wie Sie eine *.vsct-Datei* erstellen, um Menüelemente, Symbolleisten und andere Benutzeroberflächenelemente (UI) zur integrierten Visual Studio-Entwicklungsumgebung (IDE) hinzuzufügen. Verwenden Sie diese Schritte, wenn Sie einem Visual Studio-Paket (VSPackage) UI-Elemente hinzufügen, das noch nicht über eine *.vsct-Datei* verfügt.

 Für neue Projekte wird empfohlen, die Visual Studio-Paketvorlage zu verwenden, da sie eine *.vsct-Datei* generiert, die je nach Auswahl bereits über die erforderlichen Elemente für einen Menübefehl, ein Toolfenster oder einen benutzerdefinierten Editor verfügt. Sie können diese *.vsct-Datei* ändern, um die Anforderungen Ihres VSPackage zu erfüllen. Weitere Informationen zum Ändern einer *.vsct-Datei* finden Sie in den Beispielen unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Erstellen der Datei
 Erstellen Sie eine *.vsct-Datei* in diesen Phasen: Erstellen Sie die Struktur für Dateien und Ressourcen, deklarieren Sie die UI-Elemente, fügen Sie die UI-Elemente in die IDE ein, und fügen Sie alle spezialisierten Verhaltensweisen hinzu.

### <a name="file-structure"></a>Dateistruktur
 Die grundlegende Struktur einer *.vsct-Datei* ist ein [CommandTable-Stammelement,](../../extensibility/commandtable-element.md) das ein [Commands-Element](../../extensibility/commands-element.md) und ein [Symbols-Element](../../extensibility/symbols-element.md) enthält.

#### <a name="to-create-the-file-structure"></a>So erstellen Sie die Dateistruktur

1. Fügen Sie Ihrem Projekt eine *.vsct-Datei* hinzu, indem Sie die Schritte unter Gewusst wie [folgt: Erstellen einer .vsct-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)ausführen.

2. Fügen Sie dem `CommandTable` Element die erforderlichen Namespaces hinzu, wie im folgenden Beispiel gezeigt:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Fügen `CommandTable` Sie im `Commands` Element ein Element hinzu, um alle benutzerdefinierten Menüs, Symbolleisten, Befehlsgruppen und Befehle zu hosten. Damit die benutzerdefinierten UI-Elemente `Commands` geladen werden `Package` können, muss das Attribut des Elements auf den Namen des Pakets festgelegt sein.

     Fügen `Commands` Sie nach `Symbols` dem Element ein Element hinzu, um die GUIDs für das Paket sowie die Namen und Befehls-IDs für ihre UI-Elemente zu definieren.

### <a name="include-visual-studio-resources"></a>Einschließen von Visual Studio-Ressourcen
 Verwenden [Extern](../../extensibility/extern-element.md) Sie das Extern-Element, um auf die Dateien zuzugreifen, die Visual Studio-Befehle definieren, und auf die Menüs, die zum Absetzen der UI-Elemente in die IDE erforderlich sind. Wenn Sie außerhalb des Pakets definierte Befehle verwenden, verwenden Sie das [UsedCommands-Element,](../../extensibility/usedcommands-element.md) um Visual Studio zu informieren.

#### <a name="to-include-visual-studio-resources"></a>So schließen Sie Visual Studio-Ressourcen ein

1. Fügen Sie oben `CommandTable` im Element `Extern` ein Element für jede externe Datei `href` hinzu, auf die verwiesen werden soll, und legen Sie das Attribut auf den Namen der Datei fest. Sie können auf die folgenden Headerdateien verweisen, um auf Visual Studio-Ressourcen zuzugreifen:

   - *Stdidcmd.h*: Definiert IDs für alle Befehle, die von Visual Studio verfügbar gemacht werden.

   - *Vsshlids.h*: Enthält Befehls-IDs für Visual Studio-Menüs.

2. Wenn Ihr Paket Befehle aufruft, die von Visual Studio `UsedCommands` oder `Commands` anderen Paketen definiert werden, fügen Sie ein Element nach dem Element hinzu. Füllen Sie dieses Element mit einem [UsedCommand-Element](../../extensibility/usedcommand-element.md) für jeden Befehl, den Sie aufrufen, der nicht Teil Ihres Pakets ist. Legen `guid` Sie `id` die Undattribute der `UsedCommand` Elemente auf die GUID- und ID-Werte der aufzurufenden Befehle fest.

   Weitere Informationen zum Suchen der GUIDs und IDs von Visual Studio-Befehlen finden Sie unter [GUIDs und IDs von Visual Studio-Befehlen](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Um Befehle von anderen Paketen aufzurufen, verwenden Sie die GUID und die ID des Befehls, wie in der *.vsct-Datei* für diese Pakete definiert.

### <a name="declare-ui-elements"></a>DEklarieren von UI-Elementen
 Deklarieren Sie alle `Symbols` neuen UI-Elemente im Abschnitt der *.vsct-Datei.*

#### <a name="to-declare-ui-elements"></a>So deklarieren Sie UI-Elemente

1. Fügen `Symbols` Sie im Element drei [GuidSymbol-Elemente](../../extensibility/guidsymbol-element.md) hinzu. Jedes `GuidSymbol` Element `name` verfügt über `value` ein Attribut und ein Attribut. Legen `name` Sie das Attribut so fest, dass es den Zweck des Elements widerspiegelt. Das `value` Attribut nimmt eine GUID. (Um eine GUID zu generieren, wählen Sie im Menü **Extras** die Option **GUID erstellen**aus, und wählen Sie dann **Registrierungsformat**aus.)

     Das `GuidSymbol` erste Element stellt Ihr Paket dar und hat in der Regel keine untergeordneten Elemente. Das `GuidSymbol` zweite Element stellt den Befehlssatz dar und enthält alle Symbole, die Ihre Menüs, Gruppen und Befehle definieren. Das `GuidSymbol` dritte Element stellt Ihren Bildspeicher dar und enthält Symbole für alle Symbole für Ihre Befehle. Wenn Sie keine Befehle haben, die Symbole `GuidSymbol` verwenden, können Sie das dritte Element weglassen.

2. Fügen `GuidSymbol` Sie in dem Element, das Ihren Befehlssatz darstellt, ein oder mehrere [IDSymbol-Elemente](../../extensibility/idsymbol-element.md) hinzu. Jeder dieser Befehle stellt ein Menü, eine Symbolleiste, eine Gruppe oder einen Befehl dar, die Sie der Benutzeroberfläche hinzufügen.

     Legen `IDSymbol` Sie für `name` jedes Element das Attribut auf den Namen fest, mit dem Sie `value` auf das entsprechende Menü, die entsprechende Gruppe oder den entsprechenden Befehl verweisen, und legen Sie das Element dann auf eine hexadezimale Zahl fest, die die Befehls-ID darstellt. Keine `IDSymbol` zwei Elemente mit demselben übergeordneten Element können denselben Wert haben.

3. Wenn eines ihrer UI-Elemente Symbole `IDSymbol` erfordert, fügen `GuidSymbol` Sie dem Element, das Ihren Bildspeicher darstellt, ein Element für jedes Symbol hinzu.

### <a name="put-ui-elements-in-the-ide"></a>UI-Elemente in die IDE einteilen
 Die Elemente [Menüs](../../extensibility/menus-element.md), [Gruppen](../../extensibility/groups-element.md)und [Schaltflächen](../../extensibility/buttons-element.md) enthalten die Definitionen für alle Menüs, Gruppen und Befehle, die in Ihrem Paket definiert sind. Legen Sie diese Menüs, Gruppen und Befehle in die IDE, indem Sie entweder ein [übergeordnetes](../../extensibility/parent-element.md) Element verwenden, das Teil der UI-Elementdefinition ist, oder indem Sie ein [CommandPlacement-Element](../../extensibility/commandplacement-element.md) verwenden, das an anderer Stelle definiert ist.

 Jedes `Menu` `Group`, `Button` und Element `guid` verfügt `id` über ein Attribut und ein Attribut. Legen Sie `guid` das Attribut immer `GuidSymbol` so fest, dass es mit `id` dem Namen des `IDSymbol` Elements übereinstimmt, das ihren Befehlssatz darstellt, und legen Sie das Attribut auf den Namen des Elements fest, das `Symbols` Ihr Menü, Ihre Gruppe oder Ihren Befehl im Abschnitt darstellt.

#### <a name="to-define-ui-elements"></a>So definieren Sie UI-Elemente

1. Wenn Sie neue Menüs, Untermenüs, Kontextmenüs oder Symbolleisten definieren, fügen Sie dem `Menus` `Commands` Element ein Element hinzu. Fügen Sie dann für jedes zu erstellende `Menus` Menü ein [Menüelement](../../extensibility/menu-element.md) zum Element hinzu.

    Legen `guid` Sie `id` die Attribute `Menu` und Attribute des `type` Elements fest, und legen Sie dann das Attribut auf die gewünschte Art des Menüs fest. Sie können das `priority` Attribut auch festlegen, um die relative Position des Menüs in der übergeordneten Gruppe festzulegen.

   > [!NOTE]
   > Das `priority` Attribut gilt nicht für Symbolleisten und Kontextmenüs.

2. Alle Befehle in der Visual Studio-IDE müssen von Befehlsgruppen gehostet werden, die die direkten untergeordneten Elemente von Menüs und Symbolleisten sind. Wenn Sie der IDE neue Menüs oder Symbolleisten hinzufügen, müssen diese neue Befehlsgruppen enthalten. Sie können auch Befehlsgruppen zu vorhandenen Menüs und Symbolleisten hinzufügen, damit Sie Ihre Befehle visuell gruppieren können.

    Wenn Sie neue Befehlsgruppen hinzufügen, `Groups` müssen Sie zuerst ein Element erstellen und ihm dann ein [Gruppenelement](../../extensibility/group-element.md) für jede Befehlsgruppe hinzufügen.

    Legen `guid` Sie `id` die Attribute `Group` und Attribute jedes `priority` Elements fest, und legen Sie dann das Attribut fest, um die relative Position der Gruppe im übergeordneten Menü festzulegen. Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Schaltflächengruppen](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Wenn Sie der IDE neue Befehle `Buttons` hinzufügen, `Commands` fügen Sie dem Element ein Element hinzu. Fügen Sie dann `Buttons` für jeden Befehl dem Element ein [Button-Element](../../extensibility/button-element.md) hinzu.

   1. Legen `guid` Sie `id` die Attribute `Button` und Attribute jedes `type` Elements fest, und legen Sie dann das Attribut auf die gewünschte Schaltfläche fest. Sie können das `priority` Attribut auch festlegen, um die relative Position des Befehls in der übergeordneten Gruppe festzulegen.

       > [!NOTE]
       > Wird `type="button"` für Standardmenübefehle und Schaltflächen auf Symbolleisten verwendet.

   2. Fügen `Button` Sie im Element ein [Strings-Element](../../extensibility/strings-element.md) hinzu, das ein [ButtonText-Element](../../extensibility/buttontext-element.md) und ein [CommandName-Element](../../extensibility/commandname-element.md) enthält. Das `ButtonText` Element stellt die Textbeschriftung für ein Menüelement oder die QuickInfo für eine Symbolleistenschaltfläche bereit. Das `CommandName` Element gibt den Namen des Befehls an, der im Befehl gut verwendet werden soll.

   3. Wenn Ihr Befehl über ein Symbol verfügt, `Button` erstellen Sie `guid` ein `id` `Bitmap` [Icon-Element](../../extensibility/icon-element.md) im Element, und legen Sie es und Attribute auf das Element für das Symbol fest.

       > [!NOTE]
       > Symbolleistenschaltflächen müssen Symbole haben.

   Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Wenn einer Ihrer Befehle Symbole erfordert, fügen `Commands` Sie dem Element ein [Bitmaps-Element](../../extensibility/bitmaps-element.md) hinzu. Fügen Sie dann `Bitmaps` für jedes Symbol dem Element ein [Bitmap-Element](../../extensibility/bitmap-element.md) hinzu. Hier geben Sie den Speicherort der Bitmapressource an. Weitere Informationen finden Sie unter [Hinzufügen von Symbolen zu Menübefehlen](../../extensibility/adding-icons-to-menu-commands.md).

   Sie können sich auf die übergeordnete Struktur verlassen, um die meisten Menüs, Gruppen und Befehle korrekt zu platzieren. Für sehr große Befehlssätze oder wenn ein Menü, eine Gruppe oder ein Befehl an mehreren Stellen angezeigt werden muss, wird empfohlen, die Befehlsplatzierung anzugeben.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>So verlassen Sie sich auf das Übergeordneten elements, um UI-Elemente in der IDE zu platzieren

1. Erstellen Sie für die `Parent` typische `Menu`Übergeordnete `Group`ein `Command` Element in jedem , und in jedem Element, das in Ihrem Paket definiert ist.

    Das Ziel `Parent` des Elements ist das Menü oder die Gruppe, das das Menü, die Gruppe oder den Befehl enthält.

   1. Legen `guid` Sie das Attribut `GuidSymbol` auf den Namen des Elements fest, das den Befehlssatz definiert. Wenn das Zielelement nicht Teil Ihres Pakets ist, verwenden Sie die GUId für diesen Befehlssatz, wie in der entsprechenden *.vsct-Datei* definiert.

   2. Legen `id` Sie fest, `id` dass das Attribut mit dem Attribut des Zielmenüs oder der Zielgruppe übereinstimmt. Eine Liste der Menüs und Gruppen, die von Visual Studio verfügbar gemacht werden, finden Sie unter [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Wenn Sie eine große Anzahl von UI-Elementen in der IDE platzieren müssen oder wenn Sie Elemente haben, die an mehreren Stellen angezeigt werden sollen, definieren Sie deren Platzierungen im [CommandPlacements-Element,](../../extensibility/commandplacements-element.md) wie in den folgenden Schritten gezeigt.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>So verwenden Sie die Befehlsplatzierung, um UI-Elemente in der IDE zu platzieren

1. Fügen Sie nach dem `Commands`-Element ein `CommandPlacements`-Element hinzu.

2. Fügen `CommandPlacements` Sie im `CommandPlacement` Element ein Element für jedes zu platzierende Menü, jede Gruppe oder jeden Befehl hinzu.

    Jedes `CommandPlacement` Element `Parent` oder Element platziert ein Menü, eine Gruppe oder einen Befehl an einem IDE-Speicherort. Ein UI-Element kann nur über ein übergeordnetes Element verfügen, es kann jedoch mehrere Befehlsplatzierungen haben. Um ein UI-Element an mehreren `CommandPlacement` Speicherorten zu platzieren, fügen Sie für jeden Speicherort ein Element hinzu.

3. Legen `guid` Sie `id` die Attribute `CommandPlacement` und Attribute jedes Elements auf das Hostingmenü oder die Host-Gruppe fest, genau wie für ein `Parent` Element. Sie können das `priority` Attribut auch festlegen, um die relative Position des UI-Elements festzulegen.

   Sie können die Platzierung durch Übergeordnete und Befehlsplatzierung mischen. Bei sehr großen Befehlssätzen wird jedoch empfohlen, nur die Befehlsplatzierung zu verwenden.

### <a name="add-specialized-behaviors"></a>Hinzufügen von spezialisierten Verhaltensweisen
 Sie können das [CommandFlag-Element](../../extensibility/command-flag-element.md) verwenden, um das Verhalten von Menüs und Befehlen zu ändern, z. B. um deren Aussehen und Sichtbarkeit zu ändern. Sie können sich auch darauf auswirken, wann ein Befehl mithilfe des [VisibilityConstraints-Elements](../../extensibility/visibilityconstraints-element.md) sichtbar ist, oder Tastenkombinationen mithilfe des [KeyBindings-Elements](../../extensibility/keybindings-element.md) hinzufügen. Bestimmte Arten von Menüs und Befehlen haben bereits spezielle Verhaltensweisen integriert.

#### <a name="to-add-specialized-behaviors"></a>So fügen Sie spezielle Verhaltensweisen hinzu

1. Um ein UI-Element nur in bestimmten UI-Kontexten sichtbar zu machen, z. B. wenn eine Lösung geladen wird, verwenden Sie Sichtbarkeitseinschränkungen.

   1. Fügen Sie nach dem `Commands`-Element ein `VisibilityConstraints`-Element hinzu.

   2. Fügen Sie für jedes zu beschränkende UI-Element ein [VisibilityItem-Element](../../extensibility/visibilityitem-element.md) hinzu.

   3. Legen `VisibilityItem` Sie für `guid` jedes `id` Element die und-Attribute auf das Menü, `context` die Gruppe oder den Befehl fest, und legen Sie dann das Attribut auf den gewünschten UI-Kontext fest, wie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse definiert.

2. Um die Sichtbarkeit oder Verfügbarkeit eines UI-Elements im Code festzulegen, verwenden Sie eines oder mehrere der folgenden Befehlsflags:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Weitere Informationen finden Sie im [CommandFlag-Element.](../../extensibility/command-flag-element.md)

3. Um die Darstellung eines Elements zu ändern oder seine Darstellung dynamisch zu ändern, verwenden Sie eines oder mehrere der folgenden Befehlsflags:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Weitere Informationen finden Sie im [CommandFlag-Element.](../../extensibility/command-flag-element.md)

4. Um zu ändern, wie ein Element reagiert, wenn es Befehle empfängt, verwenden Sie eines oder mehrere der folgenden Befehlsflags:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Weitere Informationen finden Sie im [CommandFlag-Element.](../../extensibility/command-flag-element.md)

5. Um eine menüabhängige Tastenkombination an ein Menü oder ein Element in einem Menü anzufügen, fügen Sie dem `ButtonText` Element für das Menü oder Menüelement ein freizügiges Zeichen (&) hinzu. Das Zeichen, das dem freizügigen Zeichen folgt, ist die aktive Tastenkombination, wenn das übergeordnete Menü geöffnet ist.

6. Um eine menüunabhängige Tastenkombination an einen Befehl anzufügen, verwenden Sie das [KeyBindings-Element.](../../extensibility/keybindings-element.md) Weitere Informationen finden Sie im [KeyBinding-Element.](../../extensibility/keybinding-element.md)

7. Verwenden Sie das `LocCanonicalName` Element, um Menütext zu lokalisieren. Weitere Informationen finden [Strings](../../extensibility/strings-element.md) Sie im Strings-Element.

   Einige Menü- und Schaltflächentypen enthalten spezielle Verhaltensweisen. In der folgenden Liste werden einige spezielle Menü- und Schaltflächentypen beschrieben. Weitere Typen finden `types` Sie in den Attributbeschreibungen in den Elementen [Menü](../../extensibility/menu-element.md), [Schaltfläche](../../extensibility/button-element.md)und [Kombination.](../../extensibility/combo-element.md)

   - Kombinationsfeld: Ein Kombinationsfeld ist eine Dropdownliste, die auf einer Symbolleiste verwendet werden kann. Um der Benutzeroberfläche [Kombinationsfelder](../../extensibility/combos-element.md) hinzuzufügen, erstellen `Commands` Sie ein Combos-Element im Element. Fügen Sie `Combos` dem `Combo` Element dann ein Element für jedes hinzuzufügende Kombinationsfeld hinzu. `Combo`Elemente haben die gleichen Attribute `Button` und untergeordneten Elemente wie Elemente und haben `DefaultWidth` auch und `idCommandList` Attribute. Das `DefaultWidth` Attribut legt die Breite in `idCommandList` Pixel fest, und das Attribut verweist auf eine Befehls-ID, die zum Auffüllen des Kombinationsfelds verwendet wird.

   - Menü-Controller: Ein Menü-Controller ist eine Schaltfläche, die einen Pfeil neben sich hat. Wenn Sie auf den Pfeil klicken, wird eine Liste geöffnet. Um der Benutzeroberfläche einen Menücontroller `Menu` hinzuzufügen, `type` erstellen `MenuController` Sie `MenuControllerLatched`ein Element, und legen Sie dessen Attribut je nach gewünschtem Verhalten auf oder fest. Um einen Menücontroller aufzufüllen, legen Sie `Group` ihn als übergeordnetes Element ein. Der Menücontroller zeigt alle untergeordneten Elemente dieser Gruppe in seiner Dropdown-Liste an.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
