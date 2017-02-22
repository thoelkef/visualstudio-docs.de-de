---
title: "Erweitern Sie im Ausgabefenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausgabefenster, Informationen über das Ausgabefenster"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Erweitern Sie im Ausgabefenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Ausgabe** Fenster ist ein Satz von Textbereichen Lese\-\/Schreibzugriff. Visual Studio verfügt über integrierte Bereiche anzeigen: **Erstellen**, Nachrichten zu Builds, in welche Projekte zu kommunizieren und **Allgemeine**, in dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nachrichten über die IDE kommuniziert. Projekte erhalten einen Verweis auf die **Erstellen** Bereich automatisch über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellenmethoden und Visual Studio bietet direkten Zugriff auf die **Allgemeine** Bereich über die <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Service. Zusätzlich zu den integrierten Bereichen können Sie erstellen und verwalten Ihre eigenen benutzerdefinierten Bereiche.  
  
 Sie können steuern, die **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> \-Schnittstelle, die von angeboten wird die <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, definiert Methoden zum Erstellen, abrufen und löschen **Ausgabe** Fensterbereichen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> \-Schnittstelle definiert Methoden für Bereiche einblenden, Ausblenden von Bereichen und Bearbeiten von Text. Eine alternative Möglichkeit zum Steuern der **Ausgabe** Fenster wird durch die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte im Objektmodell von Visual Studio\-Automatisierung. Diese Objekte kapseln fast die gesamte Funktionalität von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstellen. Darüber hinaus die <xref:EnvDTE.OutputWindow> und <xref:EnvDTE.OutputWindowPane> Objekte hinzufügen, einige auf höherer Ebene Funktionen zum Auflisten von erleichtern die **Ausgabe** Bereiche und zum Abrufen von Text aus den Bereichen.  
  
## Erstellen eine Erweiterung, die verwendet den Ausgabebereich  
 Sie können eine Erweiterung erstellen, die verschiedene Aspekte der Ausgabebereich ausführt.  
  
1.  Erstellen Sie ein VSIX\-Projekt mit dem Namen `TestOutput` einen Befehl mit dem Namen **TestOutput**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Fügen Sie die folgenden Verweise hinzu:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  TestOutput.cs, fügen Sie folgende using\-Anweisung:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  Löschen Sie in TestOutput.cs die ShowMessageBox\-Methode. Fügen Sie den folgenden Methodenstub hinzu:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  Ändern Sie im Konstruktor TestOutput Befehlshandler in OutputCommandHandler ein. Hier ist das Teil, das die Befehle hinzugefügt:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  In den folgenden Abschnitten sind verschiedene Methoden, die unterschiedliche Methoden zum Umgang mit im Ausgabebereich angezeigt. Sie können die folgenden Verfahren den Text der Methode OutputCommandHandler\(\) aufrufen. Der folgende Code fügt z. B. die CreatePane\(\)\-Methode, die im nächsten Abschnitt erhalten.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## Erstellen ein Ausgabefenster mit IVsOutputWindow  
 In diesem Beispiel wird gezeigt, wie zum Erstellen eines neuen **Ausgabe** Fensterbereich mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle.  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte die **Ausgabe** Fenster mit einem Header, die besagt, **Ausgabe anzeigen von: CreatedPane** und die Wörter **Dies ist der Bereich erstellt** im Bereich selbst.  
  
## Erstellen ein Ausgabefenster mit OutputWindow  
 In diesem Beispiel wird gezeigt, wie zum Erstellen einer **Ausgabe** Fensterbereich mithilfe der <xref:EnvDTE.OutputWindow> Objekt.  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 Obwohl die <xref:EnvDTE.OutputWindowPanes> Auflistung können Sie Abrufen einer **Ausgabe** Fensterbereich mit dem Titel im Bereich Titel sind nicht unbedingt eindeutig sein. Verwenden Sie gegebenenfalls die Eindeutigkeit der Titel der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den richtigen Bereich anhand seiner GUID abzurufen.  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte im Ausgabefenster mit einem Header, die besagt, **Ausgabe anzeigen von: DTEPane** und die Wörter **DTE\-Bereich hinzugefügt** im Bereich selbst.  
  
## Löschen ein Ausgabefenster  
 Dieses Beispiel zeigt die Vorgehensweise beim Löschen einer **Ausgabe** Fensterbereich.  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **aufrufen TestOutput** Befehl sollte im Ausgabefenster mit einem Header, die besagt, **Ausgabe anzeigen von: neue Bereich** und die Wörter **erstellten Bereich hinzugefügt** im Bereich selbst. Wenn Sie auf die **aufrufen TestOutput** Befehl erneut aus, der Bereich wird gelöscht.  
  
## Bereich "Allgemein" des Ausgabefensters abrufen  
 Dieses Beispiel zeigt, wie die integrierte **Allgemeine** im Bereich der **Ausgabe** Fenster.  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 Wenn Sie diese Methode, um die Erweiterung, die im vorherigen Abschnitt angegeben wird hinzufügen, wenn Sie auf die **TestOutput Aufrufen** Befehl sollte angezeigt werden, die **Ausgabe** Fenster werden die Wörter **im Bereich Allgemein gefunden** im Bereich.  
  
## Abrufen von den Build\-Fensterbereich des Ausgabefensters  
 Dieses Beispiel zeigt, wie finden den Build\-Fensterbereich und in ihn schreiben. Da die Build\-Fensterbereich standardmäßig aktiviert ist nicht, wird es auch aktiviert.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```