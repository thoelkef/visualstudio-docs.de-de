---
title: "H&#228;ufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 22
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# H&#228;ufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Add\-Ins sind jetzt veraltet. Um eine neue Visual Studio\-Erweiterung zu machen, müssen Sie eine VSIX\-Erweiterung zu erstellen. Hier werden die Antworten auf einige häufig gestellten Fragen dazu, wie Sie ein Visual Studio\-add\-in in einer VSIX\-Erweiterung zu konvertieren.  
  
> [!WARNING]
>  Für c\# und Visual Basic\-Projekten in Visual Studio 2015 beginnen können Sie das VSIX\-Projekt verwenden und Hinzufügen von Elementvorlagen für Menübefehle, Toolfenstern und VSPackages. Weitere Informationen finden Sie unter [Was ist neu in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  In vielen Fällen können Sie einfach den Add\-in Code um ein VSIX\-Projekt mit einem Projektelement VSPackage übertragen. Sie erhalten das DTE\-Automatisierungsobjekt durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Weitere Informationen finden Sie unter [Wie kann ich mein Add-in-Code in einem VSPackage ausführen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) unten.  
  
## Welche Software brauche ich VSIX\-Erweiterungen entwickeln?  
 Visual Studio\-Erweiterungen erfordern die Visual Studio 2015 SDK zusätzlich zu Visual Studio 2015.  Wenn Sie ein VSIX\-Projekt erstellen oder ein vorhandenes VSIX\-Projekt öffnen, lädt Visual Studio die erforderliche Software. Weitere Informationen zum Installieren von Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Wo ist die Erweiterung\-Dokumentation?  
 Beginnen Sie mit [Starten Visual Studio\-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md). Weitere Artikel zur Entwicklung von VSSDK\-Erweiterung auf MSDN finden Sie weiter unten, dass ein.  
  
## Kann ich mein Add\-In\-Projekt in ein VSIX\-Projekt konvertieren?  
 Ein Add\-In Projekt kann nicht direkt in ein VSIX\-Projekt konvertiert werden, da die verwendeten Mechanismen in VSIX\-Projekten nicht identisch mit denen im Add\-in\-Projekte sind. Die VSIX\-Projektvorlage, sowie die richtige Projektelementvorlagen haben viel Code, mit dem relativ einfach einrichten und als einer VSIX\-Erweiterungs ausgeführt wird.  
  
##  <a name="BKMK_StartDeveloping"></a> Wie starte ich die VSIX\-Erweiterungen entwickeln?  
 Hier ist, wie Sie eine VSIX erstellen, die einen Menübefehl hat:  
  
#### Zu einer VSIX\-Erweiterung, die über einen Menübefehl verfügt  
  
1.  Erstellen eines VSIX\-Projekts \(**Datei**, **Neu**, **Projekt**, oder geben Sie **Projekt** in der **Schnellstartleiste** Fenster\). In der **Neues Projekt** Dialogfeld erweitern Sie **Visual c\# \/ Erweiterbarkeit** oder **Visual Basic \/ Erweiterbarkeit** und wählen Sie **VSIX\-Projekt**.\) Nennen Sie das Projekt **TestExtension** und geben Sie einen Speicherort für sie.  
  
2.  Hinzufügen einer **Befehl benutzerdefinierte** Projektelementvorlage. \(Mit der rechten Maustaste des Projektknoten in der **Projektmappen\-Explorer** und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Projekt** Dialogfeld für Visual c\# oder Visual Basic, wählen Sie die **Erweiterbarkeit** Knoten, und wählen **Befehl benutzerdefinierte**.\)  
  
3.  Drücken Sie F5, um das Projekt im Debugmodus ausführen.  
  
     Eine zweite Instanz von Visual Studio wird angezeigt. Diese zweite Instanz wird experimentelle Instanz genannt, und sie verfügen möglicherweise nicht über den gleichen Einstellungen wie die Instanz von Visual Studio, die Sie zum Schreiben von Code verwenden. Beim ersten die experimentelle Instanz ausführen aufgefordert werden VS Online anmelden und Ihr Design und Profil.  
  
     Auf der **Tools** Menü \(in der experimentellen Instanz\) sollte eine Schaltfläche namens **Mein Befehlsname**. Wenn Sie auf diese Schaltfläche auswählen, eine Meldung angezeigt: **Inside TestVSPackagePackage.MenuItemCallback\(\)**.  
  
##  <a name="BKMK_RunAddin"></a> Wie kann ich mein Add\-in\-Code in einem VSPackage ausführen?  
 Add\-in\-Code wird in der Regel in zwei Arten ausgeführt:  
  
-   Ausgelöst durch einen Menübefehl \(der Code ist in der `IDTCommandTarget.Exec` Methode\)  
  
-   Automatisch beim Start \(der Code ist in der `OnConnection` \-Ereignishandler.\)  
  
 In einem VSPackage können Sie das gleiche tun. Hier ist das Add\-in\-Code in der Rückrufmethode hinzufügen:  
  
#### Implementieren ein Menübefehls in einem VSPackage  
  
1.  Erstellen Sie ein VSPackage, das einen Menübefehl hat. \(Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).\)  
  
2.  Öffnen Sie die Datei mit der Definition des VSPackage. \(In einem C\#\-Projekt kann *\< Projektname \>*Package.cs.\)  
  
3.  Fügen Sie die folgenden `using` \-Anweisungen in die Datei:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback` Methode. Fügen Sie einen Aufruf an <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zum Abrufen der <xref:EnvDTE80.DTE2> Objekt:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code, die das Add\-in in seine `IDTCommandTarget.Exec` Methode. Hier ist z. B. Code, der einen neuen Bereich zum fügt die **Ausgabe** Fenster und druckt "Some Text" im neuen Bereich.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Erstellen Sie und führen Sie dieses Projekt. Drücken Sie F5, oder wählen Sie **Start** auf der **Debuggen** Symbolleiste. In der experimentellen Instanz von Visual Studio die **Tools** Menü müsste eine Schaltfläche mit dem Namen **Mein Befehlsname**. Bei Auswahl dieser Schaltfläche, die Wörter **Some Text** sollte angezeigt werden, einer **Ausgabe** Fensterbereich. \(Möglicherweise müssen Sie öffnen die **Ausgabe** Fenster.\)  
  
 Sie können auch den Code, der beim Start ausführen lassen. Dieser Ansatz ist jedoch im Allgemeinen für VSPackage\-Erweiterungen nicht empfehlenswert. Wenn zu viele Erweiterungen versuchen, die beim Starten von Visual Studio geladen wird, kann die Startzeit erheblich verlängern. Eine bessere Vorgehensweise ist das VSPackage automatisch geladen, wenn eine Bedingung erfüllt ist, \(z. B. eine Projektmappe geöffnet wird\).  
  
 Dieses Verfahren veranschaulicht, wie Add\-in\-Code in einem VSPackage ausführen, das automatisch geladen, wenn eine Projektmappe geöffnet ist:  
  
#### Automatisches Laden eines VSPackages  
  
1.  Erstellen Sie ein VSIX\-Projekt mit einem Projektelement für Visual Studio\-Paket. \(Die Schritte hierzu finden Sie unter [Wie starte ich die VSIX-Erweiterungen entwickeln?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Fügen Sie einfach die **Visual Studio\-Paket** stattdessen Projektelemente.\) Nennen Sie das VSIX\-Projekt **TestAutoload**.  
  
2.  Öffnen Sie TestAutoloadPackage.cs. Suchen Sie die Zeile, in die Klasse deklariert wird:  
  
    ```c#  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Oberhalb dieser Zeile befindet sich eine Reihe von Attributen. Fügen Sie dieses Attribut hinzu:  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Legen Sie einen Haltepunkt der `Initialize()` \-Methode und starten Sie das debugging \(F5\).  
  
5.  Öffnen Sie ein Projekt in der experimentellen Instanz. Das VSPackage sollte geladen, und der Haltepunkt erreicht werden.  
  
 Sie können angeben, dass andere Sicherheitskontexten, in denen das VSPackage geladen wird, über die Felder des <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## Wie kann ich das DTE\-Objekt?  
 Wenn Ihr Add\-in\-Benutzeroberfläche nicht angezeigt wird, z. B. Menübefehle, Schaltflächen der Symbolleiste oder Toolfenster – möglicherweise verwenden Sie den Code als\-ist, solange Sie das DTE\-Automatisierungsobjekt aus dem VSPackage abrufen. Hier ist wie:  
  
#### Das DTE\-Objekt aus einem VSPackage abrufen  
  
1.  Suchen Sie in einem VSIX\-Projekt mit einer Elementvorlage für Visual Studio\-Paket nach dem *\< Projektname \>*Datei Package.cs. Dies ist die Klasse, die von abgeleitet <xref:Microsoft.VisualStudio.Shell.Package>; sie können Ihnen helfen, mit Visual Studio zu interagieren. In diesem Fall verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zum Abrufen der <xref:EnvDTE80.DTE2> Objekt.  
  
2.  Fügen Sie `using` Anweisungen:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Suchen Sie die `Initialize` Methode. Diese Methode verarbeitet den Befehl, den Sie im Paket\-Assistenten angegeben haben. Fügen Sie einen Aufruf an <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zum Abrufen des DTE\-Objekts:  
  
    ```c#  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Nachdem Sie haben die <xref:EnvDTE.DTE> \-Automatisierungsobjekt abgerufen haben, Sie können den Rest der Add\-in Code zum Projekt hinzufügen. Wenn Sie müssen die <xref:EnvDTE80.DTE2> \-Objekt können Sie das gleiche tun.  
  
## Wie ändere ich Menübefehle und Schaltflächen der Symbolleiste in Mein Add\-in, den Stil des VSPackages?  
 VSPackage\-Erweiterungen verwenden die VSCT\-Datei, um die meisten Menübefehle, Symbolleisten, Symbolleisten\-Schaltflächen und andere Benutzeroberfläche zu erstellen. Die **Befehl benutzerdefinierte** Projektelementvorlage haben Sie die Möglichkeit zum Erstellen eines Befehls für die **Tools** Menü. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu VSCT\-Dateien finden Sie unter [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Exemplarische Vorgehensweisen für die Verwendung die VSCT\-Datei Menübefehlen, Symbolleisten und Schaltflächen der Symbolleiste hinzufügen, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
## Wie füge ich in VSPackages benutzerdefinierte Toolfenster hinzu?  
 Die benutzerdefinierte Toolfenster Projektelementvorlage bietet Ihnen die Möglichkeit, ein Toolfenster erstellen. Weitere Informationen zu diesem Projektelementvorlage, finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Informationen zum Tool Windows finden Sie unter [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md) und in den Artikeln, insbesondere [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
## Wie verwalte ich Visual Studio\-Fenster VSPackages?  
 Wenn das Add\-in Visual Studio\-Fenster verwaltet, sollte der Add\-in\-Code in einem VSPackage funktionieren. Dieses Verfahren wird gezeigt, wie Sie Code hinzufügen, der verwaltet die **Aufgabenliste** an die `MenuItemCallback` \-Methode des VSPackages.  
  
#### Zum Einfügen von Code im Fenster Verwaltung aus ein Add\-in in einem VSPackage  
  
1.  Erstellen Sie ein VSPackage, das einen Menübefehl verfügt die [Wie starte ich die VSIX-Erweiterungen entwickeln?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) Abschnitt.  
  
2.  Öffnen Sie die Datei mit der Definition des VSPackage. \(In einem C\#\-Projekt kann *\< Projektname \>*Package.cs.\)  
  
3.  Fügen Sie `using` Anweisungen:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback` Methode. Fügen Sie einen Aufruf an <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zum Abrufen der <xref:EnvDTE80.DTE2> Objekt:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code über das Add\-in. Hier ist z. B. Code, der die neue Aufgaben, fügt die **Aufgabenliste**, die die Anzahl der Aufgaben aufgelistet und anschließend eine Aufgabe gelöscht.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## Wie verwalte ich Projekte und Projektmappen in einem VSPackage?  
 Wenn Ihr Add\-in\-Projekte und Projektmappen verwaltet werden, sollte der Add\-in\-Code in einem VSPackage funktionieren. Diese Prozedur gezeigt, wie Sie Code hinzufügen, der das Startprojekt abruft.  
  
1.  Erstellen Sie ein VSPackage, das einen Menübefehl verfügt die [Wie starte ich die VSIX-Erweiterungen entwickeln?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) Abschnitt.  
  
2.  Öffnen Sie die Datei mit der Definition des VSPackage. \(In einem C\#\-Projekt kann *\< Projektname \>*Package.cs.\)  
  
3.  Fügen Sie `using` Anweisungen:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback` Methode. Fügen Sie einen Aufruf an <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zum Abrufen der <xref:EnvDTE80.DTE2> Objekt:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code über das Add\-in. Beispielsweise ruft der folgende Code den Namen des Startprojekts in einer Projektmappe. \(Eine Projektmappe mit mehreren Projekte muss geöffnet sein, wenn dieses Paket ausgeführt wird.\)  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## Wie richte ich Tastenkombinationen in einem VSPackage?  
 Verwenden Sie das `<KeyBindings>` \-Element der .vsct\-Datei. Im folgenden Beispiel wird die Tastenkombination für den Befehl `idCommand1` ist Alt \+ A, und die Tastenkombination für den Befehl `idCommand2` ist Alt \+ Strg \+ A. Beachten Sie die Syntax für die Schlüsselnamen.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## Wie behandle ich Automatisierungsereignisse in einem VSPackage?  
 Sie behandeln von Automatisierungsereignissen in einem VSPackage auf die gleiche Weise wie das Add\-in. Der folgende Code zeigt, wie behandelt die `OnItemRenamed` Ereignis. \(In diesem Beispiel wird davon ausgegangen, dass Sie bereits das DTE\-Objekt gelangt sind.\)  
  
```c#  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```