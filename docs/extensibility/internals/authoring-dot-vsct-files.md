---
title: Erstellen. VSCT-Dateien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fa274c807aaa1ed212a7b283a35e510615561eb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-vsct-files"></a>Erstellen. VSCT-Dateien
Dieses Dokument zeigt, wie zum Erstellen einer VSCT-Datei, um die integrierte Entwicklungsumgebung (IDE) von Visual Studio Menüelemente, Symbolleisten und andere Elemente der Benutzeroberfläche (UI) hinzuzufügen. Gehen Sie folgendermaßen vor, wenn Sie Elemente der Benutzeroberfläche eine Visual Studio-Paket (VSPackage) hinzufügen, die nicht bereits über eine VSCT-Datei verfügt.  
  
 Bei neuen Projekten wird empfohlen, dass Sie die Visual Studio-Paket-Vorlage verwenden, da es sich um eine VSCT-Datei generiert, die abhängig von Ihrer Auswahl bereits die erforderlichen Elemente für einen Menübefehl, eines Toolfensters oder einen benutzerdefinierten Editor aufweist. Sie können diese VSCT-Datei, um den Anforderungen Ihres VSPackage ändern. Weitere Informationen zum Ändern einer VSCT-Datei finden Sie unter den Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Konfiguration der Datei  
 Erstellen eine VSCT-Datei in dieser Phasen: Erstellen Sie die Struktur für Dateien und Ressourcen, deklarieren Sie die Elemente der Benutzeroberfläche, platzieren Sie die Elemente der Benutzeroberfläche in der IDE und fügen Sie speziellen Verhaltensweisen.  
  
### <a name="file-structure"></a>Dateistruktur  
 Die grundlegende Struktur einer VSCT-Datei ist eine [CommandTable](../../extensibility/commandtable-element.md) Root-Element enthält eine [Befehle](../../extensibility/commands-element.md) Element und ein [Symbole](../../extensibility/symbols-element.md) Element.  
  
##### <a name="to-create-the-file-structure"></a>Beim Erstellen der Dateistruktur  
  
1.  Anhand der Schritte in einer VSCT-Datei dem Projekt hinzufügen [Vorgehensweise: Erstellen einer. VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Fügen Sie die erforderlichen Namespaces, die `CommandTable` Element, wie im folgenden Beispiel dargestellt.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  In der `CommandTable` Element, Hinzufügen einer `Commands` Element, um alle Ihre benutzerdefinierten Menüs, Symbolleisten, Befehlsgruppen und Befehle zu hosten. Damit Ihre benutzerdefinierten Benutzeroberflächenelemente laden können, die `Commands` muss seine `Package` Attribut auf den Namen des Pakets festgelegt.  
  
     Nach der `Commands` Element, Hinzufügen einer `Symbols` Element zu definieren, die GUIDs für das Paket und die Namen der Befehls-IDs für Ihre UI-Elemente.  
  
### <a name="including-visual-studio-resources"></a>Das Einschließen von Visual Studio-Ressourcen  
 Verwenden der ["extern"](../../extensibility/extern-element.md) Element auf die Dateien zugreifen, die Visual Studio-Befehle und die Menüs, die erforderlich sind, um die Elemente der Benutzeroberfläche in der IDE put definieren. Wenn Sie Befehle, die außerhalb des Pakets definiert verwenden möchten, verwenden Sie die [UsedCommands](../../extensibility/usedcommands-element.md) Element, um Visual Studio zu informieren.  
  
##### <a name="to-include-visual-studio-resources"></a>Visual Studio-Ressourcen enthalten.  
  
1.  Am oberen Rand der `CommandTable` Element, fügen Sie einen `Extern` -Element für jede externe Datei, die auf die verwiesen wird und festgelegt werden, die `href` -Attribut auf den Namen der Datei. Sie können die folgenden Headerdateien für den Zugriff auf Visual Studio-Ressourcen verweisen:  
  
    -   Stdidcmd.h, definiert die IDs für alle Befehle, die von Visual Studio verfügbar gemacht werden.  
  
    -   Vsshlids.h, enthält die Befehls-IDs für Visual Studio-Menüs.  
  
2.  Wenn Ihr Paket Befehle, die von Visual Studio oder von anderen Paketen definiert sind aufruft, fügen Sie eine `UsedCommands` Elements nach dem `Commands` Element. Füllen Sie dieses Element mit einem [UsedCommand](../../extensibility/usedcommand-element.md) Element für jeden Befehl, die Sie aufrufen, d. h. nicht Teil des Pakets. Legen Sie die `guid` und `id` Attribute der `UsedCommand` Elemente mit den GUID und ID-Werten der Befehle zum Aufrufen. Weitere Informationen dazu, wie die GUIDs und IDs von Visual Studio-Befehle finden, finden Sie unter [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Um Befehle von anderen Paketen aufzurufen, verwenden Sie die GUID und die ID des Befehls gemäß Definition in der VSCT-Datei für diese Pakete aus.  
  
### <a name="declaring-ui-elements"></a>Deklarieren von UI-Elemente  
 Deklarieren Sie alle Elemente der neuen Benutzeroberfläche in der `Symbols` Abschnitt der VSCT-Datei.  
  
##### <a name="to-declare-ui-elements"></a>Um Benutzeroberflächenelemente zu deklarieren.  
  
1.  In der `Symbols` Element, fügen Sie drei [GuidSymbol](../../extensibility/guidsymbol-element.md) Elemente. Jede `GuidSymbol` Element verfügt über eine `name` Attribut und einem `value` Attribut. Legen Sie die `name` Attribut, damit es sich um den Zweck des Elements widerspiegelt. Die `value` -Attribut nimmt eine GUID. (Zum Generieren einer GUID, die für die **Tools** Menü klicken Sie auf **GUID erstellen**, und wählen Sie dann **Registrierungsformat**.)  
  
     Die erste `GuidSymbol` Element des Pakets darstellt und in der Regel weist keine untergeordneten Elemente. Die zweite `GuidSymbol` Element darstellt, mit dem Befehl festgelegt und enthält alle Symbole, die die Menüs, Gruppen und Befehle zu definieren. Das dritte `GuidSymbol` Element stellt die imagespeicher und enthält Symbole für alle Symbole für die Befehle. Wenn Sie keine Befehle, die Symbole verwenden verfügen, können Sie das dritte weglassen `GuidSymbol` Element.  
  
2.  In der `GuidSymbol` Element, das Ihre Befehlssatz dargestellt hinzufügen, eine oder mehrere [IDSymbol](../../extensibility/idsymbol-element.md) Elemente. Jede dieser darstellen, ein Menü, Symbolleiste, Gruppe oder Befehl ein, die Sie an die Benutzeroberfläche hinzufügen.  
  
     Für jede `IDSymbol` -Elementgruppe, die `name` -Attribut auf den Namen, die Sie verwenden, um auf das entsprechende Menü, eine Gruppe oder ein Befehl verweisen, und legen Sie dann die `value` Element in eine hexadezimale Zahl, die die Befehls-Id darstellt. Keine zwei `IDSymbol` Elemente mit demselben übergeordneten Element den gleichen Wert aufweisen können.  
  
3.  Wenn keines der Elemente der Benutzeroberfläche Symbole benötigen, fügen Sie ein `IDSymbol` -Element für jedes Symbol, um die `GuidSymbol` Element, das die imagespeicher darstellt.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Wenn Sie Elemente der Benutzeroberfläche in der IDE  
 Die [Menüs](../../extensibility/menus-element.md) Element [Gruppen](../../extensibility/groups-element.md) Element, und [Schaltflächen](../../extensibility/buttons-element.md) -Element enthalten, die Definitionen für alle Menüs, Gruppen und Befehle, die im Paket definiert sind. Platzieren Sie diese Menüs, Gruppen und Befehle in der IDE mithilfe einer [übergeordneten](../../extensibility/parent-element.md) Elements, d. h. der Teil der Definition des UI-Element, oder mit einer [CommandPlacement](../../extensibility/commandplacement-element.md) Element definiert, der an anderer Stelle.  
  
 Jede `Menu`, `Group`, und `Button` Element verfügt über eine `guid` Attribut und ein `id` Attribut. Immer festgelegt die `guid` Attribut entsprechend den Namen des der `GuidSymbol` Element, das den Befehl dargestellt festgelegt, und legen die `id` -Attribut auf den Namen des der `IDSymbol` Element, das die im Menü, eine Gruppe oder ein Befehl in der darstellt`Symbols`Abschnitt.  
  
##### <a name="to-define-ui-elements"></a>Um Elemente der Benutzeroberfläche zu definieren.  
  
1.  Wenn Sie neuen Menüs, Untermenüs, Kontextmenüs oder Symbolleisten definieren, fügen Sie eine `Menus` Element an der `Commands` Element. Für die einzelnen Menüs erstellt werden soll, fügen Sie dann eine [Menü](../../extensibility/menu-element.md) Element an der `Menus` Element.  
  
     Festlegen der `guid` und `id` Attribute der `Menu` -Element, und legen die `type` -Attribut auf die Art des gewünschten Menüs. Sie können auch festlegen, die `priority` Attribut, um die relative Position des Menüs in der übergeordneten Gruppe herzustellen.  
  
    > [!NOTE]
    >  Die `priority` Attribut gilt nicht für Symbolleisten und Kontextmenüs zu sehen.  
  
2.  Alle Befehle in der Visual Studio-IDE müssen von Befehlsgruppen gehostet werden, die die direkten untergeordneten Elemente des Menüs und Symbolleisten sind. Wenn Sie neue Menüs oder Symbolleisten der IDE hinzufügen, müssen diese neue Befehlsgruppen enthalten. Sie können auch Befehlsgruppen zu vorhandenen Menüs und Symbolleisten hinzufügen, damit Sie Ihre Befehle visuell gruppiert werden können.  
  
     Wenn Sie neue Befehlsgruppen hinzufügen, müssen Sie zuerst erstellen eine `Groups` Element, und fügen Sie dann darauf ein [Gruppe](../../extensibility/group-element.md) -Element für jeden Befehlsgruppe.  
  
     Legen Sie die `guid` und `id` Attribute der einzelnen `Group` -Element, und legen die `priority` Attribut, um die relative Position der Gruppe im übergeordneten Menü herzustellen. Weitere Informationen finden Sie unter [erstellen Wiederverwendbarer Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Wenn Sie der IDE neue Befehle hinzufügen, fügen Sie eine `Buttons` Element an der `Commands` Element. Fügen Sie dann für jeden Befehl eine [Schaltfläche](../../extensibility/button-element.md) Element an der `Buttons` Element.  
  
    1.  Legen Sie die `guid` und `id` Attribute der einzelnen `Button` -Element, und legen Sie anschließend die `type` -Attribut auf die Art der gewünschten Schaltfläche. Sie können auch festlegen, die `priority` Attribut, um die relative Position des Befehls in der übergeordneten Gruppe herzustellen.  
  
        > [!NOTE]
        >  Verwendung `type="button"` für standard Menübefehle und Schaltflächen in Symbolleisten.  
  
    2.  In der `Button` Element, Hinzufügen einer [Zeichenfolgen](../../extensibility/strings-element.md) -Element, enthält eine [ButtonText](../../extensibility/buttontext-element.md) Element und ein [CommandName](../../extensibility/commandname-element.md) Element. Die `ButtonText` -Element stellt die Beschriftung für ein Menüelement oder der QuickInfo für eine Symbolleisten-Schaltfläche. Die `CommandName` Element enthält den Namen des Befehls im Befehl verwenden.  
  
    3.  Wenn der Befehl ein Symbol aufweisen soll, erstellen eine [Symbol](../../extensibility/icon-element.md) Element in der `Button` -Element, und legen seine `guid` und `id` -Attribute verwenden, um die `Bitmap` -Element für das Symbol ".  
  
        > [!NOTE]
        >  Schaltflächen der Symbolleiste benötigen Symbole.  
  
     Weitere Informationen finden Sie unter [MenuCommand-und. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Wenn Ihre Befehle Symbole benötigen, fügen Sie eine [Bitmaps](../../extensibility/bitmaps-element.md) Element an der `Commands` Element. Fügen Sie dann für jedes Symbol ein [Bitmap](../../extensibility/bitmap-element.md) Element an der `Bitmaps` Element. Dies ist in dem Sie den Speicherort der Bitmapressource angeben. Weitere Informationen finden Sie unter [Hinzufügen von Symbolen zu Menübefehlen](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Sie können auf die Überordnung-Struktur, die meisten Menüs, Gruppen und Befehle ordnungsgemäß platzieren verlassen. Für sehr große Befehlssätze oder wenn ein Menü, eine Gruppe oder ein Befehl an mehreren Stellen angezeigt werden muss, wird empfohlen, dass Sie die Platzierung des Befehls angeben.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Überordnung an Benutzeroberflächenelemente in der IDE vertrauen  
  
1.  Für typische Überordnung erstellen eine `Parent` -Element in jedem `Menu`, `Group`, und `Command` -Element, das im Paket definiert ist.  
  
     Das Ziel der `Parent` Element ist das Menü oder Gruppe, die das Menü enthält, Gruppe oder -Befehl.  
  
    1.  Legen Sie die `guid` auf den Namen des Attributs der `GuidSymbol` Element, das den Befehlssatz definiert. Wenn das Zielelement nicht Teil des Pakets ist, verwenden Sie die Guid für diese Befehl festgelegt ist, wie in der entsprechenden VSCT-Datei definiert.  
  
    2.  Legen Sie die `id` Attribut entsprechend den `id` Attribut des Zielmenü oder der Gruppe. Eine Liste der Menüs und Gruppen, die von Visual Studio bereitgestellt werden, finden Sie unter [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Wenn Sie eine große Anzahl von Elementen der Benutzeroberfläche, die in der IDE platziert haben, oder Elemente vorhanden sein, die an mehreren Stellen angezeigt werden soll, definieren Sie ihre Standorte in der [CommandPlacements](../../extensibility/commandplacements-element.md) Element, wie in den folgenden Schritten dargestellt.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Befehl Platzierung verwenden, um Benutzeroberflächenelemente in der IDE zu platzieren  
  
1.  Nach der `Commands` Element, Hinzufügen einer `CommandPlacements` Element.  
  
2.  In der `CommandPlacements` Element, Hinzufügen einer `CommandPlacement` -Element für jedes Menü, Gruppe oder den Befehl platzieren.  
  
     Jede `CommandPlacement` Element oder `Parent` Element wird ein Menü, Gruppe oder den Befehl in einem IDE-Speicherort. Ein Element der Benutzeroberfläche kann nur ein übergeordnetes Element haben kann, er jedoch mehrere befehlsplatzierungen. Um ein Element der Benutzeroberfläche an mehreren Speicherorten zu platzieren, Hinzufügen einer `CommandPlacement` -Element für jeden Standort.  
  
3.  Legen Sie die `guid` und `id` Attribute der einzelnen `CommandPlacement` Element das hosting Menü oder einer Gruppe, so wie Sie möchten für ein `Parent` Element. Sie können auch Festlegen der `priority` Attribut, um die relative Position des Benutzeroberflächenelements herzustellen.  
  
 Sie können die Platzierung von Überordnung und Befehl Platzierung kombinieren. Für sehr große Befehlssätze empfehlen wir jedoch, dass Sie nur die Platzierung Befehl verwenden.  
  
### <a name="adding-specialized-behaviors"></a>Hinzufügen von spezielle Verhaltensweisen  
 Sie können [CommandFlag](../../extensibility/command-flag-element.md) Elemente, um das Verhalten von Menüs und Befehle, z. B. ändern, um ihre Darstellung und Sichtbarkeit zu ändern. Sie können auch beeinflussen, wenn ein Befehl angezeigt, mithilfe von wird [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), oder fügen Sie mithilfe von Tastenkombinationen [Schlüsselbindungen](../../extensibility/keybindings-element.md). Bestimmte Arten von Menüs und Befehle bereits spezielle Verhaltensweisen erstellt.  
  
##### <a name="to-add-specialized-behaviors"></a>So fügen Sie spezielle Verhaltensweisen hinzu  
  
1.  Um ein Element der Benutzeroberfläche sichtbar machen nur in bestimmten UI-Kontexten z. B. wenn eine Projektmappe geladen wird, verwenden Sie Sichtbarkeit-Einschränkungen.  
  
    1.  Nach der `Commands` Element, Hinzufügen einer `VisibilityConstraints` Element.  
  
    2.  Für jedes Element der Benutzeroberfläche, die zu beschränken, Hinzufügen einer [VisibilityItem](../../extensibility/visibilityitem-element.md) Element.  
  
    3.  Für jede `VisibilityItem` -Elementgruppe, die `guid` und `id` Attribute auf das Menü, Gruppe oder Befehl, und legen die `context` Attribut an den UI-Kontext werden soll, gemäß der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse. Weitere Informationen finden Sie unter [VisibilityItem Element](../../extensibility/visibilityitem-element.md).  
  
2.  Um die Sichtbarkeit oder die Verfügbarkeit eines Benutzeroberflächenautomatisierungs-Elements im Code festzulegen, verwenden Sie eine oder mehrere der folgenden Befehlsflags aus:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Weitere Informationen finden Sie unter [Flags Befehlselement](../../extensibility/command-flag-element.md).  
  
3.  Verwenden Sie zum Ändern, wie ein Element angezeigt wird, oder seine Darstellung dynamisch ändern, eine oder mehrere der folgenden Befehlsflags aus:  
  
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
  
    -   TextChanges  
  
    -   TextOnly  
  
     Weitere Informationen finden Sie unter [Flags Befehlselement](../../extensibility/command-flag-element.md).  
  
4.  Um ein Element wie reagiert, wenn Befehle empfangen zu ändern, verwenden Sie eine oder mehrere der folgenden Befehlsflags aus:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Durch Drücken  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Weitere Informationen finden Sie unter [Flags Befehlselement](../../extensibility/command-flag-element.md).  
  
5.  Um ein Menü abhängiges Tastenkombination eines Menüs oder ein Element in einem Menü zuzuordnen, fügen Sie ein kaufmännisches und-Zeichen ("&") in der `ButtonText` -Element für das Menü oder Menüelement. Das Zeichen, das kaufmännische und-Zeichen folgt, ist die aktive Tastenkombination aus, wenn im übergeordneten Menü geöffnet ist.  
  
6.  Um einen Befehl eine Tastenkombination Menü typunabhängig anzufügen, verwenden Sie [Schlüsselbindungen](../../extensibility/keybindings-element.md). Weitere Informationen finden Sie unter [KeyBinding Element](../../extensibility/keybinding-element.md).  
  
7.  Um Menütext zu lokalisieren, verwenden Sie die `LocCanonicalName` Element. Weitere Informationen finden Sie unter [Zeichenfolgen Element](../../extensibility/strings-element.md).  
  
 Einige Menüs und Schaltflächen die folgenden Anweisungstypen spezielle Verhaltensweisen. In der folgenden Tabelle werden einige spezielle Menü und die Schaltflächentypen beschrieben. Andere Typen finden Sie unter der `types` -Attribut Beschreibungen in [Menu-Element](../../extensibility/menu-element.md), [Schaltflächenelement](../../extensibility/button-element.md), und [Kombinationsfeld Element](../../extensibility/combo-element.md).  
  
 Kombinationsfeld  
 Ein Kombinationsfeld ist eine Dropdown-Liste, die auf einer Symbolleiste verwendet werden kann. Kombinationsfelder an die Benutzeroberfläche hinzufügen möchten, erstellen Sie eine [Tastenkürzel](../../extensibility/combos-element.md) Element in der `Commands` Element. Fügen Sie dann auf die `Combos` Element ein `Combo` -Element für jedes im Kombinationsfeld hinzufügen. `Combo`Elemente aufweisen, die dieselben Attribute und untergeordneten Elemente als `Button` Elemente und außerdem `DefaultWidth` und `idCommandList` Attribute. Die `DefaultWidth` -Attribut legt die Breite in Pixel und die `idCommandList` -Attribut verweist auf eine Befehls-ID, die zum Auffüllen des Kombinationsfelds verwendet wird. Weitere Informationen finden Sie unter der `Combo` Element-Dokumentation.  
  
 MenuController  
 Ein Menücontroller ist eine Schaltfläche mit einem Pfeil angezeigt. Durch Klicken auf den Pfeil wird eine Liste. Um die Benutzeroberfläche ein Menücontroller hinzugefügt haben, erstellen Sie eine `Menu` Element, und legen seine `type` -Attribut **MenuController** oder **MenuControllerLatched**, je nachdem, auf das gewünschte Verhalten. Um ein Menücontroller aufzufüllen, legen Sie sie als das übergeordnete Element von einem `Group` Element. Der Menücontroller im werden alle untergeordneten Elemente dieser Gruppe in der Dropdown-Liste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)