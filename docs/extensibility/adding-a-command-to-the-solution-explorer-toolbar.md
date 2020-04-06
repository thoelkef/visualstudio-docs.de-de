---
title: Hinzufügen eines Befehls zur Projektmappen-Toolleiste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740335"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Hinzufügen eines Befehls zur Symbolleiste des Projektmappen-Explorers
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie der Symbolleiste des **Projektmappen-Explorers** eine Schaltfläche hinzufügen.

 Jeder Befehl auf einer Symbolleiste oder einem Menü wird in Visual Studio als Schaltfläche bezeichnet. Wenn auf die Schaltfläche geklickt wird, wird der Code im Befehlshandler ausgeführt. In der Regel werden verwandte Befehle zu einer Gruppe gruppiert. Menüs oder Symbolleisten dienen als Container für Gruppen. Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü oder auf der Symbolleiste angezeigt werden. Sie können verhindern, dass eine Schaltfläche auf der Symbolleiste oder im Menü angezeigt wird, indem Sie die Sichtbarkeit steuern. Ein Befehl, der `<VisibilityConstraints>` in einem Abschnitt der *.vsct-Datei* aufgeführt ist, wird nur im zugeordneten Kontext angezeigt. Die Sichtbarkeit kann nicht auf Gruppen angewendet werden.

 Weitere Informationen zu Menüs, Symbolleistenbefehlen und *.vsct-Dateien* finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Verwenden Sie XML-Befehlstabellendateien (*.vsct*) Dateien anstelle der Befehlstabellenkonfiguration (*.ctc*) Dateien, um zu definieren, wie Menüs und Befehle in Ihren VSPackages angezeigt werden. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabelle (. Vsct)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
 Erstellen Sie ein `SolutionToolbar`VSIX-Projekt mit dem Namen . Fügen Sie eine Menübefehlselementvorlage mit dem Namen **ToolbarButton**hinzu. Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Hinzufügen einer Schaltfläche zur Symbolleiste des Projektmappen-Explorers
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie Sie der Symbolleiste des **Projektmappen-Explorers** eine Schaltfläche hinzufügen. Wenn auf die Schaltfläche geklickt wird, wird der Code in der Rückrufmethode ausgeführt.

1. Wechseln Sie in der Datei *ToolbarButtonPackage.vsct* zum `<Symbols>` Abschnitt. Der `<GuidSymbol>` Knoten enthält die Menügruppe und den Befehl, die von der Paketvorlage generiert wurden. Fügen `<IDSymbol>` Sie diesem Knoten ein Element hinzu, um die Gruppe zu deklarieren, die Ihren Befehl enthält.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Definieren `<Groups>` Sie im Abschnitt nach dem vorhandenen Gruppeneintrag die neue Gruppe, die Sie im vorherigen Schritt deklariert haben.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Wenn Sie das übergeordnete GUID:ID-Paar auf `guidSHLMainMenu` die Symbolleiste des `IDM_VS_TOOL_PROJWIN` **Projektmappen-Explorers** festlegen und diese Gruppe auf diese Gruppe setzen und einen Wert mit hoher Priorität festlegen, wird es hinter den anderen Befehlsgruppen gesetzt.

3. Ändern `<Buttons>` Sie im Abschnitt die übergeordnete `<Button>` ID des generierten Eintrags, um die Gruppe widerzuspiegeln, die Sie im vorherigen Schritt definiert haben. Das `<Button>` geänderte Element sollte wie folgt aussehen:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

     In der **Symbolleiste des Projektmappen-Explorers** sollte die neue Befehlsschaltfläche rechts neben den vorhandenen Schaltflächen angezeigt werden. Das Schaltflächensymbol ist der Durchschlag.

5. Klicken Sie auf die neue Schaltfläche.

     Ein Dialogfeld mit der Meldung **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** sollte angezeigt werden.

## <a name="control-the-visibility-of-a-button"></a>Steuern der Sichtbarkeit einer Schaltfläche
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie Sie die Sichtbarkeit einer Schaltfläche auf einer Symbolleiste steuern. Indem Sie einen Kontext auf ein `<VisibilityConstraints>` oder mehrere Projekte im Abschnitt der *Datei SolutionToolbar.vsct* festlegen, schränken Sie eine Schaltfläche darauf ein, dass sie nur angezeigt wird, wenn ein Projekt oder Projekte geöffnet sind.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>So zeigen Sie eine Schaltfläche an, wenn ein oder mehrere Projekte geöffnet sind

1. Fügen `<Buttons>` Sie im Abschnitt *von ToolbarButtonPackage.vsct*dem `<Button>` vorhandenen Element `<Strings>` `<Icons>` zwei Befehlsflags zwischen den und-Tags hinzu.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Die `DefaultInvisible` `DynamicVisibility` und Flags müssen so gesetzt `<VisibilityConstraints>` werden, dass Einträge im Abschnitt wirksam werden können.

2. Erstellen `<VisibilityConstraints>` Sie einen `<VisibilityItem>` Abschnitt mit zwei Einträgen. Setzen Sie den neuen `</Commands>` Abschnitt direkt nach dem schließenden Tag.

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

    Jedes Sichtbarkeitselement stellt eine Bedingung dar, unter der die angegebene Schaltfläche angezeigt wird. Um mehrere Bedingungen anzuwenden, müssen Sie mehrere Einträge für dieselbe Schaltfläche erstellen.

3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

    Die **Symbolleiste des Projektmappen-Explorers** enthält nicht die Durchstreichen-Schaltfläche.

4. Öffnen Sie jede Projektmappe, die ein Projekt enthält.

    Die Durchschlagsschaltfläche wird auf der Symbolleiste rechts neben den vorhandenen Schaltflächen angezeigt.

5. Klicken Sie im Menü **Datei** auf **Projektmappe schließen**. Die Schaltfläche verschwindet aus der Symbolleiste.

   Die Sichtbarkeit der Schaltfläche [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird durch gesteuert, bis das VSPackage geladen wird. Nach dem Laden des VSPackage wird die Sichtbarkeit der Schaltfläche durch das VSPackage gesteuert.  Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
