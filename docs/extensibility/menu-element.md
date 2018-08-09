---
title: Menu-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d69a6951cdae84ba2abc06bcdfde19fffa665c03
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637509"
---
# <a name="menu-element"></a>Menu-element
Definiert ein Menüelement. Hierbei handelt es sich um die sechs Arten von Menüs: Kontext, Menüs, MenuController, MenuControllerLatched, Symbolleiste und ToolWindowToolbar.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID der Befehls-ID der GUID-ID.|  
|ID|Erforderlich. ID des Befehls-ID der GUID-ID.|  
|priority|Dies ist optional. Ein numerischer Wert, der angibt, die relative Position eines Menüs in einer Gruppe von Menüs.|  
|ToolbarPriorityInBand|Dies ist optional. Ein numerischer Wert, der die relative Position einer Symbolleiste in einem Band angibt, wenn das Fenster angedockt wird.|  
|Typ|Dies ist optional. Ein Enumerationswert, der die Art des Elements angibt.<br /><br /> Wenn Sie nicht vorhanden ist, ist der Standardtyp Menü aus.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer ein Fenster mit der rechten Maustaste. Ein Kontextmenü weist folgende Merkmale auf:<br /><br /> – Verwendet nicht die **übergeordneten** und **Priorität** Felder, wenn das Menü wird als ein Kontextmenü angezeigt werden soll.<br />– Sie können als Untermenü sowie als Kontextmenü verwendet werden. In diesem Fall sowohl **Gruppen-ID** und **Priorität** Felder berücksichtigt werden.<br />– Dies ist nicht immer zur Verfügung.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn die folgenden Bedingungen erfüllt sind:<br /><br /> -Das Fenster, das als Host dienende wird angezeigt.<br />– Ein Mauszeiger-Handler im VSPackage erkennt eine mit der rechten Maustaste auf das Fenster und ruft dann eine Methode, die den Befehl behandelt.<br />-Das Kontextmenü wird angezeigt, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Methode (empfohlen) oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> Methode.<br /><br /> Menü<br /> Stellt ein Dropdown-Menü. Ein Dropdown-Menü weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition respektiert.<br />-Muss es sich um eine übergeordnete Gruppe oder einem CommandPlacement zu einer Gruppe aufweisen.<br />– Ein Untermenü in eine andere Art von Menü Sie können sein.<br />– Wird automatisch angezeigt, bei jedem übergeordneten Menü angezeigt wird.<br />– Die Implementierung des VSPackage von Code erleichtern angezeigt ist nicht erforderlich werden.<br /><br /> MenuController<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü, der in Symbolleisten in der Regel verwendet wird. Ein Menü MenuController weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über übergeordnete oder CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition respektiert.<br />– Sie können jede Art von Menü als übergeordnetes Element haben.<br />– Wird automatisch zur Verfügung gestellt bei jedem übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung im angezeigten Menü vornehmen ist nicht erforderlich werden.<br /><br /> Ein Befehl im Menü der unterteilten Schaltfläche wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> – Es ist mit dem letzten Befehl, der verwendet wurde, wenn der Befehl weiterhin angezeigt, und aktiviert ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> MenuControllerLatched<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü, das für die ein Befehl als Standardauswahl angegeben werden kann durch markieren den Befehl aus, wie ein Latchtyp zugeordnet.<br /><br /> Ein eingerastet Befehl ist ein Befehl, der im Menü als ausgewählt, in der Regel markiert ist, indem ein Häkchen angezeigt. Ein Befehl kann gekennzeichnet werden, wie ein Latchtyp zugeordnet, wenn sie die OLECMDF_LATCHED verfügt flagssatz darauf in einer Implementierung von der `QueryStatus` -Methode der der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Ein Menü MenuControllerLatched weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über eine übergeordnete Gruppe oder ein CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition respektiert.<br />– Sie können jede Art von Menü als übergeordnetes Element haben.<br />– Dies ist zur Verfügung gestellt, wenn die übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung im angezeigten Menü vornehmen ist nicht erforderlich werden.<br /><br /> Ein Befehl im Menü der unterteilten Schaltfläche wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> – Es ist mit dem ersten angezeigten Befehl, der ein Latchtyp zugeordnet ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> Symbolleiste<br /> Enthält eine Symbolleiste an. Eine Symbolleiste weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann kein Untermenü der Gruppe "alle", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />– Sie können immer angezeigt werden, indem Sie auf **Symbolleisten** auf die **Ansicht** Menü.<br />– Sie können angezeigt werden, indem eine [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Code zu erstellen erfordert keine. Ein Beispiel dazu, wie Sie eine Symbolleiste erstellen, finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Enthält eine Symbolleiste, die mit einem bestimmten Toolfenster, verbunden ist, wie eine Symbolleiste mit der Entwicklungsumgebung verbunden ist.<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann kein Untermenü der Gruppe "alle", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />– Wird nur angezeigt, wenn das Toolfenster, das die Symbolleiste hostet angezeigt wird, und das VSPackage wird explizit die Symbolleiste, um das Fenster hinzugefügt. Dies erfolgt normalerweise, wenn das Toolfenster erstellt wird, durch die Toolbar-Host-Eigenschaft abrufen (dargestellt durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> Schnittstelle) aus der Toolfensterrahmen aufrufen und anschließend die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> Methode.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Dies ist optional. Das übergeordnete Element des Menüelements.|  
|CommandFlag|Erforderlich. Finden Sie unter [commandflag-Element](../extensibility/command-flag-element.md). Gültige Werte für ein Menü CommandFlag sind wie folgt aus:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -dieses Flag hat keine Auswirkungen auf die Anzeige von Symbolleisten.<br />-   **DontCache**<br />-   **DynamicVisibility** -dieses Flag hat keine Auswirkungen auf die Anzeige von Symbolleisten.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Zeichenfolgen|Erforderlich. Finden Sie unter [Strings-Element](../extensibility/strings-element.md). Das untergeordnete Element `ButtonText` Element definiert werden muss.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Menus-element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (.vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)