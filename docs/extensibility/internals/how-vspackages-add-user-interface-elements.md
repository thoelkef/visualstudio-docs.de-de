---
title: Wie VSPackages Benutzeroberflächenelemente hinzufügen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b392c962a2ddbed57ca1af934c0ef9d8b5175595
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418396"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Wie VSPackages Benutzeroberflächenelemente hinzufügen
Eine VSPackage hinzufügen Elemente der Benutzeroberfläche (UI), z. B. Menüs, Symbolleisten und Toolfenster in Visual Studio mit der die *VSCT* Datei.

 Finden Sie Richtlinien zum Entwerfen von UI-Elementen an [Richtlinien zur benutzerfreundlichkeit Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Die Tabelle-Architektur von Visual Studio-Befehl
 Wie bereits erwähnt, unterstützt der-Tabelle befehlsarchitektur die vorstehenden architektonischen Prinzipien. Die Grundsätze hinter der Abstraktionen, Datenstrukturen und Tools von der-Tabelle befehlsarchitektur lauten wie folgt aus:

- Es gibt drei grundlegende Arten von Elementen: Menüs, Befehle und Gruppen. Menüs können in der Benutzeroberfläche wie Menüs, Untermenüs, Symbolleisten und Toolfenster verfügbar gemacht werden. Befehle sind Prozeduren, die der Benutzer kann in der IDE ausführen, und sie können als Menüelemente, Schaltflächen, Listenfelder oder andere Steuerelemente verfügbar gemacht werden. Gruppen sind Container für Menüs und Befehle.

- Jedes Element wird durch eine Definition angegeben, die beschreibt, das Element, dessen Priorität relativ zu anderen Elementen und die Flags, die das Verhalten zu ändern.

- Jedes Element verfügt über eine Platzierung, die das übergeordnete Element des Elements beschreibt. Ein Element kann über mehrere übergeordnete Elemente, verfügen, damit er an mehreren Standorten in der Benutzeroberfläche angezeigt werden kann.

     Jeder Befehl muss eine Gruppe als übergeordnetes verfügen, auch wenn es das einzige untergeordnete Element in dieser Gruppe ist. Jede Standardmenü muss auch eine übergeordnete Gruppe verfügen. Fungieren als ihre eigenen Eltern, Symbolleisten und Toolfenster. Eine Gruppe kann als das übergeordnete Element der wichtigsten Visual Studio-Menüleiste oder alle Menüs, Symbolleiste oder Toolfenster aufweisen.

### <a name="how-items-are-defined"></a>Wie die Elemente definiert werden
 Ein *VSCT* Datei ist im XML-Format formatiert. Definiert die Elemente der Benutzeroberfläche für ein Paket und bestimmt, in dem diese Elemente in der IDE angezeigt werden. Jedes Menü, eine Gruppe oder ein Befehl in das Paket wird zuerst zugewiesen, eine GUID und ID in der `Symbols` Abschnitt. Im weiteren Verlauf der *VSCT* -Datei, jedes Menü, Befehl und -Gruppe wird durch die Kombination seiner GUID und ID identifiziert. Das folgende Beispiel zeigt eine typische `Symbols` im Abschnitt über die Visual Studio-Paketvorlage generiert bei einem **Menübefehl** in der Vorlage ausgewählt ist.

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

 Element der obersten Ebene der `Symbols` Abschnitt ist die [GuidSymbol-Element](../../extensibility/guidsymbol-element.md). `GuidSymbol` kartenelemente Namen zu GUIDs, die von der IDE verwendet werden, um Pakete und ihre Bestandteile zu identifizieren.

> [!NOTE]
> GUIDs werden über die Visual Studio-Paketvorlage automatisch generiert. Sie können auch eine eindeutige GUID erstellen, indem Sie auf **GUID erstellen** auf die **Tools** Menü.

 Die erste `GuidSymbol` Element `guid<PackageName>Pkg`, ist die GUID des Pakets selbst. Dies ist die GUID, die von Visual Studio zum Laden des Pakets verwendet wird. Es ist in der Regel keine untergeordneten-Elemente enthalten.

 Gemäß der Konvention, Menüs und Befehle unter einer Sekunde gruppiert werden `GuidSymbol` Element `guid<PackageName>CmdSet`, Bitmaps sind unter einer dritten `GuidSymbol` Element `guidImages`. Sie müssen keine dieser Konvention folgen, aber jedes Menü, Gruppe, Befehl und Bitmap muss ein untergeordnetes Element von einem `GuidSymbol` Element.

 In der zweiten `GuidSymbol` -Element, das den Befehlssatz Paket darstellt, sind mehrere `IDSymbol` Elemente. Jede [IDSymbol-Element](../../extensibility/idsymbol-element.md) ordnet einen Namen in einen numerischen Wert und ein Menü, eine Gruppe oder ein Befehl, der Teil der Befehl ist darstellen kann. Die `IDSymbol` Elemente in der dritten `GuidSymbol` Element darstellen Bitmaps, die als Symbole für Befehle verwendet werden kann. Da GUID-ID-Paaren in einer Anwendung, die keine zwei untergeordnete Elemente des gleichen eindeutig sein müssen `GuidSymbol` Element möglicherweise den gleichen Wert aufweisen.

### <a name="menus-groups-and-commands"></a>Menüs, Gruppen und Befehle
 Wenn ein Menü, Gruppe oder den Befehl wird eine GUID und ID aufweist, können sie der IDE hinzugefügt werden. Jedes Benutzeroberflächenelement muss über Folgendes verfügen:

- Ein `guid` Attribut, das den Namen des entspricht der `GuidSymbol` -Element, das das Element der Benutzeroberfläche unter definiert ist.

- Ein `id` Attribut, das den Namen des zugeordneten entspricht `IDSymbol` Element.

     Zusammen, die `guid` und `id` compose-Attribute der *Signatur* des UI-Elements.

- Ein `priority` -Attribut, das die Platzierung des UI-Elements in der übergeordneten Menüs oder einer Gruppe bestimmt.

- Ein [übergeordnetes Element](../../extensibility/parent-element.md) , bei dem `guid` und `id` Attribute, die die Signatur des übergeordneten Menüs oder der Gruppe angeben.

#### <a name="menus"></a>Menüs
 Jedes Menü wird definiert, wie eine [Menu-Element](../../extensibility/menu-element.md) in die `Menus` Abschnitt. Menüs müssen `guid`, `id`, und `priority` Attribute, und ein `Parent` -Element, und auch die folgenden zusätzlichen Attribute und untergeordnete Elemente:

- Ein `type` Attribut, das angibt, ob Sie im Menü in der IDE als eine Art von Menü oder eine Symbolleiste angezeigt werden soll.

- Ein [Strings-Element](../../extensibility/strings-element.md) , enthält eine [ButtonText-Element](../../extensibility/buttontext-element.md), dem gibt den Titel des Menüs an, in der IDE und ein [CommandName-Element](../../extensibility/commandname-element.md), die angibt, dass der Name, ist verwendet die **Befehl** Fenster aus, um das Menü zuzugreifen.

- Optionale Kennzeichen. Ein [CommandFlag-Element](../../extensibility/command-flag-element.md) kann in einem menüdefinition so ändern Sie seine Darstellung oder Verhalten in der IDE angezeigt werden.

  Jede `Menu` Element muss eine Gruppe als übergeordnetes aufweisen, es sei denn, es sich um ein andockbares Element wie z. B. eine Symbolleiste ist. Ein andockbares Menü ist eigenes übergeordnetes Element. Weitere Informationen zu Menüs und Werte für die `type` Attribut, finden Sie unter den [Menu-Element](../../extensibility/menu-element.md) Dokumentation.

  Das folgende Beispiel zeigt eine im angezeigten Menü auf der Menüleiste von Visual Studio neben der **Tools** Menü.

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
 Eine Gruppe ist ein Element, das in definiert ist die `Groups` Teil der *VSCT* Datei. Gruppen sind lediglich Container. Sie werden nicht in der IDE außer als eine Trennlinie in einem Menü angezeigt. Aus diesem Grund eine [Group-Element](../../extensibility/group-element.md) wird nur durch die Signatur, eine Priorität und ein übergeordnetes Element definiert.

 Eine Gruppe kann ein Menü, eine andere Gruppe oder selbst als übergeordnetes Element aufweisen. Allerdings ist das übergeordnete Element in der Regel ein Menü oder Symbolleiste. Klicken Sie im Menü im vorangehenden Beispiel ist ein untergeordnetes Element des der `IDG_VS_MM_TOOLSADDINS` Gruppe und die Gruppe ist ein untergeordnetes Element von der Visual Studio-Menüleiste. Die Gruppe im folgenden Beispiel wird ein untergeordnetes Element des Menüs im vorherigen Beispiel.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Da sie Teil eines Menüs ist, würde diese Gruppe in der Regel Befehle enthalten. Es kann jedoch auch andere Menüs enthalten. Dies ist wie Untermenüs definiert werden, wie im folgenden Beispiel gezeigt.

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
 Ein Befehl, der für der IDE bereitgestellt wird, wird definiert, entweder als eine [Schaltflächenelement](../../extensibility/button-element.md) oder [Combo-Element](../../extensibility/combo-element.md). Und in einem Menü oder einer Symbolleiste angezeigt wird, muss der Befehl eine Gruppe als übergeordnete Klasse verfügen.

##### <a name="buttons"></a>Schaltflächen
 Schaltflächen sind definiert, der `Buttons` Abschnitt. Ein Menüelement, Schaltfläche oder anderen Element, das ein Benutzer klickt, um das Ausführen eines einzelnen Befehls gilt eine Schaltfläche. Einige Schaltflächentypen können auch Funktionen enthalten. Schaltflächen sind dem gleichen erforderlichen und optionalen Attributen die Menüs zu haben, und kann sogar eine [Icon-Element](../../extensibility/icon-element.md) , der angibt, die GUID und ID der Bitmap, die die Schaltfläche in der IDE darstellt. Weitere Informationen zu Schaltflächen und ihre Attribute finden Sie unter den [Buttons-Element](../../extensibility/buttons-element.md) Dokumentation.

 Die Schaltfläche im folgenden Beispiel ist ein untergeordnetes Element der Gruppe der im vorherigen Beispiel, und Sie erscheinen in der IDE als ein Menüelement im übergeordneten Menü dieser Gruppe.

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
 Combos werden definiert, der `Combos` Abschnitt. Jede `Combo` -Element stellt ein Dropdown-Listenfeld, das in der IDE dar. Im Listenfeld können oder nicht beschreibbaren von Benutzern, abhängig vom Wert der `type` Attribut des Kombinationsfeld. Combos haben die gleichen Elemente und Verhalten, die Schaltflächen, und können auch die folgenden zusätzlichen Attribute:

- Ein `defaultWidth` Attribut, das Breite in Pixel angibt.

- Ein `idCommandList` -Attribut, das eine Liste gibt an, die die Elemente enthält, die Sie im Listenfeld angezeigt werden. Die Befehlsliste muss deklariert werden, in der gleichen `GuidSymbol` Knoten, der das Kombinationsfeld enthält.

  Das folgende Beispiel definiert einen Combo-Element.

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
 Befehle, die zusammen mit einem Symbol angezeigt wird, müssen enthalten eine `Icon` -Element, das in eine Bitmap bezeichnet, mit der GUID und ID Jede Bitmap ist definiert als eine [Bitmapelement](../../extensibility/bitmap-element.md) in die `Bitmaps` Abschnitt. Das einzige erforderliche Attribute für eine `Bitmap` Definition gibt es `guid` und `href`, das zeigt, an der Quelldatei. Wenn die Quelldatei ein Streifen Ressource ist eine **"usedlist"** Attribut ist auch erforderlich, um die verfügbaren Images in den Streifen aufzulisten. Weitere Informationen finden Sie unter den [Bitmapelement](../../extensibility/bitmap-element.md) Dokumentation.

### <a name="parenting"></a>Überordnen von
 Die folgenden Regeln steuern, wie ein Element auf ein anderes Element als übergeordnetes aufrufen kann.

|Element|In diesem Abschnitt der Befehlstabelle definierten|Möglicherweise enthalten sein (als übergeordnetes Element oder durch Platzierung in der `CommandPlacements` Abschnitt oder beides)|Darf (bezeichnet als übergeordnetes Element)|
|-------------| - | - | - |
|Gruppieren|[Groups-Element](../../extensibility/groups-element.md), die IDE, die anderen VSPackages|Ein Menü, eine Gruppe, das Element selbst|Menüs, Gruppen und Befehle|
|Menü|[Menus-Element](../../extensibility/menus-element.md), die IDE, die anderen VSPackages|1 bis *n* Gruppen|0 bis *n* Gruppen|
|Symbolleiste|[Menus-Element](../../extensibility/menus-element.md), die IDE, die anderen VSPackages|Das Element selbst|0 bis *n* Gruppen|
|Menübefehl|[Buttons-Element](../../extensibility/buttons-element.md), die IDE, die anderen VSPackages|1 bis *n* gruppiert werden, das Element selbst|-0, um *n* Gruppen|
|Schaltfläche|[Buttons-Element](../../extensibility/buttons-element.md), die IDE, die anderen VSPackages|1 bis *n* gruppiert werden, das Element selbst||
|Combo|[Combos-Element](../../extensibility/combos-element.md), die IDE, die anderen VSPackages|1 bis *n* gruppiert werden, das Element selbst||

### <a name="menu-command-and-group-placement"></a>Menü-Befehl und Group-Platzierung
 Ein Menü, eine Gruppe oder ein Befehl kann in mehreren Speicherorten in der IDE angezeigt. Für ein Element an mehreren Orten angezeigt werden, es muss hinzugefügt werden die `CommandPlacements` Abschnitt als eine [CommandPlacement-Element](../../extensibility/commandplacement-element.md). Alle Menü, eine Gruppe oder ein Befehl kann als eine Platzierung Befehl hinzugefügt werden. Symbolleisten können nicht jedoch auf diese Weise angeordnet werden, da sie in mehreren kontextbezogene Standorten nicht verwendet werden.

 Haben Sie befehlsplatzierungen `guid`, `id`, und `priority` Attribute. Die GUID und ID müssen des Elements übereinstimmen, die positioniert ist. Die `priority` Attribut bestimmt die Platzierung des Elements im Hinblick auf andere Elemente. Bei die IDE auf zwei oder mehr Elemente, die dieselbe Priorität haben zusammengeführt, sind ihre Platzierungen nicht definiert, da die IDE nicht garantiert, dass Paketressourcen in der gleichen Reihenfolge jedes Mal gelesen werden, die das Paket erstellt wird.

 Wenn ein Menü oder die Gruppe an mehreren Orten angezeigt wird, werden alle untergeordneten Elemente dieses Menü oder einer Gruppe in den einzelnen Instanzen angezeigt.

## <a name="command-visibility-and-context"></a>Befehl Sichtbarkeit und Kontext
 Bei der Installation von mehreren VSPackages möglicherweise eine bereitzuhalten von Menüs, Menüelemente und Symbolleisten die IDE mit überflüssigen Daten gefüllt. Um dieses Problem zu vermeiden, können Sie die Sichtbarkeit der einzelnen Elemente der Benutzeroberfläche steuern, indem Sie mithilfe von *Sichtbarkeit Einschränkungen* und Befehlsflags.

### <a name="visibility-constraints"></a>Einschränkungen der Sichtbarkeit
 Eine sichtbarkeitseinschränkung festgelegt ist, als eine [VisibilityItem-Element](../../extensibility/visibilityitem-element.md) in die `VisibilityConstraints` Abschnitt. Eine sichtbarkeitseinschränkung definiert bestimmte Benutzeroberfläche-Kontexte, die in denen das Target-Element angezeigt wird. Ein Menü oder einen Befehl, der in diesem Abschnitt enthalten ist, ist sichtbar, nur, wenn eine der definierten Kontexte aktiv ist. Wenn ein Menü oder einen Befehl in diesem Abschnitt nicht verwiesen wird, ist es immer standardmäßig sichtbar. Dieser Abschnitt gilt nicht für Gruppen.

 `VisibilityItem` Elemente müssen drei Attribute wie folgt: die `guid` und `id` der Ziel-UI-Elements und `context`. Die `context` Attribut gibt an, wenn das Zielelement werden angezeigt und akzeptiert alle gültige UI-Kontext als Wert. Die Konstanten des UI-Kontext für Visual Studio sind Mitglied der <xref:Microsoft.VisualStudio.VSConstants> Klasse. Jede `VisibilityItem` Element kann nur eine Kontextwert annehmen. Um einen zweiten Kontext anzuwenden, erstellen Sie eine zweite `VisibilityItem` Element, auf das gleiche Element zeigt, wie im folgenden Beispiel gezeigt.

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
 Die folgenden Befehlsflags können die Sichtbarkeit von Menüs und Befehle, die für denen Sie geltende auswirken.

 `AlwaysCreate` Menü "wird erstellt, auch wenn keine Gruppen oder Schaltflächen verfügbar sind.

 Gültig für: `Menu`

 `CommandWellOnly` Dieses Flag, wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt, und Sie es zusätzliche Shell Anpassung zur Verfügung stellen möchten z. B. angewendet werden, es an einen Schlüssel binden. Nach der Installation des VSPackages kann ein Benutzer mit diesen Befehlen anpassen, indem Sie öffnen die **Optionen** Dialogfeld und bearbeiten Sie dann die Platzierung der Befehl unter der **Tastatur Umgebung** Kategorie. Die Platzierung auf Kontextmenüs, Symbolleisten, Menücontroller oder Untermenüs hat keine Auswirkungen auf.

 Gültig für: `Button`, `Combo`

 `DefaultDisabled` Der Befehl ist standardmäßig deaktiviert, wenn das VSPackage, das den Befehl implementiert nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.

 Gültig für: `Button`, `Combo`

 `DefaultInvisible` Standardmäßig ist der Befehl nicht sichtbar, wenn das VSPackage, das den Befehl implementiert nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.

 Kombiniert werden soll, mit der `DynamicVisibility` Flag.

 Gültig für: `Button`, `Combo`, `Menu`

 `DynamicVisibility` Die Sichtbarkeit des Befehls kann geändert werden, indem die `QueryStatus` Methode oder eine Kontext-GUID, der Bestandteil der `VisibilityConstraints` Abschnitt.

 Gilt für Befehle in Menüs, nicht auf der Symbolleiste angezeigt werden. Elemente der obersten Ebene Symbolleiste können deaktiviert, jedoch nicht ausgeblendet, wenn die `OLECMDF_INVISIBLE` Flag wird zurückgegeben, die `QueryStatus` Methode.

 In einem Menü gibt dieses Flag auch, dass es automatisch ausgeblendet werden soll, wenn ihre Member ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dies bereits über Menüs der obersten Ebene verfügen.

 Kombiniert werden soll, mit der `DefaultInvisible` Flag.

 Gültig für: `Button`, `Combo`, `Menu`

 `NoShowOnMenuController` Wenn ein Befehl, der dieses Flag hat auf ein Menücontroller positioniert ist, wird der Befehl nicht in der Dropdown-Liste angezeigt.

 Gültig für: `Button`

 Weitere Informationen zu Befehlsflags, finden Sie unter den [CommandFlag-Element](../../extensibility/command-flag-element.md) Dokumentation.

#### <a name="general-requirements"></a>Allgemeine Anforderungen
 Der Befehl muss die folgende Reihe von Tests übergeben, bevor es angezeigt und aktiviert werden kann:

- Der Befehl ist richtig positioniert.

- Die `DefaultInvisible` Flag nicht festgelegt.

- Das übergeordnete Menü oder einer Symbolleiste wird angezeigt.

- Der Befehl ist kein nicht sichtbar aufgrund eines Eintrags Kontext, in der [VisibilityConstraints-Element](../../extensibility/visibilityconstraints-element.md) Abschnitt.

- VSPackage-Code zum Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle angezeigt und können Sie den Befehl. Keine Schnittstellencode abgefangen und darauf reagiert.

- Klickt ein Benutzer den Befehl, wird Sie gemäß der Prozedur, die in beschriebenen [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Aufruf von vordefinierten Befehlen
 Die [UsedCommands-Element](../../extensibility/usedcommands-element.md) ermöglicht VSPackages, Zugriff auf die Befehle, die von anderen VSPackages oder von der IDE bereitgestellt werden. Zu diesem Zweck erstellen Sie eine [UsedCommand-Element](../../extensibility/usedcommand-element.md) hat die GUID und ID des Befehls verwendet. Dadurch wird sichergestellt, dass der Befehl von Visual Studio geladen werden, auch wenn er nicht Teil der aktuellen Visual Studio-Konfiguration ist. Weitere Informationen finden Sie unter [UsedCommand-Element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Darstellung der Benutzeroberfläche-element
 Überlegungen zur Auswahl, und Positionieren von befehlselementen lauten wie folgt aus:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet viele Elemente der Benutzeroberfläche, die je nach Platzierung unterschiedlich angezeigt werden.

- Ein Benutzeroberflächenelement, das mit definiert ist die `DefaultInvisible` Flag wird nicht in der IDE angezeigt werden, es sei denn, es ist entweder eine VSPackage-Implementierung des angezeigt der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> -Methode, oder für einen bestimmten UI-Kontext, in der `VisibilityConstraints` Abschnitt.

- Sogar ein erfolgreich positionierte-Befehl kann nicht angezeigt werden. Dies ist da die IDE automatisch ausgeblendet oder einige Befehle, abhängig von Schnittstellen, die das VSPackage hat zeigt (oder nicht) implementiert. Z. B. eine VSPackage Implementierung einiger erstellen Schnittstellen bewirkt, dass auf Builds bezogene Menüelemente automatisch angezeigt werden.

- Anwenden der `CommandWellOnly` Flag in der Definition der UI-Element bedeutet, dass der Befehl nur durch Anpassung hinzugefügt werden kann.

- Befehle können nur in bestimmten Benutzeroberflächen-Kontexten zu, z. B. verfügbar sein, nur, wenn ein Dialogfeld angezeigt wird, wenn die IDE in der Entwurfsansicht befindet.

- Um die dazu führen, dass bestimmte Elemente der Benutzeroberfläche, die in der IDE angezeigt werden, müssen Sie eine oder mehrere Schnittstellen implementieren oder Code schreiben.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)