---
title: "Hinzufügen eines Kontextmenüs in einem Toolfenster | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ab921bec73528be7207baebdf9cb31885e2253fd
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Hinzufügen eines Kontextmenüs in einem Toolfenster
In dieser exemplarischen Vorgehensweise wird ein Kontextmenü in einem Toolfenster. Ein Kontextmenü ist ein Menü, das angezeigt wird, wenn ein Benutzer eine Schaltfläche, das Textfeld oder Hintergrund klickt. Befehle im Kontextmenü weisen das gleiche Verhalten wie die Befehle in anderen Menüs oder Symbolleisten. Um ein Kontextmenü zu unterstützen, geben Sie es in der VSCT-Datei und deren Anzeige in Antwort auf der rechten Maustaste.  
  
 Ein Toolfenster besteht aus einem WPF-Benutzersteuerelement in ein benutzerdefiniertes Tool Fensterklasse, die von <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> erbt  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht, wie ein Kontextmenü als Visual Studio-Menü erstellen, deklarieren Elemente in der VSCT-Datei, und dann die Managed Package Framework zur Implementierung in der Klasse, die das Toolfenster definiert. Dieser Ansatz ermöglicht den Zugriff auf Visual Studio-Befehle, Elemente der Benutzeroberfläche und das Automatisierungsobjektmodell.  
  
 Wenn die im Kontextmenü nicht Visual Studio-Funktionen zugreifen, Sie können auch die <xref:System.Windows.FrameworkElement.ContextMenu%2A>Eigenschaft eines XAML-Elements im Benutzersteuerelement.</xref:System.Windows.FrameworkElement.ContextMenu%2A> Weitere Informationen finden Sie unter [ContextMenu](http://msdn.microsoft.com/Library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Erstellen des Pakets im Menü für Fenster-Kontextmenü-Tool  
  
1.  Erstellen Sie ein VSIX-Projekt namens `TWShortcutMenu` und fügen Sie eine Vorlage für Fenster Tool namens **Kontextmenü** darauf. Weitere Informationen zum Erstellen eines Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Das Kontextmenü angeben  
 Wählen Sie ein Kontextmenü mit Optionen wie z. B. der in dieser exemplarischen Vorgehensweise gezeigten der Benutzer kann aus einer Liste von Farben, die zum Ausfüllen des Toolfensters verwendet werden.  
  
1.  Suchen Sie in ShortcutMenuPackage.vsct in der GuidSymbol-Element, das mit dem Namen GuidShortcutMenuPackageCmdSet und im Kontextmenü, Verknüpfung Menügruppe und Menüoptionen deklariert. Das GuidSymbol-Element sollte jetzt wie folgt aussehen:  
  
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
  
2.  Unmittelbar vor dem Element Schaltflächen erstellen Sie ein Element des Menüs, und definieren Sie dann im Kontextmenü darin.  
  
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
  
     Ein Kontextmenü muss kein übergeordnetes Element, da er nicht von einem Menü oder einer Symbolleiste gehört.  
  
3.  Erstellen Sie eine Gruppen-Element mit einem Group-Element, Kontextmenüs enthält, und ordnen Sie der Gruppe mit dem Kontextmenü.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Definieren Sie im Schaltflächen-Element die einzelnen Befehle, die angezeigt wird, im Kontextmenü auf. Das Schaltflächen-Element sollte wie folgt aussehen:  
  
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
  
5.  Fügen Sie in ShortcutMenuPackageGuids.cs die Definitionen für den Befehl GUID und im Kontextmenü Menüelemente festgelegt.  
  
    ```c#  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Dies sind die gleichen Befehls-IDs, die im Abschnitt "Symbole" der Datei ShortcutMenuPackage.vsct definiert sind. Die Kontextgruppe ist hier nicht enthalten, da es nur in der VSCT-Datei erforderlich ist.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementieren das Kontextmenü  
 In diesem Abschnitt wird das Kontextmenü und die zugehörigen Befehle implementiert.  
  
1.  Klicken Sie im ShortcutMenu.cs das Toolfenster kann den Menü-Befehl-Dienst abrufen, jedoch nicht das Steuerelement, das es enthält. Die folgenden Schritte zeigen, wie den Befehl-Dienst im Menü auf das Benutzersteuerelement verfügbar gemacht wird.  
  
2.  ShortcutMenu.cs, fügen Sie folgende using-Anweisungen:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Überschreiben Sie das Toolfenster Initialize()-Methode Menü Befehl-Dienst, und fügen Sie das Steuerelement, den Dienst im Menü Befehl an den Konstruktor übergeben:  
  
    ```c#  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Entfernen Sie die Zeile, die das Steuerelement hinzufügt, im Kontextmenü Tool-Fenster-Konstruktor. Der Konstruktor sollte jetzt wie folgt aussehen:  
  
    ```c#  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  ShortcutMenuControl.xaml.cs fügen Sie ein privates Feld für den Menü-Befehl-Dienst hinzu und ändern Sie den Konstruktor des Steuerelements, um den Dienst im Menü Befehl ausgeführt werden. Verwenden Sie dann den Befehl-Dienst im Menü Kontextmenübefehle hinzufügen. Der Konstruktor ShortcutMenuControl sollte jetzt wie im folgenden Code aussehen. Der Befehlshandler wird später definiert werden.  
  
    ```c#  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  Fügen Sie in ShortcutMenuControl.xaml, ein <xref:System.Windows.UIElement.MouseRightButtonDown>Ereignis auf der obersten Ebene <xref:System.Windows.Controls.UserControl>Element.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.UIElement.MouseRightButtonDown> Die XAML-Datei sollte nun folgendermaßen aussehen:  
  
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
  
7.  Fügen Sie in ShortcutMenuControl.xaml.cs einen Stub für den Ereignishandler ein.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Fügen Sie die folgende using-Anweisungen in derselben Datei:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementieren der `MyToolWindowMouseRightButtonDown` Ereignis wie folgt.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Auf diese Weise erstellt ein <xref:System.ComponentModel.Design.CommandID>Objekt für das Kontextmenü gibt die Position des Mausklicks und öffnet das Kontextmenü an diesem Speicherort mithilfe der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>-Methode.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> </xref:System.ComponentModel.Design.CommandID>  
  
10. Implementieren Sie den Befehlshandler.  
  
    ```c#  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     In diesem Fall behandelt nur eine Methode Ereignisse für alle Menüelemente durch Identifizieren der <xref:System.ComponentModel.Design.CommandID>und die Hintergrundfarbe entsprechend festlegen.</xref:System.ComponentModel.Design.CommandID> Wenn die Menüelemente unabhängigen Befehle enthalten ist, würden Sie einen separaten Ereignishandler für jeden Befehl erstellt haben.  
  
## <a name="testing-the-tool-window-features"></a>Testen der Funktionen der Tool-Fenster  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2.  Klicken Sie in der experimentellen Instanz auf **anzeigen / andere Fenster**, und klicken Sie dann auf **Kontextmenü**. Dadurch sollte das Toolfenster angezeigt werden.  
  
3.  Mit der rechten Maustaste im Text des Toolfensters. Ein Kontextmenü, das eine Liste von Farben enthält, sollte angezeigt werden.  
  
4.  Klicken Sie auf eine Farbe im Kontextmenü. Hintergrundfarbe des Tool sollte in der ausgewählten Farbe geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)
