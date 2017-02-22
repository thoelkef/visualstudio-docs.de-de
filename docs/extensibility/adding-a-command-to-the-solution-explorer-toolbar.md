---
title: "Hinzuf&#252;gen eines Befehls auf der Symbolleiste des Projektmappen-Explorers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbolleisten [Visual Studio], Hinzufügen von Schaltflächen"
  - "Schaltflächen [Visual Studio], dem Projektmappen-Explorer hinzufügen"
  - "Projektmappen-Explorer das Hinzufügen von Schaltflächen"
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 39
caps.handback.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
---
# Hinzuf&#252;gen eines Befehls auf der Symbolleiste des Projektmappen-Explorers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie eine Schaltfläche zum Hinzufügen der **Projektmappen\-Explorer** Symbolleiste.  
  
 Alle Befehle auf Symbolleisten oder Menüs ist eine Schaltfläche in Visual Studio aufgerufen. Wenn die Schaltfläche geklickt wird, wird der Code in den Befehlshandler ausgeführt. In der Regel werden verwandte Befehle gruppiert, um eine Gruppe zu bilden. Menüs oder Symbolleisten fungieren als Container für Gruppen. Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü oder auf der Symbolleiste angezeigt werden. Sie können verhindern, dass eine Schaltfläche auf der Symbolleiste oder im Menü angezeigt wird, durch dessen Sichtbarkeit zu steuern. Ein Befehl, der im aufgelistet ist ein `<VisibilityConstraints>` \-Abschnitt der VSCT\-Datei wird nur in der zugeordneten Kontext angezeigt. Die Sichtbarkeit kann auf Gruppen angewendet werden.  
  
 Weitere Informationen zu den Menüs, Befehle und VSCT\-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Verwenden Sie XML\-Befehl \(VSCT\) Dateien anstelle Befehl Tabelle Konfigurationsdateien \(.ctc\) definieren, wie Menüs und Befehlen in Ihrem VSPackages angezeigt werden. Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eine Erweiterung mit einem Menübefehl  
 Erstellen Sie ein VSIX\-Projekt namens `SolutionToolbar`. Hinzufügen eine Menü Befehl Elementvorlage, die mit dem Namen **ToolbarButton**. Informationen hierzu finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Hinzufügen einer Schaltfläche auf der Symbolleiste des Projektmappen\-Explorers  
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie eine Schaltfläche zum Hinzufügen der **Projektmappen\-Explorer** Symbolleiste. Wenn die Schaltfläche geklickt wird, wird der Code in der Rückrufmethode ausgeführt.  
  
1.  Wechseln Sie in der Datei ToolbarButtonPackage.vsct zu den  `<Symbols>` Abschnitt. Die `<GuidSymbol>`  Knoten enthält die Gruppe und den Befehl, der von der Paketvorlage generiert wurde. Hinzufügen einer `<IDSymbol>` Element auf diesen Knoten, um die Gruppe zu deklarieren, die den Befehl enthält.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  In der `<Groups>` Abschnitt nach der vorhandenen Gruppe Eintrag, definieren Sie die neue Gruppe, die Sie deklariert im vorherigen Schritt.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Festlegen der übergeordneten GUID:ID Paar auf `guidSHLMainMenu` und `IDM_VS_TOOL_PROJWIN` werden dieser Gruppe auf die **Projektmappen\-Explorer** Symbolleiste und eine wichtige Einstellung fügt Sie es nach dem anderen Befehlsgruppen.  
  
3.  In der `<Buttons>` im Abschnitt, ändern Sie die übergeordnete ID des generierten `<Button>` Eintrag, um die Gruppe anzugeben, die Sie im vorherigen Schritt definiert. Die geänderte `<Button>` \-Element sollte wie folgt aussehen:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
     Die **Projektmappen\-Explorer** Symbolleiste sollte die neue Schaltfläche rechts neben der vorhandenen Schaltflächen angezeigt. Das Symbol für ist die durchgestrichen.  
  
5.  Klicken Sie auf die Schaltfläche "Neu".  
  
     Ein Dialogfeld mit der Meldung **ToolbarButtonPackage in SolutionToolbar.ToolbarButton.MenuItemCallback\(\)** angezeigt werden soll.  
  
## Steuern der Sichtbarkeit einer Schaltfläche  
 In diesem Abschnitt der exemplarischen Vorgehensweise veranschaulicht, wie die Sichtbarkeit der Schaltfläche auf einer Symbolleiste steuern. Indem Sie einen Kontext auf ein oder mehrere Projekte in der `<VisibilityConstraints>` Abschnitt der Datei SolutionToolbar.vsct, beschränken Sie eine Schaltfläche angezeigt werden, nur wenn ein Projekt oder Projekte geöffnet sind.  
  
#### Eine Schaltfläche angezeigt, wenn ein oder mehrere Projekte geöffnet sind.  
  
1.  In der `<Buttons>` Abschnitt fügen Sie der ToolbarButtonPackage.vsct, zwei Befehlsflags den vorhandenen `<Button>` Element, zwischen der `<Strings>` und `<Icons>` Tags.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     Die `DefaultInvisible` und `DynamicVisibility` Flags müssen festgelegt werden, also diese Einträge in der `<VisibilityConstraints>` Abschnitt wirksam.  
  
2.  Erstellen Sie eine `<VisibilityConstraints>` \-Abschnitt, der zwei `<VisibilityItem>` Einträge. Setzen den neuen Abschnitt unmittelbar nach dem schließenden `</Commands>` Tag.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Jedes Visibility\-Element stellt eine Bedingung, unter der die angegebene Schaltfläche angezeigt wird. Um mehrere zutrifft, müssen Sie mehrere Einträge für die gleiche Schaltfläche erstellen.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
     Die **Projektmappen\-Explorer** Symbolleiste enthält nicht die Schaltfläche "durchgestrichen".  
  
4.  Öffnen Sie eine Projektmappe, die ein Projekt enthält.  
  
     Die Schaltfläche "durchgestrichen" wird auf der Symbolleiste neben der vorhandenen Schaltflächen angezeigt.  
  
5.  Auf der **Datei** Menü klicken Sie auf **Projektmappe schließen**. Die Schaltfläche wird über die Symbolleiste ausgeblendet.  
  
 Die Sichtbarkeit der Schaltfläche wird gesteuert, von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bis das VSPackage geladen wird. Nachdem das VSPackage geladen wurde, wird die Sichtbarkeit der Schaltfläche durch das VSPackage gesteuert.  Weitere Informationen finden Sie unter [MenuCommand\- und OleMenuCommand\-Objekte](../misc/menucommands-vs-olemenucommands.md).  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)