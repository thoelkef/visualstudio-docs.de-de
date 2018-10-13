---
title: 'Häufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b391c11fe47914df9c7b3ab1af12d8cbb5a55d9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221272"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ: Konvertieren von Add-Ins in VSPackage-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Add-Ins sind jetzt veraltet. Um eine neue Visual Studio-Erweiterung zu machen, müssen Sie eine VSIX-Erweiterung zu erstellen. Hier sind die Antworten auf einige häufig gestellten Fragen dazu, wie Sie ein Visual Studio-add-in in einer VSIX-Erweiterung zu konvertieren.  
  
> [!WARNING]
>  Ab Visual Studio 2015 für c# und Visual Basic-Projekte, können Sie mithilfe der VSIX-Projekts und hinzufügen-Elementvorlagen für Menübefehle, Toolfenster und VSPackages. Weitere Informationen finden Sie unter [Neuigkeiten in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  In vielen Fällen können Sie einfach Ihren Code-add-in einem VSIX-Projekt mit einem VSPackage-Projektelement übertragen. Das DTE-Automatisierungsobjekt können Sie durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>-Methode abrufen.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Weitere Informationen finden Sie unter [wie kann ich meinen Add-in Code in einem VSPackage ausführen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) unten.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Welche Software benötige ich zum Entwickeln von VSIX-Erweiterungen?  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Wo befindet sich die Dokumentation zur Erweiterung?  
 Beginnen Sie mit [ab Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md). Weitere Artikel zur Entwicklung von VSSDK-Erweiterung auf MSDN finden Sie unten, dass ein.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Kann ich meinen Add-In-Projekt in ein VSIX-Projekt konvertieren?  
 Ein Add-In Projekt kann nicht direkt in einem VSIX-Projekt nicht konvertiert werden, da die verwendeten Mechanismen in VSIX-Projekte nicht identisch mit denen-Add-in-Projekte sind. Die VSIX-Projektvorlage sowie die richtige Projektelementvorlagen haben viel Code, der es relativ einfach einzurichten und als VSIX-Erweiterung ausgeführt wird.  
  
##  <a name="BKMK_StartDeveloping"></a> Wie beginne ich mit der Entwicklung von VSIX-Erweiterungen?  
 Hier ist, wie Sie einer VSIX-Datei vornehmen, die einen Menübefehl hat:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Um eine VSIX-Erweiterung zu machen, die über einen Menübefehl verfügt  
  
1.  Erstellen eines VSIX-Projekts (**Datei**, **neu**, **Projekt**, oder geben **Projekt** in die **Schnellstart** Fenster). In der **neues Projekt** Dialogfeld erweitern Sie **Visual c# / Erweiterbarkeit** oder **Visual Basic / Erweiterungen** , und wählen Sie **VSIX-Projekt**.) Nennen Sie das Projekt **TestExtension** und geben Sie einen Speicherort für sie.  
  
2.  Hinzufügen einer **benutzerdefinierten Befehls** Projektelementvorlage. (Mit der rechten Maustaste des Knotens "Projekt" in der **Projektmappen-Explorer** , und wählen Sie **hinzufügen / neues Element**. In der **neues Projekt** Dialogfeld für Visual c# oder Visual Basic, wählen Sie die **Erweiterbarkeit** Knoten, und wählen **benutzerdefinierten Befehls**.)  
  
3.  Drücken Sie F5, um das Projekt im Debugmodus zu erstellen und auszuführen.  
  
     Eine zweite Instanz von Visual Studio wird geöffnet. Diese zweite Instanz wird experimentelle Instanz genannt und besitzt möglicherweise nicht die gleichen Einstellungen wie die Instanz von Visual Studio, die Sie zum Schreiben von Code verwenden. Wenn Sie die experimentelle Instanz zum ersten Mal ausführen, müssen Sie sich bei VS Online anmelden und Ihr Design und Profil festlegen.  
  
     Auf der **Tools** Menü (in der experimentellen Instanz) sollte eine Schaltfläche namens **mein Befehlsname**. Wenn Sie diese Schaltfläche auswählen, eine Meldung angezeigt: **Inside TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a> Wie kann ich meinen Add-in Code in einem VSPackage ausführen?  
 Add-In-Code kann auf zwei Arten ausgeführt werden:  
  
-   Ausgelöst durch einen Menübefehl (Der Code befindet sich in der `IDTCommandTarget.Exec`-Methode.)  
  
-   Automatisch beim Start (Der Code befindet sich im `OnConnection`-Ereignishandler.)  
  
 Das Gleiche ist in einem VSPackage möglich. So fügen Sie Add-In-Code zur Rückrufmethode hinzu:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Implementieren eines Menübefehls in ein VSPackage  
  
1.  Erstellen Sie ein VSPackage, das über einen Menübefehl verfügt. (Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem C#-Projekt hat  *\<Projektname >* Package.cs.)  
  
3.  Fügen Sie folgende `using`-Anweisungen in die Datei ein:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code aus der `IDTCommandTarget.Exec`-Methode des Add-Ins hinzu. Hier ist z. B. Code, der einen neuen Bereich zum fügt die **Ausgabe** Fenster und gibt "Some Text" im neuen Bereich.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Erstellen Sie das Projekt, und führen Sie es aus. Drücken Sie F5, oder wählen Sie **starten** auf die **Debuggen** Symbolleiste. In der experimentellen Instanz von Visual Studio die **Tools** Menü müssen auf eine Schaltfläche namens **mein Befehlsname**. Wenn Sie diese Schaltfläche auswählen, die Wörter **Some Text** sollte angezeigt werden, eine **Ausgabe** Fensterbereich. (Möglicherweise müssen Sie Sie öffnen die **Ausgabe** Fenster.)  
  
 Sie können den Code auch beim Start ausführen lassen. Dieser Ansatz wird jedoch für VSPackage-Erweiterungen generell nicht empfohlen. Wenn beim Start von Visual Studio versucht wird, zu viele Erweiterungen zu laden, kann sich die Startzeit erheblich verlängern. Eine bessere Vorgehensweise ist es, das VSPackage nur automatisch zu laden, wenn eine Bedingung erfüllt ist (beispielsweise, wenn eine Projektmappe geöffnet wird).  
  
 Dieses Verfahren zeigt, wie Sie Add-In-Code in einem VSPackage ausführen können, das automatisch geladen wird, wenn eine Projektmappe geöffnet wird:  
  
#### <a name="to-autoload-a-vspackage"></a>Automatisches Laden eines VSPackages  
  
1.  Erstellen Sie ein VSIX-Projekt mit einem Visual Studio-Paket-Projektelement. (Die Schritte hierzu finden Sie unter [wie beginne ich mit der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Fügen Sie einfach die **Visual Studio-Paket** Projektelement stattdessen.) Nennen Sie das VSIX-Projekt **TestAutoload**.  
  
2.  Öffnen Sie TestAutoloadPackage.cs. Suchen Sie die Zeile, in der die Paketklasse deklariert ist:  
  
    ```csharp  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Über dieser Zeile befindet sich ein Satz Attribute. Fügen Sie dieses Attribut hinzu:  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Setzen Sie einen Haltepunkt in der `Initialize()`-Methode, und starten Sie das Debuggen (F5).  
  
5.  Öffnen Sie in der experimentellen Instanz ein Projekt. Das VSPackage sollte geladen und der Haltepunkt erreicht werden.  
  
 Sie können andere Kontexte angeben, in denen das VSPackage geladen werden soll, indem Sie die Felder von <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> verwenden. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Wie kann ich das DTE-Objekt abrufen?  
 Wenn das Add-In kein Benutzeroberfläche – zum Beispiel Menübefehle, Schaltflächen der Symbolleiste oder Toolfenster – anzeigt, können Sie möglicherweise den Code unverändert nutzen, solange Sie das DTE-Automatisierungsobjekt aus dem VSPackage abrufen. Gehen Sie dabei folgendermaßen vor:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Abrufen des DTE-Objekts aus einem VSPackage  
  
1.  Suchen Sie in einem VSIX-Projekt mit einer Elementvorlage für Visual Studio-Paket nach der  *\<Projektname >* Datei Package.cs. Dies ist die Klasse, die von <xref:Microsoft.VisualStudio.Shell.Package> abgeleitet wird. Sie kann Ihnen helfen, mit Visual Studio zu interagieren. In diesem Fall verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>-Methode, um das <xref:EnvDTE80.DTE2>-Objekt zu suchen.  
  
2.  Fügen Sie diese `using`-Anweisungen hinzu:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Suchen Sie die `Initialize`-Methode. Diese Methode behandelt den Befehl, den Sie im Paket-Assistenten angegeben haben. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das DTE-Objekt abzurufen:  
  
    ```csharp  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Wenn Sie das <xref:EnvDTE.DTE>-Automatisierungsobjekt abgerufen haben, können Sie den übrigen Code zum Projekt hinzufügen. Wenn Sie das <xref:EnvDTE80.DTE2>-Objekt benötigen, können Sie ebenso verfahren.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Wie ändere ich Menübefehle und Schaltflächen der Symbolleisten im Add-In in den Stil des VSPackages?  
 VSPackage-Erweiterungen nutzen die .vsct-Datei zur Erstellung der meisten Menübefehle, Symbolleisten, Schaltflächen der Symbolleisten und anderer Elemente der Benutzeroberfläche. Die **benutzerdefinierten Befehls** Projektelementvorlage bietet Ihnen die Möglichkeit, einen Befehl zu erstellen, auf die **Tools** Menü. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu VSCT-Dateien, finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Exemplarische Vorgehensweisen, die zeigen, wie Sie die VSCT-Datei zu verwenden, um das Hinzufügen von Menübefehlen, Symbolleisten und Schaltflächen der Symbolleiste finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Wie füge ich in VSPackages benutzerdefinierte Toolfenster hinzu?  
 Die benutzerdefinierte Toolfenster Projektelementvorlage bietet Ihnen die Option zum Erstellen eines Toolfensters. Weitere Informationen zu diesem Projektelementvorlage, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Weitere Informationen zu Toolfenstern, finden Sie unter [erweitern und Anpassen von Tool Windows](../extensibility/extending-and-customizing-tool-windows.md) und in den Artikeln, darunter insbesondere [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Wie verwalte ich Visual Studio-Fenster mit VSPackages?  
 Wenn das Add-In Visual Studio-Fenster verwaltet, sollte der Code des Add-Ins auch in einem VSPackage funktionieren. Beispielsweise dieses Verfahren veranschaulicht das Hinzufügen von Code, der verwaltet die **Aufgabenliste** auf die `MenuItemCallback` -Methode des VSPackages.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Einfügen von Code zur Fensterverwaltung von einem Add-In in ein VSPackage  
  
1.  Erstellen Sie eine VSPackage mit einem Menübefehl, wie in der [wie beginne ich mit der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) Abschnitt.  
  
2.  Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem C#-Projekt hat  *\<Projektname >* Package.cs.)  
  
3.  Fügen Sie diese `using`-Anweisungen hinzu:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code aus dem Add-In hinzu. Hier ist z. B. Code, der die neue Aufgaben fügt die **Aufgabenliste**, listet die Anzahl der Aufgaben, und klicken Sie dann eine Aufgabe gelöscht.  
  
    ```csharp  
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
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Wie verwalte ich Projekte und Projektmappen in einem VSPackage?  
 Wenn das Add-In Projekte und Projektmappen verwaltet, sollte der Code des Add-Ins auch in einem VSPackage funktionieren. Dieser Vorgang zeigt beispielsweise, wie Sie Code hinzufügen können, der das Startprojekt abruft.  
  
1.  Erstellen Sie eine VSPackage mit einem Menübefehl, wie in der [wie beginne ich mit der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) Abschnitt.  
  
2.  Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem C#-Projekt hat  *\<Projektname >* Package.cs.)  
  
3.  Fügen Sie diese `using`-Anweisungen hinzu:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Fügen Sie den Code aus dem Add-In hinzu. Der folgende Code ruft beispielsweise den Namen eine Startprojekts in einer Projektmappe ab. (Eine Projektmappe mit mehreren Projekten muss geöffnet sein, wenn dieses Paket ausgeführt wird.)  
  
    ```csharp  
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
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Wie lege ich Tastenkombinationen in einem VSPackage fest?  
 Verwenden Sie das `<KeyBindings>`-Element der .vsct-Datei. Im folgenden Beispiel ist die Tastenkombination für den Befehl `idCommand1` Alt+A. Die Tastenkombination für den Befehl `idCommand2` ist Alt+Ctrl+A. Beachten Sie die Sytax für die Schlüsselnamen.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Wie behandle ich Automatisierungsereignisse in einem VSPackage?  
 Automatisierungsereignisse in einem VSPackage behandeln Sie genauso wie im Add-In. Im folgenden Codebeispiel wird die Behandlung des `OnItemRenamed`-Ereignisses veranschaulicht. (In diesem Beispiel wird angenommen, dass Sie das DTE-Objekt bereits abgerufen haben.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```

