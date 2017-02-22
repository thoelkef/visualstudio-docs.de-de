---
title: "Erstellen. VSCT-Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien, die manuelle Erstellung"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen. VSCT-Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses Dokument zeigt die zum Erstellen eine VSCT\-Datei zum Hinzufügen von Menübefehlen, Symbolleisten und andere Elemente der Benutzeroberfläche \(UI\) auf die Visual Studio integrated Development Environment \(IDE\). Verwenden Sie folgende Schritte aus, wenn Sie Elemente der Benutzeroberfläche einer Visual Studio\-Paket \(VSPackage\) hinzufügen, die nicht bereits eine VSCT\-Datei.  
  
 Bei neuen Projekten wird empfohlen, dass Sie die Visual Studio\-Paket\-Vorlage verwenden, da es sich um eine VSCT\-Datei generiert, die abhängig von Ihrer Auswahl bereits die erforderlichen Elemente für einen Menübefehl, ein Fenster oder einen benutzerdefinierten Editor verfügt. Sie können diese VSCT\-Datei, um die Bedürfnisse Ihrer VSPackage ändern. Weitere Informationen zum Ändern einer VSCT\-Datei finden Sie in den Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
## Schreiben der Datei  
 Erstellen eine VSCT\-Datei in diesen Phasen: Erstellen Sie die Struktur für Dateien und Ressourcen, deklarieren Sie die Elemente der Benutzeroberfläche, setzen Sie die Elemente der Benutzeroberfläche in der IDE und speziellen Verhaltensweisen hinzuzufügen.  
  
### Dateistruktur  
 Die grundlegende Struktur einer VSCT\-Datei ist eine [CommandTable](../../extensibility/commandtable-element.md) Stammelement, enthält eine [Befehle](../../extensibility/commands-element.md) Element und ein [Symbole](../../extensibility/symbols-element.md) Element.  
  
##### Um die Struktur der Datei zu erstellen.  
  
1.  Anhand der Schritte in einer VSCT\-Datei dem Projekt hinzufügen [Gewusst wie: Erstellen einer. VSCT\-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Fügen Sie die erforderlichen Namespaces, die die `CommandTable` Element, wie im folgenden Beispiel dargestellt.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  In der `CommandTable` \-Element, Hinzufügen einer `Commands` Element, um alle Ihre benutzerdefinierten Menüs, Symbolleisten, Befehlsgruppen und Befehle zu hosten. Damit Ihre Benutzeroberflächenelemente geladen werden können, die `Commands` Element müssen die `Package` \-Attribut auf den Namen des Pakets festgelegt.  
  
     Nach dem `Commands` \-Element, Hinzufügen einer `Symbols` Element zu definieren, die GUIDs für das Paket und die Namen der Befehls\-IDs für die Elemente der Benutzeroberfläche.  
  
### Visual Studio\-Ressourcen einschließlich  
 Verwenden der [Extern](../../extensibility/extern-element.md) Element auf die Dateien zugreifen, die Visual Studio\-Befehle und Menüs, die erforderlich sind, stellen Sie Ihre Benutzeroberflächenelemente in der IDE definieren. Wenn Sie außerhalb des Pakets definiert Befehle verwenden möchten, verwenden Sie die [UsedCommands](../../extensibility/usedcommands-element.md) Element, um Visual Studio zu informieren.  
  
##### Visual Studio\-Ressourcen enthalten.  
  
1.  Am oberen Rand der `CommandTable` \-Element, fügen Sie eine `Extern` Element für jede externe Datei, auf die verwiesen wird und festgelegt werden, das `href` \-Attribut auf den Namen der Datei. Sie können die folgenden Header\-Dateien für den Zugriff auf Visual Studio\-Ressourcen verweisen:  
  
    -   Stdidcmd.h, definiert die IDs für alle Befehle, die von Visual Studio verfügbar gemacht werden.  
  
    -   Vsshlids.h, enthält die Befehls\-IDs für Visual Studio\-Menüs.  
  
2.  Wenn Ihr Paket Befehle, die von Visual Studio oder von anderen Paketen definiert sind aufruft, fügen Sie ein `UsedCommands` Element an, nach der `Commands` Element. Füllen Sie dieses Element mit einem [UsedCommand](../../extensibility/usedcommand-element.md) Element für jeden Befehl, die Sie aufrufen, d. h. nicht Teil des Pakets. Festlegen der `guid` und `id` Attribute der `UsedCommand` Elemente, die die GUID und ID\-Werte der Befehle zum Aufrufen. Weitere Informationen dazu, wie Sie die GUIDs und IDs von Visual Studio\-Befehle finden Sie unter [GUIDs und IDs der Visual Studio\-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Um Befehle aus andere Pakete aufzurufen, verwenden Sie die GUID und die ID des Befehls in der VSCT\-Datei für diese Pakete definiert.  
  
### Deklarieren von Benutzeroberflächenelementen  
 Deklarieren Sie alle Elemente der neuen Benutzeroberfläche in der `Symbols` \-Abschnitt der VSCT\-Datei.  
  
##### Deklarieren von UI\-Elemente  
  
1.  In der `Symbols` \-Element, fügen Sie drei [GuidSymbol](../../extensibility/guidsymbol-element.md) Elemente. Jede `GuidSymbol` Element verfügt über ein `name` Attribut und einem `value` Attribut. Legen Sie die `name` \-Attributs so, dass es sich um den Zweck des Elements widerspiegelt. Das `value` \-Attribut nimmt eine GUID. \(Zum Erstellen einer GUID in die **Tools** Menü klicken Sie auf **GUID erstellen**, und wählen Sie dann **Registrierungsformat**.\)  
  
     Die erste `GuidSymbol` Element darstellt, das Paket und in der Regel hat keine untergeordneten Elemente. Die zweite `GuidSymbol` Element stellt der Befehl festgelegt und enthält alle Symbole, die die Menüs, Gruppen und Befehle zu definieren. Die dritte `GuidSymbol` Element stellt die Image\-Speicher und enthält Symbole für alle Symbole für die Befehle. Wenn Sie keine Befehle, die Symbole verwenden, können Sie die dritte weglassen `GuidSymbol` Element.  
  
2.  In der `GuidSymbol` \-Element, das den Befehlssatz hinzufügen, eine oder mehrere [IDSymbol](../../extensibility/idsymbol-element.md) Elemente. Jede dieser darstellen, ein Menü, Symbolleiste, Gruppe oder Befehl, den Sie der Benutzeroberfläche hinzugefügt werden.  
  
     Für jede `IDSymbol` \-Element das `name` \-Attribut auf den Namen, die Sie zum Verweisen auf die entsprechenden Menüs, eine Gruppe oder ein Befehl, und legen Sie dann die `value` Element in eine hexadezimale Zahl, die die Befehls\-Id darstellt. Keine zwei `IDSymbol` Elemente mit demselben übergeordneten Element den gleichen Wert aufweisen.  
  
3.  Wenn keines der Elemente der Benutzeroberfläche Symbole benötigen, fügen Sie ein `IDSymbol` \-Element für jedes Symbol, um die `GuidSymbol` Element, das die Image\-Speicher darstellt.  
  
### Platzieren Benutzeroberflächenelemente in der IDE  
 Die [Menüs](../../extensibility/menus-element.md) Element [Gruppen](../../extensibility/groups-element.md) \-Element, und [Schaltflächen](../../extensibility/buttons-element.md) Element enthält die Definitionen für alle Menüs, Gruppen und Befehle, die im Paket definiert sind. Setzen diese Menüs, Gruppen und Befehle in der IDE mithilfe einer [übergeordneten](../../extensibility/parent-element.md) \-Element, das Teil der Benutzeroberfläche Elementdefinition oder mithilfe einer [CommandPlacement](../../extensibility/commandplacement-element.md) Element definiert, an anderer Stelle.  
  
 Jede `Menu`, `Group`, und `Button` Element verfügt über ein `guid` Attribut und ein `id` Attribut. Immer festgelegt der `guid` Attribut entsprechend den Namen des der `GuidSymbol` Element, das den Befehl darstellt und die `id` \-Attribut auf den Namen des der `IDSymbol` Element, das die Menü, einer Gruppe oder Befehl in darstellt der `Symbols` Abschnitt.  
  
##### UI\-Elemente definieren.  
  
1.  Wenn Sie alle neuen Menüs, Untermenüs, Kontextmenüs oder Symbolleisten definieren, fügen Sie ein `Menus` Element der `Commands` Element. Für die einzelnen Menüs erstellt werden soll, fügen Sie dann eine [Menü](../../extensibility/menu-element.md) Element der `Menus` Element.  
  
     Festlegen der `guid` und `id` Attribute der `Menu` \-Element, und legen die `type` \-Attribut auf die Art des gewünschten Menüs. Sie können auch festlegen, die `priority` Attribut, um die relative Position des Menüs in der übergeordneten Gruppe herstellen.  
  
    > [!NOTE]
    >  Die `priority` Attribut gilt nicht für Symbolleisten und Kontextmenüs.  
  
2.  Alle Befehle in Visual Studio\-IDE müssen von Befehlsgruppen gehostet werden, die die direkten untergeordneten Elemente des Menüs und Symbolleisten sind. Wenn Sie auf die IDE neue Menüs oder Symbolleisten hinzufügen, müssen diese neue Befehlsgruppen enthalten. Sie können auch Befehlsgruppen zu vorhandenen Menüs und Symbolleisten hinzufügen, damit Sie Ihre Befehle visuell gruppieren können.  
  
     Wenn Sie neue Befehlsgruppen hinzufügen, müssen Sie zuerst erstellen ein `Groups` \-Element, und fügen Sie dann hinzu ein [Gruppe](../../extensibility/group-element.md) \-Element für jede Befehlsgruppe.  
  
     Festlegen der `guid` und `id` Attribute der einzelnen `Group` \-Element, und legen die `priority` Attribut, um die relative Position der Gruppe im übergeordneten Menü herzustellen. Weitere Informationen finden Sie unter [Erstellen von wieder verwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Wenn Sie neue Befehle in der IDE hinzufügen, fügen Sie ein `Buttons` Element der `Commands` Element. Fügen Sie dann für jeden Befehl eine [Schaltfläche](../../extensibility/button-element.md) Element, das `Buttons` Element.  
  
    1.  Legen Sie die `guid` und `id` Attribute der einzelnen `Button` \-Element, und legen die `type` \-Attribut auf die Art der gewünschten Schaltfläche. Sie können auch festlegen, die `priority` Attribut, um die relative Position des Befehls in der übergeordneten Gruppe herstellen.  
  
        > [!NOTE]
        >  Verwendung `type="button"` für standardmäßigen Menübefehle und Schaltflächen in Symbolleisten.  
  
    2.  In der `Button` \-Element, Hinzufügen einer [Zeichenfolgen](../../extensibility/strings-element.md) \-Element, enthält eine [ButtonText](../../extensibility/buttontext-element.md) Element und ein [CommandName](../../extensibility/commandname-element.md) Element. Das `ButtonText` \-Element stellt die Beschriftung für ein Menüelement oder die QuickInfo für eine Symbolleisten\-Schaltfläche. Die `CommandName` Element enthält den Namen des Befehls im Befehl verwenden.  
  
    3.  Wenn der Befehl ein Symbol verfügen, erstellen eine [Symbol](../../extensibility/icon-element.md) Element in der `Button` \-Element, und legen seine `guid` und `id` Attribute auf die `Bitmap` \-Element für das Symbol.  
  
        > [!NOTE]
        >  Schaltflächen der Symbolleiste müssen Symbole.  
  
     Weitere Informationen finden Sie unter [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md).  
  
4.  Wenn Ihre Befehle Symbole benötigen, fügen Sie eine [Bitmaps](../../extensibility/bitmaps-element.md) Element der `Commands` Element. Fügen Sie dann für jedes Symbol eine [Bitmap](../../extensibility/bitmap-element.md) Element, das `Bitmaps` Element. Dies ist, in dem Sie den Speicherort der Bitmapressource angeben. Weitere Informationen finden Sie unter [Hinzufügen von Symbolen zu Menübefehlen](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Sie können auf die überordnen\-Struktur, die meisten Menüs, Gruppen und Befehle korrekt platziert verlassen. Für sehr große Befehlssätze oder wenn ein Menü, eine Gruppe oder ein Befehl an mehreren Stellen angezeigt werden muss, wird empfohlen, Sie Befehl Platzierung anzugeben.  
  
##### Überordnung an Benutzeroberflächenelemente in der IDE verwenden  
  
1.  Für normale Überordnung erstellen eine `Parent` \-Element in jedem `Menu`, `Group`, und `Command` \-Element, das im Paket definiert ist.  
  
     Das Ziel der `Parent` Element ist das Menü oder Gruppe, die das Menü enthält, Gruppe oder Befehl.  
  
    1.  Legen Sie die `guid` auf den Namen des Attributs der `GuidSymbol` Element, das den Befehlssatz definiert. Wenn das Zielelement nicht Teil des Pakets ist, verwenden Sie die Guid für diese Befehl festgelegt ist, wie in der entsprechenden VSCT\-Datei definiert.  
  
    2.  Legen Sie die `id` Attribut entsprechend der `id` Attribut des Menü "Ziel" oder der Gruppe. Eine Liste der Menüs und Gruppen, die von Visual Studio bereitgestellt werden, finden Sie unter [GUIDs und IDs der Visual Studio\-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio\-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Wenn Sie eine große Anzahl von Elementen der Benutzeroberfläche in der IDE platziert haben oder Elemente enthalten sind, die an mehreren Stellen angezeigt werden soll, definieren Sie ihre Standorte in der [CommandPlacements](../../extensibility/commandplacements-element.md) Element, wie in den folgenden Schritten dargestellt.  
  
##### Auf die Platzierung der Befehl verwenden, um Benutzeroberflächenelemente in der IDE  
  
1.  Nach dem `Commands` \-Element, Hinzufügen einer `CommandPlacements` Element.  
  
2.  In der `CommandPlacements` \-Element, Hinzufügen einer `CommandPlacement` \-Element für jedes Menü, Gruppe oder den Befehl platzieren.  
  
     Jede `CommandPlacement` Element oder `Parent` Element wird ein Menü, Gruppe oder den Befehl in einem IDE\-Speicherort. Ein UI\-Element kann nur ein übergeordnetes Element haben, aber es kann mehrere Befehl Standorte haben. Um ein Element der Benutzeroberfläche an mehreren Standorten zu platzieren, Hinzufügen einer `CommandPlacement` \-Element für jeden Standort.  
  
3.  Legen Sie die `guid` und `id` Attribute der einzelnen `CommandPlacement` Element auf das hosting Menü oder die Gruppe, so wie Sie würden für ein `Parent` Element. Zudem lassen sich die `priority` Attribut, um die relative Position des Benutzeroberflächenelements herzustellen.  
  
 Sie können die Platzierung von Überordnung und Platzierung der Befehl kombinieren. Für sehr große Befehlssätze empfehlen wir jedoch, dass Sie nur die Platzierung Befehl verwenden.  
  
### Hinzufügen von speziellen Verhaltensweisen  
 Sie können [CommandFlag](../../extensibility/command-flag-element.md) Elemente, um das Verhalten von Menüs und Befehlen, z. B. ändern, um ihre Darstellung und Sichtbarkeit ändern. Sie können auch beeinflussen, wenn ein Befehl angezeigt, mithilfe von wird [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), oder fügen Sie mithilfe von Tastenkombinationen [KeyBindings](../../extensibility/keybindings-element.md). Bestimmte Arten von Menüs und Befehlen bereits spezielle Verhaltensweisen, die in erstellt.  
  
##### Spezielle Verhaltensweisen hinzufügen  
  
1.  Um ein Element der Benutzeroberfläche sichtbar machen nur in bestimmten Benutzeroberflächen\-Kontexte, z. B. wenn eine Projektmappe geladen ist, verwenden Sie Sichtbarkeit\-Einschränkungen.  
  
    1.  Nach dem `Commands` \-Element, Hinzufügen einer `VisibilityConstraints` Element.  
  
    2.  Fügen Sie für jedes Element der Benutzeroberfläche eingeschränkt, einen [VisibilityItem](../../extensibility/visibilityitem-element.md) Element.  
  
    3.  Für jede `VisibilityItem` \-Element legen Sie die `guid` und `id` Attribute, die im Menü, Gruppe oder Befehl, und wählen Sie anschließend die `context` \-Attribut an den Benutzeroberflächenkontext werden sollen, im Sinne der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse. Weitere Informationen finden Sie unter [VisibilityItem\-Element](../../extensibility/visibilityitem-element.md).  
  
2.  Um die Sichtbarkeit oder die Verfügbarkeit eines UI\-Elements im Code festzulegen, verwenden Sie eine oder mehrere der folgenden Befehlsflags:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Weitere Informationen finden Sie unter [Command\-Flag\-Element](../../extensibility/command-flag-element.md).  
  
3.  Verwenden Sie zum Ändern ein Elements angezeigt wird, oder die Darstellung dynamisch ändern, eine oder mehrere der folgenden Befehlsflags:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextÄndert  
  
    -   TextOnly  
  
     Weitere Informationen finden Sie unter [Command\-Flag\-Element](../../extensibility/command-flag-element.md).  
  
4.  Um ein Element wie reagiert, wenn Befehle empfangen zu ändern, verwenden Sie eine oder mehrere der folgenden Befehlsflags:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Filter\-Schlüssel  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Weitere Informationen finden Sie unter [Command\-Flag\-Element](../../extensibility/command-flag-element.md).  
  
5.  Um ein Menü oder ein Element in einem Menü eine Tastenkombination im Menü abhängige zuzuordnen, fügen Sie ein kaufmännisches und\-Zeichen \("&"\) in der `ButtonText` \-Element für das Menü oder Menüelement. Das Zeichen, das kaufmännische und\-Zeichen folgt, ist die aktive Tastenkombination, wenn im übergeordneten Menü geöffnet ist.  
  
6.  Um einen Befehl eine Tastenkombination im Menü unabhängig anzufügen, verwenden Sie [KeyBindings](../../extensibility/keybindings-element.md). Weitere Informationen finden Sie unter [KeyBinding\-Element](../../extensibility/keybinding-element.md).  
  
7.  Um Menüs zu lokalisieren, verwenden die `LocCanonicalName` Element. Weitere Informationen finden Sie unter [Zeichenfolgen\-Element](../../extensibility/strings-element.md).  
  
 Einige Typen Menü und die Schaltfläche enthalten spezielle Verhaltensweisen. Die folgende Tabelle beschreibt einige spezielle Menü und Schaltflächen. Andere Typen, die `types` \-Attribut Beschreibungen in [Menu\-Element](../../extensibility/menu-element.md), [Button\-Element](../../extensibility/button-element.md), und [Kombinationsfeld\-Element](../../extensibility/combo-element.md).  
  
 Kombinationsfeld  
 Ein Kombinationsfeld ist eine Dropdown\-Liste, die auf einer Symbolleiste verwendet werden kann. Um Kombinationsfelder der UI hinzuzufügen, erstellen Sie eine [Tastenkürzel](../../extensibility/combos-element.md) Element in der `Commands` Element. Klicken Sie dann auf Hinzufügen die `Combos` Element ein `Combo` \-Element für jedes im Kombinationsfeld hinzu.`Combo` Elemente sind die gleichen Attribute und untergeordneten Elemente wie `Button` Elemente und `DefaultWidth` und `idCommandList` Attribute. Das `DefaultWidth` \-Attribut legt die Breite in Pixel und die `idCommandList` \-Attribut verweist auf eine Befehls\-ID, die verwendet wird, um das Kombinationsfeld aufzufüllen. Weitere Informationen finden Sie unter der `Combo` Element\-Dokumentation.  
  
 MenuController  
 Ein Menü\-Controller ist eine Schaltfläche mit einem Pfeil daneben. Auf den Pfeil klicken, wird eine Liste angezeigt. Zum Hinzufügen eines Controllers im Menü auf die Benutzeroberfläche erstellen Sie ein `Menu` Element, und legen seine `type` \-Attribut **MenuController** oder **MenuControllerLatched**, je nachdem, auf das gewünschte Verhalten. Um ein Menü Controller aufzufüllen, legen Sie es als das übergeordnete Element von einem `Group` Element. Der Controller im Menü werden alle untergeordneten Elemente dieser Gruppe auf die Dropdown\-Liste angezeigt.  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML\-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)