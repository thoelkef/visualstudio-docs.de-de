---
title: "Menu-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, Menüs"
  - "Menüs-Element (VSCT-XML-Schema)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Menu-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert ein Menüelement. Dies sind die sechs Arten von Menüs: Kontext, Menü, MenuController, MenuControllerLatched, Symbolleiste und ToolWindowToolbar.  
  
## Syntax  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die GUID der GUID\-ID\-Befehls\-ID.|  
|ID|Erforderlich. ID der GUID\-ID\-Befehls\-ID.|  
|priority|Optional. Einen numerischen Wert, der die relative Position eines Menüs in einer Gruppe von Menüs.|  
|ToolbarPriorityInBand|Optional. Einen numerischen Wert, der die relative Position der Symbolleiste in einem Band angibt, wenn das Fenster angedockt wird.|  
|Typ|Optional. Ein Enumerationswert, der die Art des Elements angibt.<br /><br /> Wenn nicht vorhanden ist, ist das Menü.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer ein Fenster mit der rechten Maustaste. Ein Kontextmenü weist folgende Merkmale auf:<br /><br /> -   Die übergeordnete und die Priorität\-Felder verwendet nicht, wenn das Menü ist als ein Kontextmenü angezeigt werden soll.<br />-   Kann als Untermenü und auch als Kontextmenü verwendet werden. In diesem Fall werden sowohl die Gruppen\-ID als auch die Priorität berücksichtigt.<br />-   Ist nicht immer verfügbar.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn Folgendes zutrifft:<br /><br /> -   Das Fenster, das es hostet angezeigt wird.<br />-   Ein Maustasten\-Ereignishandler in der VSPackage erkennt einen Rechtsklick auf das Fenster, und ruft dann eine Methode, die den Befehl verarbeitet.<br />-   Das Kontextmenü wird angezeigt, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> \-Methode \(empfohlen\) oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> Methode.<br /><br /> Menü<br /> Enthält ein Dropdown\-Menü. Ein Dropdown Menü weist folgende Merkmale auf:<br /><br /> -   Das übergeordnete Element in der Definition wird berücksichtigt.<br />-   Muss eine übergeordnete Gruppe oder ein CommandPlacement zu einer Gruppe sein.<br />-   Kann ein Untermenü in eine andere Art von Menü.<br />-   Wird automatisch angezeigt, wenn die übergeordneten Menü angezeigt wird.<br />-   Erfordert keine die Implementierung von VSPackage Code zu vereinfachen angezeigt.<br /><br /> MenuController<br /> Bietet eine Trennschaltfläche Dropdown\-Menü, das in der Regel in Symbolleisten verwendet wird. Ein MenuController hat die folgenden Merkmale:<br /><br /> -   Muss in einem anderen Menü über über\- oder CommandPlacement enthalten sein.<br />-   Das übergeordnete Element in der Definition wird berücksichtigt.<br />-   Kann jede Art von Menü als übergeordnetes Element haben.<br />-   Wird automatisch zur Verfügung gestellt bei jedem übergeordneten Menü angezeigt wird.<br />-   Erfordert keine programmgesteuerte Support, wenn Sie im Menü angezeigt.<br /><br /> Ein Befehl im Menü Trennschaltfläche wird auf die Schaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> -   Es ist mit dem letzten Befehl, der verwendet wurde, wenn der Befehl weiterhin angezeigt und aktiviert ist.<br />-   Es ist der erste Befehl angezeigt.<br /><br /> MenuControllerLatched<br /> Bietet eine Trennschaltfläche Dropdown\-Menü für die ein Befehl als Standardauswahl angegeben werden kann, indem Sie den Befehl als aktiviert gekennzeichnet.<br /><br /> Ein gesperrtes Befehl ist ein Befehl, der im Menü ausgewählt, in der Regel markiert ist, indem ein Häkchen angezeigt. Ein Befehl kann gekennzeichnet werden, wie aktiviert, verfügt die OLECMDF\_LATCHED flag festgelegt, es in einer Implementierung von der `QueryStatus` Methode der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Ein MenuControllerLatched hat die folgenden Merkmale:<br /><br /> -   Muss in einem anderen Menü über eine übergeordnete Gruppe oder CommandPlacement enthalten sein.<br />-   Das übergeordnete Element in der Definition wird berücksichtigt.<br />-   Kann jede Art von Menü als übergeordnetes Element haben.<br />-   Wird zur Verfügung gestellt, wenn die übergeordneten Menü angezeigt wird.<br />-   Erfordert keine programmgesteuerte Support, wenn Sie im Menü angezeigt.<br /><br /> Ein Befehl im Menü Trennschaltfläche wird auf die Schaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> -   Es ist der erste angezeigte Befehl, der aktiviert ist.<br />-   Es ist der erste Befehl angezeigt.<br /><br /> Symbolleiste<br /> Eine Symbolleiste bereitgestellt. Eine Symbolleiste weist folgende Merkmale auf:<br /><br /> -   Das übergeordnete Element in der Definition wird ignoriert.<br />-   Kann ein Untermenü keiner Gruppe auch mithilfe von CommandPlacement gemacht werden.<br />-   Können immer angezeigt werden, indem Sie auf **Symbolleisten** auf der **Ansicht** Menü.<br />-   Können angezeigt werden, indem eine [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis).<br />-   Erfordert keine Code zu erstellen. Ein Beispiel dazu, wie Sie eine Symbolleiste erstellen, finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Enthält eine Symbolleiste, die einem bestimmten Toolfenster, zugeordnet ist, wie eine Symbolleiste mit der Development\-Umgebung verbunden ist.<br /><br /> -   Das übergeordnete Element in der Definition wird ignoriert.<br />-   Kann ein Untermenü keiner Gruppe auch mithilfe von CommandPlacement gemacht werden.<br />-   Wird nur angezeigt, wenn das Toolfenster, das die Symbolleiste enthält wird angezeigt, und das VSPackage explizit der Symbolleiste auf das Toolfenster fügt. Dies erfolgt normalerweise, wenn das Toolfenster erstellt wird, erhalten Sie die Toolbar\-Host\-Eigenschaft \(dargestellt durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> Schnittstelle\) aus der Toolfenster, Rahmen und zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> Methode.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Übergeordnetes Element|Optional. Das übergeordnete Element des Menüelements.|  
|CommandFlag|Erforderlich. Siehe [Command\-Flag\-Element](../extensibility/command-flag-element.md). Gültige Werte für ein Menü CommandFlag sind wie folgt:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-dieses Flag hat keine Auswirkung auf die Anzeige der Symbolleisten.<br />-   **DontCache**<br />-   **DynamicVisibility** \-dieses Flag hat keine Auswirkung auf die Anzeige der Symbolleisten.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextÄndert**<br />-   **TextIsAnchorCommand**|  
|Zeichenfolgen|Erforderlich. Siehe [Zeichenfolgen\-Element](../extensibility/strings-element.md). Das untergeordnete Element `ButtonText` Element definiert werden muss.|  
|Anmerkung|Optionaler Kommentar.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Menüs\-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|  
  
## Beispiel  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)