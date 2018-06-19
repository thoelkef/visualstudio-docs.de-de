---
title: Verwalten von universelle Windows-Projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d251818d9fba0c025b94fa17611a725daad3cec8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147593"
---
# <a name="managing-universal-windows-projects"></a>Verwalten von universellen Windows-Projekten
Universelle Windows-apps sind apps, die Windows 8.1 und Windows Phone 8.1, die es Entwicklern ermöglicht, mithilfe von Code und anderen Ressourcen auf beiden Plattformen ausgerichtet, sind. Die freigegebenen Code und die Ressourcen werden in einem freigegebenen Projekt enthalten, während die plattformspezifischen Code und die Ressourcen in separaten Projekten, eine für Windows und die andere für Windows Phone aufbewahrt werden. Weitere Informationen zu universellen Windows-apps, finden Sie unter [universelle Windows-Apps](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Visual Studio-Erweiterungen, die Projekte verwalten sollten bedenken, dass Projekte der universellen Windows-app eine Struktur aufweisen, die von einer Plattform-apps unterscheidet. In dieser exemplarischen Vorgehensweise wird gezeigt, wie das freigegebene Projekt navigieren und freigegebene Elemente zu verwalten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Wechseln Sie das freigegebene Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt namens **TestUniversalProject**. (**Datei "," Neu "," Projekt** und dann **C#-Erweiterbarkeit von Visual Studio-Paket**). Hinzufügen einer **benutzerdefinierte Befehl** Projektelementvorlage (klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projektknotens, und wählen **hinzufügen / neues Element**, dann wechseln Sie zu **Erweiterbarkeit**). Nennen Sie die Datei **TestUniversalProject**.  
  
2.  Hinzufügen eines Verweises auf Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll und Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (in der **Erweiterungen** Abschnitt).  
  
3.  Öffnen Sie TestUniversalProject.cs, und fügen Sie die folgenden `using` Anweisungen:  
  
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
  
4.  Fügen Sie in der Klasse TestUniversalProject ein privates Feld zeigen die **Ausgabe** Fenster.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Legen Sie den Verweis in den Ausgabebereich innerhalb TestUniversalProject Konstruktors:  
  
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
  
6.  Entfernen Sie den vorhandenen Code aus der `ShowMessageBox` Methode:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Abrufen der DTE-Objekt, das für verschiedene Zwecke in dieser exemplarischen Vorgehensweise verwendet wird. Stellen Sie außerdem sicher, dass eine Projektmappe geladen wird, wenn auf die Schaltfläche geklickt wird.  
  
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
  
8.  Suchen Sie das freigegebene Projekt. Das freigegebene Projekt ist ein reines Container; Es werden keine erstellen oder Ausgaben erzeugen. Die folgende Methode sucht das erste freigegebene Projekt in der Lösung für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Objekt, das das freigegebene Projekt Fähigkeit verfügt.  
  
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
  
9. In der `ShowMessageBox` Methode ausgegeben, die Beschriftung (den Namen des Projekts, die in angezeigt wird der **Projektmappen-Explorer**) des freigegebenen Projekts.  
  
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
  
10. Rufen Sie die aktive Plattform-Projekt. Platform-Projekte sind Projekte, die plattformspezifischen Code und Ressourcen enthalten. Die folgende Methode verwendet das neue Feld <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> um das Projekt für die aktive Plattform abzurufen.  
  
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
  
11. In der `ShowMessageBox` -Methode ausgegeben, die Beschriftung des Projekts aktive Plattform.  
  
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
  
12. Durchlaufen Sie die Plattformprojekte. Die folgende Methode ruft die importierende (Plattform) Projekte aus dem freigegebenen Projekt ab.  
  
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
    >  Wenn der Benutzer ein C++ universelle Windows-app-Projekt in der experimentellen Instanz geöffnet wurde, löst der obige Code eine Ausnahme aus. Dies ist ein bekanntes Problem. Um die Ausnahme zu vermeiden, ersetzen die `foreach` blockieren oben durch Folgendes:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. In der `ShowMessageBox` -Methode ausgegeben, die Beschriftung jedes Projekts Plattform. Fügen Sie den folgenden Code nach der Zeile, die die Beschriftung des Projekts aktive Plattform ausgibt. Nur die Plattformprojekte, die geladen werden, die in dieser Liste angezeigt werden.  
  
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
  
14. Ändern Sie die aktive Plattform-Projekt. Die folgende Methode legt fest, das aktive Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. In der `ShowMessageBox` -Methode, die aktive Plattform-Projekt zu ändern. Fügen Sie diesen Code in die `foreach` Block.  
  
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
  
16. Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C#-Hub universal app-Projekt in der experimentellen Instanz (in der **neues Projekt** Dialogfeld **Visual c# / Windows / Windows 8 / Universal / Hub-App**). Nachdem die Projektmappe geladen wurde, wechseln Sie zu der **Tools** Menü, und klicken Sie auf **TestUniversalProject Aufrufen**, und überprüfen Sie den Text in der **Ausgabe** Bereich. Sie sollte etwa wie folgt angezeigt:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Verwalten Sie freigegebene Elemente in der plattformprojekt  
  
1.  Suchen Sie die freigegebene Elemente im plattformprojekt. Die Elemente im freigegebenen Projekt werden im plattformprojekt als freigegebene Elemente angezeigt. Nicht angezeigt werden, in der **Projektmappen-Explorer**, aber Sie können angeben, führt die Projekthierarchie, um sie zu finden. Die folgende Methode führt die Hierarchie und alle freigegebenen Elemente erfasst. Es gibt optional die Beschriftung jedes Elements. Die freigegebene Elemente werden durch die neue Eigenschaft identifiziert <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
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
  
2.  In der `ShowMessageBox` -Methode, fügen Sie folgenden Code aus, um die Plattform-Projektelemente Hierarchie zu durchlaufen. Fügen Sie ihn in die `foreach` Block.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Lesen Sie die freigegebene Elemente. Freigegebene Elemente werden in der plattformprojekt als ausgeblendete verknüpfte Dateien angezeigt, und Sie können alle Eigenschaften als gewöhnliche verknüpfte Dateien lesen. Der folgende Code liest den vollständigen Pfad des ersten freigegebenen Elements.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C#-Hub universal app-Projekt in der experimentellen Instanz (in der **neues Projekt** Dialogfeld **Visual c# / Windows / Windows 8 / Universal / Hub-App**) wechseln Sie zu der **Tools** Menü, und klicken Sie auf **aufrufen TestUniversalProject**, und überprüfen Sie den Text in der **Ausgabe** Bereich. Sie sollte etwa wie folgt angezeigt:  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Erkennen von Änderungen in Plattformprojekte und gemeinsam genutzte Projekte  
  
1.  Hierarchie und Projekt Ereignisse können zum Erkennen von Änderungen in gemeinsam genutzte Projekte, ebenso wie Sie für die plattformprojekten. Allerdings sind die Projektelemente im freigegebenen Projekt nicht sichtbar, was bedeutet, dass bestimmte Ereignisse nicht ausgelöst werden, wenn Elemente des freigegebenen Projekts geändert werden.  
  
     Betrachten Sie die Abfolge von Ereignissen beim Umbenennen einer Datei in einem Projekt ein:  
  
    1.  Der Dateiname ist auf dem Datenträger geändert.  
  
    2.  Die Projektdatei wird aktualisiert, um den neuen Namen der Datei enthalten.  
  
     Hierarchieereignisse (z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) im Allgemeinen Nachverfolgen der Änderungen in der Benutzeroberfläche angezeigt wird, wie in der **Projektmappen-Explorer**. Hierarchieereignisse sollten Sie eine Datei Umbenennungsvorgang aus einer Datei löschen und dann eine Datei hinzufügen bestehen. Allerdings beim unsichtbare Elemente geändert werden, die Hierarchie-Ereignissystem löst ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis jedoch kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis. Aus diesem Grund, wenn Sie eine Datei in einem plattformprojekt umbenennen, erhalten Sie beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, aber wenn Sie eine Datei in einem freigegebenen Projekt umbenennen, erhalten Sie nur <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Sie können zum Nachverfolgen von Änderungen in Projektelementen DTE-Element Projektereignisse behandeln (diejenigen gefunden <xref:EnvDTE.ProjectItemsEventsClass>). Jedoch, wenn Sie zahlreiche Ereignisse behandeln, erhalten Sie eine bessere Leistung Behandeln der Ereignisse in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. In dieser exemplarischen Vorgehensweise werden nur die Hierarchieereignisse und die DTE-Ereignisse anzeigen. In diesem Verfahren fügen Sie einen Ereignislistener zu einem freigegebenen Projekt und eine plattformprojekt hinzu. Klicken Sie dann, wenn Sie eine Datei in einem freigegebenen Projekt und eine andere Datei in einem plattformprojekt umbenennen, können die Ereignisse angezeigt werden, die für die einzelnen Rename-Vorgänge ausgelöst werden.  
  
     In diesem Verfahren fügen Sie einen Ereignislistener zu einem freigegebenen Projekt und eine plattformprojekt hinzu. Klicken Sie dann, wenn Sie eine Datei in einem freigegebenen Projekt und eine andere Datei in einem plattformprojekt umbenennen, können die Ereignisse angezeigt werden, die für die einzelnen Rename-Vorgänge ausgelöst werden.  
  
2.  Fügen Sie einen Ereignislistener hinzu. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und rufen Sie es HierarchyEventListener.cs.  
  
3.  Öffnen Sie die Datei HierarchyEventListener.cs, und fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  Haben die `HierarchyEventListener` Klasse implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Implementieren Sie die Mitglieder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, wie im folgenden Code.  
  
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
  
6.  Fügen Sie einen anderen Ereignishandler für das DTE-Ereignis in der gleichen Klasse <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, Dies tritt ein, ein Projektelement umbenannt wird.  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Registrieren Sie sich für die Hierarchieereignisse an. Sie müssen separat für jedes Projekt registrieren, den Sie nachverfolgen. Fügen Sie den folgenden Code in `ShowMessageBox`, eine für das freigegebene Projekt, und die andere für eine von der plattformprojekten.  
  
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
  
8.  Registrieren Sie sich für das DTE-Projekt Elementereignis <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Fügen Sie den folgenden Code aus, nachdem Sie den zweiten Listener verknüpft.  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Ändern Sie das freigegebene Element an. Sie können freigegebene Elemente in einem plattformprojekt nicht ändern; Stattdessen müssen Sie sie im freigegebenen Projekt ändern, die der aktuelle Besitzer dieser Elemente ist. Sie können die entsprechenden Element-ID abrufen, mit dem gemeinsamen Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, und geben sie Ihnen vollständigen Pfad für das freigegebene Element. Dann können Sie das freigegebene Element ändern. Die Änderung wird an die Plattformprojekte weitergegeben.  
  
    > [!IMPORTANT]
    >  Sie sollten ermitteln, und zwar unabhängig davon, ob ein Projektelement einem freigegebenen Element ist, bevor Sie Sie ändern.  
  
     Die folgende Methode wird der Name einer Projektdatei für das Element geändert.  
  
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
  
10. Diese Methode aufrufen, nachdem alle den anderen Code in `ShowMessageBox` nennen Sie das Element im freigegebenen Projekt so ändern Sie die Datei. Fügen Sie dies nach dem Code, der den vollständigen Pfad des Elements im freigegebenen Projekt abruft.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Erstellen Sie das Projekt, und führen Sie es aus. Erstellen Sie eine C#-universal-Hub-app in der experimentellen Instanz, navigieren Sie zu der **Tools** Menü, und klicken Sie auf **TestUniversalProject Aufrufen**, und überprüfen Sie den Text im Ausgabebereich Allgemein. Der Name des ersten Elements im freigegebenen Projekt (wir erwarten, dass er zu der Datei "App.xaml") sollte geändert werden und sollte angezeigt werden, die <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> Ereignis ausgelöst wurde. Da umbenennen App.xaml bewirkt, dass die App.xaml.cs ebenfalls umbenannt werden soll, sollten Sie in diesem Fall vier Ereignisse (zwei für jedes plattformprojekt) angezeigt. (DTE-Ereignisse nicht die Elemente im freigegebenen Projekt nachverfolgen.) Sehen Sie zwei <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignissen (eine für alle Plattformprojekte), aber keine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignisse.  
  
12. Umbenennen einer Datei in einem plattformprojekt wird nun versucht, und sehen Sie den Unterschied in der Ereignisse, die ausgelöst wird, erhalten. Fügen Sie den folgenden Code in `ShowMessageBox` nach dem Aufruf von `ModifyFileName`.  
  
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
  
13. Erstellen Sie das Projekt, und führen Sie es aus. Eine universelle C#-Projekt in der experimentellen Instanz zu erstellen, wechseln Sie zu der **Tools** Menü, und klicken Sie auf **TestUniversalProject Aufrufen**, und überprüfen Sie den Text in dem allgemeine Ausgabebereich angezeigt. Nachdem die Datei im plattformprojekt umbenannt wurde, sehen Sie sowohl eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis und eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis. Da Änderungen verursacht die Datei keine anderen Dateien geändert werden, und da Änderungen an Elementen in einem plattformprojekt an einer beliebigen Stelle nicht weitergegeben werden, ist nur ein jedes dieser Ereignisse.