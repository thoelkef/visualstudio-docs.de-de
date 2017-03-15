---
title: "&#196;ndern der Darstellung eines Befehls | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ändern der Darstellung von Befehlen"
  - "Ändern der Darstellung von Menübefehlen"
  - "Ändern der Darstellung von Befehl Menüs"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# &#196;ndern der Darstellung eines Befehls
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Ihre Benutzer Feedback bereitzustellen, durch Ändern der Darstellung eines Befehls. Beispielsweise sollten Sie einen Befehl anders aussehen, wenn sie nicht verfügbar ist. Sie können damit Befehle verfügbar sind, ausblenden oder anzeigen, oder überprüfen oder deaktivieren Sie sie im Menü.  
  
 Führen Sie zum Ändern der Darstellung eines Befehls eine der folgenden Aktionen aus:  
  
-   Geben Sie den geeigneten Flags in der Command\-Definition in der Befehlsdatei\-Tabelle.  
  
-   Verwenden der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Service.  
  
-   Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle und die unformatierte Befehlsobjekte zu ändern.  
  
 Die folgenden Schritte zeigen, wie Sie suchen und aktualisieren Sie die Darstellung eines Befehls mit dem Managed Package Framework \(MPF\).  
  
### So ändern Sie die Darstellung eines Menübefehls  
  
1.  Gehen Sie im [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) So erstellen Sie ein Menüelement mit dem Namen `New Text`.  
  
2.  Fügen Sie in der Datei ChangeMenuText.cs die folgende using\-Anweisung:  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  Fügen Sie in der Datei ChangeMenuTextPackageGuids.cs die folgende Zeile hinzu:  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Ersetzen Sie in der Datei ChangeMenuText.cs den Code in die ShowMessageBox\-Methode durch Folgendes:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Der Befehl, die Sie aktualisieren möchten die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Objekt, und klicken Sie dann die entsprechenden Eigenschaften für das Befehlsobjekt festlegen. Beispielsweise wird die folgende Methode den angegebenen Befehlssatz aus einem VSPackage\-Befehl verfügbar oder nicht verfügbar. Im folgenden Code wird das Menüelement `New Text` nicht verfügbar, nachdem auf sie geklickt wurde.  
  
    ```c#  
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
  
7.  Auf der **Tools** Menü klicken Sie auf die **aufrufen ChangeMenuText** Befehl. Zu diesem Zeitpunkt ist der Name des Befehls **aufrufen ChangeMenuText**, sodass der Befehlshandler ChangeMyCommand\(\) aufgerufen wird.  
  
8.  Auf der **Tools** Sie sollten nun sehen Sie im Menü **neuen Text**. Klicken Sie auf **neuen Text**. Der Befehl sollte jetzt abgeblendet.  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)