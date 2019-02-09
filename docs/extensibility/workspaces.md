---
title: Arbeitsbereiche in Visual Studio | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: da61f3f46d9737bef6c14cf69a52be1951da28fb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925435"
---
# <a name="workspaces"></a>Arbeitsbereiche

Ein Arbeitsbereich ist Darstellungsweise von einer Sammlung von Dateien in Visual Studio ["Ordner öffnen"](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), und es wird durch die <xref:Microsoft.VisualStudio.Workspace.IWorkspace> Typ. Selbst nicht der Arbeitsbereich die Inhalte oder Features, die im Zusammenhang mit Dateien im Ordner vertraut machen. Stattdessen bietet es einen allgemeinen Satz von APIs für Funktionen und Erweiterungen erstellen und Nutzen von Daten, denen andere Benutzer darauf reagieren können. Die Hersteller bestehen über die [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) mit verschiedenen Attributen exportieren.

## <a name="workspace-providers-and-services"></a>Arbeitsbereich-Anbieter und -Dienste

Arbeitsbereich-Anbieter und -Dienste geben Sie die Daten und Funktionen, auf den Inhalt eines Arbeitsbereichs zu reagieren. Sie können bieten kontextbezogene Dateiinformationen, Symbole in Quelldateien oder Funktionen zu erstellen.

Verwenden Sie die beiden Konzepte eine [Factorymuster](https://en.wikipedia.org/wiki/Factory_method_pattern) und über MEF durch den Arbeitsbereich importiert werden. Implementieren Sie alle ExportAttribute `IProviderMetadataBase` oder `IWorkspaceServiceFactoryMetadata`, aber es gibt konkrete Typen, die Erweiterungen für die exportierten Typen verwendet werden soll.

Ein Unterschied zwischen Anbietern und -Diensten ist die Beziehung mit dem Arbeitsbereich. Viele Anbieter von einem bestimmten Typ kann über einen Arbeitsbereich verfügen, aber nur ein Dienst von einem bestimmten Typ wird pro Arbeitsbereich erstellt. Z. B. ein Arbeitsbereich verfügt über viele dateianbieter Scanner, aber der Arbeitsbereich bietet nur einen Indexdienst pro Arbeitsbereich.

Ein weiterer wesentlicher Unterschied ist die Nutzung von Daten von Anbietern und -Dienste. Der Arbeitsbereich ist der Einstiegspunkt zum Abrufen von Daten von Anbietern Gründen. Zuerst müssen die Anbieter in der Regel einige schmalen Satz von Daten, die sie erstellen. Die Daten möglicherweise Symbole für eine C# Quelldatei oder erstellen Sie die dateikontexte für einen _Datei "cmakelists.txt"_ Datei. Der Arbeitsbereich wird Consumer Anforderung an die Anbieter, deren Metadaten ausrichten, mit der Anforderung, überein. Zweitens: Einige Szenarien zu ermöglichen, für viele Anbieter zum mitwirken an den eine Anforderung, während andere Szenarien verwenden Sie den Anbieter mit der höchsten Priorität.

Im Gegensatz dazu können Erweiterungen Instanzen abgerufen und direkt mit dem Arbeitsbereich-Diensten zu interagieren. Erweiterungsmethoden für `IWorkspace` stehen für die Dienste, die von Visual Studio bereitgestellt, wie z. B. <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Die Erweiterung kann es sich um einen Arbeitsbereich-Dienst für die Komponenten in Ihrer Erweiterung oder für andere Erweiterungen Nutzen bieten. Consumer verwenden sollten <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> oder eine Erweiterungsmethode, die Sie angeben, auf die `IWorkspace` Typ.

>[!WARNING]
> Geschrieben Sie Dienste, die in mit Visual Studio Konflikt nicht werden. Es kann zu unerwarteten Problemen führen.

## <a name="disposal-on-workspace-closure"></a>Löschung auf Arbeitsbereich schließen

Extender möglicherweise auf den Abschluss eines Arbeitsbereichs, dispose, aber aufrufen asynchroner Code. Die <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Schnittstelle zur Verfügung, um diesen Code einfach ist.

## <a name="related-types"></a>Verwandte Typen

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> ist die zentrale Entität für eine geöffnete Arbeitsbereich wie einen geöffneten Ordner.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> erstellt einen Anbieter pro Arbeitsbereich instanziiert.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> erstellt einen Dienst pro Arbeitsbereich instanziiert.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> sollte auf Anbieter und Dienste, die zum Ausführen von asynchronen Codes bei der Freigabe müssen implementiert werden.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Stellt Hilfsmethoden für den Zugriff auf bekannten Dienste oder beliebige Dienste bereit.

## <a name="workspace-settings"></a>Arbeitsbereichseinstellungen

Arbeitsbereiche umfassen eine <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> mit einfachen, aber leistungsfähigen Kontrolle über einen Arbeitsbereich. Eine grundlegende Übersicht über die Einstellungen finden Sie unter [Anpassen von Build- und debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Einstellungen für die meisten `SettingsType` Typen sind _JSON_ Dateien, z. B. _VSWorkspaceSettings.json_ und _"Tasks.VS.JSON"_.

Die Leistungsfähigkeit von arbeitsbereichseinstellungen decken einen "Bereiche", die einfach Pfade innerhalb des Arbeitsbereichs sind. Wenn ein Consumer aufruft <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, werden alle Bereiche, die den angeforderten Pfad und den Typ der Einstellung enthalten aggregiert. Bereich Aggregation Priorität lautet wie folgt aus:

1. "Lokale Einstellungen" in der Regel dem arbeitsbereichstamm `.vs` Verzeichnis.
1. Der angeforderte Pfad selbst.
1. Das übergeordnete Verzeichnis der der angeforderte Pfad.
1. Alle übergeordneten Weitere Verzeichnisse bis zur und einschließlich dem arbeitsbereichstamm.
1. "Global Settings", die in einem Benutzerverzeichnis ist.

Das Ergebnis ist eine Instanz der <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Dieses Objekt enthält die Einstellungen für einen bestimmten Typ und kann abgefragt werden, für Schlüsselnamen festlegen, die als gespeicherte `string`. Die <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Methoden und <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> Erweiterungsmethoden erwarten, dass den Aufrufer den Typ des angeforderten Einstellungswerts kennen. Wie die meisten Einstellungsdateien, als beibehalten werden _JSON_ -Dateien verwenden viele Aufrufe `string`, `bool`, `int`, und Arrays dieser Typen. Objekttypen werden ebenfalls unterstützt. In diesen Fällen können Sie `IWorkspaceSettings` selbst als Typargument. Zum Beispiel:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Sofern diese Einstellungen wurden in eines vom Benutzers _VSWorkspaceSettings.json_, die Daten zugegriffen werden können:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Diese Einstellungen APIs sind unabhängig von den APIs zur Verfügung, in der `Microsoft.VisualStudio.Settings` Namespace. Arbeitsbereichseinstellungen sind unabhängig von dem Host und Arbeitsbereich spezifische Dateien oder dynamische Einstellungsanbieter verwenden.

### <a name="providing-dynamic-settings"></a>Bereitstellen von dynamischen-Einstellungen

Extensions bieten <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Diese in-Memory-Anbieter können Erweiterungen zum Hinzufügen von Einstellungen oder anderen überschreiben.

Exportieren einer `IWorkspaceSettingsProvider` unterscheidet sich von anderen Anbietern Arbeitsbereich. Die Factory ist nicht `IWorkspaceProviderFactory` und kein besonderes Attribut-Typ vorhanden ist. Implementieren Sie stattdessen <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> und `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Bei der Implementierung von Methoden, die zurückgeben `IWorkspaceSettingsSource` (z. B. `IWorkspaceSettingsProvider.GetSingleSettings`), eine Instanz des zurückgeben `IWorkspaceSettings` statt `IWorkspaceSettingsSource`. `IWorkspaceSettings` enthält weitere Informationen, die bei der einige Einstellungen Aggregationen nützlich sein kann.

### <a name="settings-related-apis"></a>Einstellungen für beziehen APIs.

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> liest und aggregiert die Einstellungen für den Arbeitsbereich.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ruft die `IWorkspaceSettingsManager` für einen Arbeitsbereich.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ruft die Einstellungen für einen bestimmten Bereich aggregiert für alle überlappenden Bereiche ab.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> enthält Einstellungen für einen bestimmten Bereich.

## <a name="workspace-suggested-practices"></a>Arbeitsbereich empfohlene Vorgehensweisen

- Zurückgeben von Objekten aus `IWorkspaceProviderFactory.CreateProvider` oder ähnliche APIs Denken Sie daran, die ihre `Workspace` Kontext beim Erstellen. Anbieter-Schnittstellen wurden erwartet, dass bei der Erstellung dieses Objekts gespeichert wird.
- Speichern Sie Arbeitsbereich spezifische Caches oder Einstellungen innerhalb der "Lokale Einstellungen"-Pfad des Arbeitsbereichs. Erstellen Sie einen Pfad für die Datei mit `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017 Version 15.6 oder höher. Verwenden Sie für Versionen vor Version 15.6 den folgenden Codeausschnitt:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Projektmappen-Ereignissen und das Paket automatisch laden

Geladenen Pakete implementieren können `IVsSolutionEvents7` , und rufen `IVsSolution.AdviseSolutionEvents`. Es enthält Ereignisse für das Öffnen und schließen einen Ordner in Visual Studio.

Ein UI-Kontext kann verwendet werden, um das Paket automatisch laden. Der Wert ist `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Das Paket SourceExplorerPackage wurde nicht ordnungsgemäß geladen.

Arbeitsbereich Erweiterbarkeit ist stark MEF-basierte und Komposition Fehler bewirken, dass das Ordner öffnen, um Fehler beim Laden der hosting-Paket. Wenn eine Erweiterung ein Typs mit exportiert z. B. `ExportFileContextProviderAttribute`, aber der Typ nur implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>`, wird eine Fehlermeldung beim Versuch, einen Ordner in Visual Studio zu öffnen. Fehlerdetails finden Sie in _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Beheben Sie alle Fehler für Typen bereit, die durch die Erweiterung implementiert.

## <a name="next-steps"></a>Nächste Schritte

* [Datei Kontexten](workspace-file-contexts.md) -dateianbieter-Kontext bringen Code Intelligence für Arbeitsbereiche, die "Ordner öffnen".
* [Indizierung](workspace-indexing.md) -Indizierung Arbeitsbereich erfasst und Informationen zum Arbeitsbereich beibehalten.
