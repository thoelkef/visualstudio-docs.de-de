---
title: Hinzufügen eines Untermenüs zu einem Menü | Microsoft-Dokumentation
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
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14ad9d2daf603dd2ca80a784251f19503fee1cba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738313"
---
# <a name="adding-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf der Demo in [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) durch Hinzufügen ein Untermenüs zum Veranschaulichen der **TestMenu** Menü.  
  
 Ein Untermenü handelt es sich um ein sekundäres Menü, das in einem anderen Menü angezeigt wird. Ein Untermenü kann durch den Pfeil, der den Namen folgt, identifiziert werden. Auf den Namen des bewirkt, dass das Untermenü und die Befehle, die angezeigt werden.  
  
 In dieser exemplarischen Vorgehensweise wird ein Untermenü in einem Menü auf der Menüleiste von Visual Studio erstellt und fügt einen neuen Befehl im Untermenü. In der exemplarischen Vorgehensweise implementiert auch den neuen Befehl.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü  
  
1.  Führen Sie die Schritte in [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) auf das Projekt und im Menü-Element zu erstellen. Die Schritte in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSIX-Projekts `TopLevelMenu`.  
  
2.  Öffnen Sie TestCommandPackage.vsct. In der `<Symbols>` Abschnitt, fügen Sie eine `<IDSymbol>` -Element für das Untermenü für die Untermenü-Gruppe und eine für den Befehl aus, in der `<GuidSymbol>` Knoten mit dem Namen "GuidTopLevelMenuCmdSet." Dies ist der gleiche Knoten, enthält die `<IDSymbol>` -Element für das Menü der obersten Ebene.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Fügen Sie die neu erstellte Untermenü die `<Menus>` Abschnitt.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Der GUID-ID-Paar des übergeordneten Elements gibt an, die Menügruppe, die generiert wurde [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), und ist ein untergeordnetes Element des Menüs der obersten Ebene.  
  
4.  Fügen Sie die Menügruppe, die in Schritt 2 definiert die `<Groups>` aus, und stellen sie ein untergeordnetes Element des Untermenüs.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Fügen Sie einen neuen `<Button>` Element, das `<Buttons>` Abschnitt aus, um den Befehl in Schritt 2 erstellt haben, als ein Element im Untermenü definieren.  
  
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
  
6.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollten angezeigt werden.  
  
7.  Klicken Sie auf **TestMenu** um ein neues Untermenü mit dem Namen finden Sie unter **Untermenü**. Klicken Sie auf **Untermenü** , öffnen Sie das Untermenü, und sehen einen neuen Befehl, **Sub-Testbefehl**. Beachten Sie, dass beim Klicken auf **Sub-Testbefehl** hat keine Auswirkungen.  
  
## <a name="adding-a-command"></a>Hinzufügen eines Befehls  
  
1.  Öffnen Sie TestCommand.cs, und fügen Sie die folgenden Befehls-ID nach der vorhandenen Befehls-ID.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Fügen Sie der Unterbefehl hinzu. Suchen Sie den Befehl-Konstruktor. Fügen Sie die folgenden Zeilen direkt nach dem Aufruf von der `AddCommand` Methode.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
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
  
3.  Fügen Sie SubItemCallback() hinzu. Dies ist die Methode, die aufgerufen wird, wenn auf der neue Befehl im Untermenü geklickt wird.  
  
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
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.  
  
5.  Auf der **TestMenu** Menü klicken Sie auf **Untermenü** , und klicken Sie dann auf **Sub-Testbefehl**. Ein Meldungsfeld angezeigt werden soll, und der Text, "Test-Befehl in TestCommand.SubItemCallback()" angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)

