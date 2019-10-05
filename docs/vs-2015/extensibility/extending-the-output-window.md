---
title: Erweitern im Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204428"
---
# <a name="extending-the-output-window"></a>Erweitern des Ausgabefensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Ausgabe** Fenster ist eine Sammlung von Textbereichen Lese-/Schreibzugriff. Visual Studio verfügt über diesen integrierten Bereichen: **Erstellen Sie**, Nachrichten zu Builds, welche Projekte kommunizieren und **allgemeine**, in dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nachrichten über die IDE kommuniziert. Projekte Abrufen eines Verweises auf die **erstellen** Bereich automatisch über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellenmethoden und Visual Studio bietet direkten Zugriff auf die **allgemeine** Bereich über die <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> -Dienst. Zusätzlich zu den integrierten Bereichen können Sie erstellen und verwalten Ihre eigenen benutzerdefinierten Bereiche.  
  
 Sie können steuern, die **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle, die von angeboten wird die <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, definiert Methoden zum Erstellen, abrufen und Zerstören von **Ausgabe** Fensterbereichen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle definiert Methoden für die Bereiche einblenden, Ausblenden von Bereichen und Bearbeiten von ihrem Text. Eine alternative Möglichkeit zum Steuern der **Ausgabe** Fenster ist über die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte im Objektmodell Visual Studio-Automatisierung. Diese Objekte zu kapseln, fast alle Funktionen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Darüber hinaus die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte hinzufügen, einige auf höherer Ebene Funktionen zum Auflisten von erleichtern die **Ausgabe** Fensterbereiche und zum Abrufen von Text aus den Bereichen.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Erstellen einer Erweiterung, die verwendet den Ausgabebereich  
 Sie können eine Erweiterung erstellen, die verschiedene Aspekte des Ausgabebereichs ausführt.  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TestOutput` mit einem Menübefehl mit dem Namen **TestOutput**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Fügen Sie die folgenden Verweise hinzu:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. TestOutput.cs, fügen Sie die folgende using-Anweisung:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. Löschen Sie in TestOutput.cs die ShowMessageBox-Methode. Fügen Sie den folgenden Methodenstub hinzu:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. Ändern Sie im Konstruktor TestOutput der Befehlshandler in OutputCommandHandler ein. Hier ist das Teil, das die Befehle hinzugefügt:  
  
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
  
6. In den folgenden Abschnitten haben verschiedene Methoden, die verschiedene Methoden zum Umgang mit den Ausgabebereich anzeigen. Sie können diese Methoden Hauptteil der OutputCommandHandler()-Methode aufrufen. Der folgende Code fügt z. B. die CreatePane()-Methode, die im nächsten Abschnitt angegeben.  
  
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
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte die **Ausgabe** Fenster mit einem Header, die besagt, **Ausgabe anzeigen Von: CreatedPane** und die Wörter **Dies ist der Bereich erstellt** im Bereich selbst.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Erstellen ein Fenster "Ausgabe" mit OutputWindow  
 Dieses Beispiel zeigt, wie Sie erstellen eine **Ausgabe** Fensterbereich mit der <xref:EnvDTE.OutputWindow> Objekt.  
  
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
  
 Obwohl die <xref:EnvDTE.OutputWindowPanes> Auflistung können Sie Abrufen einer **Ausgabe** Fensterbereich anhand von dessen Titel, Bereich Titel werden nicht unbedingt eindeutig sein. Wenn Sie die Eindeutigkeit eines Titels bezweifle, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den richtigen Bereich durch ihre GUID abzurufen.  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte im Ausgabefenster mit einem Header, die besagt, **Ausgabe anzeigen von: DTEPane** und die Wörter **DTE-Bereich hinzugefügt** im Bereich selbst.  
  
## <a name="deleting-an-output-window"></a>Ein Fenster "Ausgabe" wird gelöscht.  
 Dieses Beispiel zeigt, wie Sie löschen eine **Ausgabe** Fensterbereich.  
  
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
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte im Ausgabefenster mit einem Header, die besagt, **Ausgabe anzeigen von: Neuer Bereich** und die Wörter **erstellten Bereich hinzugefügt** im Bereich selbst. Wenn Sie auf die **aufrufen TestOutput** erneut den Befehl im Bereich wird gelöscht.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Bereich "Allgemein" des Ausgabefensters abrufen  
 Dieses Beispiel zeigt, wie Sie die integrierte abrufen **allgemeine** im Bereich der **Ausgabe** Fenster.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **TestOutput Aufrufen** Befehl sollte angezeigt werden, die **Ausgabe** Fenster zeigt die Wörter **allgemeine gefunden Bereich** im Bereich.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Abrufen von den Build-Fensterbereich des Ausgabefensters  
 Dieses Beispiel zeigt, wie Sie den Build-Fensterbereich zu finden und in ihn schreiben. Da der Build-Bereich wird standardmäßig nicht aktiviert ist, wird es ebenfalls aktiviert.  
  
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
