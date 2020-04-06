---
title: Wie VSPackages Benutzeroberflächenelemente hinzufügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7d37bfe81c77536871248592d4a2e0734d1c62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707762"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Wie VSPackages Benutzeroberflächenelemente hinzufügen
Ein VSPackage kann Visual Studio mithilfe der *.vsct-Datei* Benutzeroberflächenelemente hinzufügen, z. B. Menüs, Symbolleisten und Toolfenster.

 Entwurfsrichtlinien für UI-Elemente finden Sie unter [Visual Studio-Benutzeroberflächenrichtlinien](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Die Visual Studio-Befehlstabellenarchitektur
 Wie bereits erwähnt, unterstützt die Befehlstabellenarchitektur die vorstehenden architekturischen Prinzipien. Die Grundsätze für die Abstraktionen, Datenstrukturen und Werkzeuge der Befehlstabellenarchitektur lauten wie folgt:

- Es gibt drei grundlegende Arten von Elementen: Menüs, Befehle und Gruppen. Menüs können in der Benutzeroberfläche als Menüs, Untermenüs, Symbolleisten oder Toolfenster verfügbar gemacht werden. Befehle sind Prozeduren, die der Benutzer in der IDE ausführen kann, und sie können als Menüelemente, Schaltflächen, Listenfelder oder andere Steuerelemente verfügbar gemacht werden. Gruppen sind Container für Menüs und Befehle.

- Jedes Element wird durch eine Definition angegeben, die das Element, seine Priorität relativ zu anderen Elementen und die Flags, die sein Verhalten ändern, beschreibt.

- Jedes Element verfügt über eine Platzierung, die das übergeordnete Element des Elements beschreibt. Ein Element kann mehrere Eltern haben, sodass es an mehreren Speicherorten in der Benutzeroberfläche angezeigt werden kann.

     Jeder Befehl muss eine Gruppe als übergeordnetes Element haben, auch wenn er das einzige untergeordnete Element in dieser Gruppe ist. Jedes Standardmenü muss auch über eine übergeordnete Gruppe verfügen. Symbolleisten und Werkzeugfenster fungieren als ihre eigenen Eltern. Eine Gruppe kann als übergeordnete seradiensals Element die Visual Studio-Hauptmenüleiste oder ein beliebiges Menü, eine Symbolleiste oder ein beliebiges Toolfenster haben.

### <a name="how-items-are-defined"></a>Wie Elemente definiert werden
 Eine *.vsct-Datei* ist in XML formatiert. Es definiert die UI-Elemente für ein Paket und bestimmt, wo diese Elemente in der IDE angezeigt werden. Jedem Menü, jeder Gruppe oder jedem Befehl im Paket wird `Symbols` im Abschnitt zunächst eine GUID und EINE ID zugewiesen. Im Weiteren Verlauf der *.vsct-Datei* wird jedes Menü, jeder Befehl und jede Gruppe durch die Kombination aus GUID und ID identifiziert. Das folgende Beispiel `Symbols` zeigt einen typischen Abschnitt, der von der Visual Studio-Paketvorlage generiert wird, wenn ein **Menübefehl** in der Vorlage ausgewählt ist.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">

    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

 Das Element der obersten `Symbols` Ebene des Abschnitts ist das [GuidSymbol-Element](../../extensibility/guidsymbol-element.md). `GuidSymbol`Elemente ordnen GUIDs, die von der IDE zum Identifizieren von Paketen und deren Komponenten verwendet werden, Namen zu.

> [!NOTE]
> GUIDs werden automatisch von der Visual Studio-Paketvorlage generiert. Sie können auch eine eindeutige GUID erstellen, indem Sie im Menü **Extras** auf **GUID erstellen** klicken.

 Das `GuidSymbol` erste `guid<PackageName>Pkg`Element, , ist die GUID des Pakets selbst. Dies ist die GUID, die von Visual Studio zum Laden des Pakets verwendet wird. In der Regel enthält es keine untergeordneten Elemente.

 Gemäß der Konvention werden Menüs und `GuidSymbol` Befehle `guid<PackageName>CmdSet`unter einem zweiten Element `GuidSymbol` gruppiert, `guidImages`und Bitmaps befinden sich unter einem dritten Element, . Sie müssen diese Konvention nicht befolgen, aber jedes Menü, jede Gruppe, `GuidSymbol` jeder Befehl und jede Bitmap muss ein untergeordnetes Element eines Elements sein.

 Im zweiten `GuidSymbol` Element, das den Paketbefehlssatz darstellt, befinden sich mehrere `IDSymbol` Elemente. Jedes [IDSymbol-Element](../../extensibility/idsymbol-element.md) ordnet einen Namen einem numerischen Wert zu und kann ein Menü, eine Gruppe oder einen Befehl darstellen, die Teil des Befehlssatzes sind. Die `IDSymbol` Elemente im `GuidSymbol` dritten Element stellen Bitmaps dar, die als Symbole für Befehle verwendet werden können. Da GUID/ID-Paare in einer Anwendung eindeutig sein `GuidSymbol` müssen, dürfen keine zwei untergeordneten Elemente desselben Elements denselben Wert haben.

### <a name="menus-groups-and-commands"></a>Menüs, Gruppen und Befehle
 Wenn ein Menü, eine Gruppe oder ein Befehl über eine GUID und ID verfügt, kann es der IDE hinzugefügt werden. Jedes UI-Element muss über die folgenden Punkte verfügen:

- Ein `guid` Attribut, das mit `GuidSymbol` dem Namen des Elements übereinstimmt, unter dem das UI-Element definiert ist.

- Ein `id` Attribut, das mit `IDSymbol` dem Namen des zugeordneten Elements übereinstimmt.

     Zusammen bilden `guid` `id` die und-Attribute die *Signatur* des UI-Elements.

- Ein `priority` Attribut, das die Platzierung des UI-Elements im übergeordneten Menü oder in der übergeordneten Gruppe bestimmt.

- Ein [übergeordnetes](../../extensibility/parent-element.md) `guid` Element `id` mit Attributen, die die Signatur des übergeordneten Menüs oder der übergeordneten Gruppe angeben.

#### <a name="menus"></a>Menüs
 Jedes Menü wird im `Menus` Abschnitt als [Menüelement](../../extensibility/menu-element.md) definiert. Menüs müssen `guid` `id`, `priority` und Attribute sowie `Parent` ein Element sowie die folgenden zusätzlichen Attribute und untergeordneten Elemente aufweisen:

- Ein `type` Attribut, das angibt, ob das Menü in der IDE als eine Art Menü oder als Symbolleiste angezeigt werden soll.

- Ein [Strings-Element,](../../extensibility/strings-element.md) das ein [ButtonText-Element](../../extensibility/buttontext-element.md)enthält, das den Titel des Menüs in der IDE angibt, und ein [CommandName-Element](../../extensibility/commandname-element.md), das den Namen angibt, der im **Befehlsfenster** für den Zugriff auf das Menü verwendet wird.

- Optionale Flags. Ein [CommandFlag-Element](../../extensibility/command-flag-element.md) kann in einer Menüdefinition angezeigt werden, um seine Darstellung oder sein Verhalten in der IDE zu ändern.

  Jedes `Menu` Element muss eine Gruppe als übergeordnetes Element haben, es sei denn, es handelt sich um ein andockbares Element, z. B. eine Symbolleiste. Ein andockbares Menü ist sein eigenes übergeordnetes Menü. Weitere Informationen zu Menüs und `type` Werten für das Attribut finden Sie in der [Menüelementdokumentation.](../../extensibility/menu-element.md)

  Das folgende Beispiel zeigt ein Menü, das in der Visual Studio-Menüleiste neben dem Menü **Extras** angezeigt wird.

```xml
<Menu guid="guidTopLevelMenuCmdSet"
id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu"
          id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Gruppen
 Eine Gruppe ist ein Element, `Groups` das im Abschnitt der *.vsct-Datei* definiert ist. Gruppen sind nur Container. Sie werden in der IDE nur als Trennlinie in einem Menü angezeigt. Daher wird ein [Group-Element](../../extensibility/group-element.md) nur durch seine Signatur, Priorität und übergeordnete neratondefiniert.

 Eine Gruppe kann ein Menü, eine andere Gruppe oder sich selbst als übergeordnete Gruppe haben. Das übergeordnete Element ist jedoch in der Regel ein Menü oder eine Symbolleiste. Das Menü im vorherigen Beispiel ist `IDG_VS_MM_TOOLSADDINS` ein untergeordnetes Element der Gruppe, und diese Gruppe ist ein untergeordnetes Element der Visual Studio-Menüleiste. Die Gruppe im folgenden Beispiel ist ein untergeordnetes Element des Menüs im vorherigen Beispiel.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Da es Teil eines Menüs ist, enthält diese Gruppe in der Regel Befehle. Es könnte jedoch auch andere Menüs enthalten. Auf diese Weise werden Untermenüs definiert, wie im folgenden Beispiel gezeigt.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"
priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Befehle
 Ein Befehl, der der IDE zur Verfügung gestellt wird, wird entweder als [Button-Element](../../extensibility/button-element.md) oder als [Combo-Element](../../extensibility/combo-element.md)definiert. Um in einem Menü oder einer Symbolleiste angezeigt zu werden, muss der Befehl eine Gruppe als übergeordnete Gruppe haben.

##### <a name="buttons"></a>Schaltflächen
 Schaltflächen sind `Buttons` im Abschnitt definiert. Jedes Menüelement, jede Schaltfläche oder ein anderes Element, auf das ein Benutzer klickt, um einen einzelnen Befehl auszuführen, wird als Schaltfläche betrachtet. Einige Schaltflächentypen können auch Listenfunktionen enthalten. Schaltflächen verfügen über dieselben erforderlichen und optionalen Attribute wie Menüs und können auch über ein [Icon-Element](../../extensibility/icon-element.md) verfügen, das die GUID und ID der Bitmap angibt, die die Schaltfläche in der IDE darstellt. Weitere Informationen zu Schaltflächen und deren Attributen finden Sie in der Dokumentation zum [Buttons-Element.](../../extensibility/buttons-element.md)

 Die Schaltfläche im folgenden Beispiel ist ein untergeordnetes Element der Gruppe im vorherigen Beispiel und wird in der IDE als Menüelement im übergeordneten Menü dieser Gruppe angezeigt.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Combos
 Combos sind im `Combos` Abschnitt definiert. Jedes `Combo` Element stellt ein Dropdown-Listenfeld in der IDE dar. Das Listenfeld kann von Benutzern abhängig vom Wert des `type` Attributs der Kombination beschreibbar sein oder nicht. Combos haben dieselben Elemente und das gleiche Verhalten wie Schaltflächen und können auch die folgenden zusätzlichen Attribute aufweisen:

- Ein `defaultWidth` Attribut, das die Pixelbreite angibt.

- Ein `idCommandList` Attribut, das eine Liste angibt, die die Elemente enthält, die im Listenfeld angezeigt werden. Die Befehlsliste muss in `GuidSymbol` demselben Knoten deklariert werden, der die Kombination enthält.

  Im folgenden Beispiel wird ein Kombinationselement definiert.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Bitmaps
 Befehle, die zusammen mit einem Symbol `Icon` angezeigt werden, müssen ein Element enthalten, das mithilfe seiner GUID und ID auf eine Bitmap verweist. Jede Bitmap wird im `Bitmaps` Abschnitt als [Bitmap-Element](../../extensibility/bitmap-element.md) definiert. Die einzigen erforderlichen Attribute `Bitmap` für `guid` `href`eine Definition sind und , die auf die Quelldatei verweist. Wenn es sich bei der Quelldatei um einen Ressourcenstreifen handelt, ist auch ein **usedList-Attribut** erforderlich, um die verfügbaren Bilder im Strip aufzulisten. Weitere Informationen finden Sie in der [Bitmap-Elementdokumentation.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Erziehung
 Die folgenden Regeln regeln, wie ein Element ein anderes Element als übergeordnetes Element aufrufen kann.

|Element|Definiert in diesem Abschnitt der Befehlstabelle|Kann enthalten sein (als übergeordnetes Element `CommandPlacements` oder durch Platzierung im Abschnitt oder beides)|Kann enthalten (als übergeordnetes Element bezeichnet)|
|-------------| - | - | - |
|Group|[Groups-Element](../../extensibility/groups-element.md), die IDE, andere VSPackages|Ein Menü, eine Gruppe, das Element selbst|Menüs, Gruppen und Befehle|
|Menü|[Menus-Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|1 bis *n* Gruppen|0 bis *n* Gruppen|
|Symbolleiste|[Menus-Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|Der Artikel selbst|0 bis *n* Gruppen|
|Menübefehl|[Buttons-Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst|-0 bis *n* Gruppen|
|Schaltfläche|[Buttons-Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst||
|Kombinationsdiagramm|[Combos-Element](../../extensibility/combos-element.md), die IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst||

### <a name="menu-command-and-group-placement"></a>Menü-, Befehls- und Gruppenplatzierung
 Ein Menü, eine Gruppe oder ein Befehl kann an mehr als einem Speicherort in der IDE angezeigt werden. Damit ein Element an mehreren Speicherorten angezeigt `CommandPlacements` wird, muss es dem Abschnitt als [CommandPlacement-Element](../../extensibility/commandplacement-element.md)hinzugefügt werden. Jedes Menü, jede Gruppe oder jeder Befehl kann als Befehlsplatzierung hinzugefügt werden. Symbolleisten können jedoch nicht auf diese Weise positioniert werden, da sie nicht an mehreren kontextabhängigen Positionen angezeigt werden können.

 Befehlsplatzierungen `guid` `id`haben `priority` , und Attribute. GuiD und ID müssen mit denen des positionierten Elements übereinstimmen. Das `priority` Attribut regelt die Platzierung des Artikels in Bezug auf andere Artikel. Wenn die IDE zwei oder mehr Elemente mit derselben Priorität zusammenführt, sind ihre Platzierungen nicht definiert, da die IDE nicht garantiert, dass Paketressourcen bei jeder Paketbildung in der gleichen Reihenfolge gelesen werden.

 Wenn ein Menü oder eine Gruppe an mehreren Speicherorten angezeigt wird, werden alle untergeordneten Elemente dieses Menüs oder dieser Gruppe in jeder Instanz angezeigt.

## <a name="command-visibility-and-context"></a>Befehlssichtbarkeit und Kontext
 Wenn mehrere VSPackages installiert sind, kann eine Fülle von Menüs, Menüelementen und Symbolleisten die IDE überladen. Um dieses Problem zu vermeiden, können Sie die Sichtbarkeit einzelner UI-Elemente mithilfe von *Sichtbarkeitseinschränkungen und Befehlsflags* steuern.

### <a name="visibility-constraints"></a>Sichtbarkeitseinschränkungen
 Eine Sichtbarkeitseinschränkung wird als [VisibilityItem-Element](../../extensibility/visibilityitem-element.md) im `VisibilityConstraints` Abschnitt festgelegt. Eine Sichtbarkeitseinschränkung definiert bestimmte UI-Kontexte, in denen das Zielelement sichtbar ist. Ein Menü oder ein Befehl, der in diesem Abschnitt enthalten ist, ist nur sichtbar, wenn einer der definierten Kontexte aktiv ist. Wenn in diesem Abschnitt nicht auf ein Menü oder ein Befehl verwiesen wird, ist es standardmäßig immer sichtbar. Dieser Abschnitt gilt nicht für Gruppen.

 `VisibilityItem`Elemente müssen wie folgt über drei `guid` `id` Attribute verfügen: das `context`und des Zielbenutzeroberflächenelements und . Das `context` Attribut gibt an, wann das Zielelement sichtbar ist, und nimmt einen gültigen UI-Kontext als Wert an. Die UI-Kontextkonstanten für Visual <xref:Microsoft.VisualStudio.VSConstants> Studio sind Mitglieder der Klasse. Jedes `VisibilityItem` Element kann nur einen Kontextwert annehmen. Um einen zweiten Kontext anzuwenden, erstellen Sie ein zweites `VisibilityItem` Element, das auf dasselbe Element verweist, wie im folgenden Beispiel gezeigt.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Befehlsflags
 Die folgenden Befehlsflags können sich auf die Sichtbarkeit der Menüs und Befehle auswirken, auf die sie angewendet werden.

 `AlwaysCreate`Menü wird erstellt, auch wenn es keine Gruppen oder Schaltflächen hat.

 Gültig für:`Menu`

 `CommandWellOnly`Wenden Sie dieses Flag an, wenn der Befehl nicht im Menü der obersten Ebene angezeigt wird und Sie es für eine zusätzliche Shellanpassung verfügbar machen möchten, z. B. wenn Sie ihn an einen Schlüssel binden. Nachdem das VSPackage installiert wurde, kann ein Benutzer diese Befehle anpassen, indem er das Dialogfeld **Optionen** öffnet und dann die Befehlsplatzierung unter der Kategorie **Tastaturumgebung** bearbeitet. Wirkt sich nicht auf die Platzierung in Kontextmenüs, Symbolleisten, Menücontrollern oder Untermenüs aus.

 Gültig für: `Button`,`Combo`

 `DefaultDisabled`Standardmäßig ist der Befehl deaktiviert, wenn das VSPackage, das den Befehl implementiert, nicht geladen ist oder die QueryStatus-Methode nicht aufgerufen wurde.

 Gültig für: `Button`,`Combo`

 `DefaultInvisible`Standardmäßig ist der Befehl unsichtbar, wenn das VSPackage, das den Befehl implementiert, nicht geladen ist oder die QueryStatus-Methode nicht aufgerufen wurde.

 Sollte mit der `DynamicVisibility` Flagge kombiniert werden.

 Gültig `Button`für: `Combo`, ,`Menu`

 `DynamicVisibility`Die Sichtbarkeit des Befehls kann `QueryStatus` mithilfe der Methode oder einer Kontext-GUID geändert werden, die `VisibilityConstraints` im Abschnitt enthalten ist.

 Gilt für Befehle, die in Menüs und nicht auf Symbolleisten angezeigt werden. Symbolleistenelemente der obersten Ebene können deaktiviert, aber `OLECMDF_INVISIBLE` nicht ausgeblendet `QueryStatus` werden, wenn das Flag von der Methode zurückgegeben wird.

 In einem Menü zeigt dieses Flag auch an, dass es automatisch ausgeblendet werden sollte, wenn seine Mitglieder ausgeblendet werden. Dieses Flag wird in der Regel Untermenüs zugewiesen, da Menüs der obersten Ebene dieses Verhalten bereits aufweisen.

 Sollte mit der `DefaultInvisible` Flagge kombiniert werden.

 Gültig `Button`für: `Combo`, ,`Menu`

 `NoShowOnMenuController`Wenn ein Befehl mit diesem Flag auf einem Menücontroller positioniert ist, wird der Befehl nicht in der Dropdownliste angezeigt.

 Gültig für:`Button`

 Weitere Informationen zu Befehlsflags finden Sie in der Dokumentation zum [CommandFlag-Element.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Allgemeine Anforderungen
 Der Befehl muss die folgende Testserie bestehen, bevor er angezeigt und aktiviert werden kann:

- Der Befehl ist korrekt positioniert.

- Das `DefaultInvisible` Flag ist nicht gesetzt.

- Das übergeordnete Menü oder die Symbolleiste ist sichtbar.

- Der Befehl ist aufgrund eines Kontexteintrags im [Elementabschnitt VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) nicht unsichtbar.

- VSPackage-Code, der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> die Schnittstelle implementiert, zeigt den Befehl an und aktiviert ihn. Kein Schnittstellencode hat ihn abgefangen und darauf reagiert.

- Wenn ein Benutzer auf Ihren Befehl klickt, unterliegt er der Prozedur, die im [Routingalgorithmus](../../extensibility/internals/command-routing-algorithm.md)beschrieben ist.

## <a name="call-pre-defined-commands"></a>Vordefinierte Befehle aufrufen
 Das [UsedCommands-Element](../../extensibility/usedcommands-element.md) ermöglicht VSPackages den Zugriff auf Befehle, die von anderen VSPackages oder von der IDE bereitgestellt werden. Erstellen Sie dazu ein [UsedCommand-Element](../../extensibility/usedcommand-element.md) mit der GUID und der ID des zu verwendenden Befehls. Dadurch wird sichergestellt, dass der Befehl von Visual Studio geladen wird, auch wenn er nicht Teil der aktuellen Visual Studio-Konfiguration ist. Weitere Informationen finden Sie unter [UsedCommand-Element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Darstellung von Schnittstellenelementen
 Überlegungen zum Auswählen und Positionieren von Befehlselementen sind wie folgt:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet viele UI-Elemente, die je nach Platzierung unterschiedlich angezeigt werden.

- Ein UI-Element, das `DefaultInvisible` mithilfe des Flags definiert wird, wird nicht in der IDE <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> angezeigt, es sei denn, `VisibilityConstraints` es wird entweder durch die VSPackage-Implementierung der Methode angezeigt oder einem bestimmten UI-Kontext im Abschnitt zugeordnet.

- Selbst ein erfolgreich positionierter Befehl wird möglicherweise nicht angezeigt. Dies liegt daran, dass die IDE automatisch einige Befehle ausblendet oder anzeigt, abhängig von Schnittstellen, die das VSPackage implementiert hat (oder nicht). Beispielsweise führt die Implementierung einiger Buildschnittstellen durch ein VSPackage dazu, dass buildbezogene Menüelemente automatisch angezeigt werden.

- Das `CommandWellOnly` Anwenden des Flags in der Definition des UI-Elements bedeutet, dass der Befehl nur durch Anpassung hinzugefügt werden kann.

- Befehle sind nur in bestimmten UI-Kontexten verfügbar, z. B. nur, wenn ein Dialogfeld angezeigt wird, wenn sich die IDE in der Entwurfsansicht befindet.

- Um zu bewirken, dass bestimmte UI-Elemente in der IDE angezeigt werden, müssen Sie eine oder mehrere Schnittstellen implementieren oder Code schreiben.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
