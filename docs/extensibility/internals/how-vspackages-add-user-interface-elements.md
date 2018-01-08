---
title: "Wie VSPackages Elemente der Benutzeroberfläche hinzufügen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 142e2a24f866db7e3ae20217b60b1ea0c201c749
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-vspackages-add-user-interface-elements"></a>Wie VSPackages Elemente der Benutzeroberfläche hinzufügen
Eine VSPackage hinzufügen (UI) Elemente der Benutzeroberfläche, z. B. Menüs, Symbolleisten und Toolfenster in Visual Studio mithilfe der VSCT-Datei.  
  
 Finden Sie Richtlinien zum Entwerfen von UI-Elementen zur [Visual Studio-Umgebung Leitfäden](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Die Tabelle-Architektur von Visual Studio-Befehl  
 Wie bereits erwähnt, unterstützt den Befehl Tabellenarchitektur vorstehenden Architekturprinzipien an. Die Grundsätze hinter der Abstraktionen, Datenstrukturen und Tools, die Architektur der Befehl besteht sind wie folgt aus:  
  
-   Es gibt drei grundlegende Arten von Elementen: Menüs, Befehle und Gruppen. Menüs können als Menüs, Untermenüs, Symbolleisten und Toolfenster in der Benutzeroberfläche verfügbar gemacht werden. Befehle sind Prozeduren, die der Benutzer in der IDE ausgeführt werden kann, und sie können als Menüelemente, Schaltflächen, Listenfelder und andere Steuerelemente verfügbar gemacht werden. Gruppen sind Container für Menüs und Befehle.  
  
-   Jedes Element wird durch eine Definition angegeben, die beschreibt, das Element, dessen Priorität relativ zu anderen Elementen und die Flags, die ihr Verhalten zu ändern.  
  
-   Jedes Element verfügt über eine Platzierung, die das übergeordnete Element des Elements beschreibt. Ein Element kann mehrere übergeordnete verfügen, sodass er an mehreren Speicherorten in der Benutzeroberfläche angezeigt werden kann.  
  
     Jeder Befehl muss eine Gruppe wie das übergeordnete Objekt verfügen, auch wenn es das einzige untergeordnete Element in dieser Gruppe ist. Jede Standardmenü muss auch eine übergeordnete Gruppe verfügen. Symbolleisten und Toolfenster dienen als ihren eigenen übergeordneten Elementen. Eine Gruppe kann als seinem übergeordneten Element der wichtigsten Visual Studio-Menüleiste oder im Menü, Symbolleiste, oder das Toolfenster "umfassen.  
  
### <a name="how-items-are-defined"></a>Wie die Elemente definiert werden  
 . VSCT-Dateien werden in XML formatiert. Eine VSCT-Datei definiert die Elemente der Benutzeroberfläche für ein Paket und bestimmt, wo diese Elemente in der IDE angezeigt. Jedes Menü, eine Gruppe oder ein Befehl in das Paket wird zuerst zugewiesen, eine GUID und die ID in der `Symbols` Abschnitt. Im weiteren Verlauf von der VSCT ist Datei, jedes Menü Befehl und Gruppe durch die Kombination seiner GUID und ID identifiziert. Das folgende Beispiel zeigt eine typische `Symbols` Abschnitt, wie von der Visual Studio-Paketvorlage generiert bei einer **Menübefehl** in der Vorlage ausgewählt ist.  
  
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
  
 Element der obersten Ebene der `Symbols` Abschnitt ist die [GuidSymbol Element](../../extensibility/guidsymbol-element.md). `GuidSymbol`kartenelemente Namen GUIDs, die von der IDE verwendet werden, um Pakete und ihre Bestandteile zu identifizieren.  
  
> [!NOTE]
>  GUIDs werden von der Visual Studio-Paketvorlage automatisch generiert. Sie können auch eine eindeutige GUID erstellen, indem Sie auf **GUID erstellen** auf die **Tools** Menü.  
  
 Die erste `GuidSymbol` Element, "Guid [PackageName] Pkg", ist die GUID des Pakets selbst. Dies ist die GUID, die von Visual Studio zum Laden des Pakets verwendet wird. Es ist in der Regel keine untergeordneten-Elemente enthalten.  
  
 Gemäß der Konvention werden Menüs und Befehlen unter einer Sekunde gruppiert sind `GuidSymbol` Element, "Guid [PackageName] CmdSet", und Bitmaps werden unter einer dritten `GuidSymbol` -Element, "GuidImages". Sie müssen keine dieser Konvention, aber jedes Menü, Gruppe Befehl und Bitmap muss ein untergeordnetes Element von einem `GuidSymbol` Element.  
  
 In der zweiten `GuidSymbol` -Element, das den Paket-Befehlssatz darstellt, sind mehrere `IDSymbol` Elemente. Jede [IDSymbol Element](../../extensibility/idsymbol-element.md) ordnet einen Namen in einen numerischen Wert und ein Menü, eine Gruppe oder ein Befehl, der den Befehlssatz gehört, darstellen kann. Die `IDSymbol` Elemente im dritten `GuidSymbol` Element darstellen Bitmaps, die als Symbole für Befehle verwendet werden kann. Da GUID-ID-Paaren in einer Anwendung, die keine zwei untergeordneten Elemente des gleichen eindeutig sein müssen `GuidSymbol` Element möglicherweise den gleichen Wert aufweisen.  
  
### <a name="menus-groups-and-commands"></a>Menüs, Gruppen und Befehle  
 Wenn ein Menü, eine Gruppe oder ein Befehl einen GUID und eine ID verfügt, können sie der IDE hinzugefügt werden. Jedes Element der Benutzeroberfläche benötigen Folgendes:  
  
-   Ein `guid` Attribut, das den Namen des entspricht der `GuidSymbol` Elements, das Benutzeroberflächenelement unter definiert ist.  
  
-   Ein `id` Attribut, das den Namen der zugeordneten entspricht `IDSymbol` Element.  
  
     Zusammen, die `guid` und `id` Attribute bilden die *Signatur* des UI-Elements.  
  
-   Ein `priority` -Attribut, das die Platzierung des UI-Elements in der übergeordneten Menü oder die Gruppe bestimmt.  
  
-   Ein [übergeordneten Elements](../../extensibility/parent-element.md) mit dem `guid` und `id` Attribute, die die Signatur des übergeordneten Menü oder der Gruppe angeben.  
  
#### <a name="menus"></a>Menüs  
 Jedes Menü wird definiert, wie eine [Menu-Element](../../extensibility/menu-element.md) in die `Menus` Abschnitt. Menüs benötigen `guid`, `id`, und `priority` Attribute, und ein `Parent` -Element, und auch die folgenden zusätzlichen Attribute und untergeordneten Elemente:  
  
-   Ein `type` Attribut, das angibt, ob das Menü in der IDE als eine Art des Menüs oder einer Symbolleiste angezeigt werden soll.  
  
-   Ein [Zeichenfolgen-Element](../../extensibility/strings-element.md) , enthält eine [ButtonText Element](../../extensibility/buttontext-element.md), dem gibt den Titel des Menüs in der IDE an und eine [CommandName Element](../../extensibility/commandname-element.md), das den Namen, der angibt verwendet die **Befehl** Fenster auf das Menü zuzugreifen.  
  
-   Optionale Kennzeichen. Ein [Flags Befehlselement](../../extensibility/command-flag-element.md) kann in einer menüdefinition so ändern Sie seine Darstellung oder Verhalten in der IDE angezeigt werden.  
  
 Jede `Menu` -Element muss eine Gruppe wie das übergeordnete Objekt aufweisen, es sei denn, es sich um ein andockbares Element wie eine Symbolleiste ist. Ein andockbares Menü ist eine eigene übergeordneten. Weitere Informationen zu Menüs und Werte für die `type` -Attribut angegeben wird, finden Sie unter der [Menu-Element](../../extensibility/menu-element.md) Dokumentation.  
  
 Das folgende Beispiel zeigt ein Menü, das in der Visual Studio-Menüleiste als Nächstes angezeigt wird der **Tools** Menü.  
  
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
 Eine Gruppe ist ein Element, das in definiert die `Groups` Abschnitt der VSCT-Datei. Gruppen sind nur Container. Sie werden nicht in der IDE außer als eine Trennlinie in einem Menü angezeigt. Aus diesem Grund eine [Gruppenelement](../../extensibility/group-element.md) wird nur durch die Signatur, Priorität und übergeordneten definiert.  
  
 Eine Gruppe kann ein Menü, eine andere Gruppe oder sich selbst als übergeordnetes Element haben. Allerdings ist das übergeordnete Element in der Regel ein Menü oder die Symbolleiste. Klicken Sie im Menü im vorangehenden Beispiel ist ein untergeordnetes Element von der `IDG_VS_MM_TOOLSADDINS` Gruppe, und dieser Gruppe ist ein untergeordnetes Element von der Visual Studio-Menüleiste. Die Gruppe im folgenden Beispiel ist ein untergeordnetes Element des Menüs im vorangehenden Beispiel.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Da es Teil eines Menüs ist, würde dieser Gruppe in der Regel Befehle enthalten. Sie können jedoch auch anderen Menüs enthalten. Dies ist wie Untermenüs definiert werden, wie im folgenden Beispiel gezeigt.  
  
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
 Ein Befehl, der der IDE bereitgestellt wird, wird entweder als definiert eine [Schaltflächenelement](../../extensibility/button-element.md) oder ein [Kombinationsfeld Element](../../extensibility/combo-element.md). In einem Menü oder einer Symbolleiste angezeigt werden sollen, muss der Befehl eine Gruppe wie das übergeordnete Objekt aufweisen.  
  
##### <a name="buttons"></a>Schaltflächen  
 Schaltflächen werden definiert, der `Buttons` Abschnitt. Alle Menüelement, Schaltfläche oder andere Elemente, die ein Benutzer klickt, um ein einzelner Befehl gilt eine Schaltfläche. Einige Schaltflächentypen können auch Funktion einschließen. Schaltflächen verfügen über dasselbe erforderlichen und optionalen Attributen die Menüs zu haben, und kann außerdem ein [Icon-Element](../../extensibility/icon-element.md) , die angibt, die GUID und die ID der Bitmap, die die Schaltfläche in der IDE darstellt. Weitere Informationen zu Schaltflächen und ihre Attribute finden Sie unter der [Schaltflächen Element](../../extensibility/buttons-element.md) Dokumentation.  
  
 Die Schaltfläche im folgenden Beispiel ist ein untergeordnetes Element der Gruppe im vorangehenden Beispiel und in der IDE als ein Menüelement im übergeordneten Menü dieser Gruppe angezeigt.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Tastenkürzel  
 Tastenkürzel werden definiert, der `Combos` Abschnitt. Jede `Combo` -Element stellt ein Dropdown-Listenfeld in der IDE dar. Im Listenfeld möglicherweise nicht oder nicht komplett beschreibbaren von Benutzern, abhängig vom Wert der `type` Attribut des Kombinationsfeld. Tastenkürzel haben dieselben Elemente und Verhalten, die Schaltflächen, und können zudem die folgenden zusätzlichen Attribute:  
  
-   Ein `defaultWidth` Attribut, das Breite in Pixel angibt.  
  
-   Ein `idCommandList` -Attribut, das eine Liste gibt an, die die Elemente enthält, die Sie im Listenfeld angezeigt werden. Die Befehlsliste muss deklariert werden, in der gleichen `GuidSymbol` Knoten, der das Kombinationsfeld enthält.  
  
 Das folgende Beispiel definiert ein Kombinationsfeld-Element.  
  
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
 Befehle, die zusammen mit einem Symbol angezeigt werden, umfasst ein `Icon` Element, das auf eine Bitmap verweist, mit dessen GUID und -ID. Jede Bitmap ist definiert als eine [Bitmapelement](../../extensibility/bitmap-element.md) in die `Bitmaps` Abschnitt. Die einzige erforderliche Attribute für eine `Bitmap` Definition sind `guid` und `href`, welche Punkte der Quelldatei. Wenn die Quelldatei Farbstreifen Ressource ist eine **UsedList** Attribut ist auch erforderlich, auf den Streifen verfügbaren Images auflisten. Weitere Informationen finden Sie unter der [Bitmapelement](../../extensibility/bitmap-element.md) Dokumentation.  
  
### <a name="parenting"></a>Überordnung  
 Die folgenden Regeln bestimmen, wie ein Element auf ein anderes Element als übergeordnetes Element aufrufen kann.  
  
|Element|In diesem Abschnitt der Befehlstabelle definierten|Möglicherweise enthalten sein (als übergeordnetes Element oder von der Position in der `CommandPlacements` Abschnitt oder beides)|Darf (bezeichnet als übergeordnetes Element)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Gruppieren|[Element für Gruppen](../../extensibility/groups-element.md), die IDE, andere VSPackages|Ein Menü, eine Gruppe, das Element selbst|Menüs, Gruppen und Befehle|  
|Menü|[Menüs Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|1 bis  *n*  Gruppen|0 bis  *n*  Gruppen|  
|Symbolleiste|[Menüs Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|Das Element selbst|0 bis  *n*  Gruppen|  
|Menübefehl|[Schaltflächen Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis  *n*  gruppiert werden, das Element selbst|-0 bis  *n*  Gruppen|  
|Schaltfläche|[Schaltflächen Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis  *n*  gruppiert werden, das Element selbst||  
|Kombinationsfeld|[Tastenkürzel Element](../../extensibility/combos-element.md), die IDE, andere VSPackages|1 bis  *n*  gruppiert werden, das Element selbst||  
  
### <a name="menu-command-and-group-placement"></a>Menü, einen Befehl, und Gruppe-Platzierung  
 Ein Menü, eine Gruppe oder ein Befehl kann in mehr als einer Position in der IDE angezeigt. Für ein Element an mehreren Positionen angezeigt, es muss hinzugefügt werden die `CommandPlacements` Abschnitt als eine [CommandPlacement Element](../../extensibility/commandplacement-element.md). Alle im Menü, eine Gruppe oder ein Befehl kann als ein Befehl Platzierung hinzugefügt werden. Allerdings können nicht Symbolleisten auf diese Weise positioniert werden, da sie in mehreren kontextbezogene Speicherorten auftreten können.  
  
 Haben Sie befehlsplatzierungen `guid`, `id`, und `priority` Attribute. Der GUID und die ID muss das Element übereinstimmen, die positioniert ist. Die `priority` Attribut bestimmt die Platzierung des Elements im Hinblick auf andere Elemente. Wenn die IDE mindestens zwei Elemente, die dieselbe Priorität haben verbindet, sind ihre Standorte nicht definiert, da die IDE nicht garantiert, dass Paketressourcen in derselben Reihenfolge jedes Mal gelesen werden, die das Paket erstellt wird.  
  
 Wenn ein Menü oder eine Gruppe an mehreren Orten angezeigt wird, werden alle untergeordneten Elemente dieses Menü oder dieser Gruppe in jeder Instanz angezeigt.  
  
## <a name="command-visibility-and-context"></a>Befehl Sichtbarkeit und Kontext  
 Wenn mehrere VSPackages installiert sind, kann eine Profusion von Menüs, Menüelemente und Symbolleisten die IDE überflüssigen Daten gefüllt. Um dieses Problem zu vermeiden, können Sie die Sichtbarkeit der einzelnen Elemente der Benutzeroberfläche steuern, indem Sie mithilfe von *Sichtbarkeit Einschränkungen* und Befehlsflags.  
  
##### <a name="visibility-constraints"></a>Sichtbarkeit Einschränkungen  
 Eine Einschränkung für die Sichtbarkeit wird festgelegt, wie eine [VisibilityItem Element](../../extensibility/visibilityitem-element.md) in die `VisibilityConstraints` Abschnitt. Eine Einschränkung Sichtbarkeit definiert bestimmte UI-Kontexten, die in denen des Zielelements sichtbar ist. Ein Menü oder einen Befehl, die in diesem Abschnitt enthalten ist, ist sichtbar, nur, wenn eine der definierten Kontexte aktiv ist. Wenn ein Menü oder einen Befehl nicht in diesem Abschnitt verwiesen wird, ist es immer standardmäßig sichtbar. Dieser Abschnitt gilt nicht für Gruppen.  
  
 `VisibilityItem`Elemente müssen drei Attribute aufweisen, wie folgt: das `guid` und `id` des Ziel-UI-Elements und `context`. Die `context` Attribut gibt an, wann des Zielelements werden angezeigt und akzeptiert gültige Benutzeroberflächenkontext als Wert. Die UI-Kontext-Konstanten für Visual Studio sind Mitglied der <xref:Microsoft.VisualStudio.VSConstants> Klasse. Jede `VisibilityItem` Element kann nur einen Kontextwert annehmen. Um einen zweiten Kontext anzuwenden, erstellen Sie eine zweite `VisibilityItem` Elements, für dasselbe Element verweist, wie im folgenden Beispiel gezeigt.  
  
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
  
##### <a name="command-flags"></a>Befehlsflags  
 Der folgende Befehlsflags können die Sichtbarkeit von Menüs und Befehle für sie geltende beeinflussen.  
  
 AlwaysCreate  
 Menü wird erstellt, selbst wenn er keine Gruppen oder Schaltflächen enthält.  
  
 Gültig für:`Menu`  
  
 CommandWellOnly  
 Dieses Flag, wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt, und es zusätzliche Shell Anpassung, verfügbar machen möchten z. B. angewendet werden, binden es an einen Schlüssel. Nach der Installation des VSPackages kann ein Benutzer diese Befehle anpassen, indem Sie öffnen die **Optionen** (Dialogfeld), und bearbeiten Sie dann die Platzierung der Befehl unter dem **Tastatur Umgebung** Kategorie. Bei der Platzierung in Kontextmenüs, Symbolleisten, Menücontroller oder Untermenüs hat keine Auswirkungen.  
  
 Gültig für: `Button`,`Combo`  
  
 DefaultDisabled  
 Der Befehl ist standardmäßig deaktiviert, wenn das VSPackage, die den Befehl nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.  
  
 Gültig für: `Button`,`Combo`  
  
 DefaultInvisible  
 Standardmäßig ist der Befehl nicht sichtbar, wenn das VSPackage, die den Befehl nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.  
  
 Kombiniert werden soll, mit der `DynamicVisibility` Flag.  
  
 Gültig für: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 Die Sichtbarkeit des Befehls geändert werden kann, über die QueryStatus-Methode oder einem Kontext GUID, die in enthalten ist das `VisibilityConstraints` Abschnitt.  
  
 Gilt für Befehle, die in Menüs, nicht auf Symbolleisten angezeigt werden. Auf der obersten Ebene Symbolleistenelemente können deaktiviert, aber nicht ausgeblendet, wenn das Flag OLECMDF_INVISIBLE von QueryStatus-Methode zurückgegeben wird.  
  
 In einem Menü gibt dieses Flag auch an, dass er automatisch ausgeblendet werden soll, wenn ihre Elemente ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dieses Verhalten bereits über Menüs der obersten Ebene verfügen.  
  
 Kombiniert werden soll, mit der `DefaultInvisible` Flag.  
  
 Gültig für: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 Wenn ein Befehl, der dieses Flag weist auf ein Menücontroller positioniert ist, wird der Befehl nicht in der Dropdown-Liste angezeigt.  
  
 Gültig für:`Button`  
  
 Weitere Informationen zu Befehlsflags, finden Sie unter der [Flags Befehlselement](../../extensibility/command-flag-element.md) Dokumentation.  
  
##### <a name="general-requirements"></a>Allgemeine Anforderungen  
 Der Befehl muss die folgende Reihe von Tests übergeben, bevor es angezeigt und aktiviert werden kann:  
  
-   Der Befehl ist korrekt positioniert.  
  
-   Die `DefaultInvisible` Flag nicht festgelegt ist.  
  
-   Der Symbolleiste oder im übergeordneten ist sichtbar.  
  
-   Der Befehl ist kein unsichtbar aufgrund eines Eintrags Kontext, in dem [VisibilityConstraints Element](../../extensibility/visibilityconstraints-element.md) Abschnitt.  
  
-   VSPackage-Code, implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle wird angezeigt und können Sie den Befehl. Keine Schnittstellencode abgefangen und entsprechend reagiert.  
  
-   Klickt ein Benutzer den Befehl, wird Sie gemäß der Prozedur, die in beschriebenen [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Vordefinierte Befehle aufrufen  
 Die [UsedCommands Element](../../extensibility/usedcommands-element.md) VSPackages Zugriff auf die Befehle, die von anderen VSPackages oder von der IDE bereitgestellt werden können. Zu diesem Zweck erstellen Sie eine [UsedCommand Element](../../extensibility/usedcommand-element.md) Listenfeldsteuerelement mit dem GUID und die ID des Befehls verwendet. Dadurch wird sichergestellt, dass der Befehl von Visual Studio geladen werden, auch wenn er nicht Teil der aktuellen Visual Studio-Konfiguration ist. Weitere Informationen finden Sie unter [UsedCommand Element](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Darstellung der Schnittstelle-Element  
 Überlegungen für die Auswahl, und positionieren die Befehlselemente lauten wie folgt:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet viele Elemente der Benutzeroberfläche, die abhängig von der Platzierung unterschiedlich angezeigt werden.  
  
-   Ein Benutzeroberflächenelement, das mit definiert ist die `DefaultInvisible` Flag wird nicht in der IDE angezeigt werden, es sei denn, es ist entweder angezeigt, durch die VSPackage-Implementierung von der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> -Methode, oder in einem bestimmten UI-Kontext zugeordnet der `VisibilityConstraints` Abschnitt.  
  
-   Auch ein erfolgreich positionierte Befehl möglicherweise nicht angezeigt werden. Dies ist, da die IDE automatisch ausgeblendet oder sind einige Befehle enthalten, je nach Schnittstellen, die das VSPackage (hat oder nicht) implementiert. Z. B. eine VSPackage Implementierung einiger erstellen Schnittstellen Ursachen buildbezogene Menüelemente automatisch angezeigt werden.  
  
-   Anwenden der `CommandWellOnly` Flag in der Definition der UI-Element bedeutet, dass der Befehl nur durch Anpassung hinzugefügt werden kann.  
  
-   Befehle können nur in bestimmten UI-Kontexten z. B. verfügbar sein, nur, wenn ein Dialogfeld angezeigt wird, wenn die IDE in der Entwurfsansicht befindet.  
  
-   Um veranlassen, bestimmte Elemente der Benutzeroberfläche, die in der IDE angezeigt werden, müssen Sie eine oder mehrere Schnittstellen implementieren oder Code schreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)