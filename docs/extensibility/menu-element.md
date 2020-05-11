---
title: Menüelement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702599"
---
# <a name="menu-element"></a>Menüelement
Definiert ein Menüelement. Dies sind die sechs Arten von Menüs: Kontext, Menü, MenuController, MenuControllerLatched, Toolbar und ToolWindowToolbar.

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

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehlsbezeichners GUID/ID.|
|id|Erforderlich. ID des BEFEHLsbezeichners GUID/ID.|
|priority|Optional. Ein numerischer Wert, der die relative Position eines Menüs in einer Gruppe von Menüs angibt.|
|ToolbarPriorityInBand|Optional. Ein numerischer Wert, der die relative Position einer Symbolleiste in einem Band angibt, wenn das Fenster angedockt wird.|
|type|Optional. Ein aufgezählter Wert, der die Art des Elements angibt.<br /><br /> Wenn nicht vorhanden, ist der Standardtyp Menü.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer mit der rechten Maustaste auf ein Fenster klickt. Ein Kontextmenü weist die folgenden Merkmale auf:<br /><br /> - Verwendet nicht die **Felder "Eltern"** und **"Priorität",** wenn das Menü als Kontextmenü angezeigt werden soll.<br />- Kann als Untermenü und auch als Shortcut-Menü verwendet werden. In diesem Fall werden sowohl **die Gruppen-ID** als auch die **Prioritätsfelder** respektiert.<br />- Ist nicht immer verfügbar.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn die folgenden Bedingungen zutreffen:<br /><br /> - Das Fenster, in dem es gehostet wird, wird angezeigt.<br />- Ein Maushandler im VSPackage erkennt einen Rechtsklick auf das Fenster und ruft dann eine Methode auf, die den Befehl verarbeitet.<br />- Das Kontextmenü wird <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> angezeigt, indem die Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> (der empfohlene Ansatz) oder die Methode aufgerufen wird.<br /><br /> Menü<br /> Stellt ein Dropdown-Menü bereit. Ein Dropdown-Menü weist folgende Merkmale auf:<br /><br /> - Respektiert die Eltern in ihrer Definition.<br />- Muss eine übergeordnete Gruppe oder eine CommandPlacement zu einer Gruppe haben.<br />- Kann ein Untermenü in jeder anderen Art von Menü sein.<br />- Wird automatisch angezeigt, wenn das übergeordnete Menü angezeigt wird.<br />- Erfordert keine Implementierung von VSPackage-Code, um ihn angezeigt zu machen.<br /><br /> MenuController<br /> Stellt ein Dropdown-Menü mit geteilten Schaltflächen bereit, das in der Regel in Symbolleisten verwendet wird. Ein MenuController-Menü weist die folgenden Merkmale auf:<br /><br /> - Muss in einem anderen Menü über Parent oder CommandPlacement enthalten sein.<br />- Respektiert die Eltern in ihrer Definition.<br />- Kann jede Art von Menü als übergeordnete.<br />- Wird automatisch zur Verfügung gestellt, wenn das übergeordnete Menü angezeigt wird.<br />- Erfordert keine programmgesteuerte Unterstützung, um das Menü anzuzeigen.<br /><br /> Ein Befehl aus dem Menü mit split-button wird auf der Menüschaltfläche angezeigt. Der angezeigte Befehl weist eines der folgenden Merkmale auf:<br /><br /> - Es ist der letzte Befehl, der verwendet wurde, wenn der Befehl noch angezeigt und aktiviert ist.<br />- Es ist der erste angezeigte Befehl.<br /><br /> MenuControllerLatched<br /> Stellt ein Dropdown-Menü mit geteilten Schaltflächen bereit, für das ein Befehl als Standardauswahl angegeben werden kann, indem der Befehl als gesperrt markiert wird.<br /><br /> Ein gesperrter Befehl ist ein Befehl, der im Menü als ausgewählt markiert ist, in der Regel durch Anzeigen eines Häkchens. Ein Befehl kann als gesperrt markiert werden, wenn in einer Implementierung `QueryStatus` der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Methode der Schnittstelle das OLECMDF_LATCHED-Flag darauf gesetzt ist. Ein MenuControllerLatched-Menü weist die folgenden Eigenschaften auf:<br /><br /> - Muss in einem anderen Menü über eine übergeordnete Gruppe oder CommandPlacement enthalten sein.<br />- Respektiert die Eltern in ihrer Definition.<br />- Kann jede Art von Menü als übergeordnete.<br />- Wird zur Verfügung gestellt, wenn das übergeordnete Menü angezeigt wird.<br />- Erfordert keine programmgesteuerte Unterstützung, um das Menü anzuzeigen.<br /><br /> Ein Befehl aus dem Menü mit split-button wird auf der Menüschaltfläche angezeigt. Der angezeigte Befehl weist eines der folgenden Merkmale auf:<br /><br /> - Es ist der erste angezeigte Befehl, der gesperrt ist.<br />- Es ist der erste angezeigte Befehl.<br /><br /> Symbolleiste<br /> Stellt eine Symbolleiste bereit. Eine Symbolleiste weist die folgenden Eigenschaften auf:<br /><br /> - Ignoriert das Übergeordnete in seiner Definition.<br />- Kann nicht zu einem Untermenü einer Gruppe gemacht werden, auch nicht mit CommandPlacement.<br />- Kann immer angezeigt **werden,** indem Sie im Menü **Ansicht** auf Symbolleisten klicken.<br />- Kann mit einem [VisibilityItem](../extensibility/visibilityitem-element.md)angezeigt werden.<br />- Erfordert keinen Code, um ihn zu erstellen. Ein Beispiel zum Erstellen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Stellt eine Symbolleiste bereit, die an ein bestimmtes Werkzeugfenster angefügt ist, genau wie eine Symbolleiste an die Entwicklungsumgebung angefügt ist.<br /><br /> - Ignoriert das Übergeordnete in seiner Definition.<br />- Kann nicht zu einem Untermenü einer Gruppe gemacht werden, auch nicht mit CommandPlacement.<br />- Wird nur angezeigt, wenn das Toolfenster, in dem die Symbolleiste gehostet wird, angezeigt wird und das VSPackage dem Toolfenster explizit die Symbolleiste hinzufügt. Dies geschieht in der Regel, wenn das Toolfenster erstellt wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> indem die Symbolleistenhosteigenschaft (wie durch die Schnittstelle dargestellt) aus dem Werkzeugfensterrahmen abruft und dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> Methode aufruft.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent|Optional. Das übergeordnete Element des Menüelements.|
|CommandFlag|Erforderlich. Siehe [Befehlsflag-Element](../extensibility/command-flag-element.md). Die gültigen CommandFlag-Werte für ein Menü lauten wie folgt:<br /><br /> -   **Alwayscreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** - Dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten aus.<br />-   **DontCache**<br />-   **DynamicVisibility** - Dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten aus.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextÄnderungen**<br />-   **TextIsAnchorCommand**|
|Zeichenfolgen|Erforderlich. Siehe [Strings-Element](../extensibility/strings-element.md). Das `ButtonText` untergeordnete Element muss definiert werden.|
|Anmerkung|Optionaler Kommentar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|

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

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabelle (.vsct) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
