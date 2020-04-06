---
title: Hinzufügen eines Shortcut-Menüs in einem Toolfenster | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740283"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Hinzufügen eines Kontextmenüs in einem Toolfenster
In dieser exemplarischen Vorgehensweise wird ein Kontextmenü in einem Toolfenster angezeigt. Ein Kontextmenü ist ein Menü, das angezeigt wird, wenn ein Benutzer mit der rechten Maustaste auf eine Schaltfläche, ein Textfeld oder einen Fensterhintergrund klickt. Befehle in einem Kontextmenü verhalten sich wie Befehle in anderen Menüs oder Symbolleisten. Um ein Kontextmenü zu unterstützen, geben Sie es in der *.vsct-Datei* an und zeigen Sie es als Antwort auf den rechtsklickenden Mausklick an.

Ein Toolfenster besteht aus einem WPF-Benutzersteuerelement in einer <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>benutzerdefinierten Toolfensterklasse, die von erbt.

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein Kontextmenü als Visual Studio-Menü erstellen, Menüelemente in der *.vsct-Datei* deklarieren und dann das Managed Package Framework verwenden, um sie in der Klasse zu implementieren, die das Toolfenster definiert. Dieser Ansatz erleichtert den Zugriff auf Visual Studio-Befehle, UI-Elemente und das Automatisierungsobjektmodell.

Wenn das Kontextmenü nicht auf die Visual Studio-Funktionalität <xref:System.Windows.FrameworkElement.ContextMenu%2A> zugreift, können Sie auch die Eigenschaft eines XAML-Elements im Benutzersteuerelement verwenden. Weitere Informationen finden Sie unter [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Voraussetzungen
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Erstellen des Kontextmenüpakets für das Toolfenster

1. Erstellen Sie ein `TWShortcutMenu` VSIX-Projekt mit dem Namen, und fügen Sie ihr eine Toolfenstervorlage mit dem Namen **ShortcutMenu** hinzu. Weitere Informationen zum Erstellen eines Toolfensters finden Sie unter [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Angeben des Kontextmenüs
Mit einem Kontextmenü, wie es in dieser exemplarischen Vorgehensweise angezeigt wird, kann der Benutzer aus einer Liste von Farben auswählen, die zum Ausfüllen des Hintergrunds des Toolfensters verwendet werden.

1. Suchen Sie in *ShortcutMenuPackage.vsct*im GuidSymbol-Element mit dem Namen guidShortcutMenuPackageCmdSet, und deklarieren Sie das Kontextmenü, die Kontextmenügruppe und die Menüoptionen. Das GuidSymbol-Element sollte nun wie folgt aussehen:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Erstellen Sie direkt vor dem Buttons-Element ein Menus-Element, und definieren Sie dann das Kontextmenü darin.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Ein Kontextmenü verfügt nicht über ein übergeordnetes Menü, da es nicht Teil eines Menüs oder einer Symbolleiste ist.

3. Erstellen Sie ein Groups-Element mit einem Gruppenelement, das die Verknüpfungsmenüelemente enthält, und ordnen Sie die Gruppe dem Kontextmenü zu.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Definieren Sie im Buttons-Element die einzelnen Befehle, die im Kontextmenü angezeigt werden. Das Buttons-Element sollte wie folgt aussehen:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. Fügen Sie in *ShortcutMenuCommand.cs*die Definitionen für die Befehlssatz-GUID, das Kontextmenü und die Menüelemente hinzu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Dies sind die gleichen Befehls-IDs, die im Abschnitt Symbole der *Datei ShortcutMenuPackage.vsct* definiert sind. Die Kontextgruppe ist hier nicht enthalten, da sie nur in der *.vsct-Datei* erforderlich ist.

## <a name="implementing-the-shortcut-menu"></a>Implementieren des Kontextmenüs
 In diesem Abschnitt werden das Kontextmenü und seine Befehle implementiert.

1. In *ShortcutMenu.cs*kann das Toolfenster den Menübefehlsdienst abrufen, aber das darin enthaltene Steuerelement kann nicht. Die folgenden Schritte zeigen, wie Sie den Menübefehlsdienst für das Benutzersteuerelement verfügbar machen.

2. Fügen Sie in *ShortcutMenu.cs*die folgenden Anweisungen mithilfe von Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Überschreiben Sie die Initialize()-Methode des Toolfensters, um den Menübefehlsdienst abzurufen und das Steuerelement hinzuzufügen, indem Sie den Menübefehlsdienst an den Konstruktor übergeben:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Entfernen Sie im ShortcutMenu-Werkzeugfensterkonstruktor die Zeile, die das Steuerelement hinzufügt. Der Konstruktor sollte nun wie folgt aussehen:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Fügen Sie in *ShortcutMenuControl.xaml.cs*ein privates Feld für den Menübefehlsdienst hinzu, und ändern Sie den Steuerelementkonstruktor, um den Menübefehlsdienst zu übernehmen. Verwenden Sie dann den Menübefehlsdienst, um die Kontextmenübefehle hinzuzufügen. Der ShortcutMenuControl-Konstruktor sollte nun wie der folgende Code aussehen. Der Befehlshandler wird später definiert.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. Fügen Sie in *ShortcutMenuControl.xaml*dem <xref:System.Windows.Controls.UserControl> Element der obersten Ebene ein <xref:System.Windows.UIElement.MouseRightButtonDown> Ereignis hinzu. Die XAML-Datei sollte nun wie folgt aussehen:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. Fügen Sie in *ShortcutMenuControl.xaml.cs*einen Stub für den Ereignishandler hinzu.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Fügen Sie der gleichen Datei Folgendes mithilfe von Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementieren `MyToolWindowMouseRightButtonDown` Sie das Ereignis wie folgt.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Dadurch wird <xref:System.ComponentModel.Design.CommandID> ein Objekt für das Kontextmenü erstellt, der Speicherort des Mausklicks <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> identifiziert und das Kontextmenü an dieser Position mithilfe der Methode geöffnet.

10. Implementieren Sie den Befehlshandler.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    In diesem Fall behandelt nur eine Methode Ereignisse für alle <xref:System.ComponentModel.Design.CommandID> Menüelemente, indem die Hintergrundfarbe entsprechend identifiziert und angepasst wird. Wenn die Menüelemente nicht verwandte Befehle enthalten hätten, hätten Sie für jeden Befehl einen separaten Ereignishandler erstellt.

## <a name="test-the-tool-window-features"></a>Testen der Toolfenster-Features

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

2. Klicken Sie in der experimentellen Instanz auf **Ansicht / Andere Windows**, und dann auf **ShortcutMenu**. Auf diese Weise sollte Ihr Toolfenster angezeigt werden.

3. Klicken Sie mit der rechten Maustaste in den Textkörper des Werkzeugfensters. Ein Kontextmenü mit einer Liste von Farben sollte angezeigt werden.

4. Klicken Sie im Kontextmenü auf eine Farbe. Die Hintergrundfarbe des Werkzeugfensters sollte in die ausgewählte Farbe geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Nutzung und Erbringung von Dienstleistungen](../extensibility/using-and-providing-services.md)
