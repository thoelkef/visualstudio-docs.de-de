---
title: Ändern des Textes eines Menübefehls | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739846"
---
# <a name="change-the-text-of-a-menu-command"></a>Ändern des Textes eines Menübefehls
Die folgenden Schritte zeigen, wie Sie die Textbeschriftung <xref:System.ComponentModel.Design.IMenuCommandService> eines Menübefehls mithilfe des Dienstes ändern.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Ändern einer Menübefehlsbezeichnung mit dem IMenuCommandService

1. Erstellen Sie ein `MenuText` VSIX-Projekt mit dem Namen mit einem Menübefehl namens **ChangeMenuText**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Fügen Sie in der Datei `TextChanges` *.vsct* das Flag zu Ihrem Menübefehl hinzu, wie im folgenden Beispiel gezeigt.

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

3. Erstellen Sie in der *datei ChangeMenuText.cs* einen Ereignishandler, der aufgerufen wird, bevor der Menübefehl angezeigt wird.

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

    Sie können auch den Status des Menübefehls <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>in <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>dieser <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Methode <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> aktualisieren, indem Sie die , und eigenschaften für das Objekt ändern.

4. Ersetzen Sie im ChangeMenuText-Konstruktor den ursprünglichen Befehlsinitialisierungs- und Platzierungscode durch Code, der einen <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anstelle eines `MenuCommand`) erstellt, der den Menübefehl darstellt, den <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler hinzufügt und den Menübefehl an den Menübefehlsdienst weitergibt.

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

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

6. Im Menü **Extras** sollte ein Befehl mit dem Namen **Invoke ChangeMenuText**angezeigt werden.

7. Klicken Sie auf den Befehl. Es sollte das Meldungsfeld angezeigt werden, in dem angekündigt wird, dass **MenuItemCallback** aufgerufen wurde. Wenn Sie das Meldungsfeld schließen, sollten Sie sehen, dass der Name des Befehls im Menü **Extras**jetzt Neuer Text ist.
