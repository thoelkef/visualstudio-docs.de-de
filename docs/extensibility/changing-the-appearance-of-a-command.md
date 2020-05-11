---
title: Ändern der Darstellung eines Befehls | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739851"
---
# <a name="change-the-appearance-of-a-command"></a>Ändern der Darstellung eines Befehls
Sie können Ihrem Benutzer Feedback geben, indem Sie die Darstellung eines Befehls ändern. Sie möchten z. B., dass ein Befehl anders aussieht, wenn er nicht verfügbar ist. Sie können Befehle verfügbar oder nicht verfügbar machen, sie ausblenden oder anzeigen oder sie im Menü überprüfen oder deaktivieren.

Um die Darstellung eines Befehls zu ändern, führen Sie eine der folgenden Aktionen aus:

- Geben Sie die entsprechenden Flags in der Befehlsdefinition in der Befehlstabellendatei an.

- Verwenden <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Sie den Dienst.

- Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sie die Schnittstelle, und ändern Sie die unformatierten Befehlsobjekte.

  Die folgenden Schritte zeigen, wie Sie die Darstellung eines Befehls mithilfe des Managed Package Framework (MPF) suchen und aktualisieren.

### <a name="to-change-the-appearance-of-a-menu-command"></a>So ändern Sie die Darstellung eines Menübefehls

1. Folgen Sie den Anweisungen unter [Ändern des Textes eines Menübefehls,](../extensibility/changing-the-text-of-a-menu-command.md) um ein Menüelement mit dem Namen `New Text`zu erstellen.

2. Fügen Sie in der *Datei ChangeMenuText.cs* die folgende Usinger Anweisung hinzu:

    ```csharp
    using System.Security.Permissions;
    ```

3. Fügen Sie in der *ChangeMenuTextPackageGuids.cs* Datei die folgende Zeile hinzu:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. Ersetzen Sie in der *Datei ChangeMenuText.cs* den Code in der ShowMessageBox-Methode durch Folgendes:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Rufen Sie den Befehl ab, <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> den Sie aktualisieren möchten, und legen Sie dann die entsprechenden Eigenschaften für das Befehlsobjekt fest. Die folgende Methode macht z. B. den angegebenen Befehl aus einem VSPackage-Befehlssatz verfügbar oder nicht verfügbar. Der folgende Code macht `New Text` das Menüelement mit dem Namen nicht verfügbar, nachdem es geklickt wurde.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))
            as OleMenuCommandService;
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

7. Klicken Sie im Menü **Extras** auf den Befehl **ChangeMenuText aufrufen.** An diesem Punkt lautet der Befehlsname **Invoke ChangeMenuText**, sodass der Befehlshandler **ChangeMyCommand()** nicht aufruft.

8. Im Menü **Extras** sollte jetzt **Neuer Text**angezeigt werden. Klicken Sie auf **Neuer Text**. Der Befehl sollte nun ausgegraut sein.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Visual Studio-Befehlstabelle (. Vsct) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
