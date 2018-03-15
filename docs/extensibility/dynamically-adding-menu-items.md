---
title: "Dynamisches Hinzufügen von Menüelementen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a803933b3b1e6d353b9899cb8997dbaa6897e
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="dynamically-adding-menu-items"></a>Dynamisches Hinzufügen von Menüelementen
Sie können Menüelemente zur Laufzeit hinzufügen, durch Angeben der `DynamicItemStart` Befehl Flag für die Definition eines Platzhalter-Schaltfläche in der Visual Studio-Befehlstabelle (VSCT)-Datei, und dann definieren (im Code) die Anzahl der im Menü angezeigt, und behandeln die Befehle Elemente. Wenn das VSPackage geladen wird, wird der Platzhalter für die dynamische Menüelemente ersetzt.  
  
 Visual Studio verwendet dynamische Listen in die **zuletzt verwendet** (MRU)-Liste, die die Namen von Dokumenten, die zuletzt geöffnet wurde anzeigt, und die **Windows** Liste aus, die die Namen von Windows angezeigt die derzeit geöffnet sind.   Die `DynamicItemStart` einer Befehlsdefinition-Flag gibt an, dass der Befehl ein Platzhalter ist, bis das VSPackage geöffnet wird. Wenn das VSPackage geöffnet wird, wird der Platzhalter ersetzt, mit 0 oder mehr Befehle, die zur Laufzeit erstellt und der dynamische Liste hinzugefügt werden. Sie können möglicherweise nicht die Position im Menü angezeigt, in dem die dynamische Liste angezeigt wird, bis das VSPackage geöffnet wird.  Um die dynamische Liste aufzufüllen, fordert Visual Studio das VSPackage, um einen Befehl mit der ID suchen, dessen ersten Zeichen, die die ID des Platzhalters identisch sind. Wenn Visual Studio einen entsprechenden Befehl gefunden wird, werden die dynamischen Liste den Namen des Befehls hinzugefügt. Anschließend inkrementiert die ID und sucht nach einer anderen übereinstimmenden Befehl aus, um die dynamische Liste hinzugefügt, bis keine weiteren dynamische Befehle vorhanden sind.  
  
 Diese exemplarische Vorgehensweise veranschaulicht, wie das Startup-Projekt in Visual Studio-Projektmappe mit einem Befehl auf dem **Projektmappen-Explorer** Symbolleiste. Er verwendet ein Menücontroller, die eine dynamische Dropdown-Liste der Projekte in der aktiven Projektmappe aufweist. Um zu verhindern, dass dieser Befehl angezeigt wird, wenn keine Projektmappe geöffnet ist, oder wenn die geöffneten Projektmappe nur ein Projekt enthält, das VSPackage wird nur geladen, wenn eine Lösung mehrere Projekte enthält.  
  
 Weitere Informationen zu VSCT-Dateien finden Sie unter [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Erstellen eine Erweiterung mit einem Menübefehl  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `DynamicMenuItems`.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für den benutzerdefinierten Befehl hinzu, und nennen Sie sie **DynamicMenu**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Einrichten der Elemente in der VSCT-Datei  
 Um mit dynamischen Menüelemente auf einer Symbolleiste ein Menücontroller zu erstellen, geben Sie die folgenden Elemente:  
  
-   Zwei Gruppen, einer mit der Menücontroller im enthält und ein anderes, das die Elemente in der Dropdownliste enthält Befehls  
  
-   Ein Menu-Element des Typs `MenuController`  
  
-   Zwei Schaltflächen, eine, die als Platzhalter für die Menüelemente und ein anderes fungiert, das das Symbol und die QuickInfo auf der Symbolleiste bereitstellt.  
  
1.  Definieren Sie in DynamicMenuPackage.vsct die Befehls-IDs. Navigieren Sie zum Abschnitt Symbole, und Ersetzen Sie die IDSymbol Elemente in der **GuidDynamicMenuPackageCmdSet** GuidSymbol-Block. Sie müssen IDSymbol Elemente für zwei Gruppen, die Menücontroller, die Platzhalter-Befehl und der Premium-Befehl definieren.  
  
    ```csharp  
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
  
2.  Klicken Sie im Abschnitt Gruppen löschen Sie die vorhandenen Gruppen, und fügen Sie die zwei Gruppen, die gerade definierte:  
  
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
  
     Fügen Sie der MenuController hinzu. Die DynamicVisibility-Befehlsflag festgelegt, da es nicht immer sichtbar ist. Die ButtonText wird nicht angezeigt.  
  
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
  
3.  Fügen Sie zwei Schaltflächen, das als Platzhalter für die dynamische Menüelemente und als Anker für die MenuController hinzu.  
  
     Das übergeordnete Element die Schaltfläche "Platzhalter" ist die **MyMenuControllerGroup**. Fügen Sie der DynamicItemStart DynamicVisibility und TextChanges-Befehlsflags hinzu, auf die Schaltfläche "Platzhalter". Die ButtonText wird nicht angezeigt.  
  
     Die Schaltfläche "Premium" enthält das Symbol und der QuickInfo-Text. Das übergeordnete Element der Anker Schaltfläche ist auch die **MyMenuControllerGroup**. Sie fügen Sie der NoShowOnMenuController-Befehlsflag, um sicherzustellen, dass die Schaltfläche mit der tatsächlich in der Controller-Dropdownliste im Menü angezeigt wird und die FixMenuController-Befehlsflag, erleichtern die permanente Anker hinzu.  
  
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
  
4.  Das Projekt (im Ordner "Ressourcen") ein Symbol hinzu, und fügen Sie den Verweis darauf in der VSCT-Datei hinzu. In dieser exemplarischen Vorgehensweise verwenden wir die Pfeile-Symbol, das in der Projektvorlage enthalten ist.  
  
5.  Fügen Sie einen Abschnitt VisibilityConstraints außerhalb der im Abschnitt "Befehle" direkt vor der Symbole im Abschnitt hinzu. (Sie können eine Warnung erhalten, wenn Sie es nach Symbolen hinzufügen.) Dieser Abschnitt stellt sicher, dass der Menücontroller im angezeigt wird, wenn nur eine Projektmappe mit mehreren Projekten geladen wird.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementieren des Menübefehls dynamische  
 Sie erstellen eine dynamisches Menü Command-Klasse, die von erben <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In dieser Implementierung gibt der Konstruktor ein Prädikat für den Abgleich von Befehlen verwendet werden. Müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode mit diesem Prädikat festgelegt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> -Eigenschaft, die den Befehl aufgerufen wird, werden identifiziert.  
  
1.  Erstellen Sie eine neue C#-Klassendatei mit dem Namen DynamicItemMenuCommand.cs, und fügen Sie eine Klasse namens **DynamicItemMenuCommand** von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie ein privates Feld zum Speichern der Übereinstimmung Prädikat hinzu:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Fügen Sie einen Konstruktor, der von erbt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Konstruktor und Befehlshandler angibt und ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Handler. Fügen Sie ein Prädikat für den Abgleich von des Befehls hinzu:  
  
    ```csharp  
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
  
5.  Überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode, sodass die Übereinstimmungen Prädikat und legt aufgerufen der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Eigenschaft:  
  
    ```csharp  
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
  
## <a name="adding-the-command"></a>Der Befehl hinzufügen  
 Der DynamicMenu-Konstruktor ist, in dem Sie Menübefehle, einschließlich dynamische Menüs und Menüelemente einrichten.  
  
1.  Fügen Sie in DynamicMenuPackage.cs die GUID für den Befehlssatz und die Befehls-ID:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  Fügen Sie in der Datei DynamicMenu.cs die folgenden using-Anweisungen:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie ein privates Feld in der Klasse DynamicMenu **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Fügen Sie eine private RootItemId Feld hinzu:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  Fügen Sie den Menübefehl im Konstruktor DynamicMenu hinzu. Im nächsten Abschnitt definieren wir die Befehlshandler der `BeforeQueryStatus` -Ereignishandler und das Prädikat übereinstimmen.  
  
    ```csharp  
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
  
## <a name="implementing-the-handlers"></a>Implementieren die Handler  
 Um dynamische Menüelemente auf ein Menücontroller zu implementieren, müssen Sie den Befehl behandeln, wenn eine dynamische Element geklickt wird. Sie müssen auch die Logik implementieren, die den Zustand des Menüelements festlegt. Der Handler der DynamicMenu-Klasse hinzufügen.  
  
1.  Zum Implementieren der **Startprojekt festlegen** Befehl, fügen Sie der **OnInvokedDynamicItem** -Ereignishandler. Anzeige für das Projekt, dessen Name identisch mit dem Text des Befehls, die aufgerufen wurde ist, und legt als Startprojekt durch Festlegen der absoluten Pfads in, der <xref:EnvDTE.SolutionBuild.StartupProjects%2A> Eigenschaft.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
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
  
2.  Hinzufügen der `OnBeforeQueryStatusDynamicItem` -Ereignishandler. Dies ist der Handler aufgerufen, bevor ein `QueryStatus` Ereignis. Sie bestimmt, ob das Menüelement ein "real" Element ist, d. h. nicht die Platzhalterelement, und gibt an, ob das Element bereits aktiviert ist (d. h., dass das Projekt bereits als Startprojekt festgelegt ist).  
  
    ```csharp  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementieren die Befehls-ID Übereinstimmung Prädikat  
  
1.  Implementieren Sie jetzt das Prädikat übereinstimmen. Es müssen zwei Dinge zu bestimmen: zuerst, ob die Befehls-ID ist ungültig (er ist größer als oder gleich dem deklarierten Befehls-ID), und Zweitens, ob es eine mögliche Projekt angegeben (es ist kleiner als die Anzahl der Projekte in der Projektmappe).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Festlegen des VSPackages beim Laden nur, wenn eine Lösung mehrere Projekte enthält  
 Da die **Startprojekt festlegen** Befehl keinen Sinn, wenn die aktive Projektmappe mehrere Projekte verfügt, können Sie Ihr VSPackage, um automatische nur in diesem Fall laden festlegen. Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> zusammen mit den Benutzeroberflächenkontext <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. Fügen Sie in der Datei DynamicMenuPackage.cs der DynamicMenuPackage-Klasse die folgenden Attribute hinzu:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackage.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Testen den Befehl Startprojekt festlegen  
 Jetzt können Sie den Code testen.  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
2.  Öffnen Sie in der experimentellen Instanz eine Lösung, die mehr als ein Projekt verfügt über ein.  
  
     Sehen Sie auf das Pfeilsymbol der **Projektmappen-Explorer** Symbolleiste. Wenn Sie ihn zu erweitern, sollte die Menüelemente, die darstellen, die verschiedenen Projekte in der Projektmappe angezeigt werden.  
  
3.  Wenn Sie eines der Projekte aktivieren, wird es das Startprojekt an.  
  
4.  Wenn Sie die Projektmappe schließen oder öffnen Sie eine Projektmappe, die nur ein Projekt verfügt, sollte die Symbolleiste auf das Symbol nicht mehr angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)