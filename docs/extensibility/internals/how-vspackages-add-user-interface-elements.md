---
title: "Wie VSPackages Benutzeroberfl&#228;chenelemente hinzuf&#252;gen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Benutzeroberflächen, Hinzufügen von Elementen"
  - "Element Entwurf der Benutzeroberfläche [Visual Studio SDK] VSPackages"
  - "VSPackages, Benutzeroberflächenelemente beitragen."
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# Wie VSPackages Benutzeroberfl&#228;chenelemente hinzuf&#252;gen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage hinzufügen \(UI\) Benutzeroberflächenelemente, z. B. Menüs, Symbolleisten und Toolfenster, Visual Studio mithilfe der VSCT\-Datei.  
  
 Finden Sie Richtlinien zum Entwerfen von UI\-Elementen zur [Visual Studio\-Richtlinien für die Gestaltung der Benutzeroberfläche](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Die Tabelle\-Architektur von Visual Studio\-Befehl  
 Wie bereits erwähnt, unterstützt den Befehl Tabellenarchitektur der vorstehenden architektonischen Prinzipien. Die Grundsätze hinter der Abstraktionen, Datenstrukturen und Tools der Befehl Tabellenarchitektur sind wie folgt:  
  
-   Es gibt drei grundlegende Arten von Elementen: Menüs, Befehle und Gruppen. Menüs können als Menüs, Untermenüs, Symbolleisten und Toolfenster in der Benutzeroberfläche verfügbar gemacht werden. Befehle sind Prozeduren, die der Benutzer in der IDE ausgeführt werden kann, und sie können als Elemente des Menüs, Schaltflächen, Listenfelder oder andere Steuerelemente verfügbar gemacht werden. Gruppen sind Container für Menüs und Befehlen.  
  
-   Jedes Element wird durch eine Definition angegeben, die beschreibt, das Element, dessen Priorität relativ zu anderen Elementen und die Flags, die ihr Verhalten zu ändern.  
  
-   Jedes Element verfügt über eine Position, die das übergeordnete Element des Elements beschreibt. Ein Element kann mehrere übergeordnete verfügen, so dass er an mehreren Speicherorten in der Benutzeroberfläche angezeigt werden kann.  
  
     Jeder Befehl muss eine Gruppe als übergeordnetes aufweisen, selbst wenn es das einzige untergeordnete Element in dieser Gruppe ist. Jede Standardmenü muss auch eine übergeordnete Gruppe verfügen. Symbolleisten und Toolfenster dienen als eigene Eltern. Eine Gruppe kann als das übergeordnete Element der Visual Studio\-Hauptmenüleiste oder alle Menüs, Symbolleiste oder Toolfenster aufweisen.  
  
### Wie werden Elemente definiert.  
 . VSCT\-Dateien werden in XML formatiert. VSCT\-Datei definiert die Elemente der Benutzeroberfläche für ein Paket und bestimmt, wo die Elemente in der IDE angezeigt werden. Jedes Menü, einer Gruppe oder Befehl in das Paket wird zuerst zugewiesen, eine GUID und ID in der `Symbols` Abschnitt. Im weiteren Verlauf der VSCT wird Datei, jedes Menü, Befehl und Gruppe durch die Kombination seiner GUID und ID identifiziert. Das folgende Beispiel zeigt eine typische `Symbols` Abschnitt der Visual Studio\-Paketvorlage generiert bei einer **Menübefehl** in der Vorlage ausgewählt ist.  
  
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
  
 Element der obersten Ebene der `Symbols` Abschnitt ist die [GuidSymbol\-Element](../../extensibility/guidsymbol-element.md).`GuidSymbol` \-Elemente ordnen Namen GUIDs, die von der IDE verwendet werden, um Pakete und deren Komponenten zu identifizieren.  
  
> [!NOTE]
>  GUIDs werden von der Visual Studio\-Paketvorlage automatisch generiert. Sie können auch eine eindeutige GUID erstellen, indem Sie auf **GUID erstellen** auf der **Tools** Menü.  
  
 Die erste `GuidSymbol` \-Element, "Guid \[PackageName\] Pkg", ist die GUID des Pakets selbst. Dies ist die GUID, die von Visual Studio verwendet wird, um das Paket zu laden. Er hat in der Regel nicht untergeordnete Elemente.  
  
 Gemäß der Konvention, Menüs und Befehlen unter einer Sekunde gruppiert werden `GuidSymbol` \-Element, "Guid \[PackageName\] CmdSet", und Bitmaps werden unter einem dritten `GuidSymbol` Element, "GuidImages". Sie müssen nicht dieser Konvention folgen, aber jedes Menü, Gruppe, Befehl und Bitmap muss ein untergeordnetes Element des ein `GuidSymbol` Element.  
  
 In der zweiten `GuidSymbol` Element, das den Befehlssatz Paket darstellt, sind mehrere `IDSymbol` Elemente. Jede [IDSymbol\-Element](../../extensibility/idsymbol-element.md) weist einen numerischen Wert und ein Menü, eine Gruppe oder ein Befehl, der Teil der Befehl ist darstellen kann. Die `IDSymbol` Elemente im dritten `GuidSymbol` Element darstellen Bitmaps, die als Symbole für Befehle verwendet werden kann. Da GUID\-ID\-Paare in einer Anwendung, die keine zwei untergeordnete Elemente des gleichen eindeutig sein müssen `GuidSymbol` Element möglicherweise denselben Wert haben.  
  
### Menüs, Gruppen und Befehle  
 Wenn ein Menü, eine Gruppe oder ein Befehl eine GUID und ID verfügt, kann er in die IDE hinzugefügt. Jedes Benutzeroberflächenelement muss über Folgendes verfügen:  
  
-   Ein `guid` Attribut, das den Namen des entspricht der `GuidSymbol` \-Element, das das Element der Benutzeroberfläche unter definiert ist.  
  
-   Ein `id` Attribut mit dem Namen des zugeordneten `IDSymbol` Element.  
  
     Zusammen, die `guid` und `id` Attribute bilden die *Signatur* des UI\-Elements.  
  
-   Ein `priority` \-Attribut, das die Platzierung des UI\-Elements im übergeordneten Menü oder Gruppe bestimmt.  
  
-   Ein [Parent\-Element](../../extensibility/parent-element.md) bei dem `guid` und `id` Attribute, die die Signatur des übergeordneten Menüs oder der Gruppe angeben.  
  
#### Menüs  
 Jedes Menü ist definiert als eine [Menu\-Element](../../extensibility/menu-element.md) in der `Menus` Abschnitt. Menüs müssen `guid`, `id`, und `priority` Attribute, und ein `Parent` \-Element, und auch die folgenden zusätzlichen Attribute und untergeordnete Elemente:  
  
-   Ein `type` \-Attribut, das angibt, ob das Menü in der IDE als eine Art von Menü oder eine Symbolleiste angezeigt werden soll.  
  
-   Ein [Zeichenfolgen\-Element](../../extensibility/strings-element.md) enthält eine [ButtonText\-Element](../../extensibility/buttontext-element.md), die gibt den Titel des Menüs in der IDE und ein [CommandName\-Element](../../extensibility/commandname-element.md), die angibt, dass der verwendete Name ist der **Befehl** Fenster auf das Menü zugreifen.  
  
-   Optionale Kennzeichen. Ein [Command\-Flag\-Element](../../extensibility/command-flag-element.md) kann in der Definition einer Menü zum Ändern der Darstellung oder Verhalten in der IDE angezeigt.  
  
 Jede `Menu` Element müssen eine Gruppe wie das übergeordnete Element, wenn es sich um ein andockbares Element wie z. B. eine Symbolleiste ist. Ein andockbares Menü ist eigenen übergeordneten Elements. Weitere Informationen zu Menüs und Werte für die `type` Attribut, finden Sie unter der [Menu\-Element](../../extensibility/menu-element.md) Dokumentation.  
  
 Das folgende Beispiel zeigt ein Menü, das in der Visual Studio\-Menüleiste neben der **Tools** Menü.  
  
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
  
#### Gruppen  
 Eine Gruppe ist ein Element, das in definiert die `Groups` \-Abschnitt der VSCT\-Datei. Gruppen sind lediglich Container. Sie werden nicht in der IDE außer als eine Trennlinie in einem Menü angezeigt. Aus diesem Grund eine [Group\-Element](../../extensibility/group-element.md) wird nur durch die Signatur, die Priorität und den übergeordneten definiert.  
  
 Eine Gruppe kann ein Menü, eine andere Gruppe oder sich selbst als übergeordnetes Element aufweisen. Allerdings ist das übergeordnete Element in der Regel ein Menü oder eine Symbolleiste. Klicken Sie im Menü im vorangehenden Beispiel ist ein untergeordnetes Element von der `IDG_VS_MM_TOOLSADDINS` \-Gruppe, und dieser Gruppe ist ein untergeordnetes Element von der Visual Studio\-Menüleiste. Die Gruppe im folgenden Beispiel ist ein untergeordnetes Element des Menüs aus dem vorherigen Beispiel.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Da sie Teil eines Menüs ist, würde dieser Gruppe in der Regel Befehle enthalten. Es kann jedoch auch andere Menüs enthalten. Dies ist wie Untermenüs definiert werden, wie im folgenden Beispiel gezeigt.  
  
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
  
#### Befehle  
 Ist ein Befehl, der für der IDE bereitgestellt wird entweder als definiert ein [Button\-Element](../../extensibility/button-element.md) oder ein [Kombinationsfeld\-Element](../../extensibility/combo-element.md). In einem Menü oder einer Symbolleiste angezeigt werden sollen, muss der Befehl eine Gruppe als übergeordnetes Element aufweisen.  
  
##### Schaltflächen  
 Schaltflächen werden in definiert das `Buttons` Abschnitt. Eine beliebige Menüoption, Schaltfläche oder andere Elemente, die ein Benutzer klickt, um das Ausführen eines einzelnen Befehls gilt eine Schaltfläche. Einige Schaltflächentypen können auch Funktion einschließen. Schaltflächen sind angefordert und optionalen Attributen, die Menüs zu haben, und kann auch eine [Icon\-Element](../../extensibility/icon-element.md) die angibt, die GUID und ID der Bitmap, die die Schaltfläche in der IDE darstellt. Weitere Informationen über Schaltflächen und ihre Attribute finden Sie unter der [Schaltflächen\-Element](../../extensibility/buttons-element.md) Dokumentation.  
  
 Die Schaltfläche im folgenden Beispiel ist ein untergeordnetes Element der Gruppe aus dem vorherigen Beispiel, und in der IDE als Menüelement im übergeordneten Menü dieser Gruppe angezeigt.  
  
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
  
##### Tastenkürzel  
 Tastenkürzel gemäß der `Combos` Abschnitt. Jede `Combo` \-Element stellt ein Dropdown\-Listenfeld in der IDE dar. Im Listenfeld kann oder nicht beschreibbar durch Benutzer, abhängig vom Wert der `type` Attribut des Kombinationsfeld. Tastenkürzel haben die gleichen Elemente und Verhalten, die Schaltflächen, und kann auch die folgenden zusätzlichen Attribute:  
  
-   Ein `defaultWidth` Attribut, das Breite in Pixel angibt.  
  
-   Ein `idCommandList` \-Attribut, das eine Liste gibt an, die die Elemente enthält, die im Listenfeld angezeigt werden. Die Befehlsliste muss deklariert werden, in der gleichen `GuidSymbol` Knoten, der das Kombinationsfeld enthält.  
  
 Das folgende Beispiel definiert ein Kombinationsfeld\-Element.  
  
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
  
##### Bitmaps  
 Befehle, die zusammen mit einem Symbol angezeigt werden, umfasst ein `Icon` \-Element, das in eine Bitmap verweist, mithilfe dessen GUID und ID Jede Bitmap ist definiert als eine [Bitmapelement](../../extensibility/bitmap-element.md) in der `Bitmaps` Abschnitt. Das einzige erforderliche Attribute für eine `Bitmap` Definition sind `guid` und `href`, der auf die Datei verweist. Wenn die Quelldatei ein Streifen Ressource ist ein **UsedList** Attribut ist auch erforderlich, zum Auflisten der verfügbaren Images in die Bereichsstreifen. Weitere Informationen finden Sie unter der [Bitmapelement](../../extensibility/bitmap-element.md) Dokumentation.  
  
### Überordnen von  
 Die folgenden Regeln bestimmen, wie ein Element auf ein anderes Element als übergeordnetes Element aufrufen kann.  
  
|Element|In diesem Abschnitt des Befehls definiert|Möglicherweise enthalten sein \(als übergeordnetes Element oder Platzierung in der `CommandPlacements` Abschnitt oder beides\)|Möglicherweise enthalten \(bezeichnet als übergeordnetes Element\)|  
|-------------|-----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|  
|Gruppieren|[Groups\-Element](../../extensibility/groups-element.md), die IDE, andere VSPackages|Ein Menü, eine Gruppe, das Element selbst|Menüs, Gruppen und Befehle|  
|Menü|[Menüs\-Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|1 bis *n* Gruppen|0 bis *n* Gruppen|  
|Symbolleiste|[Menüs\-Element](../../extensibility/menus-element.md), die IDE, andere VSPackages|Das Element selbst|0 bis *n* Gruppen|  
|Menübefehl|[Schaltflächen\-Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis *n* gruppiert, das Element selbst|\-0 bis *n* Gruppen|  
|Schaltfläche|[Schaltflächen\-Element](../../extensibility/buttons-element.md), die IDE, andere VSPackages|1 bis *n* gruppiert, das Element selbst||  
|Kombinationsfeld|[Tastenkürzel\-Element](../../extensibility/combos-element.md), die IDE, andere VSPackages|1 bis *n* gruppiert, das Element selbst||  
  
### Menü, einen Befehl, und Gruppe Platzierung  
 Ein Menü, eine Gruppe oder ein Befehl kann in mehr als einer Position in der IDE angezeigt. Für ein Element an mehreren Orten angezeigt werden, er muss hinzugefügt werden die `CommandPlacements` im Abschnitt als ein [CommandPlacement\-Element](../../extensibility/commandplacement-element.md). Alle im Menü, eine Gruppe oder ein Befehl kann als ein Befehl Platzierung hinzugefügt werden. Symbolleisten können nicht jedoch auf diese Weise angeordnet werden, da sie an Standorten, kontextbezogene angezeigt werden können.  
  
 Befehl Standorte haben `guid`, `id`, und `priority` Attribute. Die GUID und ID muss das Element übereinstimmen, die positioniert wird. Die `priority` Attribut bestimmt die Position des Elements im Hinblick auf andere Elemente. Wenn die IDE zwei oder mehr Elemente, die die gleiche Priorität haben zusammenführt, sind ihre Standorte nicht definiert, da die IDE nicht garantiert, dass Paketressourcen in der gleichen Reihenfolge jedes Mal gelesen werden, die das Paket erstellt wird.  
  
 Wenn ein Menü oder eine Gruppe an mehreren Orten angezeigt wird, werden in jeder Instanz alle untergeordneten Elemente dieses Menü oder einer Gruppe angezeigt.  
  
## Befehl Sichtbarkeit und Kontext  
 Wenn mehrere VSPackages installiert sind, kann ein Liebe stets von Menüs, Menüelemente und Symbolleisten die IDE überlasten. Um dieses Problem zu vermeiden, können Sie die Sichtbarkeit der einzelnen Elemente der Benutzeroberfläche steuern, indem Sie mithilfe von *Sichtbarkeit Einschränkungen* und Befehlsflags.  
  
##### Sichtbarkeit Einschränkungen  
 Eine sichtbarkeitseinschränkung wird festgelegt, wie ein [VisibilityItem\-Element](../../extensibility/visibilityitem-element.md) in der `VisibilityConstraints` Abschnitt. Eine sichtbarkeitseinschränkung definiert bestimmte Benutzeroberflächen\-Kontexte, in denen das Zielelement sichtbar ist. Ein Menü oder einen Befehl, der in diesem Abschnitt enthalten ist, ist nur dann, wenn eine der definierten Kontexte aktiv ist sichtbar. Wenn ein Menü oder Befehl nicht in diesem Abschnitt verwiesen wird, ist es immer standardmäßig sichtbar. Dieser Abschnitt gilt nicht für Gruppen.  
  
 `VisibilityItem` Elemente müssen drei Attribute, die wie folgt: die `guid` und `id` des Zielelements Benutzeroberfläche und `context`. Die `context` Attribut gibt an, wenn das Zielelement sichtbar, und nimmt eine beliebige gültige Benutzeroberflächenkontext als Wert. Die UI\-Kontext\-Konstanten für Visual Studio sind Mitglieder der <xref:Microsoft.VisualStudio.VSConstants> Klasse. Jede `VisibilityItem` Element kann nur eine Kontextwert annehmen. Um einen zweiten Kontext anzuwenden, erstellen Sie eine zweite `VisibilityItem` Element, das gleiche Element zeigt, wie im folgenden Beispiel gezeigt.  
  
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
  
##### Befehlsflags  
 Die folgenden Befehlsflags beeinträchtigt die Sichtbarkeit von Menüs und Befehle, denen sie zuweisen.  
  
 AlwaysCreate  
 Menü wird erstellt, auch wenn es keine Gruppen und Schaltflächen aufweist.  
  
 Gültig für: `Menu`  
  
 CommandWellOnly  
 Anwenden dieses Flag Wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt und für zusätzliche Shell\-Anpassung verfügbar zu machen soll z. B. Binden an einen Schlüssel. Nach der Installation des VSPackages kann Benutzer mit diesen Befehlen anpassen, indem Sie öffnen die **Optionen** \(Dialogfeld\), und bearbeiten Sie anschließend den Befehl Platzierung unter der **Tastatur Umgebung** Kategorie. Platzierung auf Kontextmenüs, Symbolleisten, Menüs oder Untermenüs betroffen nicht.  
  
 Gültig für: `Button`, `Combo`  
  
 DefaultDisabled  
 Der Befehl ist standardmäßig deaktiviert, wenn VSPackages, die der Befehl implementiert nicht geladen wurde oder die QueryStatus\-Methode nicht aufgerufen wurde.  
  
 Gültig für: `Button`, `Combo`  
  
 DefaultInvisible  
 Standardmäßig ist der Befehl nicht sichtbar, wenn das VSPackage, die der Befehl implementiert nicht geladen wurde oder die QueryStatus\-Methode nicht aufgerufen wurde.  
  
 Kombiniert werden soll, mit der `DynamicVisibility` Flag.  
  
 Gültig für: `Button`, `Combo`, `Menu`  
  
 DynamicVisibility  
 Die Sichtbarkeit des Befehls kann geändert werden, mit der QueryStatus\-Methode oder eine Kontext\-GUID, der Bestandteil der `VisibilityConstraints` Abschnitt.  
  
 Gilt für Befehle in Menüs, nicht auf Symbolleisten angezeigt werden. Elemente der obersten Ebene können deaktiviert, aber nicht ausgeblendet, wenn das OLECMDF\_INVISIBLE\-Flag aus der QueryStatus\-Methode zurückgegeben wird.  
  
 In einem Menü gibt dieses Flag auch, dass es automatisch ausgeblendet werden soll, wenn ihre Member ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dieses Verhalten bereits über Menüs der obersten Ebene verfügen.  
  
 Kombiniert werden soll, mit der `DefaultInvisible` Flag.  
  
 Gültig für: `Button`, `Combo`, `Menu`  
  
 NoShowOnMenuController  
 Wenn ein Befehl, der dieses Flag hat auf einem Domänencontroller im Menü positioniert ist, wird der Befehl nicht in der Dropdown\-Liste angezeigt.  
  
 Gültig für: `Button`  
  
 Weitere Informationen zu Befehlsflags, finden Sie unter der [Command\-Flag\-Element](../../extensibility/command-flag-element.md) Dokumentation.  
  
##### Allgemeine Anforderungen  
 Der Befehl muss die folgende Reihe von Tests übergeben, bevor er angezeigt und aktiviert werden kann:  
  
-   Der Befehl ist richtig positioniert.  
  
-   Die `DefaultInvisible` Flag nicht festgelegt ist.  
  
-   Das übergeordnete Menü oder die Symbolleiste wird angezeigt.  
  
-   Der Befehl ist aufgrund eines Eintrags Kontext in nicht unsichtbar der [VisibilityConstraints\-Element](../../extensibility/visibilityconstraints-element.md) Abschnitt.  
  
-   VSPackage\-Code zum Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zeigt und ermöglicht es den Befehl. Keine Schnittstellencode abgefangen und entsprechend reagiert.  
  
-   Ein Benutzer den Befehl klickt, wird das Verfahren, die in beschriebenen [Routing\-Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
## Aufruf von vordefinierten Befehle  
 Die [UsedCommands\-Element](../../extensibility/usedcommands-element.md) VSPackages Zugriff auf die Befehle, die durch andere VSPackages oder von der IDE bereitgestellt werden können. Zu diesem Zweck erstellen Sie eine [UsedCommand\-Element](../../extensibility/usedcommand-element.md) bei dem die GUID und ID des Befehls verwenden. Dadurch wird sichergestellt, dass der Befehl von Visual Studio geladen wird, ist er nicht Teil der aktuellen Visual Studio\-Konfiguration. Weitere Informationen finden Sie unter [UsedCommand\-Element](../../extensibility/usedcommand-element.md).  
  
## Darstellung der Schnittstelle\-Element  
 Aspekte für die Auswahl und Positionierung Befehlselemente lauten wie folgt:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet viele Elemente der Benutzeroberfläche, die unterschiedlich je nach Position.  
  
-   Ein Element der Benutzeroberfläche, die mithilfe von definiert ist die `DefaultInvisible` Flag wird in der IDE nicht angezeigt, es sei denn, es ist entweder angezeigt, wenn seine VSPackage\-Implementierung von der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> \-Methode oder in einem bestimmten Benutzeroberflächenkontext zugeordnet der `VisibilityConstraints` Abschnitt.  
  
-   Sogar ein erfolgreich positionierter Befehl kann nicht angezeigt werden. Dies ist die IDE automatisch ausgeblendet oder zeigt einige Befehle, je nach Schnittstellen, die das VSPackage ist \(oder nicht\) implementiert. Angenommen, ein VSPackage\-Implementierung einiger erstellen Schnittstellen Ursachen buildbezogene Menüelemente automatisch angezeigt werden.  
  
-   Anwenden der `CommandWellOnly` Kennzeichen in der Definition der UI\-Element bedeutet, dass der Befehl nur durch Anpassung hinzugefügt werden kann.  
  
-   Befehle können nur in bestimmten Benutzeroberflächen\-Kontexte, z. B. verfügbar sein, nur, wenn ein Dialogfeld angezeigt wird, wenn die IDE in der Entwurfsansicht befindet.  
  
-   Wenn sich bestimmte Elemente der Benutzeroberfläche in der IDE angezeigt werden sollen, müssen Sie eine oder mehrere Schnittstellen implementieren oder Code schreiben.  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)