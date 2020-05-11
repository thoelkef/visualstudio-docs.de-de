---
title: Hinzufügen einer Symbolleiste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740214"
---
# <a name="add-a-toolbar"></a>Hinzufügen einer Symbolleiste
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie der Visual Studio-IDE eine Symbolleiste hinzufügen.

 Eine Symbolleiste ist ein horizontaler oder vertikaler Streifen, der Schaltflächen enthält, die an Befehle gebunden sind. Je nach Implementierung kann eine Symbolleiste in der IDE neu positioniert, an jeder Seite des IDE-Hauptfensters angedockt oder vor anderen Fenstern angezeigt werden.

 Darüber hinaus können Benutzer Befehle zu einer Symbolleiste hinzufügen oder sie mithilfe des Dialogfelds **Anpassen** daraus entfernen. In der Regel sind Symbolleisten in VSPackages vom Benutzer angepasst werden können. Die IDE verarbeitet alle Anpassungen, und das VSPackage reagiert auf Befehle. Das VSPackage muss nicht wissen, wo sich ein Befehl physisch befindet.

 Weitere Informationen zu Menüs finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Erstellen einer Erweiterung mit einer Symbolleiste
 Erstellen Sie ein `IDEToolbar`VSIX-Projekt mit dem Namen . Fügen Sie eine Menübefehlselementvorlage mit dem Namen **ToolbarTestCommand**hinzu. Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Erstellen einer Symbolleiste für die IDE

1. Suchen Sie in *ToolbarTestCommandPackage.vsct*nach dem Abschnitt Symbole. Fügen Sie im GuidSymbol-Element mit dem Namen guidToolbarTestCommandPackageCmdSet deklarationen für eine Symbolleiste und eine Symbolleistengruppe wie folgt hinzu.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Erstellen Sie oben im Abschnitt Befehle einen Menüabschnitt. Fügen Sie dem Menüabschnitt ein Menüelement hinzu, um die Symbolleiste zu definieren.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Symbolleisten können nicht wie Untermenüs verschachtelt werden. Daher müssen Sie keine übergeordnete Gruppe zuweisen. Außerdem müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel wird die Erstplatzierung einer Symbolleiste programmgesteuert definiert, aber nachfolgende Änderungen durch den Benutzer bleiben erhalten.

3. Definieren Sie im Abschnitt [Gruppen](../extensibility/groups-element.md) nach dem vorhandenen Gruppeneintrag ein [Gruppenelement,](../extensibility/group-element.md) das die Befehle für die Symbolleiste enthält.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Lassen Sie die Schaltfläche auf der Symbolleiste erscheinen. Ersetzen Sie im Abschnitt Schaltflächen den übergeordneten Block in der Schaltfläche auf der Symbolleiste. Der resultierende Button-Block sollte wie folgt aussehen:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Wenn eine Symbolleiste keine Befehle hat, wird sie standardmäßig nicht angezeigt.

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

6. Klicken Sie mit der rechten Maustaste auf die Menüleiste von Visual Studio, um die Liste der Symbolleisten abzurufen. Wählen Sie **Test Toolbar**.

7. Sie sollten Ihre Symbolleiste nun als Symbol rechts neben dem Symbol "In Dateien suchen" sehen. Wenn Sie auf das Symbol klicken, sollte ein Meldungsfeld mit der Meldung **ToolbarTestCommandPackage angezeigt werden. Innerhalb IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
