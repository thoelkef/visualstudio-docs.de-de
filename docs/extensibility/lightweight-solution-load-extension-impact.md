---
title: "Einfache Lösung laden (LSL) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>Einfache Lösung laden (LSL)

## <a name="background-information-on-lsl"></a>Hintergrundinformationen zu LSL

Einfache Projektmappe zu laden ist ein neues Feature in Visual Studio 2017, Ladezeit Lösung wird erheblich aktivieren Sie schnell produktiver sein. Wenn LSL aktiviert ist, wird Visual Studio nicht vollständig Projekte geladen, wenn Sie mit ihnen zu arbeiten beginnen.

LSL kann Visual Studio-Erweiterungen wirksam. Erweiterungen, die an einem Projekt geladen werden, deren Funktionen abhängen möglicherweise nicht funktioniert oder nicht ordnungsgemäß arbeiten, ohne die Anweisungen in diesem Dokument aufgeführten.

Weitere Hintergrundinformationen zur LSL verwenden Sie die folgenden Links:

* [Einfache Lösung Load-Blog](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Fragen? Kontaktieren Sie uns[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Aktivieren Sie die Einstellung zum Laden von Projekten im Modus "verzögerte"

1. Schließen Sie alle geöffneten Projektmappen.
2. Wechseln Sie zu **Tools** > **Option** > **Projekte und Projektmappen** > **allgemeine** Einstellungsseite.
3. Überprüfen Sie die **einfache Lösung Load** um die Einstellung zu aktivieren.

Beim Öffnen einer Projektmappe mit der oben genannten Einstellung aktiviert ist, die IDE zeigt eine reguläre Ansicht der Projekte, aber die Projekte werden nicht geladen.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Unterschiede bei der verzögerten Laden und reguläre Laden von Projekten

Laden der Lightweight-Projektmappe Projekte nicht geladen, wenn Sie eine Projektmappe öffnen. Für diesen "verzögerte Projekten" ist eine Stub-Hierarchie erstellt. Im Projektmappen-Explorer zeigt die erwarteten Ansicht mit Symbolen und Namen von Projekten, es gibt keine UI-hin, dass einige oder alle Projekte in "Verzögerungsmodus" befinden.

Mit LSL aktiviert können die Erweiterungen nicht mehr erwarten, erforderlichen Projekte bereits vollständig geladen sind, wenn eine Operation ausgelöst wird. Aufrufer müssen überprüfen, ob diese geladenen Projekte eine Abhängigkeit aufweisen. Wenn eine Erweiterung Informationen aus einem verzögerten Projekt erfordert müssen, die Erweiterung folgendermaßen vor:

1. Laden Sie die Projekte nach Bedarf.
2. Verwenden Sie die neue **APIs Arbeitsbereich** zum Abrufen von Informationen von einer verzögerten Projekt, ohne sie zu laden.

Die neue **Arbeitsbereich APIs** zum Abrufen von Informationen, z. B. eine Quelldatei und alle Quelldateien für ein bestimmtes Projekt, das gewünschte Projekt aus einem Projekt verzögerte Erweiterungen zulassen. In einigen Fällen nur eine begrenzte Anzahl von Projekten geladen werden müssen. Die richtige Option ist ein Gleichgewicht zwischen der Häufigkeit der Vorgänge, einfache alternative Ansätze und optimiert.

Alle Projekt- und Laden der Projektmappe-bezogene Ereignisse im LSL Modus weiterhin ausgelöst werden. Dadurch können Komponenten, um das erwartete Verhalten in VS abzurufen und sie verhalten sich genauso wie bei Projekten geladen werden. Das Laden des Projekts bezogenen Arbeit während der geöffneten Projektmappe jedoch erheblich reduziert wird.

## <a name="ui-requirements-and-changes"></a>UI-Anforderungen und Änderungen

Wird keine Benutzeroberfläche muss geladen und zurückgestellte Projekte als gleich behandelt. Dies bedeutet, dass alle Aktionen, die für ein geladenes Projekt ausgeführt werden kann mit einigen Ausnahmen für verzögerte Projekte muss. Damit können Funktionen dazu, wurden einige vorhandene Plattform-APIs sowie die Einführung neuer APIs geändert.

### <a name="expectations-for-ui"></a>Ziele für die Benutzeroberfläche

1. Funktionen anzeigen müssen nicht visuell abhängig Unterschiede, wenn Projekte geladen oder zurückgestellt werden.
2. Jede Auflistung oder eines Enumerationswerts über die Projekte der Projektmappe geladen muss verzögerte Projekte enthalten.
3. Jede Aktion, die für ein geladenes Projekt sollte für eine verzögerte Projekt verfügbar sein.
4. Funktionen müssen Anforderung zum Laden Projekte nur, wenn:
  * Es gibt direkte Benutzerinteraktion mit einer Funktion. Laden Sie die Projekte nicht präemptiv.
  * Eine "Weitere Ergebnisse anzeigen" Bewegung erfolgt durch den Benutzer. Diese UI-Richtlinie finden Sie unten.
  * Nur die vollständig geladene Projekt kann verwendet werden, um die Aktion zu erfüllen. Verwenden Sie LSL und öffnen Sie Project-APIs nach Möglichkeit, und senden Sie Anforderung zur gefragt werden, wenn Funktionen nicht vorhanden ist.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Änderungen im Plattform-APIs UI bringen

1. Neue APIs werden bereitgestellt, der Lösung zu Fragen, ob sie geöffnet wurde, im Laden einer Projektmappe Lightweight-Modus und wie viele Projekte in einem verzögerte Zustand befinden.
2. Neues Ereignis wird für bereitgestellt, wenn alle verzögerten Projekte in der Projektmappe geladen werden.
3. Neue APIs werden bereitgestellt, ein Projekt zu Fragen, ob es verzögert wird.
4. Vorhandenen APIs werden aktualisiert, um die verzögerte Projekte umfassen, wenn für die geladenen Projekte.
5. Vorhandenen APIs werden aktualisiert, um schnelle Lösung vollständig geladen wird nach Projektmappe geöffnet wird.

### <a name="how-to-add-see-more-results-for-a-feature"></a>"Weitere Ergebnisse anzeigen" für ein Feature hinzufügen

Funktionen, die eine Abfrage für den Inhalt von Projekten ausführen, sollten die Auswirkung der verzögerte Projekte. In einigen Situationen können Features die Ergebnisse ihrer Abfrage von LSL und Arbeitsbereich-APIs für eine verzögerte Projekt erhalten. In anderen Fällen erfordern ein Feature Einschränkungen Projekte geladen werden. Beide Situationen sollte eine neue "Weitere Ergebnisse anzeigen" Geste bereitstellen, die Benutzern ermöglicht, Projekte und erneut Abfragen vollständig geladen. Diese Bewegung aktiviert Funktionen, um eine optimale Schätzung zu erstellen, wenn es verzögerte Projekte sind und des Benutzers eine Möglichkeit, das perfekte Ergebnis zu erhalten, wenn Projekte tatsächlich geladen werden.

Der allgemeine Algorithmus für Features muss:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Wenn die Abfrage über ein einzelnes Projekt ausgeführt wird

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Wenn die Abfrage ausgeführt wird, über die gesamte Projektmappe

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>API-Änderungen

### <a name="new-api"></a>Neue API

IVsSolution7.IsSolutionLoadDeferred (out Bool zurückgestellt)

Gibt True zurück, wenn die aktuelle Projektmappe im zurückgestellten Modus geladen wurde. Beachten Sie, die, wenn die Projektmappe zunächst in Verzögerungsmodus geladen wurde, selbst wenn alle verzögerten Projekte schließlich sind in der aktuellen Sitzung (durch explizite Benutzeraktionen oder erzwungene von Vorgängen), diese Eigenschaft geladen, würde true zurückgeben.

__VSPROPID7. VSPROPID_DeferredProjectCount

Gibt die Anzahl der Projekte, die zurzeit im Verzögerungsmodus zurück. Diese Eigenschaft wird einen Wert im Bereich [0, VSPROPID_ProjectCount] haben.

__VSHPROPID9. VSHPROPID_IsDeferred

Gibt True zurück, wenn das verzögerte Laden eine Projekthierarchie ist.

Mit den Werten EPF_DEFERRED und EPF_NOTDEFERRED __VSENUMPROJFLAGS3

Diese Flags übergeben werden können, um [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) verzögerte und nicht verzögerte Projekten durchlaufen.

### <a name="new-events"></a>Neue Ereignisse

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Dieses Ereignis wird ausgelöst, nachdem alle verzögerten Projekte geladen wurden. An diesem Punkt ist VSPROPID_DeferredProjectCount gleich 0. Beachten Sie, dass dieses Ereignis nicht als Teil der Lösung Load ausgelöst und kann nicht ausgelöst werden alle in einer Sitzung. Es wird nur ausgelöst, wenn alle verzögerten Projekte geladen werden.

### <a name="changes-to-existing-api"></a>Änderungen an vorhandenen API

* Übergeben von [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION, [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) gibt Projekte zurückgestellt.
* Übergeben von [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION gibt keine verzögerte Projekte zurück.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) Wert true für Projektmappe öffnen. Verzögerte Projekte werden behandelt, wie geladen werden, damit dieser Kontext viel festgelegt wurde früher als in nicht-LSL-Modus.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount gibt die Summe der geladen und zurückgestellte Projekte zurück.

## <a name="helpful-code-snippets"></a>Hilfreiche Codeausschnitte

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Überprüfen Sie, ob eine Projektmappe, im Modus für verzögertes Laden geöffnet wurde

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Überprüfen Sie, ob ein Projekt verzögert wird

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Laden Sie ein Projekt

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Laden Sie einen Satz von Projekten

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Überprüft, ob die Projektmappe Projekte verzögerte

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Beim Abrufen des ausführliche Informationen mit Workspace-APIs

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Gewusst wie: erhalten Sie detaillierte Informationen auf eine LSL-Lösung

Neuen Arbeitsbereich-APIs werden über IVsSolutionWorkspaceService, um detaillierte Informationen zu einer Lösung abzurufen verfügbar gemacht.

Diese APIs kann verwendet werden, um den aktuellen Arbeitsbereich, der aktiven Projektmappe, die verwaltete Befehlszeile Informationen sowie den Indexdienst für den Arbeitsbereich abrufen. Diese APIs können Sie den Indexdienst zum Abrufen der detaillierter Daten, z. B. alle Quelldateien in einem Projekt, das gewünschte Projekt einer Quelldatei alle Projekte in der aktuellen Projektmappe, alle P2P-Verweise in einem Projekt usw. weiter nutzen.

Die folgenden Codeausschnitte veranschaulichen die Verwendung der Workspace-APIs.

### <a name="get-ivssolutionworkspaceservice-initially"></a>IVsSolutionWorkspaceService Anfangs abrufen

>**Hinweis:** IVsSolutionWorkspaceService Bitte nur in LSL Szenarien zu vermeiden, das Laden des Pakets Workspace-API abrufen.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Hinweis:** nehmen Sie an die folgenden Codeausschnitten _solutionWorkspaceService bereits verzögert initialisiert wird.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Verwaltete Befehlszeile Informationen für verzögerte Projekte für die aktive Projektmappenkonfiguration abrufen

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Rufen Sie die Lösung für die aktive Datei in LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Rufen Sie das besitzende Projekt einer Quelldatei

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Rufen Sie aller Quelldateien aus einem Projekt ab

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Abrufen der P2P-Verweise in einem Projekt

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Erhalten Sie alle Projekte in einer Projektmappe

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Problembehandlung

Aufgrund der Natur der LSL ist es beabsichtigt, dass Benutzer einen Unterschied zwischen geladen und zurückgestellte Projekte sehen können. Dies kann Featureentwicklung und Tests erschweren.

Sie können visuelle Hinweise in der Benutzeroberfläche für verzögerte Projekte wie folgt aktivieren:

1. Schließen Sie Visual Studio.
2. Regedit.exe
3. Wählen Sie HKLM
4. Datei > Struktur laden
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Geben Sie "VisualStudio" als ein Schlüsselname
7. Legen Sie `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Wählen Sie HKLM\VisualStudio
9. Datei > entladen
10. Starten Sie Visual Studio

Noch weiteren Fragen wenden Sie sich an [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).







