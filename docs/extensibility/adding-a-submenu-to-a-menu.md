---
title: "Hinzufügen eines Untermenüs zum Menü | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 19bf2ca98c7ba6227e791a7df44b34aa125cc786
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="adding-a-submenu-to-a-menu"></a>Ein Menü hinzugefügt ein Untermenü
Diese exemplarische Vorgehensweise basiert auf der Demo in [der Visual Studio-Menüleiste ein Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) durch Hinzufügen ein Untermenüs zum Veranschaulichen der **TestMenu** Menü.  
  
 Ein Untermenü ist ein sekundärer Menü, das in einem anderen Menü angezeigt wird. Ein Untermenü kann durch den Pfeil, der den Namen folgt, identifiziert werden. Auf den Namen bewirkt, dass das Untermenü die Option und die zugehörigen Befehle angezeigt werden.  
  
 In dieser exemplarischen Vorgehensweise ein Untermenü in einem Menü in der Menüleiste von Visual Studio erstellt und stellt einen neuen Befehl in das Untermenü. Die exemplarischen Vorgehensweise implementiert auch den neuen Befehl verwenden.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Ein Menü hinzugefügt ein Untermenü  
  
1.  Führen Sie die Schritte in [der Visual Studio-Menüleiste ein Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) auf das Projekt und im Menü-Element zu erstellen. Die Schritte in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSIX-Projekts `TopLevelMenu`.  
  
2.  Öffnen Sie TestCommandPackage.vsct. In der `<Symbols>` Abschnitt, fügen Sie ein `<IDSymbol>` -Element für das Untermenü, der Gruppe "Untermenü" und der Befehl, alle in der `<GuidSymbol>` Knoten mit dem Namen "GuidTopLevelMenuCmdSet." Dies ist der gleichen Knoten, enthält die `<IDSymbol>` -Element für das Menü der obersten Ebene.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Das neu erstellte Untermenü die Option zum Hinzufügen der `<Menus>` Abschnitt.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Das GUID-ID-Paar des übergeordneten Elements gibt Menügruppe, die generiert wurde [der Visual Studio-Menüleiste ein Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), und ist ein untergeordnetes Element des Menüs der obersten Ebene.  
  
4.  Fügen Sie die im Menügruppe definiert, die in Schritt 2, um die `<Groups>` Abschnitt, und stellen Sie es ein untergeordnetes Element des im Untermenü.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Fügen Sie einen neuen `<Button>` Element an der `<Buttons>` Abschnitt aus, um den Befehl in Schritt 2 erstellt haben, als ein Element im Untermenü definieren.  
  
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
  
6.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
7.  Klicken Sie auf **TestMenu** um ein neues Untermenü mit dem Namen finden Sie unter **Untermenü**. Klicken Sie auf **Untermenü** öffnen im Untermenü und Anzeigen eines neuen Befehls **Test Unterbefehl**. Beachten Sie, dass beim Klicken auf **Test Unterbefehl** wird keine Aktion ausgeführt.  
  
## <a name="adding-a-command"></a>Hinzufügen eines Befehls  
  
1.  Öffnen Sie TestCommand.cs, und fügen Sie die folgenden Befehls-ID nach den vorhandenen Befehls-ID.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Fügen Sie der Unterbefehl hinzu. Suchen Sie den Befehl-Konstruktor. Fügen Sie die folgenden Zeilen einfach nach dem Aufruf der `AddCommand` Methode.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     Die `SubItemCallback` Befehlshandler später definiert werden. Der Konstruktor sollte jetzt wie folgt aussehen:  
  
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
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Fügen Sie SubItemCallback() hinzu. Dies ist die Methode, die aufgerufen wird, wenn der neue Befehl im Untermenü geklickt wird.  
  
    ```csharp  
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
  
5.  Auf der **TestMenu** Menü klicken Sie auf **Untermenü** , und klicken Sie dann auf **Test Unterbefehl**. Ein Meldungsfeld angezeigt werden soll, und der Text "Test-Befehl innerhalb TestCommand.SubItemCallback()" angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Menüs auf der Menüleiste von Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
