---
title: 'Häufig gestellte Fragen: Umrechnen von Add-Ins in VSPackage-Erweiterungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841189"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ: Konvertieren von Add-Ins in VSPackage-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Add-Ins sind jetzt veraltet. Um eine neue Visual Studio-Erweiterung zu erstellen, müssen Sie eine VSIX-Erweiterung erstellen. Hier finden Sie Antworten auf einige häufig gestellte Fragen zum Konvertieren eines Visual Studio-Add-Ins in eine VSIX-Erweiterung.  
  
> [!WARNING]
> Ab Visual Studio 2015 können Sie für c#-und Visual Basic Projekte das VSIX-Projekt verwenden und Element Vorlagen für Menübefehle, Tool Fenster und VSPackages hinzufügen. Weitere Informationen finden Sie unter [What es New in the Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> In vielen Fällen können Sie einfach den Add-in-Code in ein VSIX-Projekt mit einem VSPackage-Projekt Element übertragen. Das DTE-Automatisierungsobjekt können Sie durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>-Methode abrufen.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Weitere Informationen finden Sie unter [wie kann ich meinen Add-in-Code in einem VSPackage ausführen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) unten.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Welche Software benötige ich zum Entwickeln von VSIX-Erweiterungen?  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Wo ist die Erweiterungs Dokumentation?  
 Beginnen Sie mit der [Entwicklung von Visual Studio-Erweiterungen](../extensibility/starting-to-develop-visual-studio-extensions.md). Weitere Artikel zur Entwicklung von VSSDK-Erweiterungen auf MSDN finden Sie unter diesem Thema.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Kann ich mein Add-in-Projekt in ein VSIX-Projekt konvertieren?  
 Ein Add-in-Projekt kann nicht direkt in ein VSIX-Projekt konvertiert werden, da die in VSIX-Projekten verwendeten Mechanismen nicht mit denen in Add-in-Projekten identisch sind. Die VSIX-Projektvorlage sowie die richtigen Projekt Element Vorlagen verfügen über viel Code, der es relativ einfach macht, als VSIX-Erweiterung zu starten.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Gewusst wie mit der Entwicklung von VSIX-Erweiterungen beginnen?  
 So erstellen Sie eine VSIX mit einem Menübefehl:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>So erstellen Sie eine VSIX-Erweiterung mit einem Menübefehl  
  
1. Erstellen eines VSIX-Projekts (**Datei**, **neu**, **Projekt**oder **typprojekt** im Fenster **Schnellstart** ). Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#/Erweiterbarkeit** oder **Visual Basic/Erweiterbarkeit** , und wählen Sie **VSIX-Projekt**aus.) Nennen Sie das Projekt **testextension** , und geben Sie einen Speicherort für das Projekt an.  
  
2. Fügen Sie eine **benutzerdefinierte Befehls** Projekt Element Vorlage hinzu. (Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wählen Sie im Dialogfeld **Neues Projekt** für Visual c# oder Visual Basic den Knoten **Erweiterbarkeit** aus, und wählen Sie **benutzerdefinierter Befehl**aus.)  
  
3. Drücken Sie F5, um das Projekt im Debugmodus zu erstellen und auszuführen.  
  
     Eine zweite Instanz von Visual Studio wird geöffnet. Diese zweite Instanz wird experimentelle Instanz genannt und besitzt möglicherweise nicht die gleichen Einstellungen wie die Instanz von Visual Studio, die Sie zum Schreiben von Code verwenden. Wenn Sie die experimentelle Instanz zum ersten Mal ausführen, müssen Sie sich bei VS Online anmelden und Ihr Design und Profil festlegen.  
  
     Im Menü **Extras (in der experimentellen** Instanz) sollte eine Schaltfläche mit dem **Namen My Command Name**angezeigt werden. Wenn Sie diese Schaltfläche auswählen, sollte eine Meldung angezeigt werden: **innerhalb von testvspackagepackage. MenuItemCallBack ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Wie kann ich meinen Add-in-Code in einem VSPackage ausführen?  
 Add-In-Code kann auf zwei Arten ausgeführt werden:  
  
- Ausgelöst durch einen Menübefehl (Der Code befindet sich in der `IDTCommandTarget.Exec`-Methode.)  
  
- Automatisch beim Start (Der Code befindet sich im `OnConnection`-Ereignishandler.)  
  
  Das Gleiche ist in einem VSPackage möglich. So fügen Sie Add-In-Code zur Rückrufmethode hinzu:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Implementieren eines Menübefehls in ein VSPackage  
  
1. Erstellen Sie ein VSPackage, das über einen Menübefehl verfügt. (Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem c#-Projekt ist <em>\<your project name></em> es Package.cs.)  
  
3. Fügen Sie der Datei die folgenden `using` -Anweisungen hinzu:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Fügen Sie den Code aus der `IDTCommandTarget.Exec`-Methode des Add-Ins hinzu. Hier sehen Sie z. b. Code, der einen neuen Bereich zum **Ausgabe** Fenster hinzufügt und "Text" im neuen Bereich ausgibt.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Erstellen Sie das Projekt, und führen Sie es aus. Drücken Sie F5, oder wählen Sie **Start** auf der Symbolleiste **Debuggen** In der experimentellen Instanz von Visual Studio sollte das **Menü Extras** über eine Schaltfläche mit dem Namen **My Command Name**verfügen. Wenn Sie diese Schaltfläche auswählen, sollten die Wörter **Text** in einem **Ausgabe** Fensterbereich angezeigt werden. (Möglicherweise müssen Sie das Fenster **Ausgabe** öffnen.)  
  
   Sie können den Code auch beim Start ausführen lassen. Dieser Ansatz wird jedoch für VSPackage-Erweiterungen generell nicht empfohlen. Wenn beim Start von Visual Studio versucht wird, zu viele Erweiterungen zu laden, kann sich die Startzeit erheblich verlängern. Eine bessere Vorgehensweise ist es, das VSPackage nur automatisch zu laden, wenn eine Bedingung erfüllt ist (beispielsweise, wenn eine Projektmappe geöffnet wird).  
  
   Dieses Verfahren zeigt, wie Sie Add-In-Code in einem VSPackage ausführen können, das automatisch geladen wird, wenn eine Projektmappe geöffnet wird:  
  
#### <a name="to-autoload-a-vspackage"></a>Automatisches Laden eines VSPackages  
  
1. Erstellen Sie ein VSIX-Projekt mit einem Visual Studio-Paket-Projekt Element. (Die Schritte hierzu finden Sie unter [Gewusst wie Starten der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Fügen Sie stattdessen nur das **Visual Studio-Paket** Projekt Element hinzu.) Nennen Sie das VSIX-Projekt " **testautoload**".  
  
2. Öffnen Sie TestAutoloadPackage.cs. Suchen Sie die Zeile, in der die Paketklasse deklariert ist:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Über dieser Zeile befindet sich ein Satz Attribute. Fügen Sie dieses Attribut hinzu:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Setzen Sie einen Haltepunkt in der `Initialize()`-Methode, und starten Sie das Debuggen (F5).  
  
5. Öffnen Sie in der experimentellen Instanz ein Projekt. Das VSPackage sollte geladen und der Haltepunkt erreicht werden.  
  
   Sie können andere Kontexte angeben, in denen das VSPackage geladen werden soll, indem Sie die Felder von <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> verwenden. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Wie kann ich das DTE-Objekt abrufen?  
 Wenn das Add-In kein Benutzeroberfläche – zum Beispiel Menübefehle, Schaltflächen der Symbolleiste oder Toolfenster – anzeigt, können Sie möglicherweise den Code unverändert nutzen, solange Sie das DTE-Automatisierungsobjekt aus dem VSPackage abrufen. Dazu gehen Sie wie folgt vor:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Abrufen des DTE-Objekts aus einem VSPackage  
  
1. Suchen Sie in einem VSIX-Projekt mit einer Visual Studio-Paket Element Vorlage nach der <em>\<project name></em> Datei Package.cs. Dies ist die Klasse, die von <xref:Microsoft.VisualStudio.Shell.Package> abgeleitet wird. Sie kann Ihnen helfen, mit Visual Studio zu interagieren. In diesem Fall verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>-Methode, um das <xref:EnvDTE80.DTE2>-Objekt zu suchen.  
  
2. Fügen Sie diese `using`-Anweisungen hinzu:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Suchen Sie die `Initialize`-Methode. Diese Methode behandelt den Befehl, den Sie im Paket-Assistenten angegeben haben. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das DTE-Objekt abzurufen:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Wenn Sie das <xref:EnvDTE.DTE>-Automatisierungsobjekt abgerufen haben, können Sie den übrigen Code zum Projekt hinzufügen. Wenn Sie das <xref:EnvDTE80.DTE2>-Objekt benötigen, können Sie ebenso verfahren.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Wie ändere ich Menübefehle und Schaltflächen der Symbolleisten im Add-In in den Stil des VSPackages?  
 VSPackage-Erweiterungen nutzen die .vsct-Datei zur Erstellung der meisten Menübefehle, Symbolleisten, Schaltflächen der Symbolleisten und anderer Elemente der Benutzeroberfläche. Die Projekt Element Vorlage für **benutzerdefinierte Befehle** bietet Ihnen die Möglichkeit, einen Befehl im **Menü Extras** zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu vsct-Dateien finden Sie unter Gewusst [wie: Hinzufügen von Benutzeroberflächen Elementen durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Exemplarische Vorgehensweisen, die veranschaulichen, wie Sie mithilfe der vsct-Datei Menü Elemente, Symbolleisten und Symbolleisten Schaltflächen hinzufügen, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Wie füge ich in VSPackages benutzerdefinierte Toolfenster hinzu?  
 Die Projekt Element Vorlage benutzerdefiniertes Tool Fenster bietet Ihnen die Möglichkeit, ein Tool Fenster zu erstellen. Weitere Informationen zu dieser Projekt Element Vorlage finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md). Informationen zu Tool Fenstern finden Sie unter [erweitern und Anpassen von Tool Fenstern](../extensibility/extending-and-customizing-tool-windows.md) und in den darin stehenden Artikeln, insbesondere durch das [Hinzufügen eines Tool Fensters](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Wie verwalte ich Visual Studio-Fenster mit VSPackages?  
 Wenn das Add-In Visual Studio-Fenster verwaltet, sollte der Code des Add-Ins auch in einem VSPackage funktionieren. Diese Prozedur zeigt beispielsweise, wie Sie Code hinzufügen, der die **Aufgabenliste** der- `MenuItemCallback` Methode des VSPackage verwaltet.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Einfügen von Code zur Fensterverwaltung von einem Add-In in ein VSPackage  
  
1. Erstellen Sie ein VSPackage mit einem Menübefehl, wie im Abschnitt [Gewusst wie beginnen Sie mit der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem c#-Projekt ist <em>\<your project name></em> es Package.cs.)  
  
3. Fügen Sie diese `using`-Anweisungen hinzu:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Fügen Sie den Code aus dem Add-In hinzu. Hier sehen Sie z. b. Code, der dem **Aufgabenliste**neue Aufgaben hinzufügt, die Anzahl der Aufgaben auflistet und dann eine Aufgabe löscht.  
  
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
  
1. Erstellen Sie ein VSPackage mit einem Menübefehl, wie im Abschnitt [Gewusst wie beginnen Sie mit der Entwicklung von VSIX-Erweiterungen?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Öffnen Sie die Datei, in der die Definition des VSPackage enthalten ist. (In einem c#-Projekt ist <em>\<your project name></em> es Package.cs.)  
  
3. Fügen Sie diese `using`-Anweisungen hinzu:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Suchen Sie die `MenuItemCallback`-Methode. Fügen Sie einen Aufruf zu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> hinzu, um das <xref:EnvDTE80.DTE2>-Objekt abzurufen:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Fügen Sie den Code aus dem Add-In hinzu. Der folgende Code ruft beispielsweise den Namen eine Startprojekts in einer Projektmappe ab. (Eine Projektmappe mit mehreren Projekten muss geöffnet sein, wenn dieses Paket ausgeführt wird.)  
  
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
