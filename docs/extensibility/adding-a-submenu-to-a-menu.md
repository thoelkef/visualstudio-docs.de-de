---
title: Hinzufügen eines Untermenüs zu einem Menü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740270"
---
# <a name="add-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü
Diese exemplarische Vorgehensweise basiert auf der Demo unter [Hinzufügen eines Menüs zur Visual Studio-Menüleiste,](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) indem gezeigt wird, wie dem **TestMenu-Menü** ein Untermenü hinzugefügt wird.

 Ein Untermenü ist ein sekundäres Menü, das in einem anderen Menü angezeigt wird. Ein Untermenü kann durch den Pfeil identifiziert werden, der seinem Namen folgt. Wenn Sie auf den Namen klicken, werden das Untermenü und seine Befehle angezeigt.

 In dieser exemplarischen Vorgehensweise wird ein Untermenü in einem Menü in der Visual Studio-Menüleiste erstellt und ein neuer Befehl in das Untermenü eingefügt. Die exemplarische Vorgehensweise implementiert auch den neuen Befehl.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü

1. Führen Sie die Schritte unter [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) aus, um das Projekt und das Menüelement zu erstellen. Bei den Schritten in dieser exemplarischen Vorgehensweise wird `TopLevelMenu`davon ausgegangen, dass der Name des VSIX-Projekts lautet.

2. Öffnen Sie *TestCommandPackage.vsct*. Fügen `<Symbols>` Sie im `<IDSymbol>` Abschnitt ein Element für das Untermenü, eines für die `<GuidSymbol>` Untermenügruppe und eines für den Befehl hinzu, alles im Knoten "guidTopLevelMenuCmdSet". Dies ist derselbe Knoten, der das `<IDSymbol>` Element für das Menü der obersten Ebene enthält.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Fügen Sie dem `<Menus>` Abschnitt das neu erstellte Untermenü hinzu.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Das GUID/ID-Paar des übergeordneten Elements gibt die Menügruppe an, die unter [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)generiert wurde, und ist ein untergeordnetes Element des Menüs der obersten Ebene.

4. Fügen Sie die in Schritt `<Groups>` 2 definierte Menügruppe zum Abschnitt hinzu, und machen Sie sie zu einem untergeordneten Element des Untermenüs.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Fügen Sie `<Button>` dem `<Buttons>` Abschnitt ein neues Element hinzu, um den in Schritt 2 erstellten Befehl als Element im Untermenü zu definieren.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Sie sollten die experimentelle Instanz sehen.

7. Klicken Sie auf **TestMenu,** um ein neues Untermenü mit dem Namen **Untermenü**anzuzeigen. Klicken Sie auf **Untermenü,** um das Untermenü zu öffnen und einen neuen **Befehl, Test Sub Command**, anzuzeigen. Beachten Sie, dass das Klicken auf **Test Sub Command** nichts bewirkt.

## <a name="add-a-command"></a>Hinzufügen eines Befehls

1. Öffnen *Sie TestCommand.cs* und fügen Sie die folgende Befehls-ID nach der vorhandenen Befehls-ID hinzu.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Fügen Sie den Unterbefehl hinzu. Suchen Sie den Befehlskonstruktor. Fügen Sie die folgenden Zeilen `AddCommand` direkt nach dem Aufruf der Methode hinzu.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Der `SubItemCallback` Befehlshandler wird später definiert. Der Konstruktor sollte nun wie folgt aussehen:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Fügen Sie `SubItemCallback()`hinzu. Dies ist die Methode, die aufgerufen wird, wenn auf den neuen Befehl im Untermenü geklickt wird.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

5. Klicken Sie im Menü **TestMenu** auf **Untermenü** und dann auf **Unterbefehl testen**. Ein Meldungsfeld sollte angezeigt werden und den Text "Test Command Inside TestCommand.SubItemCallback()" anzeigen.

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
