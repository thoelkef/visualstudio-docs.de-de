---
title: "Hinzufügen eines Kontextmenüs in einem Toolfenster | Microsoft Docs"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 661e31f32f176e48ea69ae92f23ecdde7911456b
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Hinzufügen eines Kontextmenüs in einem Toolfenster
In dieser exemplarischen Vorgehensweise wird ein Kontextmenü in einem Toolfenster. Ein Kontextmenü ist ein Menü, das angezeigt wird, wenn ein Benutzer eine Schaltfläche, das Textfeld oder Fenster im Hintergrund klickt. Befehle im Kontextmenü Verhalten sich wie die Befehle in anderen Menüs oder Symbolleisten. Um ein Kontextmenü zu unterstützen, geben sie in der VSCT-Datei, und zeigen Sie es als Reaktion auf der rechten Maustaste.  
  
 Ein Toolfenster besteht aus einem WPF-Benutzersteuerelement in ein benutzerdefiniertes Tool Fenster-Klasse, die von erben <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht das Erstellen eines Kontextmenüs als Visual Studio-Menü durch Deklarieren der Menüelemente in der VSCT-Datei, und klicken Sie dann mithilfe des Managed Package Framework, die um sie in der Klasse zu implementieren, die das Toolfenster definiert. Dieser Ansatz ermöglicht den Zugriff auf Visual Studio-Befehle, die Elemente der Benutzeroberfläche und das Automatisierungsobjektmodell.  
  
 Wenn Ihre Kontextmenü nicht Visual Studio-Funktionalität zugreifen, Sie können auch die <xref:System.Windows.FrameworkElement.ContextMenu%2A> Eigenschaft einem XAML-Elements im Steuerelement. Weitere Informationen finden Sie unter [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Das Fenster Verknüpfung im Menü USMT-Paket erstellen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TWShortcutMenu` und fügen Sie eine Vorlage für Fenster Tool namens **Kontextmenü** darauf. Weitere Informationen zum Erstellen eines Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Das Kontextmenü angeben  
 Wählen Sie ein Kontextmenü aufrufen, wie z. B. der in dieser exemplarischen Vorgehensweise gezeigten der Benutzer kann aus einer Liste von Farben, die zum Ausfüllen des Toolfensters verwendet werden.  
  
1.  In ShortcutMenuPackage.vsct in dem genannten GuidShortcutMenuPackageCmdSet GuidSymbol-Element sowie das Kontextmenü, Kontextmenü Menügruppe und Menüoptionen deklariert. Das Element GuidSymbol sollte jetzt wie folgt aussehen:  
  
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
  
2.  Unmittelbar vor das Schaltflächen-Element erstellen Sie ein Element für Menüs, und klicken Sie dann definieren Sie im Kontextmenü darin zu.  
  
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
  
     Ein Kontextmenü verfügt keinem übergeordneten Element, da er nicht Teil eines Menüs oder einer Symbolleiste ist.  
  
3.  Erstellen Sie eine Groups-Element mit einem Group-Element, das den Tastenkombinations-Menüelemente enthält, und im Kontextmenü ordnen Sie die Gruppe zu.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Definieren Sie in das Schaltflächen-Element die einzelnen Befehle, die angezeigt werden, werden im Kontextmenü aus. Das Schaltflächen-Element sollte wie folgt aussehen:  
  
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
  
5.  Fügen Sie in ShortcutMenuPackageGuids.cs die Definitionen für den Befehl festgelegten GUID und das Kontextmenü Menüelemente hinzu.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Dies sind die gleichen Befehls-IDs, die im Abschnitt "Symbole" der Datei ShortcutMenuPackage.vsct definiert sind. Der Gruppe "Kontext" ist hier nicht enthalten, da er nur in der VSCT-Datei erforderlich ist.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementieren das Kontextmenü  
 In diesem Abschnitt implementiert das Kontextmenü und die zugehörigen Befehle.  
  
1.  Klicken Sie in ShortcutMenu.cs das Toolfenster der menüdienst-Befehl abrufen kann, aber die darin enthaltenen Steuerelement nicht möglich. Die folgenden Schritte zeigen, wie der Befehl menüdienst auf das Benutzersteuerelement verfügbar zu machen.  
  
2.  In ShortcutMenu.cs, fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Überschreiben Sie das Toolfenster Initialize()-Methode der menüdienst-Befehl, und fügen Sie das Steuerelement, das der menüdienst-Befehl an den Konstruktor übergeben:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Entfernen Sie die Zeile, die das Steuerelement hinzufügt, im Kontextmenü Tool Fenster-Konstruktor. Der Konstruktor sollte jetzt wie folgt aussehen:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  ShortcutMenuControl.xaml.cs fügen Sie ein privates Feld für den Menü-Befehl-Dienst hinzu und ändern Sie den Konstruktor des Steuerelements, um den Befehl menüdienst zu nutzen. Verwenden Sie dann der menüdienst-Befehl, um die Kontextmenübefehle hinzuzufügen. Der Konstruktor ShortcutMenuControl müsste jetzt wie im folgenden Code aussehen. Der Befehlshandler wird später definiert werden.  
  
    ```csharp  
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
  
6.  Fügen Sie in ShortcutMenuControl.xaml, eine <xref:System.Windows.UIElement.MouseRightButtonDown> Ereignis auf der obersten Ebene <xref:System.Windows.Controls.UserControl> Element. Die XAML-Datei sollte nun wie folgt aussehen:  
  
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
  
7.  Fügen Sie in ShortcutMenuControl.xaml.cs einen Stub für den Ereignishandler hinzu.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Fügen Sie die folgenden using-Anweisungen auf dieselbe Datei:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementieren der `MyToolWindowMouseRightButtonDown` Ereignis wie folgt.  
  
    ```csharp  
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
  
     Dies erstellt eine <xref:System.ComponentModel.Design.CommandID> Objekt für das Kontextmenü, gibt die Position des Mausklicks und öffnet das Kontextmenü an diesem Speicherort mithilfe der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> Methode.  
  
10. Implementieren Sie die Befehlshandler.  
  
    ```csharp  
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
  
     In diesem Fall behandelt nur eine Methode Ereignisse für alle Menüelemente durch Identifizieren der <xref:System.ComponentModel.Design.CommandID> und die Farbe des Hintergrunds entsprechend festlegen. Wenn die Menüelemente nicht verknüpfte Befehle enthalten ist, würden Sie einen separaten Ereignishandler für jeden Befehl erstellt haben.  
  
## <a name="testing-the-tool-window-features"></a>Testen die Tool-Fenster-Funktionen  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2.  Klicken Sie in der experimentellen Instanz auf **Ansicht / Weitere Fenster**, und klicken Sie dann auf **Kontextmenü**. Dadurch sollte Ihr Toolfenster angezeigt werden.  
  
3.  Mit der rechten Maustaste im Text des Toolfensters. Ein Kontextmenü aufrufen, die eine Liste von Farben aufweist, sollte angezeigt werden.  
  
4.  Klicken Sie auf eine Farbe im Kontextmenü. Die Hintergrundfarbe des Tool-Fenster sollte in der ausgewählten Farbe geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
