---
title: Hinzufügen einer Symbolleiste zu einem Werkzeugfenster | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740249"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Hinzufügen einer Symbolleiste zu einem Toolfenster
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einem Werkzeugfenster eine Symbolleiste hinzufügen.

 Eine Symbolleiste ist ein horizontaler oder vertikaler Streifen, der Schaltflächen enthält, die an Befehle gebunden sind. Die Länge einer Symbolleiste in einem Werkzeugfenster entspricht immer der Breite oder Höhe des Werkzeugfensters, je nachdem, wo die Symbolleiste angedockt ist.

 Im Gegensatz zu Symbolleisten in der IDE muss eine Symbolleiste in einem Werkzeugfenster angedockt sein und kann nicht verschoben oder angepasst werden. Wenn das VSPackage in umanaged Code geschrieben wird, kann die Symbolleiste an jeder Kante angedockt werden.

 Weitere Informationen zum Hinzufügen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Erstellen einer Symbolleiste für ein Werkzeugfenster

1. Erstellen Sie ein `TWToolbar` VSIX-Projekt mit dem Namen, das sowohl einen Menübefehl mit dem Namen **TWTestCommand als** auch ein Toolfenster mit dem Namen **TestToolWindow**enthält. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) und Erstellen einer Erweiterung mit einem [Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Sie müssen die Befehlselementvorlage hinzufügen, bevor Sie die Vorlagenvorlage für das Toolfenster hinzufügen.

2. Suchen Sie in *TWTestCommandPackage.vsct*nach dem Abschnitt Symbole. Im GuidSymbol-Knoten mit dem Namen guidTWTestPackagePackageCmdSet deklarieren Sie eine Symbolleiste und eine Symbolleistengruppe wie folgt.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Erstellen Sie oben `Commands` im Abschnitt `Menus` einen Abschnitt. Fügen `Menu` Sie ein Element hinzu, um die Symbolleiste zu definieren.

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

     Symbolleisten können nicht wie Untermenüs verschachtelt werden. Daher müssen Sie kein übergeordnetes Element zuweisen. Außerdem müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel wird die Erstplatzierung einer Symbolleiste programmgesteuert definiert, aber nachfolgende Änderungen durch den Benutzer bleiben erhalten.

4. Definieren Sie im Abschnitt Gruppen eine Gruppe, die die Befehle für die Symbolleiste enthält.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Ändern Sie im Abschnitt Schaltflächen das übergeordnete Element des vorhandenen Button-Elements in die Symbolleistengruppe, sodass die Symbolleiste angezeigt wird.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Wenn eine Symbolleiste keine Befehle hat, wird sie standardmäßig nicht angezeigt.

     Da die neue Symbolleiste nicht automatisch zum Werkzeugfenster hinzugefügt wird, muss die Symbolleiste explizit hinzugefügt werden. Dies wird im nächsten Abschnitt erläutert.

## <a name="add-the-toolbar-to-the-tool-window"></a>Hinzufügen der Symbolleiste zum Werkzeugfenster

1. Fügen *Sie TWTestCommandPackageGuids.cs* die folgenden Zeilen hinzu.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Fügen *Sie TestToolWindow.cs* die folgende Usingsanweisung hinzu.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. Fügen Sie im TestToolWindow-Konstruktor die folgende Zeile hinzu.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testen der Symbolleiste im Werkzeugfenster

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

2. Klicken Sie im Menü **Ansicht / Andere Windows** auf **ToolWindow testen,** um das Toolfenster anzuzeigen.

     Sie sollten eine Symbolleiste (es sieht aus wie das Standardsymbol) oben links im Werkzeugfenster sehen, direkt unter dem Titel.

3. Klicken Sie auf der Symbolleiste auf das Symbol, um die Meldung **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()** anzuzeigen.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)
