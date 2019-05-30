---
title: Dynamisches Hinzufügen von Menüelementen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 619c06d23e3bc1abfce1473627fb483612766728
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353388"
---
# <a name="dynamically-add-menu-items"></a>Hinzufügen von Menüelementen
Sie können Menüelemente zur Laufzeit hinzufügen, durch Angabe der `DynamicItemStart` Befehl Flag für die Definition eines Platzhalter-Schaltfläche in der Visual Studio-Befehlstabelle (*VSCT*) Datei, und dann (im Code) definieren, die Anzahl der anzuzeigenden Menüelemente und behandeln die Befehle an. Wenn das VSPackage geladen wird, wird der Platzhalter durch die dynamische Menüelemente ersetzt.

 Visual Studio verwendet dynamische Listen in die **zuletzt verwendet** (MRU)-Liste, in dem die Namen der Dokumente angezeigt werden, die vor kurzem geöffnet wurden, und die **Windows** Liste, die die Namen von Windows zeigt die gerade geöffnet sind.   Die `DynamicItemStart` -Flag auf eine Befehlsdefinition gibt an, dass der Befehl ein Platzhalter ist, bis das VSPackage geöffnet wird. Wenn das VSPackage geöffnet wird, wird der Platzhalter ersetzt, mit 0 oder mehr Befehle, die zur Laufzeit erstellt und die dynamische Liste hinzugefügt. Sie können möglicherweise nicht die Position im Menü angezeigt, in denen die dynamische Liste angezeigt wird, bis das VSPackage geöffnet wird.  Um die dynamische Liste aufzufüllen, fragt Visual Studio das VSPackage, um einen Befehl mit der ID suchen, deren erste Zeichen, die die ID des Platzhalters identisch sind. Wenn Visual Studio einen entsprechenden Befehl gefunden wird, fügt es der Name des Befehls Liste mit den dynamischen hinzu. Anschließend inkrementiert die ID und sucht nach einer anderen entsprechenden Befehl aus, um die dynamische Liste hinzugefügt werden soll, bis keine weiteren dynamischer Befehle vorhanden sind.

 Diese exemplarische Vorgehensweise veranschaulicht die legen Sie des Startprojekt in Visual Studio-Projektmappe mit einem Befehl auf dem **Projektmappen-Explorer** Symbolleiste. Er verwendet ein Menücontroller, die eine dynamische Dropdownliste mit den Projekten in der aktiven Projektmappe. Um zu verhindern, dass dieser Befehl angezeigt wird, wenn keine Projektmappe geöffnet ist, oder wenn die geöffnete Projektmappe nur ein Projekt enthält, das VSPackage wird nur geladen, wenn eine Lösung mehrere Projekte enthält.

 Weitere Informationen zu *VSCT* finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen Sie eine Erweiterung mit einem Menübefehl

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `DynamicMenuItems`.

2. Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für den benutzerdefinierten Befehl hinzu, und nennen Sie sie **DynamicMenu**. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Einrichten der Elemente in der *VSCT* Datei
 Um für dynamische Menüelemente in einer Symbolleiste ein Menücontroller zu erstellen, geben Sie die folgenden Elemente:

- Zwei Befehl, Gruppen, die Menücontroller enthält und eine andere, die die Elemente in der Dropdownliste enthält

- Ein Menüelement vom Typ `MenuController`

- Zwei Schaltflächen, die als Platzhalter für die Menüelemente und einen weiteren fungiert, die das Symbol und die QuickInfo auf der Symbolleiste bereitstellt.

1. In *DynamicMenuPackage.vsct*, definieren Sie die Befehls-IDs. Wechseln Sie zu dem Abschnitt "Symbols", und Ersetzen Sie die IDSymbol-Elemente in der **GuidDynamicMenuPackageCmdSet** GuidSymbol-Block. Sie müssen IDSymbol-Elemente für die beiden Gruppen, die Menücontroller, die Platzhalter-Befehl und den Ankerbefehl zu definieren.

    ```xml
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

2. Klicken Sie im Abschnitt Gruppen löschen Sie die vorhandenen Gruppen, und fügen Sie die beiden Gruppen, die gerade definierte:

    ```xml
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

     Fügen Sie der MenuController hinzu. Legen Sie die DynamicVisibility-Befehlsflag, da es nicht immer sichtbar ist. Die ButtonText wird nicht angezeigt.

    ```xml
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

3. Fügen Sie zwei Schaltflächen, das als Platzhalter für dynamische Menüelemente und als Anker für die MenuController hinzu.

     Das übergeordnete Element die Schaltfläche "Platzhalter" ist die **MyMenuControllerGroup**. Fügen Sie der DynamicItemStart DynamicVisibility und TextChanges-Befehlsflags hinzu, auf die Schaltfläche "Platzhalter". Die ButtonText wird nicht angezeigt.

     Die Schaltfläche mit den Anker enthält das Symbol und der QuickInfo-Text. Das übergeordnete Element die Schaltfläche "Premium" ist auch die **MyMenuControllerGroup**. Sie fügen die NoShowOnMenuController-Befehlsflag, um sicherzustellen, dass die Schaltfläche mit der tatsächlich in der Dropdownliste des Menüs Controller nicht angezeigt wird und das Flag FixMenuController-Befehl, um es dauerhaften Anker zu erhalten.

    ```xml
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

4. Fügen Sie ein Symbol für das Projekt (in der *Ressourcen* Ordner), und fügen Sie dann den Verweis darauf in der *VSCT* Datei. In dieser exemplarischen Vorgehensweise verwenden wir die Pfeile, das in der Projektvorlage angezeigt wird.

5. Fügen Sie einen Abschnitt VisibilityConstraints außerhalb der Abschnitt "Commands" direkt vor dem Abschnitt "Symbols" hinzu. (Sie können eine Warnung erhalten, wenn Sie es nach Symbole hinzufügen.) In diesem Abschnitt wird sichergestellt, dass es sich bei der Menücontroller im angezeigt wird, wenn nur eine Projektmappe mit mehreren Projekten geladen wird.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementieren der dynamischen Menübefehl
 Sie erstellen eine dynamisches Menü Command-Klasse, die von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In dieser Implementierung gibt den Konstruktor ein Prädikat für den Abgleich von Befehlen verwendet werden. Muss überschrieben werden die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode mit diesem Prädikat Festlegen der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> -Eigenschaft, die identifiziert der Befehl aufgerufen werden.

1. Erstellen Sie eine neue C#-Klassendatei mit dem Namen *DynamicItemMenuCommand.cs*, und fügen Sie eine Klasse, die mit dem Namen **DynamicItemMenuCommand** von erbt <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Fügen Sie die folgenden using-Anweisungen:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Fügen Sie ein privates Feld zum Speichern von des Prädikats übereinstimmen:

    ```csharp
    private Predicate<int> matches;

    ```

4. Fügen Sie einen Konstruktor, der von erbt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Konstruktor und gibt einen Befehlshandler und <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Handler. Fügen Sie ein Prädikat für den Abgleich des Befehls hinzu:

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

5. Überschreiben der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode, dass die It die Übereinstimmungen aufruft und Prädikat und legt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Eigenschaft:

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

## <a name="add-the-command"></a>Fügen Sie den Befehl
 Der Konstruktor des Objekts ist, in dem Sie Menübefehle, einschließlich der dynamischen Menüs und Menüelemente einrichten.

1. In *DynamicMenuPackage.cs*, fügen Sie die GUID für den Befehlssatz, und die Befehls-ID hinzu:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. In der *DynamicMenu.cs* Datei, fügen Sie die folgenden using-Anweisungen:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. In der `DynamicMenu` -Klasse ein privates Feld hinzu **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Fügen Sie ein privates RootItemId-Feld hinzu:

    ```csharp
    private int rootItemId = 0;
    ```

5. Fügen Sie in den Konstruktor des Objekts des Menübefehls ein. Im nächsten Abschnitt definieren wir die Befehlshandler, der `BeforeQueryStatus` -Ereignishandler und dem Prädikat übereinstimmen.

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

## <a name="implement-the-handlers"></a>Implementieren Sie die Handler
 Um dynamische Menüelemente auf ein Menücontroller zu implementieren, müssen Sie den Befehl behandeln, wenn eine dynamische Element geklickt wird. Sie müssen auch die Logik implementieren, die den Zustand des Menüelements festlegt. Die Handler zum Hinzufügen der `DynamicMenu` Klasse.

1. Zum Implementieren der **Startprojekt festlegen** Befehl, fügen Sie der **OnInvokedDynamicItem** -Ereignishandler. Sucht, das Projekt, dessen Name identisch mit dem Text des Befehls, die aufgerufen wurde ist, und wird als Startprojekt durch Festlegen der absoluten Pfads, in, der <xref:EnvDTE.SolutionBuild.StartupProjects%2A> Eigenschaft.

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

2. Hinzufügen der `OnBeforeQueryStatusDynamicItem` -Ereignishandler. Dies ist der Handler wird aufgerufen, bevor eine `QueryStatus` Ereignis. Es bestimmt, ob das Menüelement ein "echten"-Element, also nicht das Platzhalterelement, und gibt an, ob das Element bereits aktiviert ist (d. h., dass das Projekt bereits als Startprojekt festgelegt ist).

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

## <a name="implement-the-command-id-match-predicate"></a>Implementieren Sie die Befehls-ID Übereinstimmung Prädikat

Implementieren Sie nun das Prädikat übereinstimmen. Wir müssen zwei Dinge zu bestimmen: zuerst, ob die Befehls-ID ist ungültig (er ist größer als oder gleich der deklarierten Befehls-ID), und Zweitens, ob sie ein Projekt möglich angegeben (es ist kleiner als die Anzahl der Projekte in der Projektmappe).

    ```csharp
    private bool IsValidDynamicItem(int commandId)
    {
        // The match is valid if the command ID is >= the id of our root dynamic start item
        // and the command ID minus the ID of our root dynamic start item
        // is less than or equal to the number of projects in the solution.
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
    }
    ```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Legen Sie das VSPackage zu laden, nur, wenn eine Lösung mehrere Projekte enthält.
 Da die **Startprojekt festlegen** Befehl ist nicht sinnvoll, wenn die aktive Projektmappe mehrere Projekte verfügt, können Sie Ihr VSPackage zu automatisch nur in diesem Fall laden. Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> zusammen mit den UI-Kontext <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. In der *DynamicMenuPackage.cs* Datei die folgenden Attribute der DynamicMenuPackage-Klasse hinzufügen:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testen Sie die Gruppe Startup-Projekt-Befehl
 Jetzt können Sie Ihren Code testen.

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.

2. Öffnen Sie eine Projektmappe mit mehr als ein Projekt, in der experimentellen Instanz.

     Daraufhin sollte das Symbol "Pfeil" auf die **Projektmappen-Explorer** Symbolleiste. Wenn Sie es erweitern, sollte die Menüelemente, die darstellen, die verschiedenen Projekte in der Projektmappe angezeigt werden.

3. Wenn Sie eines der Projekte aktivieren, wird es das Startprojekt an.

4. Wenn Sie schließen Sie die Projektmappe, oder öffnen Sie eine Projektmappe, die nur ein Projekt verfügt, sollte das Symbol auf der Symbolleiste angezeigt werden.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)