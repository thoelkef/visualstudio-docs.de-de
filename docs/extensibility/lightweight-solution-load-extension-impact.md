---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
Title: "einfache Laden der Projektmappe (LSL) | Microsoft Docs"ms.custom:" "ms.date:" 01/17/2017"ms.reviewer:" "ms.suite:" "ms.technology: 
  - MS. tgt_pltfrm "Vs Ide Sdk": "" ms.topic: "Artikel" Helpviewer_keywords: 
  - "VSPackages, einfache Lösung laden
  - "VSPackages, schnelle Laden der Projektmappe" ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1-Autor: "Gregvanl" ms.author: "Gregvanl"-Manager: Ghogen
---
# <a name="lightweight-solution-load-lsl"></a>Einfache Lösung, Load (LSL)

## <a name="background-information-on-lsl"></a>Hintergrundinformationen zu LSL

Einfache Projektmappe zu laden, ist ein neues Feature in VS 2017 an erheblich Ladezeit Lösung zu reduzieren, sodass Sie schnell produktiver zu sein. Wenn LSL aktiviert ist, wird Visual Studio nicht vollständig Projekte geladen werden erst beim Arbeiten mit ihnen starten.

LSL kann Visual Studio-Erweiterungen beeinträchtigen. Erweiterungen, die an einem Projekt geladen werden, deren Funktionen abhängen, möglicherweise nicht funktioniert oder ohne gemäß der Anleitung in diesem Dokument aufgeführten voll funktionsfähig oder fehlerhaft.

Weitere Hintergrundinformationen zu LSL verwenden Sie die folgenden Links:

* [Einfache Lösung Load-Blog](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Fragen? Wenden Sie sich an uns[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Aktivieren der Einstellung, um Projekte in "Verzögerungsmodus" zu laden.

1. Schließen Sie alle aktuell geöffnete Projektmappe.
2. Wechseln Sie zu **Tools** > **Option** > **Projekte und Projektmappen** > **allgemeine** Einstellungen Seite ".
3. Überprüfen Sie die **einfache Lösung laden** die Einstellung zu aktivieren.

Beim Öffnen einer Projektmappe mit der oben genannten Einstellung aktiviert, die IDE zeigt eine reguläre Ansicht der Projekte, aber die Projekte werden nicht geladen.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Unterschiede bei der verzögerten Laden und reguläre Laden von Projekten

Mit Lightweight Projektmappe Laden werden die Projekte beim Öffnen einer Projektmappe nicht geladen. Für diese "verzögerte Projekte" wird eine Stub-Hierarchie erstellt. Im Projektmappen-Explorer zeigt die erwarteten Ansicht mit Symbolen und Namen von Projekten, es gibt keinen UI-Hinweis, der einige oder alle Projekte in "Verzögerungsmodus" sind.

Mit LSL aktiviert können Erweiterungen nicht mehr erwartet, dass erforderlichen Projekte bereits vollständig geladen werden, wenn ein Vorgang ausgelöst wird. Aufrufer müssen überprüfen, ob sie eine Abhängigkeit geladenen Projekte aufweisen. Wenn eine Erweiterung mit Informationen aus einem verzögerten Projekt erforderlich ist, führen Sie die Erweiterung folgende:

1. Laden Sie die Projekte nach Bedarf.
2. Verwenden Sie die neue **Arbeitsbereich APIs** beim Abrufen von Informationen aus einem verzögerten-Projekt, ohne sie zu laden.

Die neue **Arbeitsbereich APIs** durch Erweiterungen zum Abrufen von Informationen, z. B. das besitzende Projekt eine Quelldatei und aller die Quelldateien für ein angegebenes Projekt aus einem Projekt verzögerte zulassen. In einigen Fällen müssen nur ein begrenzten Satz von Projekten geladen werden. Die richtige Option ist ein Gleichgewicht zwischen der Häufigkeit der Vorgänge, einfache alternative Ansätze und durchgängig Benutzer.

Alle Projekt- und Laden der Projektmappe-bezogene Ereignisse im LSL Modus weiterhin ausgelöst werden. Dies ermöglicht Komponenten das erwartete Verhalten in VS abrufen und sie verhalten sich genauso wie bei Projekten geladen werden. Im Zusammenhang mit des Laden des Projekts Arbeit, die während der geöffneten Projektmappe jedoch erheblich reduziert wird.

## <a name="ui-requirements-and-changes"></a>UI-Anforderungen und Änderungen

Alle UI muss geladen und verzögerte Projekte als gleich behandelt. Dies bedeutet, dass alle Aktionen, die auf einem anderen geladenen Projekt ausgeführt werden, kann mit einigen Ausnahmen auch für verzögerte Projekte muss. Um dies zu erreichen Funktionen zu erleichtern, stehen Änderungen für einige vorhandene Plattform-APIs als auch in der Einführung der neuen APIs zur Verfügung.

### <a name="expectations-for-ui"></a>Anforderungen an die Benutzeroberfläche

1. Funktionen müssen werden angezeigt, dass kein visuelles abhängig Unterschiede, wenn Projekte geladen oder verzögert werden.
2. Eine Liste oder eines Enumerationswerts über die Projekte der Projektmappe geladen muss verzögerte Projekte enthalten.
3. Alle Aktionen zur Verfügung, mit einem anderen geladenen Projekt sollte für eine verzögerte Projekt verfügbar sein.
4. Funktionen müssen Anforderung zum Laden Projekte nur, wenn:
  * Es gibt direkte Interaktion mit einer Funktion. Laden Sie die Projekte nicht präemptiv.
  * Eine Geste "Finden Sie weitere Ergebnisse" wird vom Benutzer vorgenommen. Dieses UI-Richtlinie finden Sie weiter unten.
  * Nur den vollständig geladene Projekt kann verwendet werden, um die Aktion zu erfüllen. Verwenden Sie LSL und geöffneten Projekt-APIs nach Möglichkeit, und senden Sie Funktionsanfrage gefragt werden, wenn Funktionen nicht vorhanden ist.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Änderungen im Plattform-APIs zu Laufwerk UI

1. Neue APIs werden bereitgestellt, um der Projektmappe zu gefragt, ob es geöffnet wurde, im Laden der Projektmappe Lightweight-Modus und wie viele Projekte in einem verzögerte Zustand befinden.
2. Neues Ereignis wird für bereitgestellt, wenn alle verzögerten Projekte in der Projektmappe geladen werden.
3. Neue APIs werden bereitgestellt, um ein Projekt zu gefragt, ob es verzögert wird.
4. Vorhandene APIs werden aktualisiert, um die verzögerte Projekte umfassen, bei der Nachfrage der geladenen Projekte.
5. Vorhandene APIs werden aktualisiert, um express die Lösung vollständig geladen wird nach der Projektmappe geöffnet ist.

### <a name="how-to-add-see-more-results-for-a-feature"></a>So fügen Sie "Finden Sie weitere Ergebnisse" für eine Funktion.

Funktionen, die eine Abfrage für den Inhalt von Projekten ausführen, sollten die Auswirkungen der verzögerten Projekte. In einigen Situationen können Features die Ergebnisse ihrer Abfrage LSL und Arbeitsbereich APIs für eine verzögerte Projekt bekommen. In anderen Fällen erfordern eine Funktion Einschränkungen Projekte geladen werden soll. Beiden Fällen sollten eine neue "Finden Sie weitere Ergebnisse" Geste bereitstellen, die Benutzern ermöglicht, Projekte und erneut abgefragt vollständig geladen. Diese Bewegung aktiviert Funktionen, um eine optimale Schätzung zu erstellen, wenn es verzögerte Projekte sind, wobei des Benutzers eine Möglichkeit, die perfekte Ergebnis zu erhalten, wenn Projekte tatsächlich geladen werden.

Der allgemeine Algorithmus für Funktionen sollten sein:

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
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
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

Gibt "true" zurück, wenn die aktuelle Projektmappe im Verzögerungsmodus geladen wurde. Beachten Sie, die, wenn die Projektmappe im Verzögerungsmodus anfänglich geladen wurde, selbst wenn die verzögerte Projekte letztendlich sind in der aktuellen Sitzung (aufgrund von expliziten Benutzergesten oder erzwungene von Vorgängen), diese Eigenschaft geladen, würde weiterhin "true" zurückgeben.

__VSPROPID7. VSPROPID_DeferredProjectCount

Gibt die Anzahl der Projekte zurück, die sich derzeit im Verzögerungsmodus befinden. Diese Eigenschaft wird einen Wert im Bereich [0, VSPROPID_ProjectCount] aufweisen.

__VSHPROPID9. VSHPROPID_IsDeferred

Gibt "true" zurück, wenn eine Projekthierarchie verzögerte Laden Status aufweist.

__VSENUMPROJFLAGS3 mit Werten EPF_DEFERRED und EPF_NOTDEFERRED

Diese Flags übergeben werden können, um [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) verzögerte und nicht verzögerte Projekten durchlaufen.

### <a name="new-events"></a>Neue Ereignisse

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Dieses Ereignis wird ausgelöst, nachdem alle verzögerten Projekte geladen wurden. An diesem Punkt ist VSPROPID_DeferredProjectCount gleich 0. Beachten Sie, dass dieses Ereignis nicht ausgelöst wird, im Rahmen des Laden der Projektmappe, und kann nicht ausgelöst werden alle in einer Sitzung. Es wird nur ausgelöst, wenn alle verzögerten Projekte geladen werden.

### <a name="changes-to-existing-api"></a>Änderungen an vorhandenen-API

* Übergeben von [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION auf [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) gibt verzögert Projekte.
* Übergeben von [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION gibt keine verzögerte Projekte zurück.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) festgelegt ist, auf "true" bei Projektmappe öffnen. Verzögerte Projekte werden behandelt, als geladen werden, damit diesem Kontext viel festgelegt ist im nicht-LSL-Modus vor.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount gibt die Summe der geladen und verzögerte Projekte zurück.

## <a name="helpful-code-snippets"></a>Hilfreiche Codeausschnitte

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Überprüfen Sie, ob eine Projektmappe, im Modus für verzögerte Laden geöffnet wurde

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
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

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

## <a name="getting-detailed-information-with-workspace-apis"></a>Abrufen von ausführliche Informationen mit der Arbeitsbereich APIs

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Gewusst wie: Abrufen von ausführliche Informationen zu einem Lösungsvorschlag LSL

Neuen Arbeitsbereich APIs werden über IVsSolutionWorkspaceService können detaillierte Informationen zu einer Lösung abrufen verfügbar gemacht.

Diese APIs kann verwendet werden, um den aktuellen Arbeitsbereich, der aktiven Projektmappe, die Informationen des verwalteten Befehlszeile sowie den Indexdienst für den Arbeitsbereich abrufen. Diese APIs können weitere den Indexdienst zum Abrufen der detaillierter Daten, z. B. alle Quelldateien in einem Projekt auf das gewünschte Projekt einer Quelldatei alle Projekte in der aktuellen Projektmappe befinden, enthalten alle P2P-Verweise in einem Projekt usw. nutzen.

Die folgenden Codeausschnitte veranschaulichen die Verwendung der APIs Arbeitsbereich.

### <a name="get-ivssolutionworkspaceservice-initially"></a>IVsSolutionWorkspaceService anfänglich abrufen

>**Hinweis:** IVsSolutionWorkspaceService geben nur LSL-Szenarios zu vermeiden, Laden des Pakets Arbeitsbereich API zu erhalten.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Hinweis:** den folgenden Codeausschnitt wird davon ausgegangen, _solutionWorkspaceService bereits verzögert initialisiert wird.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Abrufen von verwalteten Befehlszeile Informationen für verzögerte Projekte für die Konfiguration der aktuellen Projektmappe

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

### <a name="get-the-active-solution-file-in-lsl"></a>Abrufen der aktiven Projektmappendatei im LSL

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

### <a name="get-the-owning-project-of-a-source-file"></a>Das besitzende Projekt einer Quelldatei abrufen

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

### <a name="get-all-the-projects-in-a-solution"></a>Abrufen Sie aller Projekte in einer Projektmappe

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

Aufgrund der Natur der LSL ist es beabsichtigt, dass Benutzer einen Unterschied zwischen geladen und verzögerte Projekte nicht angezeigt. Dies kann Feature Entwicklungs- und Testzwecken erschweren.

Sie können visuelle Hinweise in der Benutzeroberfläche für verzögerte Projekte aktivieren, indem Sie auf folgende Weise:

1. Schließen Sie Visual Studio.
2. Regedit.exe
3. Wählen Sie HKLM
4. Datei > Struktur laden
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Geben Sie "VisualStudio" als ein Schlüsselname
7. Legen Sie `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Wählen Sie HKLM\VisualStudio
9. Datei > Struktur entfernen
10. Starten Sie Visual Studio

Alle weiteren Fragen wenden Sie Remoteknoten [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).






