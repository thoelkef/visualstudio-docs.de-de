---
title: Menu-Element | Microsoft Docs
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
ms.openlocfilehash: 5c44ca8a78a331d66d099b8d141c4b66c1144949
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143451"
---
# <a name="menu-element"></a>Menu-Element
Definiert ein Menüelement an. Hierbei handelt es sich um die sechs Typen von Menüs: Kontext, Menüs, MenuController, MenuControllerLatched, Symbolleisten und ToolWindowToolbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|guid|Erforderlich. GUID des Bezeichners GUID-ID-Befehl.|  
|ID|Erforderlich. ID des Bezeichners GUID-ID-Befehl.|  
|priority|Dies ist optional. Ein numerischer Wert, der die relative Position eines Menüs in einer Gruppe von Menüs angibt.|  
|ToolbarPriorityInBand|Dies ist optional. Ein numerischer Wert, der die relative Position der Symbolleiste in einem Band angibt, wenn das Fenster angedockt wird.|  
|Typ|Dies ist optional. Ein Enumerationswert, der die Art des Elements angibt.<br /><br /> Wenn Sie nicht vorhanden ist, ist der Standardtyp Menü aus.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer ein Fenster klickt. Ein Kontextmenü weist folgende Merkmale auf:<br /><br /> -Die übergeordnete und die Priorität Felder wird nicht verwendet werden, wenn das Menü ist als ein Kontextmenü angezeigt werden.<br />-Kann als ein Untermenü und auch als ein Kontextmenü verwendet werden. In diesem Fall werden sowohl die Gruppen-ID als auch die Priorität berücksichtigt.<br />– Dies ist nicht immer verfügbar.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn Folgendes zutrifft:<br /><br /> -Das Fenster, das sie hostet wird angezeigt.<br />– Ein Maushandler im VSPackage erkennt einen Rechtsklick auf das Fenster, und ruft dann eine Methode, die den Befehl behandelt.<br />-Das Kontextmenü wird angezeigt, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Methode (empfohlen) oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> Methode.<br /><br /> Menü<br /> Enthält ein Dropdown-Menü an. Ein Dropdown-Menü weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition berücksichtigt.<br />-Muss eine übergeordnete Gruppe oder ein CommandPlacement zu einer Gruppe werden kann.<br />-Ein Untermenü in eine beliebige andere Art des Menüs möglich.<br />-Wird automatisch angezeigt werden, wenn die übergeordneten Menü angezeigt wird.<br />– Die Implementierung des VSPackage von Code erleichtern angezeigt ist nicht erforderlich ist.<br /><br /> MenuController<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü, das in der Regel in Symbolleisten verwendet wird. Ein Menü MenuController weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über übergeordnete oder CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition berücksichtigt.<br />-Kann jede Art von Menü wie das übergeordnete Objekt haben.<br />– Wird automatisch zur Verfügung gestellt bei jedem übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung auf Stellen Sie im Menü angezeigt ist nicht erforderlich ist.<br /><br /> Ein unterteilte Schaltfläche im Menü den Befehl wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt, verfügt über einen der folgenden Merkmale:<br /><br /> – Es ist mit dem letzten Befehl, der verwendet wurde, wenn der Befehl weiterhin angezeigt und aktiviert ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> MenuControllerLatched<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü für die ein Befehl als Standardauswahl angegeben werden kann durch die Markierung des Befehls wie als ausgewählt markiert.<br /><br /> Ein gesperrtes Befehl dient, die Sie im Menü ausgewählt, in der Regel markiert ist, indem ein Häkchen angezeigt. Ein Befehl kann gekennzeichnet werden, wie ein, wenn sie die OLECMDF_LATCHED verfügt flag festgelegt darauf in einer Implementierung von der `QueryStatus` Methode der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Ein Menü MenuControllerLatched weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über eine übergeordnete Gruppe oder CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition berücksichtigt.<br />-Kann jede Art von Menü wie das übergeordnete Objekt haben.<br />– Dies ist zur Verfügung gestellt, wenn die übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung auf Stellen Sie im Menü angezeigt ist nicht erforderlich ist.<br /><br /> Ein unterteilte Schaltfläche im Menü den Befehl wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt, verfügt über einen der folgenden Merkmale:<br /><br /> -Es ist mit dem ersten angezeigten Befehl, der als ausgewählt markiert ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> Symbolleiste<br /> Eine Symbolleiste bereitgestellt. Eine Symbolleiste weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann ein Untermenü der Gruppe "Jeder", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />-Kann immer angezeigt werden, indem Sie auf **Symbolleisten** auf die **Ansicht** Menü.<br />-Können angezeigt werden, indem eine [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Keinen Code für die Erstellung erfordert keine. Ein Beispiel zum Erstellen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Enthält eine Symbolleiste, die an einem bestimmten Toolfenster angefügt wird, ebenso wie eine Symbolleiste mit der Entwicklungsumgebung verbunden ist.<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann ein Untermenü der Gruppe "Jeder", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />– Wird nur angezeigt, wenn das Toolfenster, das die Symbolleiste hostet angezeigt wird und das VSPackage explizit die Symbolleiste auf das Toolfenster hinzufügt. Dies erfolgt normalerweise, wenn das Toolfenster erstellt wird, indem Sie die Symbolleiste Hosteigenschaft abrufen (dargestellt durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> Schnittstelle) aus der Toolfensterrahmen aufrufen und anschließend die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> Methode.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Dies ist optional. Das übergeordnete Element des Menüelements.|  
|CommandFlag|Erforderlich. Finden Sie unter [Befehl Flag Element](../extensibility/command-flag-element.md). Gültige Werte für ein Menü CommandFlag sind wie folgt aus:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten.<br />-   **DontCache**<br />-   **DynamicVisibility** -dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Zeichenfolgen|Erforderlich. Finden Sie unter [Zeichenfolgen Element](../extensibility/strings-element.md). Das untergeordnete Element `ButtonText` Element definiert werden muss.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die eine VSPackage implementiert.|  
  
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
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)