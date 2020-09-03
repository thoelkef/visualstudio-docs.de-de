---
title: Erweitern der Ausgabefenster | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204428"
---
# <a name="extending-the-output-window"></a>Erweitern des Ausgabefensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster **Ausgabe** ist ein Satz von Textbereichen mit Lese-/Schreibzugriff. Visual Studio verfügt über die folgenden integrierten Bereiche: **Build**, in denen Projekte Nachrichten über Builds und **Allgemeine**Informationen kommunizieren, in denen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nachrichten über die IDE kommuniziert. Projekte erhalten automatisch einen Verweis auf den Bereich **Build** über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellen Methoden, und Visual Studio bietet direkten Zugriff auf den **allgemeinen** Bereich über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Dienst. Zusätzlich zu den integrierten Bereichen können Sie eigene benutzerdefinierte Bereiche erstellen und verwalten.  
  
 Sie können das **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle und die-Schnittstelle steuern <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle, die vom Dienst angeboten wird <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> , definiert Methoden zum Erstellen, abrufen und zerstören von **Ausgabe** Fensterbereichen. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle definiert Methoden, um Bereiche anzuzeigen, Bereiche zu verbergen und Ihren Text zu bearbeiten. Eine alternative Möglichkeit, das **Ausgabe** Fenster zu steuern, ist die über das <xref:EnvDTE.OutputWindow> -Objekt und das- <xref:EnvDTE.OutputWindowPane> Objekt im Visual Studio-Automatisierungs Objektmodell. Diese Objekte Kapseln fast alle Funktionen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle und der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstelle. Außerdem werden mit dem <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> -Objekt und dem-Objekt einige Funktionen höherer Ebene hinzugefügt, um die Enumeration der Fensterbereiche des **Ausgabe** Fensters und das Abrufen von Text aus den Bereichen zu vereinfachen.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Erstellen einer Erweiterung, die den Ausgabebereich verwendet  
 Sie können eine Erweiterung erstellen, mit der verschiedene Aspekte des Ausgabe Bereichs trainiert werden.  
  
1. Erstellen Sie ein VSIX-Projekt namens `TestOutput` mit einem Menübefehl mit dem Namen " **testoutput**". Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Fügen Sie die folgenden Verweise hinzu:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. Fügen Sie in TestOutput.cs die folgende using-Anweisung hinzu:  
  
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
  
5. Ändern Sie im testoutput-Konstruktor den Befehls Handler in outputcommandhandler. Hier ist der Teil, in dem die Befehle hinzugefügt werden:  
  
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
  
6. In den folgenden Abschnitten finden Sie verschiedene Methoden, die verschiedene Möglichkeiten zum Umgang mit dem Ausgabebereich veranschaulichen. Sie können diese Methoden als Text der outputcommandhandler ()-Methode aufzurufen. Der folgende Code fügt z. b. die im nächsten Abschnitt angegebene Methode "-Methode ()" hinzu.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Erstellen einer Ausgabefenster mit ivsoutputwindow  
 Dieses Beispiel zeigt, wie ein neuer **Ausgabe** Fensterbereich mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle erstellt wird.  
  
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
  
 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl " **testoutput aufrufen** " das **Ausgabe** Fenster mit einem Header anzeigen, der besagt, dass **Ausgabe anzeigen aus: "kreatedpane" angezeigt** **wird. Dies ist der erstellte** Bereich im Bereich.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Erstellen einer Ausgabefenster mit OutputWindow  
 In diesem Beispiel wird gezeigt, wie ein **Ausgabe** Fensterbereich mithilfe des-Objekts erstellt wird <xref:EnvDTE.OutputWindow> .  
  
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
  
 Obwohl die-Auflistung das <xref:EnvDTE.OutputWindowPanes> Abrufen eines **Ausgabe** Fenster Bereichs anhand seines Titels ermöglicht, ist es nicht gewährleistet, dass Pane-Titel eindeutig sind. Wenn Sie die Eindeutigkeit eines Titels zweifelhaft sind, verwenden Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den korrekten Bereich anhand seiner GUID abzurufen.  
  
 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl " **testoutput aufrufen** " das Ausgabefenster mit einem Header anzeigen, der den Befehl **Ausgabe aus: dtepane anzeigen** und den Bereich für **hinzugefügte DTE** -Elemente im Bereich selbst.  
  
## <a name="deleting-an-output-window"></a>Löschen eines Ausgabefenster  
 Dieses Beispiel zeigt, wie ein **Ausgabe** Fensterbereich gelöscht wird.  
  
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
  
 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl **testoutput aufrufen** das Fenster Ausgabe mit einem Header mit dem Text **Ausgabe anzeigen aus: neuer** Bereich und den Text **hinzugefügten** Bereich im Bereich Selbstanzeigen. Wenn Sie erneut auf den Befehl " **testoutput aufrufen** " klicken, wird der Bereich gelöscht.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Der allgemeine Bereich des Ausgabefenster wird angezeigt.  
 Dieses Beispiel zeigt, wie Sie den integrierten **allgemeinen** Bereich des **Ausgabe** Fensters erhalten.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl **testoutput aufrufen** sehen, dass im Fenster **Ausgabe** der Bereich **Allgemeine** Wörter angezeigt wird.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Der Bereich "Build" des Ausgabefenster wird angezeigt.  
 Dieses Beispiel zeigt, wie Sie den Buildbereich suchen und darin schreiben. Da der Bereich "Build" nicht standardmäßig aktiviert ist, wird er ebenfalls aktiviert.  
  
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
