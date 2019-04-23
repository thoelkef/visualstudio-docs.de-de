---
title: Hinzufügen einer Symbolleiste | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0485b6649396239d2b6501c65e801a03767d5df1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082294"
---
# <a name="add-a-toolbar"></a>Hinzufügen einer Symbolleiste
Diese exemplarische Vorgehensweise zeigt, wie Visual Studio-IDE eine Symbolleiste hinzugefügt wird.

 Eine Symbolleiste ist eine horizontale oder vertikale entfernen, die Schaltflächen enthält, die auf Befehle gebunden sind. Abhängig von der Implementierung kann eine Symbolleiste in der IDE neu angeordnet, auf jeder Seite des Hauptfensters der IDE angedockt, oder gemacht werden vor anderen Fenstern zu bleiben.

 Darüber hinaus können Benutzer hinzufügen von Befehlen zu einer Symbolleiste oder diese daraus entfernen, mit der **anpassen** Dialogfeld. Symbolleisten in VSPackages sind in der Regel Benutzer anpassbar. Verarbeitet die IDE-Anpassungen, und das VSPackage auf Befehle reagiert. Das VSPackage muss nicht wissen, wo sich ein Befehl physisch befindet.

 Weitere Informationen zu Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Erstellen Sie eine Erweiterung mit einer Symbolleiste
 Erstellen Sie ein VSIX-Projekt mit dem Namen `IDEToolbar`. Fügen Sie eine Elementvorlage der Menü-Befehl mit dem Namen **ToolbarTestCommand**. Informationen hierzu finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Erstellen Sie eine Symbolleiste für die IDE

1. In *ToolbarTestCommandPackage.vsct*, suchen Sie nach dem Abschnitt "Symbols". Fügen Sie im GuidSymbol-Element mit dem Namen GuidToolbarTestCommandPackageCmdSet Deklarationen für eine Symbolleiste und einer Symbolleistengruppe wie folgt hinzu.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Am oberen Rand im Abschnitt-Befehle erstellen Sie einen Abschnitt des Menüs. Fügen Sie ein Menüelement im im Menüs Abschnitt definieren Sie eine Symbolleiste hinzu.

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

     Symbolleisten können nicht geschachtelt werden, wie die Untermenüs. Aus diesem Grund müssen Sie keine übergeordneten Gruppe zuweisen. Darüber hinaus müssen Sie keinen zum Festlegen einer Priorität, da der Benutzer die Symbolleisten wechseln kann. In der Regel anfängliche Platzierung einer Symbolleiste programmgesteuert definiert ist, aber nachfolgende Änderungen durch den Benutzer beibehalten werden.

3. In der [Gruppen](../extensibility/groups-element.md) Abschnitt definieren Sie nach den vorhandenen Gruppeneintrag eine [Gruppe](../extensibility/group-element.md) Element enthält die Befehle für die Symbolleiste.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Stellen Sie die Schaltfläche mit den auf der Symbolleiste angezeigt. Ersetzen Sie im Abschnitt "Schaltflächen" den übergeordneten Block in der Schaltfläche auf der Symbolleiste aus. Die daraus resultierenden Befehlsblock der Schaltfläche sollte wie folgt aussehen:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     In der Standardeinstellung Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.

6. Mit der rechten Maustaste in der Menüleiste von Visual Studio zum Abrufen der Liste der Symbolleisten. Wählen Sie **testen Symbolleiste**.

7. Eine Symbolleiste sollte jetzt als Symbol rechts neben der Suche in Dateien Symbol angezeigt werden. Wenn Sie das Symbol klicken, sollten Sie sehen, dass ein Dialogfeld mit der Meldung **ToolbarTestCommandPackage. Inside IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)