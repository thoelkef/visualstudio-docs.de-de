---
title: Hinzufügen eines Kontextmenüs in einem Toolfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 179a103475a47be95cbf45f88640b8a635a7ff34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796219"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Hinzufügen eines Kontextmenüs in einem Toolfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird ein Kontextmenü in einem Toolfenster. Ein Kontextmenü wird ein Menü, das angezeigt wird, wenn ein Benutzer eine Schaltfläche, im Textfeld oder Fensterhintergrund klickt. Befehle im Kontextmenü der Verhalten sich wie die Befehle auf anderen Menüs oder Symbolleisten. Um ein Kontextmenü zu unterstützen, geben Sie es in der VSCT-Datei, und als Reaktion auf der rechten Maustaste anzuzeigen.  
  
 Ein Toolfenster besteht aus einer WPF-Benutzersteuerelement in ein benutzerdefiniertes Tool-Fenster-Klasse, die von erbt <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie ein Kontextmenü als ein Visual Studio-Menü Menüelemente in der VSCT-Datei zu deklarieren und dann dem Managed Package Framework, die sie in der Klasse implementieren, die das Fenster definiert. Dieser Ansatz ermöglicht den Zugriff auf Visual Studio-Befehle, Elemente der Benutzeroberfläche und das Automatisierungsobjektmodell.  
  
 Wenn Ihr Kontextmenü nicht Visual Studio-Funktionen zugreifen, Sie können auch die <xref:System.Windows.FrameworkElement.ContextMenu%2A> Eigenschaft eines XAML-Elements im Steuerelement. Weitere Informationen finden Sie unter [ContextMenu](http://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Erstellen die Verknüpfung im Menü-Fensterpakets  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TWShortcutMenu` und fügen Sie eine Tool-Fenster-Vorlage mit dem Namen **Kontextmenü** zuzuweisen. Weitere Informationen zum Erstellen eines Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Im Kontextmenü den Befehl angeben  
 Wählen Sie ein Kontextmenü aufrufen, wie z. B. in dieser exemplarischen Vorgehensweise gezeigt mit der Benutzer kann aus einer Liste von Farben, die verwendet werden, um den Hintergrund des Toolfensters zu füllen.  
  
1.  Finden Sie in ShortcutMenuPackage.vsct in der GuidSymbol-Element, das mit dem Namen GuidShortcutMenuPackageCmdSet und im Kontextmenü, Kontextmenü Menügruppe und Menüoptionen deklariert. GuidSymbol-Element sollte jetzt wie folgt aussehen:  
  
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
  
2.  Erstellen Sie ein Element des Menüs, und definieren Sie dann im Kontextmenü den Befehl in ihr, unmittelbar vor dem Element Schaltflächen.  
  
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
  
     Ein Kontextmenü muss ein übergeordnetes Element nicht, da er nicht Teil von einem Menü oder Symbolleiste ist.  
  
3.  Erstellen Sie einer Groups-Element mit einem Group-Element, das die Elemente des Kontextmenüs enthält, und im Kontextmenü ordnen Sie die Gruppe zu.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Definieren Sie in das Schaltflächen-Element die einzelnen Befehle, die angezeigt werden, werden im Kontextmenü aus. Das Schaltflächen-Element sollte folgendermaßen aussehen:  
  
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
  
5.  Fügen Sie in ShortcutMenuPackageGuids.cs, dass die Definitionen für den Befehl GUID, die im Kontextmenü den Befehl und die Menüelemente festgelegt.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Dies sind die gleichen Befehls-IDs, die in den Abschnitt "Symbols" der Datei ShortcutMenuPackage.vsct definiert sind. Der Gruppe "Kontext" ist hier nicht enthalten, da er nur in der VSCT-Datei erforderlich ist.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementieren das Kontextmenü  
 In diesem Abschnitt werden die im Kontextmenü den Befehl und seine Befehle implementiert.  
  
1.  Klicken Sie in ShortcutMenu.cs das Toolfenster der Menübefehlsdienst erhalten, aber die darin enthaltenen Steuerelement nicht möglich. Die folgenden Schritte zeigen, wie der Menübefehlsdienst auf das Benutzersteuerelement verfügbar gemacht wird.  
  
2.  ShortcutMenu.cs, fügen Sie die folgende using-Anweisungen:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Überschreiben Sie die Initialize()-Methode des Toolfensters, zum Abrufen der Menübefehlsdienst und zum Hinzufügen des Steuerelements, dem Menübefehlsdienst an den Konstruktor übergeben:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Entfernen Sie in den Konstruktor der Kontextmenü-Tool-Fenster die Zeile, die das Steuerelement hinzufügt. Der Konstruktor sollte jetzt wie folgt aussehen:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  Klicken Sie in ShortcutMenuControl.xaml.cs fügen Sie ein privates Feld für die Menübefehlsdienst hinzu, und ändern Sie den Konstruktor des Steuerelements, um dem Menübefehlsdienst zu nutzen. Verwenden Sie dann dem Menübefehlsdienst, um die Kontextmenübefehle hinzuzufügen. Der Konstruktor ShortcutMenuControl sollte jetzt wie im folgenden Code aussehen. Die Befehlshandler wird weiter unten definiert.  
  
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
  
6.  Fügen Sie in ShortcutMenuControl.xaml, eine <xref:System.Windows.UIElement.MouseRightButtonDown> Ereignis auf der obersten Ebene <xref:System.Windows.Controls.UserControl> Element. Die XAML-Datei sollte jetzt wie folgt aussehen:  
  
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
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Fügen Sie die folgenden using-Anweisungen in dieselbe Datei:  
  
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
  
     Dies erstellt eine <xref:System.ComponentModel.Design.CommandID> Objekt für das Kontextmenü identifiziert die Position des Mausklicks und öffnet Sie das Kontextmenü an diesem Speicherort mithilfe der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> Methode.  
  
10. Implementieren der Befehlshandler.  
  
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
  
     In diesem Fall nur eine Methode Ereignisse für alle Menüelemente behandelt, durch das Identifizieren der <xref:System.ComponentModel.Design.CommandID> und die Hintergrundfarbe entsprechend festlegen. Wenn die Menüelemente unabhängigen Befehle enthalten ist, würden Sie einen separaten Ereignishandler für jeden Befehl erstellt haben.  
  
## <a name="testing-the-tool-window-features"></a>Testen der Tool-Fenster-Features  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2.  Klicken Sie in der experimentellen Instanz auf **anzeigen / Other Windows**, und klicken Sie dann auf **Kontextmenü**. Dadurch sollte das Toolfenster angezeigt werden.  
  
3.  Mit der rechten Maustaste in den Text des Toolfensters. Ein Kontextmenü, das eine Liste der Farben enthält, sollte angezeigt werden.  
  
4.  Klicken Sie auf eine Farbe im Kontextmenü auf. Hintergrundfarbe des Tool sollte auf die ausgewählte Farbe geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)

