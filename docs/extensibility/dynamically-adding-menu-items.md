---
title: Dynamisches Hinzufügen von Menüelementen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712067"
---
# <a name="dynamically-add-menu-items"></a>Dynamisches Hinzufügen von Menüelementen
Sie können Menüelemente zur Laufzeit hinzufügen, indem Sie das `DynamicItemStart` Befehlsflag für eine Platzhalterschaltflächendefinition in der Visual Studio-Befehlstabelle (*.vsct*) -Datei angeben und dann (im Code) die Anzahl der anzuzeigenden Menüelemente definieren und die Befehle behandeln. Wenn das VSPackage geladen wird, wird der Platzhalter durch die dynamischen Menüelemente ersetzt.

 Visual Studio verwendet dynamische Listen in der Liste der **zuletzt verwendeten** Dokumente (MRU), in der die Namen der kürzlich geöffneten Dokumente angezeigt werden, und in der **Windows-Liste,** in der die Namen der derzeit geöffneten Fenster angezeigt werden.   Das `DynamicItemStart` Flag in einer Befehlsdefinition gibt an, dass der Befehl ein Platzhalter ist, bis das VSPackage geöffnet wird. Wenn das VSPackage geöffnet wird, wird der Platzhalter durch 0 oder mehr Befehle ersetzt, die zur Laufzeit erstellt und der dynamischen Liste hinzugefügt werden. Möglicherweise können Sie die Position im Menü, an der die dynamische Liste angezeigt wird, erst sehen, wenn das VSPackage geöffnet wird.  Um die dynamische Liste aufzufüllen, fordert Visual Studio das VSPackage auf, nach einem Befehl mit einer ID zu suchen, deren erste Zeichen mit der ID des Platzhalters übereinstimmen. Wenn Visual Studio einen übereinstimmenden Befehl findet, wird der dynamischen Liste der Name des Befehls hinzugefügt. Anschließend wird die ID erhöht und nach einem weiteren übereinstimmenden Befehl gesucht, der der dynamischen Liste hinzugefügt werden soll, bis keine dynamischen Befehle mehr vorhanden sind.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie das Startprojekt in einer Visual Studio-Lösung mit einem Befehl auf der **Projektmappensymbolleiste** festlegen. Es verwendet einen Menücontroller mit einer dynamischen Dropdownliste der Projekte in der aktiven Projektmappe. Damit dieser Befehl nicht angezeigt wird, wenn keine Projektmappe geöffnet ist oder wenn die offene Projektmappe nur über ein Projekt verfügt, wird das VSPackage nur geladen, wenn eine Projektmappe mehrere Projekte enthält.

 Weitere Informationen *zu .vsct-Dateien* finden Sie unter [Visual Studio-Befehlstabelle (.vsct)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl

1. Erstellen Sie ein `DynamicMenuItems`VSIX-Projekt mit dem Namen .

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehlselementvorlage hinzu, und nennen Sie sie **DynamicMenu**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Einrichten der Elemente in der *.vsct-Datei*
 Um einen Menücontroller mit dynamischen Menüelementen auf einer Symbolleiste zu erstellen, geben Sie die folgenden Elemente an:

- Zwei Befehlsgruppen, eine mit dem Menücontroller und eine andere, die die Menüelemente in der Dropdownliste enthält

- Ein Menüelement des Typs`MenuController`

- Zwei Schaltflächen, eine, die als Platzhalter für die Menüelemente fungiert, und eine andere, die das Symbol und die QuickInfo auf der Symbolleiste bereitstellt.

1. Definieren Sie in *DynamicMenuPackage.vsct*die Befehls-IDs. Wechseln Sie zum Abschnitt Symbole, und ersetzen Sie die IDSymbol-Elemente im **GuidDynamicMenuPackageCmdSet** GuidSymbol-Block. Sie müssen IDSymbol-Elemente für die beiden Gruppen definieren, den Menücontroller, den Platzhalterbefehl und den Befehl anchor.

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

2. Löschen Sie im Abschnitt Gruppen die vorhandenen Gruppen, und fügen Sie die beiden Gruppen hinzu, die Sie gerade definiert haben:

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

     Fügen Sie den MenuController hinzu. Legen Sie das DynamicVisibility-Befehlsflag fest, da es nicht immer sichtbar ist. Der ButtonText wird nicht angezeigt.

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

3. Fügen Sie zwei Schaltflächen hinzu, eine als Platzhalter für die dynamischen Menüelemente und eine als Anker für den MenuController.

     Das übergeordnete Element der Platzhalterschaltfläche ist die **MyMenuControllerGroup**. Fügen Sie der Platzhalterschaltfläche die Befehlsflags DynamicItemStart, DynamicVisibility und TextChanges hinzu. Der ButtonText wird nicht angezeigt.

     Die Ankerschaltfläche enthält das Symbol und den QuickInfo-Text. Das übergeordnete Element der Ankerschaltfläche ist auch die **MyMenuControllerGroup**. Sie fügen das NoShowOnMenuController-Befehlsflag hinzu, um sicherzustellen, dass die Schaltfläche nicht tatsächlich in der Dropdown-Liste des Menücontrollers angezeigt wird, und das FixMenuController-Befehlsflag, um sie zum permanenten Anker zu machen.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
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

4. Fügen Sie dem Projekt (im Ordner *Ressourcen)* ein Symbol hinzu, und fügen Sie dann den Verweis in die *.vsct-Datei* hinzu. In dieser exemplarischen Vorgehensweise verwenden wir das Pfeil-Symbol, das in der Projektvorlage enthalten ist.

5. Fügen Sie einen Abschnitt VisibilityConstraints außerhalb des Abschnitts Befehle kurz vor dem Abschnitt Symbole hinzu. (Sie erhalten möglicherweise eine Warnung, wenn Sie sie nach Symbolen hinzufügen.) In diesem Abschnitt wird sichergestellt, dass der Menücontroller nur angezeigt wird, wenn eine Projektmappe mit mehreren Projekten geladen wird.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementieren des dynamischen Menübefehls
 Sie erstellen eine dynamische Menübefehlsklasse, die von erbt. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> In dieser Implementierung gibt der Konstruktor ein Prädikat an, das für übereinstimmende Befehle verwendet werden soll. Sie müssen die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Methode überschreiben, um dieses <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Prädikat zum Festlegen der Eigenschaft zu verwenden, die den befehl identifiziert, der aufgerufen werden soll.

1. Erstellen Sie eine neue C-Klassendatei mit dem Namen *DynamicItemMenuCommand.cs*, und <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>fügen Sie eine Klasse mit dem Namen **DynamicItemMenuCommand** hinzu, die von :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Fügen Sie die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Fügen Sie ein privates Feld hinzu, um das Übereinstimmungsprädikat zu speichern:

    ```csharp
    private Predicate<int> matches;

    ```

4. Fügen Sie einen Konstruktor hinzu, der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> vom Konstruktor erbt und einen Befehlshandler und einen <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Handler angibt. Fügen Sie ein Prädikat zum Abgleichen des Befehls hinzu:

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

5. Überschreiben <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> Sie die Methode, sodass das Übereinstimmungsprädikat aufruft und die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Eigenschaft festgelegt wird:

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

## <a name="add-the-command"></a>Hinzufügen des Befehls
 Im DynamicMenu-Konstruktor richten Sie Menübefehle ein, einschließlich dynamischer Menüs und Menüelemente.

1. Fügen Sie in *DynamicMenuPackage.cs*die GUID des Befehlssatzes und die Befehls-ID hinzu:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Fügen Sie in der *Datei DynamicMenu.cs* die folgenden Anweisungen hinzu:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Fügen `DynamicMenu` Sie in der Klasse ein privates Feld **dte2**hinzu.

    ```csharp
    private DTE2 dte2;
    ```

4. Hinzufügen eines privaten rootItemId-Felds:

    ```csharp
    private int rootItemId = 0;
    ```

5. Fügen Sie im DynamicMenu-Konstruktor den Menübefehl hinzu. Im nächsten Abschnitt definieren wir den Befehlshandler, den `BeforeQueryStatus` Ereignishandler und das Übereinstimmungsprädikat.

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

## <a name="implement-the-handlers"></a>Implementieren der Handler
 Um dynamische Menüelemente auf einem Menücontroller zu implementieren, müssen Sie den Befehl behandeln, wenn auf ein dynamisches Element geklickt wird. Sie müssen auch die Logik implementieren, die den Status des Menüelements festlegt. Fügen Sie die `DynamicMenu` Handler der Klasse hinzu.

1. Um den Befehl **Startprojekt festlegen** zu implementieren, fügen Sie den **OnInvokedDynamicItem-Ereignishandler** hinzu. Es sucht nach dem Projekt, dessen Name mit dem Text des aufgerufenen Befehls identisch ist, und <xref:EnvDTE.SolutionBuild.StartupProjects%2A> legt es als Startprojekt fest, indem der absolute Pfad in der Eigenschaft festgelegt wird.

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

2. Fügen `OnBeforeQueryStatusDynamicItem` Sie den Ereignishandler hinzu. Dies ist der `QueryStatus` Handler, der vor einem Ereignis aufgerufen wird. Es bestimmt, ob es sich bei dem Menüelement um ein "reales" Element handelt, d. h. nicht um das Platzhalterelement, und ob das Element bereits überprüft ist (d. h., das Projekt ist bereits als Startprojekt festgelegt).

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

## <a name="implement-the-command-id-match-predicate"></a>Implementieren des Befehls-ID-Übereinstimmungsprädikats

Implementieren Sie nun das Matchprädikat. Wir müssen zwei Dinge bestimmen: erstens, ob die Befehls-ID gültig ist (sie ist größer oder gleich der deklarierten Befehls-ID), und zweitens, ob sie ein mögliches Projekt angibt (sie ist kleiner als die Anzahl der Projekte in der Projektmappe).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Festlegen des VSPackage zum Laden nur, wenn eine Projektmappe mehrere Projekte hat
 Da der Befehl **Startprojekt festlegen** nur sinnvoll ist, wenn die aktive Projektmappe über mehr als ein Projekt verfügt, können Sie Ihr VSPackage nur in diesem Fall auf automatisches Laden festlegen. Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> verwenden zusammen mit <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>dem UI-Kontext . Fügen *Sie* im DynamicMenuPackage.cs Datei der DynamicMenuPackage-Klasse die folgenden Attribute hinzu:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testen des Befehls "Set-Startprojekt"
 Jetzt können Sie Ihren Code testen.

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

2. Öffnen Sie in der experimentellen Instanz eine Projektmappe, die über mehr als ein Projekt verfügt.

     Das Pfeilsymbol sollte auf der Symbolleiste des **Projektmappen-Explorers** angezeigt werden. Wenn Sie sie erweitern, sollten Menüelemente angezeigt werden, die die verschiedenen Projekte in der Projektmappe darstellen.

3. Wenn Sie eines der Projekte überprüfen, wird es zum Startprojekt.

4. Wenn Sie die Projektmappe schließen oder eine Projektmappe öffnen, die nur über ein Projekt verfügt, sollte das Symbol der Symbolleiste ausgeblendet werden.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
