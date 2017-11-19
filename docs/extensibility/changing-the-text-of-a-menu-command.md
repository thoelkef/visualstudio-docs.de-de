---
title: "Ändern den Text eines Menübefehls | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65e7d3d4e3d9a4034a948ee0fa094efbb45b6a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-text-of-a-menu-command"></a>Ändern den Text eines Menübefehls
Die folgenden Schritte zeigen, so ändern Sie die Beschriftung eines Menübefehls mithilfe der <xref:System.ComponentModel.Design.IMenuCommandService> Dienst.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Ändern einen Befehl menübezeichnung mit der IMenuCommandService  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `MenuText` eines Menübefehls mit dem Namen **ChangeMenuText**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Fügen Sie in der Datei .vstc die `TextChanges` flag auf den Menübefehl, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Erstellen Sie einen Ereignishandler, der aufgerufen wird, bevor der Menübefehl angezeigt wird, in der Datei ChangeMenuText.cs.  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     Sie können auch den Status des Menübefehls in dieser Methode aktualisieren, durch Ändern der <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, und <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Eigenschaften auf der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Objekt.  
  
4.  Ersetzen Sie den ursprünglichen Befehl Initialisierung und Platzierung der Code im Konstruktor ChangeMenuText mit Code, der erstellt eine <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anstelle eines `MenuCommand`), die den Menübefehl darstellt, fügt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler, und erhalten Sie im Menü Befehl, der menüdienst-Befehl.  
  
     Hier ist, wie es aussehen sollte:  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
6.  Auf der **Tools** Menü sehen Sie einen Befehl mit dem Namen **aufrufen ChangeMenuText**.  
  
7.  Klicken Sie auf den Befehl. Daraufhin sollte die Meldung an, das angibt, dass es sich bei MenuItemCallback aufgerufen wurde. Wenn Sie das Meldungsfeld schließen, sollte angezeigt werden, dass der Name des Befehls auf das Menü "Extras" jetzt **neuen Text**.
