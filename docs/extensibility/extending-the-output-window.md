---
title: Erweitern im Fenster "Ausgabe" | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e183413446bbca2ffed0642619ab63538fae0f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-output-window"></a>Erweitern Sie im Fenster "Ausgabe"
Die **Ausgabe** Fenster ist ein Satz von Lese-/Schreibzugriff Textbereiche. Visual Studio umfasst diese integrierten Bereiche: **erstellen**, Meldungen zu Builds, in welche Projekte zu kommunizieren und **allgemeine**, in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Meldungen über die IDE kommuniziert. Projekte Abrufen eines Verweises auf die **erstellen** Bereich automatisch durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellenmethoden und Visual Studio bietet direkten Zugriff auf die **allgemeine** Bereich über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> -Dienst. Zusätzlich zu den integrierten Bereichen können Sie erstellen und verwalten Ihre eigenen benutzerdefinierten Bereiche.  
  
 Sie können steuern, die **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle, die von angeboten wird die <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, definiert Methoden zum Erstellen, abrufen und Zerstören von **Ausgabe** Fensterbereiche. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle definiert Methoden für Bereiche einblenden, Ausblenden von Bereichen und Bearbeiten von Text. Eine alternative Möglichkeit zum Steuern der **Ausgabe** Fenster wird durch die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte in der Visual Studio-Automatisierungsobjektmodell. Diese Objekte kapseln nahezu alle Funktionen von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Darüber hinaus die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte hinzufügen, einige Funktionen auf höherer Ebene, zum Auflisten von erleichtern die **Ausgabe** Fensterbereiche und zum Abrufen von Text aus den Bereichen.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Erstellen eine Erweiterung, die verwendet den Ausgabebereich  
 Sie können eine Erweiterung vornehmen, die verschiedene Aspekte der im Ausgabebereich ausführt.  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TestOutput` eines Menübefehls mit dem Namen **TestOutput**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Fügen Sie die folgenden Verweise hinzu:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  In TestOutput.cs, fügen Sie die folgende Anweisung:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Löschen Sie im TestOutput.cs die ShowMessageBox-Methode. Fügen Sie den folgenden Methodenstub hinzu:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  Ändern Sie in den Konstruktor TestOutput Befehlshandler in OutputCommandHandler. Hier ist das Teil, das die Befehle hinzugefügt:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Die folgenden Abschnitte haben unterschiedliche Methoden, die verschiedenen Methoden zum Umgang mit im Ausgabebereich anzuzeigen. Sie können diese Methoden zum Text der Methode OutputCommandHandler() aufrufen. Der folgende Code fügt z. B. die CreatePane()-Methode, die im nächsten Abschnitt gegeben.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Erstellen ein Fenster "Ausgabe" mit IVsOutputWindow  
 In diesem Beispiel wird gezeigt, wie zum Erstellen eines neuen **Ausgabe** Fensterbereich mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **TestOutput Aufrufen** Befehl sollte die **Ausgabe** Fenster mit einem Header, der besagt, **Ausgabe anzeigen von: CreatedPane** und die Wörter **Dies ist der Bereich erstellt** im Bereich selbst.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Erstellen ein Fenster "Ausgabe" mit OutputWindow  
 In diesem Beispiel wird gezeigt, wie zum Erstellen einer **Ausgabe** Fensterbereich mit der <xref:EnvDTE.OutputWindow> Objekt.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Obwohl die <xref:EnvDTE.OutputWindowPanes> Auflistung können Sie Abrufen einer **Ausgabe** Fensterbereich durch den Titel, Bereich Titel ist nicht gewährleistet eindeutig sein. Wenn Sie die Eindeutigkeit eines Titels Zweifel haben, verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den richtigen Bereich durch ihre GUID abzurufen.  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte das Ausgabefenster mit einem Header, der besagt, **Ausgabe anzeigen von: DTEPane** und die Wörter **DTE-Bereich hinzugefügt** im Bereich selbst.  
  
## <a name="deleting-an-output-window"></a>Löschen ein Fenster "Ausgabe"  
 In diesem Beispiel wird gezeigt, wie zum Löschen einer **Ausgabe** Fensterbereich.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte das Ausgabefenster mit einem Header, der besagt, **Ausgabe anzeigen von: Neuer Bereich** und die Wörter **erstellten Bereich hinzugefügt** im Bereich selbst. Wenn Sie auf die **TestOutput Aufrufen** Befehl erneut aus, der Bereich wird gelöscht.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Bereich "Allgemein" im Fenster "Ausgabe" Abrufen  
 In diesem Beispiel wird gezeigt, wie die integrierte abzurufenden **allgemeine** im Bereich der **Ausgabe** Fenster.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte angezeigt werden, die **Ausgabe** Fenster zeigt die Wörter **allgemeine gefunden Bereich** im Bereich.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Abrufen der Build-Bereich, der das Fenster "Ausgabe"  
 Dieses Beispiel zeigt, wie finden im Bereich Build und in diese schreiben. Seit der Build-Bereich in der Standardeinstellung aktiviert ist nicht, wird er auch aktiviert.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```