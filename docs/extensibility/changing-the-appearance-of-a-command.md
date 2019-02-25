---
title: Ändern der Darstellung eines Befehls | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7431fa1670f6a75b69c1a1033a51975307426771
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691344"
---
# <a name="change-the-appearance-of-a-command"></a>Ändern der Darstellung eines Befehls
Sie können Feedback für den Benutzer angeben, durch Ändern der Darstellung eines Befehls. Beispielsweise sollten Sie einen Befehl anders aussehen, wenn sie nicht verfügbar ist. Sie können Befehle stellen, verfügbar oder nicht verfügbar, ausblenden oder anzeigen, oder aktivieren bzw. deaktivieren sie im Menü.

Um die Darstellung eines Befehls zu ändern, führen Sie eine der folgenden Aktionen:

- Geben Sie den geeigneten Flags in der Befehlsdefinition in der Befehlsdatei für die Tabelle ein.

- Verwenden der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Service.

- Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle und die unformatierte Befehlsobjekte zu ändern.

  Die folgenden Schritte zeigen, wie Sie suchen und aktualisieren Sie die Darstellung eines Befehls mit dem Managed Package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>So ändern Sie die Darstellung eines Menübefehls

1. Befolgen Sie die Anweisungen in [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) So erstellen Sie ein Menüelement namens `New Text`.

2. In der *ChangeMenuText.cs* Datei, fügen Sie die folgenden using-Anweisung:

    ```csharp
    using System.Security.Permissions;
    ```

3. In der *ChangeMenuTextPackageGuids.cs* Datei, fügen Sie die folgende Zeile hinzu:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. In der *ChangeMenuText.cs* Datei, ersetzen Sie den Code in der ShowMessageBox-Methode durch Folgendes:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Abrufen den Befehl, der aktualisiert werden sollen die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Objekt aus, und legen Sie dann die entsprechenden Eigenschaften für das Command-Objekt. Beispielsweise wird die folgende Methode der angegebenen Befehlssatz aus einem VSPackage-Befehl verfügbar oder nicht verfügbar. Im folgenden Code werden das Menü, das Element mit dem Namen `New Text` nicht verfügbar, nachdem sie bereits geklickt wurde.

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

7. Auf der **Tools** Menü klicken Sie auf die **aufrufen ChangeMenuText** Befehl. Zu diesem Zeitpunkt ist der Name des Befehls **aufrufen ChangeMenuText**, sodass die Befehlshandler Aufrufen nicht **ChangeMyCommand()**.

8. Auf der **Tools** Menü jetzt angezeigt werden sollte **neuen Text**. Klicken Sie auf **neuen Text**. Der Befehl sollte jetzt abgeblendet.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)
- [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
