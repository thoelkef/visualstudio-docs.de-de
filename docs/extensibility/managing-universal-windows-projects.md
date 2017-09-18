---
title: "Verwalten von universellen Windows-Projekten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Verwalten von universellen Windows-Projekten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Universelle Windows\-apps werden apps für Windows 8.1 und Windows Phone 8.1, die es Entwicklern ermöglicht, Code und andere Ressourcen auf beiden Plattformen verwenden. Die freigegebenen Code und Ressourcen werden in einem freigegebenen Projekt enthalten, während die plattformspezifischen Code und Ressourcen in separate Projekte für Windows und die andere für Windows Phone aufbewahrt werden. Weitere Informationen zu universellen Windows\-apps, finden Sie unter [universelle Windows\-Apps](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Visual Studio\-Erweiterungen, die Projekte verwalten sollten bedenken, dass die universelle Windows\-app\-Projekte eine Struktur aufweisen, die von einer Plattform\-apps unterscheidet. In dieser exemplarischen Vorgehensweise erfahren Sie, wie das freigegebene Projekt navigieren und Verwalten der freigegebenen Elemente.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Wechseln Sie das freigegebene Projekt  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt namens **TestUniversalProject**. \(**Datei, neu, Projekt** und **C\#\-Erweiterbarkeit von Visual Studio\-Paket**\). Hinzufügen einer **Befehl benutzerdefinierte** Projektelementvorlage \(klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste des Projektknotens, und wählen Sie **Hinzufügen \/ neues Element**, wechseln Sie zu **Erweiterbarkeit**\). Nennen Sie die Datei **TestUniversalProject**.  
  
2.  Hinzufügen eines Verweises auf Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll und Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll \(in der **Extensions** Abschnitt\).  
  
3.  Öffnen Sie TestUniversalProject.cs, und fügen Sie die folgenden `using` Anweisungen:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  Fügen Sie in der Klasse TestUniversalProject ein privates Feld, das auf den **Ausgabe** Fenster.  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Legen Sie den Verweis in den Ausgabebereich in TestUniversalProject\-Konstruktor:  
  
    ```c#  
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
  
6.  Entfernen Sie den vorhandenen Code aus der `ShowMessageBox` Methode:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Erhalten Sie das DTE\-Objekt, das wir für verschiedene Zwecke in dieser exemplarischen Vorgehensweise verwenden. Stellen Sie außerdem sicher, dass eine Projektmappe geladen wird, wenn auf die Schaltfläche geklickt wird.  
  
    ```c#  
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
  
8.  Suchen Sie das freigegebene Projekt. Das freigegebene Projekt ist eine reine Container. Es werden keine erstellen oder eine Ausgabe produzieren. Die folgende Methode sucht das erste freigegebene Projekt in der Projektmappe für das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> \-Objekt, das das freigegebene Projekt kann.  
  
    ```c#  
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
  
9. In der `ShowMessageBox` \-Methode ausgegeben, die Beschriftung \(den Namen des Projekts, das in wird die **Projektmappen\-Explorer**\) des freigegebenen Projekts.  
  
    ```c#  
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
  
10. Rufen Sie die aktive Plattform\-Projekt. Projekte sind Projekte, die plattformspezifischen Code und Ressourcen enthalten. Im folgenden wird des neuen Felds <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> die aktive Plattform\-Projekt abgerufen.  
  
    ```c#  
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
  
11. In der `ShowMessageBox` \-Methode, die Beschriftung des Projekts aktive Plattform ausgeben.  
  
    ```c#  
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
  
12. Durchlaufen Sie die Projekte aus. Die folgende Methode ruft die importieren \(Platform\)\-Projekte aus dem freigegebenen Projekt.  
  
    ```c#  
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
    >  Wenn der Benutzer ein C\+\+ universelles Windows\-app\-Projekt in der experimentellen Instanz geöffnet, in der oben angegebenen Code eine Ausnahme auslöst. Dies ist ein bekanntes Problem. Um die Ausnahme zu vermeiden, ersetzen die `foreach` Blockieren oben durch den folgenden:  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. In der `ShowMessageBox` \-Methode, die Beschriftung jedes Projekts Plattform ausgeben. Fügen Sie den folgenden Code nach der Zeile, die die Beschriftung des Projekts aktive Plattform ausgibt. Nur die Projekte, die geladen werden, die in dieser Liste angezeigt werden.  
  
    ```c#  
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
  
14. Ändern Sie die aktive Plattform\-Projekt. Die folgende Methode legt das aktive Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. In der `ShowMessageBox` \-Methode, die aktive Plattform\-Projekt ändern. Fügen Sie diesen Code innerhalb der `foreach` Block.  
  
    ```c#  
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
  
16. Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C\#\-universal\-Hub\-app\-Projekt in der experimentellen Instanz \(in der **Neues Projekt** im Dialogfeld **Visual c\# \/ Windows \/ Windows 8 \/ Universal \/ Hub\-App**\). Nachdem die Projektmappe geladen ist, fahren Sie mit der **Tools** Menü **TestUniversalProject Aufrufen**, und überprüfen Sie dann den Text in der **Ausgabe** Bereich. Folgendes sollte angezeigt werden:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### Verwalten von freigegebenen Elemente in der plattformprojekt  
  
1.  Suchen Sie die freigegebene Elemente im plattformprojekt. Die Elemente in das freigegebene Projekt werden in der plattformprojekt als freigegebene Elemente angezeigt. Sie nicht sehen sie in der **Projektmappen\-Explorer**, aber Sie können angeben, wie die Projekthierarchie, um sie zu finden. Die folgende Methode durchläuft die Hierarchie und alle freigegebenen Elemente erfasst. Es gibt optional die Beschriftung jedes Elements. Freigegebene Elemente werden durch die neue Eigenschaft identifiziert <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
    ```c#  
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
  
2.  In der `ShowMessageBox` \-Methode den folgenden Code zum Durchlaufen der Plattform Hierarchie Projektelemente hinzufügen. Fügen Sie es in die `foreach` blockieren.  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Lesen Sie die freigegebene Elemente. Freigegebene Elemente werden als ausgeblendete verknüpften Dateien im plattformprojekt angezeigt, und Sie können alle Eigenschaften als normale verknüpfte Dateien lesen. Der folgende Code liest den vollständigen Pfad des ersten freigegebenen Elements.  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C\#\-universal\-Hub\-app\-Projekt in der experimentellen Instanz \(in der **Neues Projekt** im Dialogfeld **Visual c\# \/ Windows \/ Windows 8 \/ Universal \/ Hub\-App**\) wechseln Sie zu der **Tools** Menü **TestUniversalProject Aufrufen**, und überprüfen Sie dann den Text in der **Ausgabe** Bereich. Folgendes sollte angezeigt werden:  
  
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
  
### Erkennen von Änderungen in die Plattform und freigegebene Projekte  
  
1.  Hierarchie und Projekt\-Ereignisse können Sie um Änderungen in freigegebene Projekte zu erkennen, wie für Ihre Projekte. Allerdings sind die Projektelemente im freigegebenen Projekt nicht sichtbar, was bedeutet, dass bestimmte Ereignisse nicht ausgelöst werden, wenn Gemeinsame Projektelemente geändert werden.  
  
     Betrachten Sie die Abfolge der Ereignisse beim Umbenennen einer Datei in einem Projekt:  
  
    1.  Der Dateiname wird auf der Festplatte geändert.  
  
    2.  Die Projektdatei wird aktualisiert, um den neuen Namen der Datei enthalten.  
  
     Hierarchieereignisse \(z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>\) im Allgemeinen verfolgen die Änderungen in der Benutzeroberfläche angezeigt wird, wie in der **Projektmappen\-Explorer**. Hierarchieereignisse sollten Sie eine Datei Umbenennungsvorgang aus einer Datei löschen und dann auf Hinzufügen einer Datei bestehen. Allerdings Wenn unsichtbare Elemente geändert werden, das System zur Hierarchie löst ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis, nicht jedoch ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis. Daher erhalten, wenn Sie eine Datei in einem plattformprojekt umbenennen, Sie beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, aber wenn Sie eine Datei in einem freigegebenen Projekt umbenennen, erhalten Sie nur <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Sie können zum Nachverfolgen von Änderungen in Projektelementen DTE Projekt Elementereignisse behandeln \(diejenigen finden Sie in <xref:EnvDTE.ProjectItemsEventsClass>\). Wenn Sie große Mengen von Ereignissen verarbeiten, Sie erhalten jedoch eine bessere Leistung, die von den Ereignissen in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. In dieser exemplarischen Vorgehensweise wird nur die Hierarchieereignisse und die DTE\-Ereignisse anzeigen. In diesem Verfahren fügen Sie einen Ereignis\-Listener auf einem freigegebenen Projekt und Plattform. Klicken Sie dann beim Umbenennen einer Datei in einem freigegebenen Projekt und eine andere Datei in einem plattformprojekt sehen die Ereignisse Sie, die für jede Umbenennungsvorgang ausgelöst werden.  
  
     In diesem Verfahren fügen Sie einen Ereignis\-Listener auf einem freigegebenen Projekt und Plattform. Klicken Sie dann beim Umbenennen einer Datei in einem freigegebenen Projekt und eine andere Datei in einem plattformprojekt sehen die Ereignisse Sie, die für jede Umbenennungsvorgang ausgelöst werden.  
  
2.  Fügen Sie einen Ereignis\-Listener hinzu. Fügen Sie dem Projekt eine neue Klassendatei, und nennen Sie es HierarchyEventListener.cs.  
  
3.  Öffnen Sie die Datei HierarchyEventListener.cs, und fügen Sie die folgende using\-Anweisungen:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  Haben die `HierarchyEventListener` Klasse implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Implementieren Sie die Mitglieder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, wie im folgenden Code.  
  
    ```c#  
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
  
6.  Fügen Sie einen anderen Ereignishandler für das DTE\-Ereignis in der gleichen Klasse <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, der auftritt, ein Projektelement umbenannt wird.  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Registrieren Sie sich für die Hierarchieereignisse an. Sie müssen separat für jedes Projekt registrieren, den Sie nachverfolgen. Fügen Sie den folgenden Code in `ShowMessageBox`, eine für das freigegebene Projekt und die andere für eines der Projekte.  
  
    ```c#  
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
  
8.  Melden Sie sich für das DTE\-Projekt das Elementereignis <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Fügen Sie den folgenden Code aus, nachdem Sie den zweiten Listener einbinden.  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Ändern Sie das freigegebene Element an. Freigegebene Elemente in einem plattformprojekt kann nicht geändert werden; Stattdessen müssen Sie diese in das freigegebene Projekt ändern, die der aktuelle Besitzer dieser Elemente ist. Sie erhalten die entsprechenden Element\-ID in das freigegebene Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, vollständigen Pfad für das freigegebene Element zuweisen. Dann können Sie das freigegebene Element ändern. Die Änderung wird an die Plattformprojekte weitergegeben.  
  
    > [!IMPORTANT]
    >  Sie sollten herausfinden, ob ein Projektelement einer freigegebenen Elements ist, vor dem ändern.  
  
     Die folgende Methode ändert den Namen einer Projektdatei für das Element.  
  
    ```c#  
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
  
10. Diese Methode aufrufen, nachdem alle anderen Code in `ShowMessageBox` So ändern Sie den Dateinamen des Elements in das freigegebene Projekt. Legen Sie dies nach dem Code, der den vollständigen Pfad des Elements im freigegebenen Projekt abruft.  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen eine C\#\-universal\-Hub\-app in der experimentellen Instanz, fahren Sie mit der **Tools** Menü **TestUniversalProject Aufrufen**, und überprüfen Sie den Text im Ausgabebereich Allgemein. Der Name des ersten Elements im freigegebenen Projekt \(wir erwarten, dass die Datei App.xaml werden\) sollte geändert werden, und sollte angezeigt werden, die <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> \-Ereignis ausgelöst hat. In diesem Fall da umbenennen App.xaml App.xaml.cs auch umbenannt werden, führt, sollten Sie vier Ereignisse \(zwei für jede plattformprojekt\) finden Sie unter. \(DTE\-Ereignisse nicht die Elemente in das freigegebene Projekt nachverfolgen.\) Sie sehen zwei <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignisse \(eine für jede Plattformprojekte\), jedoch keine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignisse.  
  
12. Versuchen Sie nun das Umbenennen einer Datei in einem plattformprojekt, und sehen Sie den Unterschied in der Ereignisse, die ausgelöst wird, erhalten. Fügen Sie den folgenden Code in `ShowMessageBox` nach dem Aufruf von `ModifyFileName`.  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Erstellen Sie das Projekt, und führen Sie es aus. Ein Universal C\#\-Projekt in der experimentellen Instanz erstellen, navigieren Sie zu der **Tools** Menü **aufrufen TestUniversalProject**, und überprüfen Sie den Text im Ausgabebereich Allgemein. Nach dem Umbenennen der Datei im plattformprojekt sollte sowohl eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis und ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis. Da Änderungen verursacht die Datei keine anderen Dateien geändert werden, und da Änderungen an Elementen in einem plattformprojekt nicht überall weitergegeben werden, wird nur jeweils eines dieser Ereignisse.