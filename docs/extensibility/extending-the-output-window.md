---
title: Erweitern im Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3545c01564a6128612d3c587df767560b59b1a49
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943512"
---
# <a name="extend-the-output-window"></a>Erweitern Sie im Ausgabefenster
Die **Ausgabe** Fenster ist eine Sammlung von Textbereichen Lese-/Schreibzugriff. Visual Studio verfügt über diesen integrierten Bereichen: **Erstellen Sie**, Nachrichten zu Builds, welche Projekte kommunizieren und **allgemeine**, in dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nachrichten über die IDE kommuniziert. Projekte Abrufen eines Verweises auf die **erstellen** Bereich automatisch über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellenmethoden und Visual Studio bietet direkten Zugriff auf die **allgemeine** Bereich über die <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> -Dienst. Zusätzlich zu den integrierten Bereichen können Sie erstellen und verwalten Ihre eigenen benutzerdefinierten Bereiche.  
  
 Sie können steuern, die **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle, die von angeboten wird die <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, definiert Methoden zum Erstellen, abrufen und Zerstören von **Ausgabe** Fensterbereichen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstelle definiert Methoden für die Bereiche einblenden, Ausblenden von Bereichen und Bearbeiten von ihrem Text. Eine alternative Möglichkeit zum Steuern der **Ausgabe** Fenster ist über die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte im Objektmodell Visual Studio-Automatisierung. Diese Objekte zu kapseln, fast alle Funktionen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Darüber hinaus die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte hinzufügen, einige auf höherer Ebene Funktionen zum Auflisten von erleichtern die **Ausgabe** Fensterbereiche und zum Abrufen von Text aus den Bereichen.  
  
## <a name="create-an-extension-that-uses-the-output-pane"></a>Erstellen Sie eine Erweiterung, die den Ausgabebereich verwendet.  
 Sie können eine Erweiterung erstellen, die verschiedene Aspekte des Ausgabebereichs ausführt.  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TestOutput` mit einem Menübefehl mit dem Namen **TestOutput**. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Fügen Sie die folgenden Verweise hinzu:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  In *TestOutput.cs*, fügen Sie die folgenden using-Anweisung:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  In *TestOutput.cs*, löschen Sie die `ShowMessageBox` Methode. Fügen Sie den folgenden Methodenstub hinzu:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  Ändern Sie im Konstruktor TestOutput der Befehlshandler in OutputCommandHandler ein. Hier ist das Teil, das die Befehle hinzugefügt:  
  
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
  
6.  In den folgenden Abschnitten haben verschiedene Methoden, die verschiedene Methoden zum Umgang mit den Ausgabebereich anzeigen. Sie können Text, der diese Methoden Aufrufen der `OutputCommandHandler()` Methode. Beispielsweise der folgende Code fügt die `CreatePane()` -Methode anhand der Angaben im nächsten Abschnitt.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="create-an-output-window-with-ivsoutputwindow"></a>Erstellen Sie ein Fenster "Ausgabe" mit IVsOutputWindow  
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
  
## <a name="create-an-output-window-with-outputwindow"></a>Erstellen Sie ein Fenster "Ausgabe" mit OutputWindow  
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
  
## <a name="delete-an-output-window"></a>Löschen Sie ein Fenster "Ausgabe"  
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
  
## <a name="get-the-general-pane-of-the-output-window"></a>Bereich "Allgemein" des Ausgabefensters abrufen  
 Dieses Beispiel zeigt, wie Sie die integrierte abrufen **allgemeine** im Bereich der **Ausgabe** Fenster.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **TestOutput Aufrufen** Befehl sollte angezeigt werden, die **Ausgabe** Fenster zeigt die Wörter **allgemeine gefunden Bereich** im Bereich.  
  
## <a name="get-the-build-pane-of-the-output-window"></a>Erhalten Sie im Bereich "Build" des Ausgabefensters  
 Dieses Beispiel zeigt, wie Sie die **erstellen** Bereich, und in ihn schreiben. Da die **erstellen** Bereich ist nicht standardmäßig aktiviert, er es ebenfalls aktiviert.  
  
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
