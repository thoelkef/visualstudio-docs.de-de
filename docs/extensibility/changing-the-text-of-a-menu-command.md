---
title: "&#196;ndern des Texts eines Men&#252;befehls | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Menüs, Ändern von text"
  - "Text, Menüs"
  - "Befehle, Ändern von text"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# &#196;ndern des Texts eines Men&#252;befehls
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden Schritte zeigen, wie ändern Sie die Beschriftung eines Menübefehls mithilfe der <xref:System.ComponentModel.Design.IMenuCommandService> Service.  
  
## Eine Bezeichnung im Menü Befehl, mit dem IMenuCommandService ändern  
  
1.  Erstellen Sie ein VSIX\-Projekt mit dem Namen `MenuText` einen Befehl mit dem Namen **ChangeMenuText**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
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
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     Sie können auch den Status des Menübefehls in dieser Methode aktualisieren, durch Ändern der <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, und <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Eigenschaften für die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Objekt.  
  
4.  Ersetzen Sie den ursprünglichen Befehl Initialisierung und Platzierung der Code im Konstruktor ChangeMenuText mit Code, der erstellt ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(anstelle eines `MenuCommand`\), die den Befehl darstellt, fügt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> \-Ereignishandler und bietet den Menübefehl zum Dienst Befehl im Menü.  
  
     Hier wird es aussehen sollte:  
  
    ```c#  
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
  
6.  Auf der **Tools** Menü sollte einen Befehl mit dem Namen **aufrufen ChangeMenuText**.  
  
7.  Klicken Sie auf den Befehl. Daraufhin sollte die Nachricht an, das angibt, dass es sich bei MenuItemCallback aufgerufen wurde. Wenn Sie das Meldungsfeld schließen, sollten Sie sehen, dass jetzt der Name des Befehls im Menü Extras ist **neuen Text**.