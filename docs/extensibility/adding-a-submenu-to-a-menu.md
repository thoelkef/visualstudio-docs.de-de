---
title: "Hinzuf&#252;gen eines Untermen&#252;s zu einem Men&#252; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Kontextmenüs"
  - "Kaskadierende Untermenüs"
  - "Kaskadierende Untermenüs"
  - "Menüs cascading Untermenüs erstellen"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 43
---
# Hinzuf&#252;gen eines Untermen&#252;s zu einem Men&#252;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf der Demo in [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) wie ein Untermenü hinzufügen der **TestMenu** Menü.  
  
 Ein Untermenü handelt es sich um ein sekundäres Menü, das in einem anderen Menü angezeigt wird. Ein Untermenü kann durch den Pfeil, der den Namen folgt, identifiziert werden. Der Name wird im Untermenü und die zugehörigen Befehle angezeigt werden.  
  
 In dieser exemplarischen Vorgehensweise erstellt ein Untermenü in einem Menü auf der Menüleiste von Visual Studio und stellt einen neuen Befehl in das Untermenü. Die exemplarische Vorgehensweise implementiert außerdem den neuen Befehl.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Hinzufügen eines Untermenüs zu einem Menü  
  
1.  Führen Sie die Schritte im [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) auf das Projekt und im Menü\-Element zu erstellen. Die Schritte in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSIX\-Projekts `TopLevelMenu`.  
  
2.  Öffnen Sie TestCommandPackage.vsct. In der `<Symbols>` enthält, fügen ein `<IDSymbol>` \-Element für das Untermenü für die Gruppe im Untermenü und eine für den Befehl in der `<GuidSymbol>` Knoten mit dem Namen "GuidTopLevelMenuCmdSet." Dies ist der gleiche Knoten, enthält das `<IDSymbol>` \-Element für das Menü der obersten Ebene.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Fügen Sie das neu erstellte Untermenü der `<Menus>` Abschnitt.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Die GUID\-ID\-Paar des übergeordneten Elements gibt Menügruppe, die generiert wurde [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), und klicken Sie im Menü der obersten Ebene untergeordnet ist.  
  
4.  Fügen Sie die Menügruppe in Schritt 2 definiert die `<Groups>` aus, und stellen Sie es ein untergeordnetes Element der im Untermenü.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Fügen Sie einen neuen `<Button>` Element, das `<Buttons>` Abschnitt den Befehl in Schritt 2 erstellt haben, als ein Element auf das Untermenü definiert.  
  
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
  
6.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
7.  Klicken Sie auf **TestMenu** ein neues Untermenü mit dem Namen finden Sie unter **Untermenü**. Klicken Sie auf **Untermenü** im Untermenü öffnen und einen neuen Befehl, **Test Unterbefehl**. Beachten Sie, dass beim Klicken auf **Test Unterbefehl** wird keine Aktion ausgeführt.  
  
## Hinzufügen eines Befehls  
  
1.  Öffnen Sie TestCommand.cs, und fügen Sie die folgenden Befehls\-ID nach der vorhandenen Befehls\-ID.  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Fügen Sie der Unterbefehl hinzu. Suchen Sie den Befehl\-Konstruktor. Fügen Sie die folgenden Zeilen direkt nach dem Aufruf an die `AddCommand` Methode.  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     Die `SubItemCallback` Befehlshandler später definiert werden. Der Konstruktor sollte jetzt wie folgt aussehen:  
  
    ```c#  
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
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Fügen Sie SubItemCallback\(\) hinzu. Dies ist die Methode, die aufgerufen wird, wenn der neue Befehl im Untermenü geklickt wird.  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
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
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
5.  Auf der **TestMenu** Menü klicken Sie auf **Untermenü** und klicken Sie dann auf **Test Unterbefehl**. Ein Meldungsfeld angezeigt werden soll, und der Text "Test\-Befehl in TestCommand.SubItemCallback\(\)" angezeigt.  
  
## Siehe auch  
 [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)