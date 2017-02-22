---
title: "Dynamisches Hinzuf&#252;gen von Men&#252;elementen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "Dynamisches Hinzufügen von Menüelementen"
  - "Menüs, dynamische Elemente hinzufügen"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
---
# Dynamisches Hinzuf&#252;gen von Men&#252;elementen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Menüelemente zur Laufzeit hinzufügen, durch Angabe der `DynamicItemStart` Befehl\-Flag auf eine Schaltfläche Platzhalterdefinition in der Visual Studio\-Befehl\-Tabelle \(VSCT\)\-Datei anschließend definieren \(im Code\) die Anzahl der im Menü angezeigt und die Befehle behandeln Elemente. Wenn das VSPackage geladen wird, wird der Platzhalter durch die dynamischen Menüelemente ersetzt.  
  
 Visual Studio verwendet dynamische Listen in der **zuletzt verwendet** Liste \(MRU\), der die Namen der Dokumente, die zuletzt geöffnet wurde angezeigt, und die **Windows** Liste, die die Namen von Windows angezeigt, die derzeit geöffnet sind. Die `DynamicItemStart` \-Flag auf eine Definition gibt an, dass der Befehl einen Platzhalter bis VSPackage geöffnet wird. Wenn das VSPackage geöffnet wird, wird der Platzhalter ersetzt, mit 0 oder mehr Befehle, die zur Laufzeit erstellt und der dynamischen Liste hinzugefügt werden. Sie können möglicherweise nicht die Position im Menü angezeigt wird, wo die dynamische Liste angezeigt wird, bis das VSPackage geöffnet wird. Um die dynamische Liste zu füllen, fordert Visual Studio das VSPackage für einen Befehl mit der ID suchen, deren ersten Zeichen als Platzhalter\-ID identisch sind. Wenn Visual Studio einen entsprechenden Befehl gefunden wird, werden der dynamischen Liste den Namen des Befehls hinzugefügt. Es erhöht die ID und sucht nach einem anderen entsprechende Befehl der dynamischen Liste hinzugefügt, bis keine weiteren dynamischen Befehle vorhanden sind.  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht, wie das Startprojekt in Visual Studio\-Projektmappe mit einem Befehl aktiviert die **Projektmappen\-Explorer** Symbolleiste. Einen Menü\-Controller, die eine dynamische Dropdown\-Liste der Projekte in der aktiven Projektmappe verwendet. Um zu verhindern, dass dieser Befehl angezeigt wird, wenn keine Projektmappe geöffnet ist, oder wenn die geöffneten Projektmappe nur ein Projekt enthält, wird das VSPackage geladen, nur, wenn eine Projektmappe mehrere Projekte enthält.  
  
 Weitere Informationen zu VSCT\-Dateien finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Erstellen eine Erweiterung mit einem Menübefehl  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `DynamicMenuItems`.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für den benutzerdefinierten Befehl hinzu, und nennen Sie sie **DynamicMenu**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Einrichten der Elemente in der VSCT\-Datei  
 Um einen Domänencontroller im Menü mit dynamischen Menüelemente auf einer Symbolleiste zu erstellen, geben Sie die folgenden Elemente:  
  
-   Zwei Gruppen, den Menü Controller enthält, und eine andere, die die Elemente in der Dropdown\-Liste enthält Befehls  
  
-   Ein Element vom Typ `MenuController`  
  
-   Zwei Schaltflächen, die als Platzhalter für die Menüelemente und anderen fungiert, die das Symbol und die QuickInfo auf der Symbolleiste bereitstellt.  
  
1.  Definieren Sie in DynamicMenuPackage.vsct die Befehls\-IDs. Finden Sie im Abschnitt Symbole, und Ersetzen Sie die IDSymbol\-Elemente in der **GuidDynamicMenuPackageCmdSet** GuidSymbol\-Block. Sie müssen IDSymbol Elemente für zwei Gruppen, den Menü\-Controller, den Platzhalter\-Befehl und der Premium\-Befehl definieren.  
  
    ```c#  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Klicken Sie im Abschnitt Gruppen löschen Sie die vorhandenen Gruppen, und fügen Sie die zwei Gruppen, die Sie soeben definiert:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Fügen Sie der MenuController hinzu. Legen Sie die Kennzeichnung des Befehls als DynamicVisibility, da es nicht immer sichtbar ist. Die ButtonText wird nicht angezeigt.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Fügen Sie zwei Schaltflächen, als Platzhalter für die dynamischen Menüelemente und als Anker für die MenuController.  
  
     Das übergeordnete Element der Schaltfläche Platzhalter ist die **MyMenuControllerGroup**. Die Platzhalter\-Schaltfläche Befehlsflags DynamicItemStart, DynamicVisibility und TextÄndert hinzugefügt. Die ButtonText wird nicht angezeigt.  
  
     Die Schaltfläche "Premium" enthält das Symbol und der QuickInfo\-Text. Das übergeordnete Element der Anker Schaltfläche ist auch die **MyMenuControllerGroup**. Sie hinzufügen die Kennzeichnung des Befehls NoShowOnMenuController um sicherzustellen, dass die Schaltfläche nicht tatsächlich in der Controller\-Dropdownliste im Menü angezeigt wird und die Kennzeichnung des Befehls FixMenuController permanente Anker machen.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Das Projekt \(im Ordner "Ressourcen"\) ein Symbol hinzu, und fügen Sie dann den Verweis auf die VSCT\-Datei hinzu. In dieser exemplarischen Vorgehensweise verwenden wir das Pfeile\-Symbol, das in der Projektvorlage enthalten ist.  
  
5.  Einen Abschnitt VisibilityConstraints außerhalb Abschnitt Befehle unmittelbar vor dem Abschnitt Symbole hinzufügen. \(Sie können eine Warnung erhalten, wenn Sie es nach Symbole hinzufügen.\) Dieser Abschnitt stellt sicher, dass der Controller im Menü angezeigt wird, nur, wenn eine Projektmappe mit mehreren Projekten geladen wird.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## Implementieren des dynamischen Menübefehls  
 Sie erstellen eine dynamisches Menü Command\-Klasse, die von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In dieser Implementierung gibt der Konstruktor ein Prädikat für den Abgleich von Befehlen verwendet werden. Müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode mit diesem Prädikat Festlegen der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> \-Eigenschaft, welcher den Befehl aufgerufen werden.  
  
1.  Erstellen Sie eine neue C\#\-Klassendatei namens DynamicItemMenuCommand.cs, und fügen Sie eine Klasse mit dem Namen **DynamicItemMenuCommand** die von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Fügen Sie die folgende using\-Anweisungen:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie ein privates Feld zum Speichern von des Prädikats übereinstimmen:  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  Fügen Sie einen Konstruktor, der von erbt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Konstruktor und gibt einen Befehlshandler und ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Handler. Fügen Sie ein Prädikat für den Abgleich mit dem Befehl:  
  
    ```c#  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode, sodass die übereinstimmenden Prädikat und legt aufgerufen die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Eigenschaft:  
  
    ```c#  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## Der Befehl hinzufügen  
 Der DynamicMenu\-Konstruktor ist, in dem Sie Menübefehle, einschließlich der dynamischen Menüs und Menüelemente einrichten.  
  
1.  Fügen Sie in DynamicMenuPackageGuids.cs die GUID für den Befehlssatz und die Befehls\-ID hinzu:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  Fügen Sie in der Datei DynamicMenu.cs die folgende using\-Anweisungen:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie ein privates Feld in der Klasse DynamicMenu **dte2**.  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  Fügen Sie eine private RootItemId\-Feld:  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  Fügen Sie im Konstruktor DynamicMenu den Menübefehl ein. Im nächsten Abschnitt definieren wir die Befehlshandler der `BeforeQueryStatus` \-Ereignishandler und dem Prädikat übereinstimmen.  
  
    ```c#  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## Implementieren die Handler  
 Um dynamische Menüelemente auf einem Domänencontroller im Menü zu implementieren, müssen Sie den Befehl behandeln, wenn eine dynamische Element geklickt wird. Sie müssen auch die Logik implementieren, die den Zustand des Menüelements festlegt. Fügen Sie die Handler zur DynamicMenu\-Klasse.  
  
1.  Implementieren der **Startprojekt festlegen** \-, hinzuzufügen, die **OnInvokedDynamicItem** \-Ereignishandler. Anscheinend für das Projekt, dessen Name dem der Text des Befehls, der aufgerufen wurde entspricht, und durch Festlegen des absoluten Pfads im Projekt als Startprojekt legt, die <xref:EnvDTE.SolutionBuild.StartupProjects%2A> Eigenschaft.  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Hinzufügen der `OnBeforeQueryStatusDynamicItem` \-Ereignishandler. Dies ist der Handler aufgerufen wird, bevor ein `QueryStatus` Ereignis. Sie bestimmt, ob das Menüelement ein "echten" Element, d. h. nicht das Platzhalter an, und gibt an, ob das Element bereits aktiviert ist \(d. h., dass das Projekt bereits als Startprojekt festgelegt ist\).  
  
    ```c#  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## Implementieren die Befehls\-ID Übereinstimmung Prädikat  
  
1.  Nun implementieren Sie das Prädikat übereinstimmen. Wir müssen zwei Dinge zu bestimmen: zuerst, ob die Befehls\-ID ist ungültig \(er ist größer als oder gleich der angegebenen Befehls\-ID\), und Zweitens, ob es eine mögliche Projekt angibt \(es ist kleiner als die Anzahl der Projekte in der Projektmappe\).  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## Festlegen des VSPackages laden, nur, wenn eine Projektmappe mehrere Projekte enthält  
 Da die **Startprojekt festlegen** Befehl keinen Sinn, wenn die aktive Projektmappe mehrere Projekte verfügt, können Sie Ihr VSPackage, automatisch in diesem Fall wird nur geladen. Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> zusammen mit den Benutzeroberflächenkontext <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. Fügen Sie in der Datei DynamicMenuPackage.cs die folgenden Attribute auf die DynamicMenuPackage\-Klasse:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## Testen den Befehl Startprojekt festlegen  
 Jetzt können Sie Ihren Code testen.  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
2.  Öffnen Sie eine Projektmappe mit mehreren Projekten in der experimentellen Instanz.  
  
     Der Pfeil sollte angezeigt werden, auf die **Projektmappen\-Explorer** Symbolleiste. Wenn Sie es erweitern, sollte die Menüelemente, die darstellen, die verschiedenen Projekte in der Projektmappe angezeigt werden.  
  
3.  Wenn Sie eines der Projekte einchecken, wird es das Startprojekt.  
  
4.  Wenn Sie die Projektmappe schließen oder eine Projektmappe nur ein Projekt öffnen, sollte das Symbol auf der Symbolleiste angezeigt werden.  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)