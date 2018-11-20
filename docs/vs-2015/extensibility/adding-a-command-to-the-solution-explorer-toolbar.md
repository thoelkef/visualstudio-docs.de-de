---
title: Hinzufügen eines Befehls zur Symbolleiste Projektmappen-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52e963a202d75c29c65521729e70e062a579d479
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753646"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Hinzufügen eines Befehls zur Symbolleiste des Projektmappen-Explorers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine Schaltfläche zum Hinzufügen der **Projektmappen-Explorer** Symbolleiste.  
  
 Jeder Befehl in einer Symbolleiste oder jedem Menü wird eine Schaltfläche in Visual Studio aufgerufen werden. Wenn die Schaltfläche geklickt wird, wird der Code in den Befehlshandler ausgeführt. In der Regel sind verwandte Befehle gruppiert, um eine Gruppe zu bilden. Menüs oder Symbolleisten fungieren als Container für Gruppen. Priorität bestimmt die Reihenfolge, in der einzelnen Befehle in einer Gruppe im Menü oder auf der Symbolleiste angezeigt werden. Sie können verhindern, dass eine Schaltfläche auf der Symbolleiste oder im Menü angezeigt wird, indem Sie deren Sichtbarkeit steuern. Ein Befehl, der in aufgelistet ist eine `<VisibilityConstraints>` Abschnitt der VSCT-Datei wird nur in den zugeordneten Kontext angezeigt. Die Sichtbarkeit kann nicht auf Gruppen angewendet werden.  
  
 Weitere Informationen über die Menüs, Befehle und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Verwenden Sie XML-Command Table (.vsct)-Dateien anstelle von Befehlsdateien Tabelle-Konfigurationsdatei (.ctc) definieren, wie Menüs und Befehle in Ihre VSPackages angezeigt werden. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl  
 Erstellen Sie ein VSIX-Projekt mit dem Namen `SolutionToolbar`. Fügen Sie eine Elementvorlage der Menü-Befehl mit dem Namen **ToolbarButton**. Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Hinzufügen einer Schaltfläche auf der Symbolleiste des Projektmappen-Explorer  
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie eine Schaltfläche zum Hinzufügen der **Projektmappen-Explorer** Symbolleiste. Wenn die Schaltfläche geklickt wird, wird der Code in der Rückrufmethode ausgeführt.  
  
1.  Wechseln Sie in der Datei ToolbarButtonPackage.vsct zu den `<Symbols>` Abschnitt. Die `<GuidSymbol>` Knoten enthält die Gruppe und der Befehl, der durch die Paket-Vorlage generiert wurde. Hinzufügen einer `<IDSymbol>` Element auf diesen Knoten aus, um die Gruppe zu deklarieren, der den Befehl enthält.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  In der `<Groups>` Abschnitt nach den vorhandenen Gruppeneintrag definieren, die neue Gruppe, die Sie deklariert haben im vorherigen Schritt.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Festlegen des GUID: ID-Paar für das übergeordnete Element `guidSHLMainMenu` und `IDM_VS_TOOL_PROJWIN` legt dieser Gruppe auf die **Projektmappen-Explorer** Symbolleiste, und eine wichtige Einstellung nach dem anderen Befehlsgruppen eingefügt.  
  
3.  In der `<Buttons>` Abschnitt, ändern Sie die übergeordnete ID der generierten `<Button>` einen Eintrag in der Gruppe anzugeben, die Sie im vorherigen Schritt definiert. Die geänderte `<Button>` -Element sollte wie folgt aussehen:  
  
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
  
     Die **Projektmappen-Explorer** Symbolleiste sollte die neue Schaltfläche rechts neben der vorhandenen Schaltflächen angezeigt. Das Symbol "Schaltfläche" ist die durchgestrichen.  
  
5.  Klicken Sie auf die Schaltfläche "Neu".  
  
     Ein Dialogfeld mit der Nachricht **ToolbarButtonPackage in SolutionToolbar.ToolbarButton.MenuItemCallback()** angezeigt werden soll.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Steuern der Sichtbarkeit einer Schaltfläche  
 In diesem Abschnitt der exemplarischen Vorgehensweise veranschaulicht, wie die Sichtbarkeit einer Schaltfläche auf einer Symbolleiste steuern. Durch Festlegen eines Kontexts auf einen oder mehrere Projekte in der `<VisibilityConstraints>` Abschnitt der Datei SolutionToolbar.vsct, beschränken Sie eine Schaltfläche angezeigt werden, nur wenn ein Projekt geöffnet sind.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Zur Anzeige einer Schaltfläche, wenn ein oder mehrere Projekte geöffnet sind.  
  
1. In der `<Buttons>` Abschnitt der ToolbarButtonPackage.vsct, fügen Sie zwei Befehlsflags hinzu, mit dem vorhandenen `<Button>` Element, das zwischen der `<Strings>` und `<Icons>` Tags.  
  
   ```xml  
   <CommandFlag>DefaultInvisible</CommandFlag>  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
    Die `DefaultInvisible` und `DynamicVisibility` Flags müssen festgelegt werden, also diese Einträge in der `<VisibilityConstraints>` Abschnitt wirksam werden kann.  
  
2. Erstellen Sie eine `<VisibilityConstraints>` -Abschnitt, der zwei `<VisibilityItem>` Einträge. Fügen den neuen Abschnitt direkt hinter dem schließenden `</Commands>` Tag.  
  
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
  
    Jedes Visibility-Element stellt eine Bedingung, unter der die angegebene Schaltfläche angezeigt wird. Um mehrere Bedingungen erfüllt sind, müssen Sie mehrere Einträge für die gleiche Schaltfläche erstellen.  
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
    Die **Projektmappen-Explorer** Symbolleiste enthält nicht die Schaltfläche "durchgestrichen".  
  
4. Öffnen Sie jede Lösung, die ein Projekt enthält.  
  
    Die Schaltfläche "durchgestrichen" wird auf der Symbolleiste rechts neben der vorhandenen Schaltflächen angezeigt.  
  
5. Auf der **Datei** Menü klicken Sie auf **Projektmappe schließen**. Die Schaltfläche wird über die Symbolleiste ausgeblendet.  
  
   Die Sichtbarkeit der Schaltfläche wird gesteuert, indem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bis das VSPackage geladen wird. Nachdem das VSPackage geladen wurde, wird die Sichtbarkeit der Schaltfläche durch das VSPackage gesteuert.  Weitere Informationen finden Sie unter [MenuCommands im Vergleich. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)

