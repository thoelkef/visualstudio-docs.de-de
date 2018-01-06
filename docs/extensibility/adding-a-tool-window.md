---
title: "Hinzufügen eines Toolfensters | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: "52"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 205c6928010d4cf3a35c6947e516c0bbc8674f29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-tool-window"></a>Hinzufügen eines Toolfensters
In dieser exemplarischen Vorgehensweise erfahren Sie, wie ein Toolfenster erstellen und seine Integration in Visual Studio auf folgende Weise:  
  
-   Hinzufügen eines Steuerelements, das Toolfenster an.  
  
-   Fügen Sie einem Toolfenster eine Symbolleiste hinzu.  
  
-   Hinzufügung eines Befehls auf der Symbolleiste.  
  
-   Implementieren Sie die Befehle an.  
  
-   Legen Sie die Standardposition für das Toolfenster an.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tool-window"></a>Erstellen eines Toolfensters  
  
1.  Erstellen Sie ein Projekt mit dem Namen **FirstToolWin** die VSIX-Vorlage, und fügen Sie eine Elementvorlage für benutzerdefiniertes Tool-Fenster mit dem Namen **FirstToolWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von Erweiterung mit einem Toolfenster, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Hinzufügen eines Steuerelements zu des Toolfensters  
  
1.  Entfernen Sie das standardmäßige Steuerelement. FirstToolWindowControl.xaml öffnen und löschen Sie die **Click Me!** Schaltfläche.  
  
2.  In der **Toolbox**, erweitern Sie die **alle WPF-Steuerelemente** Abschnitt, und ziehen Sie die **Media-Element** die Steuerung an die **FirstToolWindowControl** Formular. Wählen Sie das Steuerelement, und klicken Sie in der **Eigenschaften** Fenster, nennen Sie dieses Element **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Das Toolfenster eine Symbolleiste hinzugefügt  
 Durch Hinzufügen einer Symbolleiste auf folgende Weise an, gewährleisten Sie, dass die Farbverläufe und Farben mit dem Rest der IDE konsistent sind.  
  
1.  In **Projektmappen-Explorer**, FirstToolWindowPackage.vsct zu öffnen. Die VSCT-Datei definiert die Elemente der grafischen Benutzeroberfläche (GUI) in Ihr Toolfenster mithilfe von XML.  
  
2.  In der `<Symbols>` Abschnitt aus, suchen Sie die `<GuidSymbol>` Knoten, deren `name` -Attribut ist `guidFirstToolWindowPackageCmdSet`. Fügen Sie die folgenden beiden `<IDSymbol>` Elemente der Liste der `<IDSymbol>` Elemente in diesem Knoten eine Symbolleiste und eine Symbolleistengruppe definiert.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Direkt über die `<Buttons>` Abschnitt, erstellen Sie eine `<Menus>` -Abschnitt, der Dies ähnelt:  
  
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
  
     Es gibt verschiedene Arten von Menü aus. Dieses Menü ist eine Symbolleiste in einem Toolfenster, definiert durch seine `type` Attribut. Die `guid` und `id` Einstellungen bilden die vollständig qualifizierte ID der Symbolleiste. In der Regel die `<Parent>` eines Menüs enthaltende Gruppe ist. Allerdings wird eine Symbolleiste als eigene übergeordnetes Attribut definiert. Daher wird für der gleiche Bezeichner verwendet die `<Menu>` und `<Parent>` Elemente. Die `priority` -Attribut ist nur ' 0'.  
  
4.  Symbolleisten, Menüs in vielerlei Hinsicht ähneln. Z. B., wie ein Menü Befehlsgruppen möglicherweise, Symbolleisten auch Gruppen möglicherweise. (In Menüs, werden die Befehlsgruppen durch horizontale Linien getrennt. Auf der Symbolleiste werden die Gruppen nicht durch visual Trennblättern getrennt.)  
  
     Hinzufügen einer `<Groups>` Abschnitt, enthält eine `<Group>` Element. Definiert die Gruppe, deren ID, die Sie in der deklariert die `<Symbols>` Abschnitt. Hinzufügen der `<Groups>` Abschnitt direkt nach der `<Menus>` Abschnitt.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Durch Festlegen der übergeordneten GUID und ID auf die GUID und die ID der Symbolleiste, fügen Sie die Gruppe auf der Symbolleiste aus.  
  
## <a name="add-a-command-to-the-toolbar"></a>Hinzufügen eines Befehls auf der Symbolleiste  
 Hinzufügung eines Befehls auf der Symbolleiste, die als eine Schaltfläche angezeigt wird.  
  
1.  In der `<Symbols>` Abschnitt, deklarieren Sie die folgenden IDSymbol Elemente direkt hinter der Symbolleiste und die Symbolleiste Gruppendeklarationen.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Fügen Sie ein Button-Element innerhalb der `<Buttons>` Abschnitt. Dieses Element wird auf der Symbolleiste im Toolfenster mit einem Suchsymbol (Vergrößerungsglas) angezeigt.  
  
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
  
3.  Öffnen Sie FirstToolWindowCommand.cs, und fügen Sie die folgenden Zeilen in der Klasse direkt hinter den vorhandenen Feldern.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     Dies macht die Befehle in Code verfügbar.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Hinzufügen einer Media Player-Eigenschaft zu FirstToolWindowControl  
 Über die Ereignishandler für das Symbolleisten-Steuerelemente muss Ihr Code Media Player-Steuerelement zugreifen, das ein untergeordnetes Element der FirstToolWindowControl-Klasse.  
  
 In **Projektmappen-Explorer**mit der rechten Maustaste auf FirstToolWindowControl.xaml, klicken Sie auf **Code anzeigen**, und fügen Sie den folgenden Code der FirstToolWindowControl-Klasse.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Instanziieren Sie das Toolfenster und Symbolleiste  
 Hinzufügen einer Symbolleiste und einen Menübefehl, die aufruft, die **geöffnete Datei** Dialogfeld und gibt die ausgewählten Mediendatei wieder.  
  
1.  Öffnen Sie FirstToolWindow.cs, und fügen Sie die folgenden `using` Anweisungen.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  Fügen Sie einen öffentlichen Verweis auf das Steuerelement FirstToolWindowControl, innerhalb der FirstToolWindow-Klasse.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  Am Ende des Konstruktors setzen Sie diese Steuerelementvariable auf das neu erstellte Steuerelement.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Instanziieren der Symbolleiste innerhalb des Konstruktors an.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  An diesem Punkt sollte der FirstToolWindow-Konstruktor wie folgt aussehen:  
  
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
  
6.  Fügen Sie den Menübefehl auf der Symbolleiste hinzu. Fügen Sie in der Klasse FirstToolWindowCommand.cs Folgendes mit-Anweisung  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  Fügen Sie den folgenden Code am Ende der ShowToolWindow()-Methode, in der FirstToolWindowCommand-Klasse. Der Befehl ButtonHandler wird im nächsten Abschnitt implementiert.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>So implementieren Sie einen Menübefehl in das Toolfenster  
  
1.  Fügen Sie in der Klasse FirstToolWindowCommand eine ButtonHandler-Methode, die aufruft, die **Dateiöffnungsmodus** Dialogfeld. Wenn eine Datei ausgewählt wurde, gibt die Mediendatei wieder.  
  
2.  Fügen Sie in der Klasse FirstToolWindowCommand einen privaten Verweis für die FirstToolWindow-Fenster, das in der FindToolWindow()-Methode erstellt wird.  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Ändern Sie die ShowToolWindow()-Methode, um das Fenster festzulegen, dem Sie oben definiert (sodass Befehlshandler ButtonHandler das Window-Steuerelement zugreifen kann. Hier ist die vollständige ShowToolWindow()-Methode.  
  
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
  
4.  Fügen Sie die ButtonHandler-Methode. Erstellt einen OpenFileDialog für den Benutzer an der Mediendatei zum wiedergegeben werden, und klicken Sie dann die ausgewählte Datei spielt.  
  
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
 Geben Sie anschließend einen Standardspeicherort in der IDE für das Toolfenster an. Konfigurationsinformationen für das Toolfenster sind in der Datei FirstToolWindowPackage.cs.  
  
1.  In FirstToolWindowPackage.cs, suchen die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Attribut für die `FirstToolWindowPackage` -Klasse, die den Typ des FirstToolWindow an den Konstruktor übergibt. Um eine Standardposition anzugeben, müssen Sie weitere Parameter an den Konstruktor mit dem folgenden Beispiel wird hinzufügen.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Der erste benannte Parameter `Style` ist und denselben Wert `Tabbed`, was bedeutet, dass das Fenster einer Registerkarte in ein vorhandenes Fenster ist. Die dockingposition wird angegeben, indem die `Window` Parameter, n diesem Fall die GUID des der **Projektmappen-Explorer**.  
  
    > [!NOTE]
    >  Weitere Informationen zu den Arten von Fenstern in der IDE finden Sie unter <xref:EnvDTE.vsWindowType>.  
  
## <a name="testing-the-tool-window"></a>Testen das Toolfenster  
  
1.  Erstellen, drücken Sie F5, um eine neue Instanz der experimentellen Visual Studio zu öffnen.  
  
2.  Auf der **Ansicht** Sie im Menü **Weitere Fenster** , und klicken Sie dann auf **ersten Toolfenster**.  
  
     Das Media Player-Toolfenster sollten öffnen Sie in der gleichen Position wie **Projektmappen-Explorer**. Wenn es weiterhin in der gleichen Position wie vor dem angezeigt wird, Zurücksetzen des Fensterlayouts (**Fenster / Fensterlayout zurücksetzen**).  
  
3.  Klicken Sie im Toolfenster auf die Schaltfläche "" (er hat das Symbol "Suche"). Wählen Sie eine unterstützte Audio oder video Datei, z. B. C:\windows\media\chimes.wav, drücken Sie dann die **öffnen**.  
  
     Sie sollten den Glockenton Sound hören.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)