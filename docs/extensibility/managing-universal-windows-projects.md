---
title: Verwalten universeller Windows-Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744940"
---
# <a name="manage-universal-windows-projects"></a>Verwalten von universellen Windows-Projekten

Universelle Windows-Apps sind Apps, die sowohl auf Windows 8.1 als auch auf Windows Phone 8.1 abzielen, sodass Entwickler Code und andere Elemente auf beiden Plattformen verwenden können. Der freigegebene Code und die freigegebenen Ressourcen werden in einem freigegebenen Projekt aufbewahrt, während der plattformspezifische Code und die Ressourcen in separaten Projekten aufbewahrt werden, eines für Windows und das andere für Windows Phone. Weitere Informationen zu universellen Windows-Apps finden Sie unter [Universelle Windows-Apps](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Visual Studio-Erweiterungen, die Projekte verwalten, sollten sich bewusst sein, dass universelle Windows-App-Projekte eine Struktur aufweisen, die sich von Einzelplattform-Apps unterscheidet. In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie im freigegebenen Projekt navigieren und die freigegebenen Elemente verwalten.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Navigieren im freigegebenen Projekt

1. Erstellen Sie ein Projekt mit dem Namen **TestUniversalProject**. (**Datei** > **Neues** > **Projekt** und dann **C-Extensibility** > **Extensibility** > Visual**Studio-Paket**). Fügen Sie eine **benutzerdefinierte** Befehlsprojektelementvorlage hinzu (im **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus , und wechseln Sie dann zu **Erweiterbarkeit**). Benennen Sie die Datei **TestUniversalProject**.

2. Fügen Sie einen Verweis auf *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* und *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (im Abschnitt **Erweiterungen)** hinzu.

3. Öffnen *Sie TestUniversalProject.cs* `using` und fügen Sie die folgenden Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. Fügen `TestUniversalProject` Sie in der Klasse ein privates Feld hinzu, das auf das **Ausgabefenster** zeigt.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Legen Sie den Verweis auf den Ausgabebereich innerhalb des TestUniversalProject-Konstruktors fest:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Entfernen Sie den `ShowMessageBox` vorhandenen Code aus der Methode:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Holen Sie sich das DTE-Objekt, das wir in dieser exemplarischen Vorgehensweise für verschiedene Zwecke verwenden werden. Stellen Sie außerdem sicher, dass eine Lösung geladen wird, wenn auf die Menüschaltfläche geklickt wird.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Suchen Sie das freigegebene Projekt. Das gemeinsam genutzte Projekt ist ein reiner Container. es baut oder produziert keine Ausgaben. Die folgende Methode findet das erste freigegebene <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Projekt in der Projektmappe, indem nach dem Objekt gesucht wird, das über die freigegebene Projektfunktion verfügt.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. Geben `ShowMessageBox` Sie in der Methode die Beschriftung (den Projektnamen, der im **Projektmappen-Explorer**angezeigt wird) des freigegebenen Projekts aus.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Holen Sie sich das aktive Plattformprojekt. Plattformprojekte sind Projekte, die plattformspezifischen Code und Ressourcen enthalten. Die folgende Methode verwendet <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> das neue Feld, um das aktive Plattformprojekt abzubekommen.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. Geben `ShowMessageBox` Sie in der Methode die Beschriftung des aktiven Plattformprojekts aus.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Iterate durch die Plattform-Projekte. Die folgende Methode ruft alle importierenden (Plattform-)Projekte aus dem freigegebenen Projekt ab.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Wenn der Benutzer ein universelles C++-Windows-App-Projekt in der experimentellen Instanz geöffnet hat, löst der obige Code eine Ausnahme aus. Dies ist ein bekanntes Problem. Um die Ausnahme zu `foreach` vermeiden, ersetzen Sie den obigen Block durch Folgendes:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Geben `ShowMessageBox` Sie in der Methode die Beschriftung jedes Plattformprojekts aus. Fügen Sie den folgenden Code nach der Zeile ein, die die Beschriftung des aktiven Plattformprojekts ausgibt. In dieser Liste werden nur die geladenen Plattformprojekte angezeigt.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Ändern Sie das aktive Plattformprojekt. Die folgende Methode legt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>das aktive Projekt mithilfe von fest.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Ändern `ShowMessageBox` Sie in der Methode das aktive Plattformprojekt. Fügen Sie diesen `foreach` Code in den Block ein.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Probieren Sie es jetzt aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie in der experimentellen Instanz ein universelles Hub-App-Projekt von C- und Hub-App (im Dialogfeld **Neues Projekt,** **Visual C-** > **Windows** > **8** > **Universal** > Hub**App**). Nachdem die Projektmappe geladen wurde, wechseln Sie zum Menü **Extras,** und klicken Sie auf **TestUniversalProject aufrufen**, und überprüfen Sie dann den Text im **Ausgabebereich.** Folgendes sollte angezeigt werden:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Verwalten der freigegebenen Elemente im Plattformprojekt

1. Suchen Sie die freigegebenen Elemente im Plattformprojekt. Die Elemente im freigegebenen Projekt werden im Plattformprojekt als freigegebene Elemente angezeigt. Sie können sie nicht im **Projektmappen-Explorer**sehen, aber Sie können die Projekthierarchie durchsuchen, um sie zu finden. Die folgende Methode führt durch die Hierarchie und sammelt alle freigegebenen Elemente. Optional wird die Beschriftung jedes Elements ausgegeben. Die freigegebenen Elemente werden <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>durch die neue Eigenschaft identifiziert.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. Fügen `ShowMessageBox` Sie in der Methode den folgenden Code hinzu, um die Plattformprojekthierarchieelemente zu gehen. Fügen Sie `foreach` es in den Block ein.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lesen Sie die freigegebenen Elemente. Die freigegebenen Elemente werden im Plattformprojekt als ausgeblendete verknüpfte Dateien angezeigt, und Sie können alle Eigenschaften als normale verknüpfte Dateien lesen. Der folgende Code liest den vollständigen Pfad des ersten freigegebenen Elements.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Probieren Sie es jetzt aus. Drücken Sie **F5,** um die experimentelle Instanz zu starten. Erstellen Sie in der experimentellen Instanz ein universelles Hub-App-Projekt von C- und Hub-Instanz (im Dialogfeld **Neues Projekt,** **Visual C-** > **Windows** > **8** > **Universal** > **Hub-App**), wechseln Sie zum Menü **Extras,** und klicken Sie auf **TestUniversalProject aufrufen**, und überprüfen Sie dann den Text im **Ausgabebereich.** Folgendes sollte angezeigt werden:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Erkennen von Änderungen in Plattformprojekten und freigegebenen Projekten

1. Sie können Hierarchie- und Projektereignisse verwenden, um Änderungen in freigegebenen Projekten zu erkennen, genau wie bei Plattformprojekten. Die Projektelemente im freigegebenen Projekt sind jedoch nicht sichtbar, was bedeutet, dass bestimmte Ereignisse nicht ausgelöst werden, wenn freigegebene Projektelemente geändert werden.

    Berücksichtigen Sie die Reihenfolge der Ereignisse, wenn eine Datei in einem Projekt umbenannt wird:

   1. Der Dateiname wird auf dem Datenträger geändert.

   2. Die Projektdatei wird aktualisiert, um den neuen Namen der Datei einzuschließen.

      Hierarchieereignisse (z. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>B. ) verfolgen im Allgemeinen die in der Benutzeroberfläche angezeigten Änderungen, wie im **Projektmappen-Explorer**. Hierarchieereignisse betrachten einen Dateiumbenennungsvorgang als aus einem Dateilöschen und dann aus einer Dateiaddition bestehen. Wenn jedoch unsichtbare Elemente geändert werden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> löst das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Hierarchieereignissystem ein Ereignis aus, aber kein Ereignis. Wenn Sie also eine Datei in einem Plattformprojekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>umbenennen, erhalten Sie beide und , aber <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>wenn Sie eine Datei in einem freigegebenen Projekt umbenennen, erhalten Sie nur .

      Um Änderungen an Projektelementen nachzuverfolgen, können Sie DTE-Projektelementereignisse (die in <xref:EnvDTE.ProjectItemsEventsClass>) behandeln. Wenn Sie jedoch eine große Anzahl von Ereignissen verarbeiten, können <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Sie eine bessere Leistung bei der Verarbeitung der Ereignisse in erhalten. In dieser exemplarischen Vorgehensweise zeigen wir nur die Hierarchieereignisse und die DTE-Ereignisse an. In diesem Verfahren fügen Sie einem freigegebenen Projekt und einem Plattformprojekt einen Ereignislistener hinzu. Wenn Sie dann eine Datei in einem freigegebenen Projekt und eine andere Datei in einem Plattformprojekt umbenennen, werden die Ereignisse angezeigt, die für jeden Umbenennungsvorgang ausgelöst werden.

      In diesem Verfahren fügen Sie einem freigegebenen Projekt und einem Plattformprojekt einen Ereignislistener hinzu. Wenn Sie dann eine Datei in einem freigegebenen Projekt und eine andere Datei in einem Plattformprojekt umbenennen, werden die Ereignisse angezeigt, die für jeden Umbenennungsvorgang ausgelöst werden.

2. Fügen Sie einen Ereignislistener hinzu. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und nennen Sie sie *HierarchyEventListener.cs*.

3. Öffnen Sie die *HierarchyEventListener.cs* Datei, und fügen Sie mithilfe von Direktiven Folgendes hinzu:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Lassen `HierarchyEventListener` Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>die Klasse implementieren:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>die Member von , wie im folgenden Code.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Fügen Sie in derselben Klasse einen weiteren <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>Ereignishandler für das DTE-Ereignis hinzu, der bei jeder Umbenennung eines Projektelements auftritt.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Registrieren Sie sich für die Hierarchieereignisse. Sie müssen sich für jedes Projekt, das Sie verfolgen, separat anmelden. Fügen Sie den `ShowMessageBox`folgenden Code in , einen für das freigegebene Projekt und den anderen für eines der Plattformprojekte hinzu.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Registrieren Sie sich für das <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>DTE-Projektelementereignis . Fügen Sie den folgenden Code hinzu, nachdem Sie den zweiten Listener angeschlossen haben.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Ändern Sie das freigegebene Element. Freigegebene Elemente in einem Plattformprojekt können nicht geändert werden. Stattdessen müssen Sie sie im freigegebenen Projekt ändern, das der tatsächliche Besitzer dieser Elemente ist. Sie können die entsprechende Element-ID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>im freigegebenen Projekt mit abrufen und ihm den vollständigen Pfad des freigegebenen Elements geben. Anschließend können Sie das freigegebene Element ändern. Die Änderung wird an die Plattformprojekte weitergegeben.

    > [!IMPORTANT]
    > Sie sollten herausfinden, ob ein Projektelement ein freigegebenes Element ist, bevor Sie es ändern.

     Die folgende Methode ändert den Namen einer Projektelementdatei.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Rufen Sie diese Methode nach `ShowMessageBox` dem gesamten anderen Code auf, um den Dateinamen des Elements im freigegebenen Projekt zu ändern. Fügen Sie diese nach dem Code ein, der den vollständigen Pfad des Elements im freigegebenen Projekt abruft.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen Sie in der experimentellen Instanz eine universelle Hub-App von C- und Hub, wechseln Sie zum Menü **Extras,** und klicken Sie auf **TestUniversalProject aufrufen**, und überprüfen Sie den Text im allgemeinen Ausgabebereich. Der Name des ersten Elements im freigegebenen Projekt (wir erwarten, dass es sich um die *App.xaml-Datei* handelt) sollte geändert werden, und Sie sollten sehen, dass das <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> Ereignis ausgelöst wurde. Da das Umbenennen von *App.xaml* dazu führt, dass *auch App.xaml.cs* umbenannt werden, sollten in diesem Fall vier Ereignisse angezeigt werden (zwei für jedes Plattformprojekt). (DTE-Ereignisse verfolgen die Elemente im freigegebenen Projekt nicht.) Es sollten <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zwei Ereignisse angezeigt werden (eines <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> für jedes Plattformprojekt), aber keine Ereignisse.

12. Versuchen Sie nun, eine Datei in einem Plattformprojekt umzubenennen, und Sie können den Unterschied in den Ereignissen sehen, die ausgelöst werden. Fügen Sie `ShowMessageBox` nach dem Aufruf `ModifyFileName`von den folgenden Code hinzu.

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen Sie in der experimentellen Instanz ein universelles Projekt von C-C-Wert, wechseln Sie zum Menü **Extras,** und klicken Sie auf **TestUniversalProject aufrufen**, und überprüfen Sie den Text im allgemeinen Ausgabebereich. Nachdem die Datei im Plattformprojekt umbenannt wurde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> sollten sowohl <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> ein Ereignis als auch ein Ereignis angezeigt werden. Da das Ändern der Datei dazu führte, dass keine anderen Dateien geändert wurden und Änderungen an Elementen in einem Plattformprojekt nirgendwo weitergegeben werden, gibt es nur ein einzelnes dieser Ereignisse.
