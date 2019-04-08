---
title: Verwalten von universellen Windows-Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e905ca4a34399c1ec590d5ff16441bd5afe9ce23
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957419"
---
# <a name="managing-universal-windows-projects"></a>Verwalten von universellen Windows-Projekten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Universelle Windows-apps sind apps sowohl Windows 8.1 und Windows Phone 8.1, und ermöglichen es Entwicklern, Code und anderen Ressourcen auf beiden Plattformen verwenden. Freigegebenen Code und Ressourcen werden in einem freigegebenen Projekt enthalten, während die plattformspezifischen Code und Ressourcen in separate Projekte für Windows und die andere für Windows Phone gespeichert werden. Weitere Informationen zu universellen Windows-apps finden Sie unter [universelle Windows-Apps](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Visual Studio-Erweiterungen, die Projekte zu verwalten sollten bedenken, dass universelle Windows-app-Projekten eine Struktur verfügen, die von apps für mehrere Plattformen abweicht. In dieser exemplarischen Vorgehensweise veranschaulicht das freigegebene Projekt navigieren und Verwalten der freigegebenen Elemente.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Wechseln Sie das freigegebene Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt mit dem Namen **TestUniversalProject**. (**Datei, neu, Projekt** und dann **C#-Erweiterbarkeit von Visual Studio-Paket**). Hinzufügen einer **benutzerdefinierten Befehls** Projektelementvorlage (klicken Sie auf im Projektmappen-Explorer mit der rechten Maustaste des Projektknotens, und wählen **hinzufügen / neues Element**, navigieren Sie zu **Erweiterbarkeit**). Nennen Sie die Datei **TestUniversalProject**.  
  
2.  Hinzufügen eines Verweises auf Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll und Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (in der **Erweiterungen** Abschnitt).  
  
3.  TestUniversalProject.cs öffnen, und fügen Sie die folgenden `using` Anweisungen:  
  
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
  
4.  Fügen Sie in der Klasse TestUniversalProject ein privates Feld, das auf die **Ausgabe** Fenster.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Legen Sie den Verweis auf den Ausgabebereich in TestUniversalProject-Konstruktor:  
  
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
  
7.  Erhalten Sie das DTE-Objekt, das wir für verschiedene Zwecke in dieser exemplarischen Vorgehensweise verwenden können. Stellen Sie außerdem sicher, dass eine Projektmappe geladen wird, wenn auf die Schaltfläche geklickt wird.  
  
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
  
8.  Suchen Sie das freigegebene Projekt. Das freigegebene Projekt ist eine reine Container. nicht erstellen oder Ausgaben generieren. Die folgende Methode sucht das erste freigegebene Projekt in der Projektmappe durch Suchen nach den <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, das freigegebene Projekt kann.  
  
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
  
9. In der `ShowMessageBox` -Methode, Ausgabe, die Beschriftung (den Namen des Projekts, das angezeigt wird der **Projektmappen-Explorer**) des freigegebenen Projekts.  
  
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
  
10. Rufen Sie das aktive Plattform-Projekt. Plattform-Projekten werden die Projekte, die plattformspezifischen Code und Ressourcen enthalten. Die folgende Methode verwendet das neue Feld <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> um das Projekt für die aktive Plattform zu erhalten.  
  
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
  
11. In der `ShowMessageBox` -Methode, Ausgabe, die Beschriftung des Projekts aktive Plattform.  
  
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
  
12. Durchlaufen Sie die Plattformprojekte aus. Die folgende Methode ruft die beim Importieren (Plattform)-Projekte aus dem freigegebenen Projekt ab.  
  
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
    >  Wenn der Benutzer in der experimentellen Instanz ein C++ universal Windows app-Projekt geöffnet, in der obige Code eine Ausnahme ausgelöst. Dies ist ein bekanntes Problem. Um die Ausnahme zu vermeiden, ersetzen die `foreach` oben durch den folgenden block:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. In der `ShowMessageBox` -Methode, Ausgabe, die Beschriftung der Projekte. Fügen Sie den folgenden Code nach der Zeile, die die Beschriftung des Projekts aktive Plattform ausgibt. Nur die Plattformprojekte, die geladen werden, die in dieser Liste angezeigt werden.  
  
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
  
15. In der `ShowMessageBox` -Methode, ändern Sie die aktive Plattform-Projekt. Fügen Sie diesen Code innerhalb der `foreach` Block.  
  
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
  
16. Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C#-universal-Hub-app-Projekt in der experimentellen Instanz (in der **neues Projekt** Dialogfeld **Visual C# / Windows / Windows 8 / Universal / Hub-App**). Nachdem die Projektmappe geladen wurde, wechseln Sie zu der **Tools** Menü, und klicken Sie auf **TestUniversalProject Aufrufen**, und überprüfen Sie dann den Text in die **Ausgabe** Bereich. Es sollte nun etwa Folgendes angezeigt werden:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Verwalten der freigegebenen Elemente im plattformprojekt  
  
1.  Suchen Sie die freigegebene Elemente im plattformprojekt. Die Elemente im freigegebenen Projekt, das im plattformprojekt als freigegebene Elemente angezeigt wird. Nicht sichtbar in der **Projektmappen-Explorer**, aber Sie können Schritt für Schritt die Projekthierarchie, um sie zu finden. Die folgende Methode führt die Hierarchie und alle freigegebenen Elemente erfasst. Es gibt optional die Beschriftung der einzelnen Elemente. Die freigegebene Elemente werden durch die neue Eigenschaft identifiziert <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
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
  
2.  In der `ShowMessageBox` -Methode den folgenden Code zum durchlaufen die Plattform Hierarchie Projektelemente hinzufügen. Fügen Sie ihn in das `foreach` Block.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Lesen Sie die freigegebene Elemente. Die freigegebene Elemente, die im plattformprojekt als ausgeblendete verknüpfte Dateien angezeigt, und Sie können alle Eigenschaften als normale verknüpfte Dateien lesen. Der folgende Code liest den vollständigen Pfad des ersten freigegebenen Elements.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Probieren Sie es aus. Drücken Sie F5, um die experimentelle Instanz zu starten. Erstellen Sie ein C#-universal-Hub-app-Projekt in der experimentellen Instanz (in der **neues Projekt** Dialogfeld **Visual C#-/ Windows / Windows 8 / Universal / Hub-App**) wechseln Sie zu der **Tools** Menü **aufrufen TestUniversalProject**, und überprüfen Sie dann den Text in die **Ausgabe** Bereich. Es sollte nun etwa Folgendes angezeigt werden:  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Erkennen von Änderungen in die Plattform und freigegebene Projekte  
  
1. Sie können die Hierarchie und Projekt-Ereignisse verwenden, zum Erkennen von Änderungen in freigegebene Projekte, ebenso wie für Plattformprojekte. Allerdings sind die Projektelemente im freigegebenen Projekt nicht sichtbar ist, was bedeutet, dass bestimmte Ereignisse nicht ausgelöst werden, wenn freigegebene Projektelemente geändert werden.  
  
    Beachten Sie die Abfolge der Ereignisse, die beim Umbenennen einer Datei in einem Projekt ein:  
  
   1. Der Dateiname wird auf dem Datenträger geändert.  
  
   2. Die Projektdatei wird aktualisiert, um den neuen Namen der Datei einzuschließen.  
  
      Hierarchienereignisse (z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) in der Regel verfolgen die Änderungen, die in der Benutzeroberfläche angezeigt wird, wie in der **Projektmappen-Explorer**. Hierarchienereignisse sollten Sie ein Umbenennungsvorgang für eine Datei aus einer Datei löschen und dann auf Hinzufügen einer Datei bestehen. Allerdings wenn nicht sichtbare Elemente geändert werden, löst das System Hierarchie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis jedoch keiner <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis. Aus diesem Grund, wenn Sie eine Datei in ein Plattform-Projekt umbenennen, erhalten Sie beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, aber wenn Sie eine Datei in einem freigegebenen Projekt umbenennen, erhalten Sie nur <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
      Sie können zum Nachverfolgen von Änderungen in Projektelementen DTE-Projekt-Elementereignisse behandeln (diejenigen finden Sie im <xref:EnvDTE.ProjectItemsEventsClass>). Aber wenn Sie große Mengen von Ereignissen verarbeiten, erhalten Sie eine bessere Leistung, die Verarbeitung der Ereignisse in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. In dieser exemplarischen Vorgehensweise wird nur die Hierarchie und das DTE-Ereignisse beschrieben. In diesem Verfahren fügen Sie ein freigegebenes Projekt und ein Plattform-Projekt einen Ereignislistener hinzu. Klicken Sie dann, wenn Sie eine Datei in einem freigegebenen Projekt und eine andere Datei in ein Plattform-Projekt umbenennen, die Ereignisse sehen Sie, die für jeden Umbenennungsvorgang ausgelöst werden.  
  
      In diesem Verfahren fügen Sie ein freigegebenes Projekt und ein Plattform-Projekt einen Ereignislistener hinzu. Klicken Sie dann, wenn Sie eine Datei in einem freigegebenen Projekt und eine andere Datei in ein Plattform-Projekt umbenennen, die Ereignisse sehen Sie, die für jeden Umbenennungsvorgang ausgelöst werden.  
  
2. Fügen Sie einen Ereignislistener hinzu. Fügen Sie dem Projekt eine neue Klassendatei hinzu und nenne HierarchyEventListener.cs.  
  
3. Öffnen Sie die HierarchyEventListener.cs-Datei, und fügen Sie die folgenden using-Anweisungen:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  
  
   ```  
  
4. Haben die `HierarchyEventListener` implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  
  
   ```  
  
5. Implementieren Sie die Mitglieder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, wie im folgenden Code.  
  
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
  
6. Fügen Sie einem anderen Ereignishandler für das DTE-Ereignis hinzu, in der gleichen Klasse <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, Dies tritt ein, ein Projektelement umbenannt wird.  
  
   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  
  
7. Registrieren Sie sich für die hierarchienereignisse an. Sie müssen separat für jedes Projekt registrieren, die nachverfolgt werden. Fügen Sie den folgenden Code in `ShowMessageBox`, eine für das freigegebene Projekt, und die andere für eines der Plattformprojekte.  
  
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
  
8. Melden Sie sich für das DTE-Projekt-Elementereignis <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Fügen Sie den folgenden Code aus, nachdem Sie den zweiten Listener einbinden.  
  
   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
   ```  
  
9. Ändern Sie das freigegebene Element an. Sie können freigegebene Elemente in ein Plattform-Projekt nicht ändern; Stattdessen müssen Sie sie im freigegebenen Projekt ändern, die die tatsächlichen Kontoinhaber dieser Elemente ist. Sie erhalten die entsprechenden Element-ID im freigegebenen Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, legen sie den vollständigen Pfad des freigegebenen Elements. Dann können Sie das freigegebene Element ändern. Die Änderung wird an die Plattformprojekte weitergegeben.  
  
    > [!IMPORTANT]
    >  Sie sollten herausfinden, ob ein Projektelement eines freigegebenen Elements ist, bevor Sie Sie ändern.  
  
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
  
10. Diese Methode aufrufen, nachdem alle anderen Codes im `ShowMessageBox` nennen Sie das Element im freigegebenen Projekt so ändern Sie die Datei. Fügen Sie Folgendes an, nach dem Code, der den vollständigen Pfad des Elements im freigegebenen Projekt abruft.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Erstellen Sie das Projekt, und führen Sie es aus. Eine C#-universal-Hub-app in der experimentellen Instanz zu erstellen, wechseln Sie zu der **Tools** Menü **TestUniversalProject Aufrufen**, und überprüfen Sie den Text in der allgemeine Ausgabebereich. Der Name des ersten Elements im freigegebenen Projekt (wir erwarten, dass es die Datei "App.xaml") sollte geändert werden und sollte angezeigt werden, die <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> -Ereignis ausgelöst hat. In diesem Fall, da das Umbenennen von "App.xaml" bewirkt, dass die Datei "App.Xaml.cs", ebenfalls umbenannt werden soll, sollte vier Ereignisse (zwei für jede Plattform-Projekt) angezeigt werden. (DTE-Ereignisse nicht die Elemente im freigegebenen Projekt nachverfolgen.) Sie sehen zwei <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> -Ereignisse (eine für die einzelnen Plattformprojekte), aber keine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignisse.  
  
12. Versuchen Sie es jetzt mit dem Umbenennen einer Datei in ein Plattform-Projekt, und sehen Sie den Unterschied in den Ereignissen, die ausgelöst wird, zu erhalten. Fügen Sie den folgenden Code in `ShowMessageBox` nach dem Aufruf von `ModifyFileName`.  
  
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
  
13. Erstellen Sie das Projekt, und führen Sie es aus. Eine universelle C#-Projekt in der experimentellen Instanz zu erstellen, wechseln Sie zu der **Tools** Menü **TestUniversalProject Aufrufen**, und überprüfen Sie den Text in der allgemeine Ausgabebereich. Nachdem die Datei in die plattformprojekt umbenannt wurde, sollte Sie sowohl eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Ereignis und einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Ereignis. Da Änderungen verursacht die Datei keine anderen Dateien geändert werden, und da Änderungen an Elementen in einem plattformprojekt an einer beliebigen Stelle nicht weitergegeben werden, ist nur ein jedes dieser Ereignisse.
