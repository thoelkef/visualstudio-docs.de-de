---
title: Hinzufügen einer Symbolleiste zu einem Toolfenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 646384f43a6196bca802998b709285c247e4c378
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843838"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Hinzufügen einer Symbolleiste zu einem Toolfenster
Diese exemplarische Vorgehensweise zeigt, wie ein Toolfenster eine Symbolleiste hinzugefügt wird.

 Eine Symbolleiste ist eine horizontale oder vertikale entfernen, die Schaltflächen auf Befehle gebunden sind. Die Länge einer Symbolleiste in einem Toolfenster ist immer identisch mit die Breite oder Höhe des Toolfensters, je nachdem, wo die Symbolleiste angedockt wird.

 Im Gegensatz zu den Symbolleisten in der IDE muss eine Symbolleiste in einem Toolfenster angedockt werden kann nicht verschoben oder angepasst. Wenn das VSPackage in Umanaged Code geschrieben ist, kann die Symbolleiste auf keinem Rand angedockt werden.

 Weitere Informationen zum Hinzufügen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Erstellen Sie eine Symbolleiste für ein Toolfenster

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TWToolbar` , die beide einen Menübefehl, mit dem Namen hat **TWTestCommand** und ein Toolfenster namens **TestToolWindow**. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) und [erstellen Sie eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Sie müssen die Elementvorlage für den Befehl vor dem Hinzufügen der Tool-Fenster-Vorlage hinzufügen.

2. In *TWTestCommandPackage.vsct*, suchen Sie nach dem Abschnitt "Symbols". Deklarieren Sie im Knoten "GuidSymbol" mit dem Namen GuidTWTestCommandPackageCmdSet wie folgt eine Symbolleiste und einer Symbolleistengruppe.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Am oberen Rand der `Commands` Abschnitt, erstellen Sie eine `Menus` Abschnitt. Hinzufügen einer `Menu` Element, um die Symbolleiste zu definieren.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Symbolleisten können nicht geschachtelt werden, wie die Untermenüs. Aus diesem Grund müssen Sie ein übergeordnetes Element zuweisen. Darüber hinaus müssen Sie eine Priorität festlegen, da der Benutzer die Symbolleisten wechseln kann. In der Regel anfängliche Platzierung einer Symbolleiste programmgesteuert definiert ist, aber nachfolgende Änderungen durch den Benutzer beibehalten werden.

4. Definieren Sie im Abschnitt Gruppen eine Gruppe, um die Befehle für die Symbolleiste enthalten.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Ändern Sie im Abschnitt "Schaltflächen" das übergeordnete Element des vorhandenen Button-Element auf der Symbolleistengruppe, sodass die Symbolleiste angezeigt wird.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     In der Standardeinstellung Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.

     Da die neue Symbolleiste im Toolfenster nicht automatisch hinzugefügt wird, muss die Symbolleiste explizit hinzugefügt werden. Dies wird im nächsten Abschnitt erläutert.

## <a name="add-the-toolbar-to-the-tool-window"></a>Fügen Sie die Symbolleiste hinzu, um das Toolfenster

1. In *TWTestCommandPackageGuids.cs* fügen Sie die folgenden Zeilen hinzu.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. In *TestToolWindow.cs* fügen Sie die folgenden using-Anweisung.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. Fügen Sie im Konstruktor TestToolWindow die folgende Zeile hinzu.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testen Sie die Symbolleiste im Toolfenster

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

2. Auf der **anzeigen / Other Windows** Menü klicken Sie auf **Test ToolWindow** das Toolfenster angezeigt.

     Sollte angezeigt werden, dass eine Symbolleiste mit der (anscheinend das Standardsymbol) am oberen Rand des Toolfensters, direkt unterhalb des Titels links.

3. Klicken Sie auf der Symbolleiste auf das Symbol, um die Anzeige der **TWTestCommandPackage in TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Siehe auch
- [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)