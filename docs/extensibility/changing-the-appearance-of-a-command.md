---
title: "Ändern der Darstellung eines Befehls | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ffb8aed183b50958c8835b2a1e79b808ac20174
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-appearance-of-a-command"></a>Ändern der Darstellung eines Befehls
Ändern der Darstellung eines Befehls können Sie Feedback, die für Benutzer bereitstellen. Beispielsweise sollten Sie einen Befehl zum anders aussehen, wenn sie nicht verfügbar ist. Sie können damit Befehle verfügbar oder nicht verfügbar, ausblenden oder anzeigen, oder aktivieren bzw. deaktivieren sie im Menü.  
  
 Führen Sie zum Ändern der Darstellung eines Befehls eine der folgenden Aktionen aus:  
  
-   Geben Sie den geeigneten Flags in der Befehlsdefinition in der Tabelle Befehlsdatei ein.  
  
-   Verwenden der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Dienst.  
  
-   Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und ändern Sie den unformatierten Befehlsobjekte.  
  
 Die folgenden Schritte zeigen, wie Suchen und aktualisieren Sie die Darstellung eines Befehls mit dem Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>So ändern Sie die Darstellung eines Menübefehls  
  
1.  Befolgen Sie die Anweisungen in [ändern den Text eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) So erstellen Sie ein Menüelement namens `New Text`.  
  
2.  Fügen Sie in der Datei ChangeMenuText.cs die folgende Anweisung:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Fügen Sie in der Datei ChangeMenuTextPackageGuids.cs die folgende Zeile hinzu:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Ersetzen Sie in der Datei ChangeMenuText.cs den Code in der Methode ShowMessageBox durch Folgendes ein:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Beziehen Sie den Befehl, den Sie aktualisieren möchten die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Objekt, und legen Sie dann die entsprechenden Eigenschaften für das Command-Objekt. Die folgende Methode macht z. B. den angegebenen Befehlssatz aus einem VSPackage-Befehl verfügbar oder nicht verfügbar. Im folgenden Code werden die Menüelement `New Text` nicht verfügbar, nachdem auf sie geklickt wurde.  
  
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
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7.  Auf der **Tools** Menü klicken Sie auf die **ChangeMenuText Aufrufen** Befehl. An diesem Punkt der Befehlsname entspricht **ChangeMenuText Aufrufen**, sodass die Befehlshandler ChangeMyCommand() aufrufen nicht.  
  
8.  Auf der **Tools** Menü sollte jetzt angezeigt **neuen Text**. Klicken Sie auf **neuen Text**. Der Befehl sollte jetzt abgeblendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)