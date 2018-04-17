---
title: Hinzufügen eines Befehls auf der Symbolleiste des Projektmappen-Explorer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6f732900ff3e73decb1dc01d5c131e26ba50669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Hinzufügen eines Befehls auf der Symbolleiste des Projektmappen-Explorers
In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine Schaltfläche zum Hinzufügen der **Projektmappen-Explorer** Symbolleiste.  
  
 Jeder Befehl in einer Symbolleiste oder im Menü wird eine Schaltfläche in Visual Studio aufgerufen werden. Wenn die Schaltfläche geklickt wird, wird der Code im Befehlshandler ausgeführt. In der Regel sind verwandte Befehle gruppiert, um eine Gruppe zu bilden. Menüs oder Symbolleisten fungieren als Container für Gruppen. Die Priorität wird bestimmt die Reihenfolge, in der einzelnen Befehle in einer Gruppe im Menü oder auf der Symbolleiste angezeigt werden. Sie können verhindern, dass eine Schaltfläche auf der Symbolleiste oder im Menü angezeigt wird, indem Sie seine Sichtbarkeit zu steuern. Ein Befehl, der in aufgeführt ist ein `<VisibilityConstraints>` Abschnitt der VSCT-Datei wird nur in den zugeordneten Kontext angezeigt. Die Sichtbarkeit kann nicht auf Gruppen angewendet werden.  
  
 Weitere Informationen über die Menüs, Befehle und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Verwenden Sie XML-Befehlstabelle (VSCT) Dateien anstelle Befehl Tabelle Konfigurationsdateien (ctc) definieren, wie Menüs und Befehle in Ihre VSPackages angezeigt werden. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Erstellen eine Erweiterung mit einem Menübefehl  
 Erstellen Sie ein VSIX-Projekt mit dem Namen `SolutionToolbar`. Hinzufügen eine Menü Befehl Elementvorlage, die mit dem Namen **ToolbarButton**. Informationen hierzu finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Hinzufügen einer Schaltfläche auf der Symbolleiste des Projektmappen-Explorers  
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie eine Schaltfläche zum Hinzufügen der **Projektmappen-Explorer** Symbolleiste. Wenn die Schaltfläche geklickt wird, wird der Code in die Rückrufmethode ausgeführt.  
  
1.  Wechseln Sie in der Datei ToolbarButtonPackage.vsct zu den `<Symbols>` Abschnitt. Die `<GuidSymbol>` Knoten enthält die Menügruppe und der Befehl, der durch die Paket-Vorlage generiert wurde. Hinzufügen einer `<IDSymbol>` Element auf diesen Knoten, um die Gruppe zu deklarieren, die den Befehl enthalten soll.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  In der `<Groups>` Abschnitt nach der vorhandenen Gruppe-Eintrag, definieren Sie die neue Gruppe, die Sie deklariert im vorherigen Schritt.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Wenn das übergeordnete Element GUID: ID-Paar auf `guidSHLMainMenu` und `IDM_VS_TOOL_PROJWIN` legt dieser Gruppe auf die **Projektmappen-Explorer** Symbolleiste und das Festlegen eines Werts hoher Priorität nach der anderen Befehlsgruppen eingefügt.  
  
3.  In der `<Buttons>` Abschnitt, ändern Sie die ID des übergeordneten Elements der generierten `<Button>` Eintrag entsprechend die Gruppe, die Sie im vorherigen Schritt definiert. Das geänderte `<Button>` -Element sollte wie folgt aussehen:  
  
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
  
     Die **Projektmappen-Explorer** Symbolleiste sollte die neue Schaltfläche rechts neben der vorhandenen Schaltflächen anzeigen. Symbol "Bildschaltfläche" ist die durchgestrichen.  
  
5.  Klicken Sie auf die Schaltfläche "Neu".  
  
     Ein Dialogfeld, das die Nachricht hat **ToolbarButtonPackage in SolutionToolbar.ToolbarButton.MenuItemCallback()** angezeigt werden soll.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Steuerung der Sichtbarkeit einer Schaltfläche  
 In diesem Abschnitt der exemplarischen Vorgehensweise veranschaulicht, wie die Sichtbarkeit einer Schaltfläche auf einer Symbolleiste steuern. Durch Festlegen von einem Kontext auf ein oder mehrere Projekte in der `<VisibilityConstraints>` Abschnitt der Datei SolutionToolbar.vsct, beschränken Sie eine Schaltfläche angezeigt werden, nur wenn ein Projekt oder Projekte geöffnet sind.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Eine Schaltfläche angezeigt, wenn ein oder mehrere Projekte geöffnet sind.  
  
1.  In der `<Buttons>` Abschnitt der ToolbarButtonPackage.vsct, fügen Sie zwei Befehlsflags hinzu, um die vorhandene `<Button>` Element, das zwischen den `<Strings>` und `<Icons>` Tags.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     Die `DefaultInvisible` und `DynamicVisibility` Flags müssen festgelegt werden, damit diese Einträge in der `<VisibilityConstraints>` Abschnitt wirksam.  
  
2.  Erstellen einer `<VisibilityConstraints>` -Abschnitt, der zwei `<VisibilityItem>` Einträge. Platzieren den neuen Abschnitt unmittelbar nach dem schließenden `</Commands>` Tag.  
  
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
  
     Jedes Visibility-Element stellt eine Bedingung, unter der die angegebene Schaltfläche angezeigt wird. Um mehrere Bedingungen zu übernehmen, müssen Sie mehrere Einträge für die gleiche Schaltfläche erstellen.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
     Die **Projektmappen-Explorer** Symbolleiste enthält nicht die Schaltfläche "durchgestrichen".  
  
4.  Öffnen Sie eine beliebige Projektmappe, die ein Projekt enthält.  
  
     Die Schaltfläche "durchgestrichen" wird auf der Symbolleiste auf die rechts neben der vorhandenen Schaltflächen angezeigt.  
  
5.  Auf der **Datei** Menü klicken Sie auf **Projektmappe schließen**. Die Schaltfläche wird über die Symbolleiste ausgeblendet.  
  
 Die Sichtbarkeit der Schaltfläche wird gesteuert, indem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bis VSPackage geladen wurde. Nachdem das VSPackage geladen wurde, wird die Sichtbarkeit der Schaltfläche durch das VSPackage gesteuert.  Weitere Informationen finden Sie unter [MenuCommand-und. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)