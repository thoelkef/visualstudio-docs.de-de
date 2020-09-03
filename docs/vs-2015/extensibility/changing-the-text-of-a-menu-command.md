---
title: Ändern des Texts eines Menübefehls | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184491"
---
# <a name="changing-the-text-of-a-menu-command"></a>Ändern des Texts eines Menübefehls
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den folgenden Schritten wird gezeigt, wie die Text Bezeichnung eines Menübefehls mithilfe des- <xref:System.ComponentModel.Design.IMenuCommandService> Dienstanbieter geändert wird.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Ändern einer Menübefehls Bezeichnung mit IMenuCommandService  
  
1. Erstellen Sie ein VSIX-Projekt `MenuText` mit dem Namen mit einem Menübefehl namens **changemenutext**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Fügen Sie in der vstc-Datei dem `TextChanges` Menübefehl das-Flag hinzu, wie im folgenden Beispiel gezeigt.  
  
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
  
3. Erstellen Sie in der Datei ChangeMenuText.cs einen Ereignishandler, der aufgerufen wird, bevor der Menübefehl angezeigt wird.  
  
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
  
     Sie können den Status des Menübefehls in dieser Methode auch aktualisieren, indem Sie die <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> Eigenschaften, und <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> für das- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Objekt ändern.  
  
4. Ersetzen Sie im changemenutext-Konstruktor den ursprünglichen Befehls Initialisierungs-und Platzierungs Code durch Code, der ein-Element <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anstelle eines) erstellt, `MenuCommand` das den Menübefehl darstellt, den Ereignishandler hinzufügt und den Menübefehl <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> an den Menübefehls Dienst übergibt.  
  
     Dies sollte wie folgt aussehen:  
  
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
  
5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
6. **Im Menü Extras** sollte ein Befehl mit dem Namen **changemenutext aufrufen**angezeigt werden.  
  
7. Klicken Sie auf den Befehl. Das Meldungs Feld wird angezeigt, dass MenuItemCallBack aufgerufen wurde. Wenn Sie das Meldungs Feld schließen, sollten Sie sehen, dass der Name des Befehls im Menü Extras nun **neuer Text**ist.
