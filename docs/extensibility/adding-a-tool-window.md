---
title: Hinzufügen eines Toolfensters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f438297a51e5b091ea8b80cf587586919d00798
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352413"
---
# <a name="add-a-tool-window"></a>Hinzufügen eines Toolfensters
In dieser exemplarischen Vorgehensweise erfahren Sie, wie zum Erstellen eines Toolfensters und integrieren in Visual Studio auf folgende Weise:

- Fügen Sie ein Steuerelement, um das Fenster.

- Fügen Sie einem Toolfenster eine Symbolleiste hinzu.

- Hinzufügen eines Befehls auf der Symbolleiste an.

- Implementieren Sie die Befehle an.

- Legen Sie die Standardposition für das Toolfenster an.

## <a name="prerequisites"></a>Vorraussetzungen
Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Erstellen eines Toolfensters

1. Erstellen Sie ein Projekt mit dem Namen **FirstToolWin** mithilfe der VSIX-Projektvorlage aus, und fügen Sie der Elementvorlage ein benutzerdefiniertes Tool-Fenster, der mit dem Namen **FirstToolWindow**.

    > [!NOTE]
    > Weitere Informationen zu eine Erweiterung mit einem Toolfenster erstellen, finden Sie unter [erstellen Sie eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Hinzufügen eines Steuerelements zu des Toolfensters

1. Entfernen Sie das Standardsteuerelement. Open *FirstToolWindowControl.xaml* und löschen Sie die **hier klicken!** Schaltfläche.

2. In der **Toolbox**, erweitern Sie die **alle WPF-Steuerelemente** Abschnitt, und ziehen Sie die **Medienelement** die Steuerung an die **FirstToolWindowControl** Formular. Wählen Sie das Steuerelement, und klicken Sie in der **Eigenschaften** Fenster, nennen Sie dieses Element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Das Toolfenster eine Symbolleiste hinzugefügt
Durch Hinzufügen einer Symbolleiste auf folgende Weise sichergestellt, dass sind die Gradienten und die Farben des Weiterleitens von der IDE.

1. In **Projektmappen-Explorer**öffnen *FirstToolWindowPackage.vsct*. Die *VSCT* Datei definiert die Elemente der grafischen Benutzeroberfläche (GUI) in das Toolfenster, mithilfe von XML.

2. In der `<Symbols>` Abschnitt, suchen Sie nach der `<GuidSymbol>` Knoten, deren `name` Attribut `guidFirstToolWindowPackageCmdSet`. Fügen Sie die folgenden beiden `<IDSymbol>` Elemente der Liste der `<IDSymbol>` Elemente in diesem Knoten aus, um eine Symbolleiste und einer Symbolleistengruppe zu definieren.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Direkt über die `<Buttons>` Abschnitt, erstellen Sie eine `<Menus>` Abschnitt die folgende angezeigt:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Es gibt verschiedene Arten von Menü aus. Dieses Menü ist, einer Symbolleiste in einem Toolfenster, definiert durch seine `type` Attribut. Die `guid` und `id` Einstellungen bilden die vollqualifizierte ID der Symbolleiste. In der Regel die `<Parent>` eines Menüs wird die Containergruppe. Allerdings wird eine Symbolleiste als eigenes übergeordnetes Element definiert. Aus diesem Grund wird für der gleiche Bezeichner verwendet die `<Menu>` und `<Parent>` Elemente. Die `priority` -Attribut ist nur ' 0'.

4. Symbolleisten, Menüs in vielerlei Hinsicht ähneln. Z. B. genau wie ein Menü Gruppen von Befehlen verfügen kann, Symbolleisten Gruppen möglicherweise auch. (In Menüs, werden die Befehlsgruppen durch horizontale Linien getrennt. Auf der Symbolleiste werden die Gruppen nicht durch visual Zeilenunterteiler getrennt.)

    Hinzufügen einer `<Groups>` Abschnitt, enthält eine `<Group>` Element. Definiert die Gruppe, deren ID mit dem Sie deklariert haben, in der `<Symbols>` Abschnitt. Hinzufügen der `<Groups>` nur nach dem Abschnitt der `<Menus>` Abschnitt.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Wenn das übergeordnete Element GUID und ID auf die GUID und ID der Symbolleiste, fügen Sie die Gruppe auf der Symbolleiste aus.

## <a name="add-a-command-to-the-toolbar"></a>Hinzufügen eines Befehls auf der Symbolleiste
 Hinzufügen eines Befehls auf der Symbolleiste, die als Schaltfläche angezeigt wird.

1. In der `<Symbols>` Abschnitt, deklarieren Sie die folgenden IDSymbol-Elemente direkt hinter der Symbolleiste und die Symbolleiste Gruppendeklarationen.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Fügen Sie ein Button-Element innerhalb der `<Buttons>` Abschnitt. Dieses Element wird angezeigt, auf der Symbolleiste im Toolfenster, mit einem **Suche** (Lupensymbol).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Open *FirstToolWindowCommand.cs* und fügen Sie die folgenden Zeilen in der Klasse direkt nach den vorhandenen Feldern.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Dies macht die Befehle in Code verfügbar.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Hinzufügen einer MediaPlayer-Eigenschaft zu FirstToolWindowControl
Aus den Ereignishandlern für die Symbolleisten-Steuerelemente muss Ihr Code auf der Media Player-Steuerelement, das ein untergeordnetes Element der FirstToolWindowControl-Klasse.

In **Projektmappen-Explorer**, mit der rechten Maustaste *FirstToolWindowControl.xaml*, klicken Sie auf **Ansichtscode**, und fügen Sie den folgenden Code der FirstToolWindowControl-Klasse.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instanziieren Sie das Toolfenster und Symbolleiste
Hinzufügen einer Symbolleiste und einen Menübefehl, die aufruft, die **geöffnete Datei** Dialogfeld und ausgewählten Medien wiedergegeben.

1. Open *FirstToolWindow.cs* und fügen Sie die folgenden `using` Anweisungen.

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Fügen Sie einen öffentlichen Verweis auf das Steuerelement FirstToolWindowControl, innerhalb der FirstToolWindow-Klasse.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Am Ende des Konstruktors legen Sie dieses Steuerelementvariable auf das neu erstellte Steuerelement.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Die Symbolleiste innerhalb des Konstruktors zu instanziieren.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. An diesem Punkt sollte die FirstToolWindow-Konstruktor wie folgt aussehen:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Fügen Sie den Menübefehl auf der Symbolleiste hinzu. Fügen Sie in der FirstToolWindowCommand.cs-Klasse, die folgenden using-Anweisung

    ```csharp
    using System.Windows.Forms;
    ```

7. Fügen Sie den folgenden Code am Ende der ShowToolWindow()-Methode, in der FirstToolWindowCommand-Klasse. Der Befehl ButtonHandler wird im nächsten Abschnitt implementiert.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Zum Implementieren eines Menübefehls im Toolfenster

1. Fügen Sie in der Klasse FirstToolWindowCommand eine ButtonHandler-Methode, die aufruft, die **geöffnete Datei** Dialogfeld. Wenn eine Datei ausgewählt wurde, gibt die Mediendatei wieder.

2. Fügen Sie einen privaten Verweis für die FirstToolWindow-Fenster, das in der FindToolWindow()-Methode erstellt wird, in der FirstToolWindowCommand-Klasse.

    ```csharp
    private FirstToolWindow window;
    ```

3. Ändern Sie die ShowToolWindow()-Methode, um das Fenster festgelegt, die, dem Sie weiter oben definiert haben (sodass die Befehlshandler ButtonHandler das Window-Steuerelement zugreifen kann. Hier ist die vollständige ShowToolWindow()-Methode.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Fügen Sie die ButtonHandler-Methode. Erstellt einen OpenFileDialog für den Benutzer an der Mediendatei hinzuzufügenden wiedergegeben, und gibt Sie die ausgewählte Datei anschließend wieder.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Legen Sie die Standardposition für das Toolfenster
 Geben Sie anschließend ein Standardverzeichnis, in der IDE für das Toolfenster. Konfigurationsinformationen für das Toolfenster sind in der *FirstToolWindowPackage.cs* Datei.

1. In *FirstToolWindowPackage.cs*, finden Sie die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> -Attribut für die `FirstToolWindowPackage` -Klasse, die den Typ FirstToolWindow an den Konstruktor übergibt. Um eine Standardposition angeben, müssen Sie weitere Parameter an den Konstruktor mit dem folgenden Beispiel hinzufügen.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Der erste benannte Parameter `Style` und sein Wert ist `Tabbed`, was bedeutet, dass das Fenster eine Registerkarte in einem vorhandenen Fenster ist. Die dockingposition wird angegeben, indem die `Window` n diesem Fall die GUID des Parameters, kann die **Projektmappen-Explorer**.

    > [!NOTE]
    > Weitere Informationen zu den Arten von Fenstern in der IDE finden Sie unter <xref:EnvDTE.vsWindowType>.

## <a name="test-the-tool-window"></a>Testen Sie das Toolfenster

1. Drücken Sie **F5** um eine neue Instanz der das experimentelle Build von Visual Studio zu öffnen.

2. Auf der **Ansicht** Startmenü **andere Windows** , und klicken Sie dann auf **erste Toolfenster**.

    Das Media Player-Toolfenster soll öffnen Sie in der gleichen Position wie **Projektmappen-Explorer**. Wenn es weiterhin in der gleichen Position wie vorher angezeigt wird, das Fensterlayout zurücksetzen (**Fenster / Fensterlayout zurücksetzen**).

3. Klicken Sie auf die Schaltfläche (sie hat die **Suche** Symbol) im Toolfenster. Wählen Sie eine unterstützte Sound oder Videodatei, z. B. *C:\windows\media\chimes.wav*, drücken Sie dann die **öffnen**.

    Sie sollten den Glockenton Sound hören.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
