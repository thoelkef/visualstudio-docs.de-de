---
title: "Hinzuf&#252;gen eines Toolfensters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lernprogramme"
  - "Toolfenster"
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 52
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 52
---
# Hinzuf&#252;gen eines Toolfensters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erfahren Sie, wie ein Toolfenster erstellen und seine Integration in Visual Studio auf folgende Weise:  
  
-   Fügen Sie ein Steuerelement, um das Toolfenster.  
  
-   Ein Toolfenster eine Symbolleiste hinzugefügt.  
  
-   Hinzufügen eines Befehls auf der Symbolleiste.  
  
-   Die Befehle zu implementieren.  
  
-   Legen Sie die Standardposition für das Toolfenster.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines Toolfensters  
  
1.  Erstellen Sie ein Projekt mit dem Namen **FirstToolWin** mithilfe der VSIX\-Projektvorlage, und fügen Sie eine benutzerdefiniertes Tool Fenster Elementvorlage, die mit dem Namen **FirstToolWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von einer Erweiterungs mit einem Toolfenster, finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Hinzufügen eines Steuerelements zum Toolfenster  
  
1.  Entfernen Sie das standardmäßige Steuerelement. Öffnen Sie FirstToolWindowControl.xaml und Löschen der **Click Me\!** Schaltfläche.  
  
2.  In der **Toolbox**, erweitern Sie die **alle WPF\-Steuerelemente** hinzu, und ziehen Sie die **Medienelement** die Steuerung an die **FirstToolWindowControl** Form. Wählen Sie das Steuerelement, und klicken Sie in der **Eigenschaften** Fenster nennen Sie dieses Element **mediaElement1**.  
  
## Hinzufügen einer Symbolleiste zum Toolfenster  
 Durch Hinzufügen einer Symbolleiste auf folgende Weise, garantieren, dass die Farbverläufe und die Farben mit dem Rest der IDE konsistent sind.  
  
1.  In **Projektmappen\-Explorer**, FirstToolWindowPackage.vsct zu öffnen. Die VSCT\-Datei definiert die GUI\-Elemente der Benutzeroberfläche \(GUI\) in das Toolfenster mit XML.  
  
2.  In der `<Symbols>` im Abschnitt, suchen Sie nach der `<GuidSymbol>` Knoten, deren `name` Attribut `guidFirstToolWindowPackageCmdSet`. Fügen Sie die folgenden beiden `<IDSymbol>` Elemente der Liste der `<IDSymbol>` Elemente in diesem Knoten eine Symbolleiste und eine Symbolleistengruppe definieren.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Direkt oberhalb der `<Buttons>` im Abschnitt, erstellen Sie ein `<Menus>` Abschnitt die folgende angezeigt:  
  
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
  
     Es gibt verschiedene Arten von Menüs. Dieses Menü ist eine Symbolleiste in einem Toolfenster definiert seine `type` Attribut. Die `guid` und  `id` Einstellungen bilden die vollqualifizierte ID der Symbolleiste. In der Regel die `<Parent>` eines Menüs wird die Gruppe. Allerdings wird eine Symbolleiste als eigenen übergeordneten Elements definiert. Daher wird der gleiche Bezeichner für die `<Menu>` und `<Parent>` Elemente. Das `priority` \-Attribut ist nur ' 0'.  
  
4.  Symbolleisten, Menüs in vielerlei Hinsicht ähneln. Z. B. wie ein Menü Befehlsgruppen haben, können Symbolleisten auch Gruppen angehören. \(In Menüs, werden die Befehlsgruppen durch horizontale Linien getrennt. Auf Symbolleisten werden die Gruppen nicht durch visual Zeilenunterteiler getrennt.\)  
  
     Hinzufügen einer `<Groups>` Abschnitt mit einer `<Group>` Element. Definiert die Gruppe, deren ID, die Sie in der deklariert die `<Symbols>` Abschnitt. Hinzufügen der `<Groups>` im Abschnitt nach der `<Menus>` Abschnitt.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Das übergeordnete GUID und ID auf die GUID und ID der Symbolleiste festlegen, wird die Symbolleiste der Gruppe hinzugefügt.  
  
## Hinzufügen eines Befehls zu einer Symbolleiste  
 Hinzufügen eines Befehls auf die Symbolleiste, die als eine Schaltfläche angezeigt wird.  
  
1.  In der `<Symbols>` im Abschnitt, deklarieren Sie die folgenden IDSymbol\-Elemente direkt hinter der Symbolleiste und Symbolleiste Gruppendeklarationen.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Fügen Sie ein Button\-Element innerhalb der `<Buttons>` Abschnitt. Dieses Element wird auf der Symbolleiste im Toolfenster mit einem Suchsymbol \(Vergrößerungsglas\) angezeigt.  
  
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
  
3.  Öffnen Sie FirstToolWindowCommand.cs, und fügen Sie die folgenden Zeilen direkt nach der vorhandenen Felder in der Klasse.  
  
    ```c#  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     Auf diese Weise wird die Befehle in Code verfügbar.  
  
## Hinzufügen einer MediaPlayer\-Eigenschaft zu FirstToolWindowControl  
 Über den\-Ereignishandler für das Symbolleisten\-Steuerelemente muss Code auf die Media Player\-Steuerelement zugreifen, das ein untergeordnetes Element der FirstToolWindowControl\-Klasse.  
  
 In **Projektmappen\-Explorer**, mit der rechten Maustaste auf FirstToolWindowControl.xaml, klicken Sie auf **Anzeigecode**, und fügen Sie den folgenden Code zur FirstToolWindowControl\-Klasse.  
  
```c#  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## Instanziieren Sie das Toolfenster und Symbolleiste  
 Hinzufügen einer Symbolleiste und einen Menübefehl, der aufruft der **geöffnete Datei** Dialogfeld ausgewählten Mediendatei abgespielt.  
  
1.  Öffnen Sie FirstToolWindow.cs, und fügen Sie die folgenden `using` Anweisungen.  
  
    ```c#  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  Fügen Sie einen öffentlichen Verweis auf das Steuerelement FirstToolWindowControl, innerhalb der FirstToolWindow\-Klasse.  
  
    ```c#  
    public FirstToolWindowControl control;  
    ```  
  
3.  Am Ende des Konstruktors legen Sie dieses Steuerelementvariable auf das neu erstellte Steuerelement.  
  
    ```c#  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Die Symbolleiste innerhalb des Konstruktors zu instanziieren.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  An diesem Punkt sollte der FirstToolWindow\-Konstruktor wie folgt aussehen:  
  
    ```c#  
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
  
6.  Fügen Sie den Menübefehl auf der Symbolleiste. Fügen Sie in der FirstToolWindowCommand.cs\-Klasse die folgende using\-Anweisung  
  
    ```c#  
    using System.Windows.Forms;  
    ```  
  
7.  Fügen Sie den folgenden Code am Ende der ShowToolWindow\(\)\-Methode, in der FirstToolWindowCommand\-Klasse. Mit dem Befehl ButtonHandler wird im nächsten Abschnitt implementiert.  
  
    ```c#  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### Implementieren Sie einen Befehl im Toolfenster  
  
1.  Fügen Sie in der FirstToolWindowCommand\-Klasse eine ButtonHandler\-Methode, die aufruft, die **geöffnete Datei** Dialogfeld. Wenn eine Datei ausgewählt wurde, gibt die Mediendatei wieder.  
  
2.  Fügen Sie einen privaten Verweis zum FirstToolWindow\-Fenster, das in der FindToolWindow\(\)\-Methode erstellt wird, in der FirstToolWindowCommand\-Klasse.  
  
    ```c#  
    private FirstToolWindow window;  
    ```  
  
3.  Ändern Sie die ShowToolWindow\(\)\-Methode zum Festlegen des oben definierten \(sodass der Befehlshandler ButtonHandler das Fenstersteuerelement zugreifen kann. Hier ist die vollständige ShowToolWindow\(\)\-Methode.  
  
    ```c#  
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
  
4.  Fügen Sie die ButtonHandler\-Methode. Erstellt einen OpenFileDialog für den Benutzer an die Mediendatei wiedergegeben und spielt anschließend die ausgewählte Datei.  
  
    ```c#  
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
  
## Legen Sie die Standardposition für das Toolfenster  
 Geben Sie anschließend einen Standardspeicherort in der IDE für das Toolfenster. Konfigurationsinformationen für das Toolfenster ist in der Datei FirstToolWindowPackage.cs.  
  
1.  Suchen in FirstToolWindowPackage.cs, die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> \-Attribut für die `FirstToolWindowPackage` \-Klasse, die den Typ des FirstToolWindow an den Konstruktor übergibt. Eine Standardposition angeben, müssen Sie weitere Parameter an den Konstruktor mit dem folgenden Beispiel hinzufügen.  
  
    ```c#  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Der erste benannte Parameter ist `Style` und sein Wert ist `Tabbed`, was bedeutet, dass das Fenster mit einer Registerkarte in ein vorhandenes Fenster werden. Die dockingposition wird angegeben, indem die `Window` Parameter, n diesem Fall die GUID für die **Projektmappen\-Explorer**.  
  
    > [!NOTE]
    >  Weitere Informationen zu den in der IDE finden Sie unter <xref:EnvDTE.vsWindowType>.  
  
## Testen das Toolfenster  
  
1.  Erstellen, drücken Sie F5, um eine neue Instanz der experimentellen Visual Studio zu öffnen.  
  
2.  Auf der **Ansicht** auf **Weitere Fenster** und klicken Sie dann auf **erste Toolfenster**.  
  
     Das Media Player\-Toolfenster in der gleichen Position wie öffnen sollten **Projektmappen\-Explorer**. Wenn es weiterhin in der gleichen Position wie zuvor angezeigt wird, das Fensterlayout zurücksetzen \(**Fenster \/ Fensterlayout zurücksetzen**\).  
  
3.  Klicken Sie \(über das Symbol suchen\) im Toolfenster. Wählen Sie eine unterstützte Audio\- oder Videodatei Datei, z. B. C:\\windows\\media\\chimes.wav, drücken Sie dann die **Öffnen**.  
  
     Sie sollten den Glockenton Sound hören.  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)