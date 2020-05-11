---
title: Hinzufügen eines Toolfensters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740254"
---
# <a name="add-a-tool-window"></a>Hinzufügen eines Werkzeugfensters

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein Toolfenster erstellen und es auf folgende Weise in Visual Studio integrieren:

- Fügen Sie dem Toolfenster ein Steuerelement hinzu.

- Fügen Sie einem Werkzeugfenster eine Symbolleiste hinzu.

- Fügen Sie der Symbolleiste einen Befehl hinzu.

- Implementieren Sie die Befehle.

- Legen Sie die Standardposition für das Werkzeugfenster fest.

## <a name="prerequisites"></a>Voraussetzungen

Das Visual Studio SDK ist als optionale Funktion in Visual Studio-Setup enthalten. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Erstellen eines Werkzeugfensters

1. Erstellen Sie ein Projekt mit dem Namen **FirstToolWin** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Vorlagenvorlage für das Toolfenster mit dem Namen **FirstToolWindow**hinzu.

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Toolfenster finden Sie unter [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Hinzufügen eines Steuerelements zum Werkzeugfenster

1. Entfernen Sie das Standardsteuerelement. Öffnen Sie *FirstToolWindowControl.xaml* und löschen Sie die **Click Me!** .

2. Erweitern Sie in der **Toolbox**den Abschnitt **Alle WPF-Steuerelemente,** und ziehen Sie das **Steuerelement Medienelement** in das **Formular FirstToolWindowControl.** Wählen Sie das Steuerelement aus, und benennen Sie im **Fenster Eigenschaften** dieses Element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Hinzufügen einer Symbolleiste zum Werkzeugfenster
Durch Hinzufügen einer Symbolleiste auf folgende Weise stellen Sie sicher, dass ihre Farbverläufe und Farben mit dem Rest der IDE konsistent sind.

1. Öffnen Sie im **Projektmappen-Explorer** *FirstToolWindowPackage.vsct*. Die *.vsct-Datei* definiert die grafischen Benutzeroberflächenelemente (GUI) in Ihrem Toolfenster mithilfe von XML.

2. Suchen `<Symbols>` Sie im `<GuidSymbol>` Abschnitt `name` den `guidFirstToolWindowPackageCmdSet`Knoten, dessen Attribut lautet. Fügen Sie `<IDSymbol>` die folgenden beiden `<IDSymbol>` Elemente der Liste der Elemente in diesem Knoten hinzu, um eine Symbolleiste und eine Symbolleistengruppe zu definieren.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Erstellen Sie `<Buttons>` direkt über `<Menus>` dem Abschnitt einen Abschnitt, der diesem ähnelt:

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

    Es gibt verschiedene Arten von Menü. Dieses Menü ist eine Symbolleiste in einem `type` Werkzeugfenster, definiert durch sein Attribut. Die `guid` `id` und Einstellungen bilden die vollqualifizierte ID der Symbolleiste. In der `<Parent>` Regel ist das eines Menüs die enthaltende Gruppe. Eine Symbolleiste ist jedoch als eigenes übergeordnetes Element definiert. Daher wird derselbe Bezeichner `<Menu>` `<Parent>` für die und-Elemente verwendet. Das `priority` Attribut ist nur '0'.

4. Symbolleisten ähneln Menüs in vielerlei Hinsicht. So wie z. B. ein Menü Gruppen von Befehlen haben kann, können Symbolleisten auch Gruppen haben. (In Menüs werden die Befehlsgruppen durch horizontale Linien getrennt. Auf Symbolleisten werden die Gruppen nicht durch visuelle Trennwände getrennt.)

    Fügen `<Groups>` Sie einen `<Group>` Abschnitt hinzu, der ein Element enthält. Dadurch wird die Gruppe definiert, `<Symbols>` deren ID Sie im Abschnitt deklariert haben. Fügen `<Groups>` Sie den `<Menus>` Abschnitt direkt nach dem Abschnitt hinzu.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Indem Sie die übergeordnete GUID und ID auf die GUID und ID der Symbolleiste festlegen, fügen Sie die Gruppe der Symbolleiste hinzu.

## <a name="add-a-command-to-the-toolbar"></a>Hinzufügen eines Befehls zur Symbolleiste

Fügen Sie der Symbolleiste einen Befehl hinzu, der als Schaltfläche angezeigt wird.

1. Deklarieren Sie im `<Symbols>` Abschnitt die folgenden IDSymbol-Elemente direkt nach den Symbolleisten- und Symbolleistengruppendeklarationen.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Fügen Sie ein `<Buttons>` Button-Element innerhalb des Abschnitts hinzu. Dieses Element wird auf der Symbolleiste im Werkzeugfenster mit einem **Suchsymbol** (Vergrößerungsglas) angezeigt.

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

3. Öffnen *Sie FirstToolWindowCommand.cs* und fügen Sie die folgenden Zeilen in der Klasse direkt nach den vorhandenen Feldern hinzu.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Dadurch werden Ihre Befehle im Code verfügbar.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Hinzufügen einer MediaPlayer-Eigenschaft zu FirstToolWindowControl
Über die Ereignishandler für die Symbolleistensteuerelemente muss Der Code auf das Media Player-Steuerelement zugreifen können, das ein untergeordnetes Element der FirstToolWindowControl-Klasse ist.

Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf *FirstToolWindowControl.xaml*, klicken Sie auf **Code anzeigen**, und fügen Sie den folgenden Code zur FirstToolWindowControl-Klasse hinzu.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instanziieren des Werkzeugfensters und der Symbolleiste
Fügen Sie eine Symbolleiste und einen Menübefehl hinzu, der das Dialogfeld **Datei** öffnen aufruft und die ausgewählte Mediendatei wiedergibt.

1. Öffnen *Sie FirstToolWindow.cs,* und fügen Sie die folgenden `using` Direktiven hinzu:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Fügen Sie innerhalb der FirstToolWindow-Klasse einen öffentlichen Verweis auf das FirstToolWindowControl-Steuerelement hinzu.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Legen Sie diese Steuerelementvariable am Ende des Konstruktors auf das neu erstellte Steuerelement fest.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Instanziieren Sie die Symbolleiste im Konstruktor.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. An dieser Stelle sollte der FirstToolWindow-Konstruktor wie folgt aussehen:

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

6. Fügen Sie den Menübefehl zur Symbolleiste hinzu. Fügen Sie in der FirstToolWindowCommand.cs-Klasse die folgende Direktive hinzu:

    ```csharp
    using System.Windows.Forms;
    ```

7. Fügen Sie in der FirstToolWindowCommand-Klasse den folgenden Code am Ende der ShowToolWindow()-Methode hinzu. Der ButtonHandler-Befehl wird im nächsten Abschnitt implementiert.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>So implementieren Sie einen Menübefehl im Toolfenster

1. Fügen Sie in der FirstToolWindowCommand-Klasse eine ButtonHandler-Methode hinzu, die das Dialogfeld **Datei öffnen** aufruft. Wenn eine Datei ausgewählt wurde, wird die Mediendatei wiedergegeben.

2. Fügen Sie in der FirstToolWindowCommand-Klasse einen privaten Verweis auf das FirstToolWindow-Fenster hinzu, das in der FindToolWindow()-Methode erstellt wird.

    ```csharp
    private FirstToolWindow window;
    ```

3. Ändern Sie die ShowToolWindow()-Methode, um das oben definierte Fenster festzulegen (damit der ButtonHandler-Befehlshandler auf das Fenstersteuerelement zugreifen kann). Hier ist die komplette ShowToolWindow()-Methode.

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

4. Fügen Sie die ButtonHandler-Methode hinzu. Es erstellt einen OpenFileDialog, mit dem der Benutzer die Mediendatei angeben kann, die wiedergegeben werden soll, und dann die ausgewählte Datei wiedergibt.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Festlegen der Standardposition für das Werkzeugfenster

Geben Sie als Nächstes einen Standardspeicherort in der IDE für das Toolfenster an. Konfigurationsinformationen für das Toolfenster befinden sich in der *FirstToolWindowPackage.cs* Datei.

1. Suchen *Sie*in <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> FirstToolWindowPackage.cs `FirstToolWindowPackage` das Attribut für die Klasse, die den Typ FirstToolWindow an den Konstruktor übergibt. Um eine Standardposition anzugeben, müssen Sie dem Konstruktor im folgenden Beispiel weitere Parameter hinzufügen.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Der erste benannte Parameter `Style` `Tabbed`ist und sein Wert ist , was bedeutet, dass das Fenster eine Registerkarte in einem vorhandenen Fenster ist. Die Andockposition wird `Window` durch den Parameter, n in diesem Fall, die GUID des **Projektmappen-Explorers**angegeben.

    > [!NOTE]
    > Weitere Informationen zu den Fenstertypen in <xref:EnvDTE.vsWindowType>der IDE finden Sie unter .

## <a name="test-the-tool-window"></a>Testen des Werkzeugfensters

1. Drücken Sie **F5,** um eine neue Instanz des experimentellen Visual Studio-Builds zu öffnen.

2. Zeigen Sie im Menü **Ansicht** auf **Andere Fenster,** und klicken Sie dann auf **Erstes Toolfenster**.

    Das Media Player-Toolfenster sollte an der gleichen Position wie der **Projektmappen-Explorer**geöffnet werden. Wenn es immer noch an der gleichen Position wie zuvor angezeigt wird, setzen Sie das Fensterlayout zurück (**Fenster / Fensterlayout zurücksetzen**).

3. Klicken Sie im Toolfenster auf die Schaltfläche (es verfügt über das **Suchsymbol).** Wählen Sie eine unterstützte Ton- oder Videodatei aus, z. B. *C:-Windows-Media-Chimes.wav*, und drücken Sie dann **Öffnen**.

    Sie sollten das Glockenspiel hören.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
