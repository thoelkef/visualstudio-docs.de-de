---
title: Arbeitsbereiche in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 4585ebc5288164f9d441c14332a6af0f1142119b
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces"></a>Arbeitsbereiche

Ein Arbeitsbereich ist wie Visual Studio stellt dar, eine beliebige Sammlung von Dateien in [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), und es wird durch die <xref:Microsoft.VisualStudio.Workspace.IWorkspace> Typ. Selbst nicht der Arbeitsbereich den Inhalt oder die Funktionen in Bezug auf die Dateien im Ordner vertraut machen. Stattdessen stellt er einen allgemeinen Satz von APIs für die Funktionen und Erweiterungen zu erzeugen und Nutzen von Daten, denen andere reagieren können. Der Producer bestehen aus über die [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) mit verschiedenen Attributen exportieren.

## <a name="workspace-providers-and-services"></a>Arbeitsbereich "Anbieter und -Dienste

Arbeitsbereich Anbieter und -Dienste geben Sie die Daten und Funktionen, auf den Inhalt eines Arbeitsbereichs zu reagieren. Sie können bieten kontextabhängige Dateiinformationen, Symbole in Quelldateien oder Funktionen zu erstellen.

Verwenden Sie die beiden Konzepte eine [Factorymuster](https://en.wikipedia.org/wiki/Factory_method_pattern) und über MEF, indem Sie den Arbeitsbereich importiert werden. Alle ExportAttribute implementieren `IProviderMetadataBase` oder `IWorkspaceServiceFactoryMetadata`, aber es gibt konkrete Typen, die Erweiterungen für die exportierten Typen verwendet werden soll.

Ein Unterschied zwischen Anbietern und -Dienste ist ihre Beziehung zu dem Arbeitsbereich. Viele Anbieter von einem bestimmten Typ kann über keinen Arbeitsbereich verfügen, aber nur ein Dienst, der einen bestimmten Typ wird pro Arbeitsbereich erstellt. Z. B. ein Arbeitsbereich verfügt über viele Datei Scanner Anbieter jedoch Arbeitsbereich hat nur einen Indexdienst pro Arbeitsbereich.

Eine andere Hauptunterschied ist die Nutzung von Daten von Anbietern und -Dienste. Der Arbeitsbereich ist der Einstiegspunkt zum Abrufen von Daten von Providern einige Gründe vorliegen. Zuerst müssen Anbieter in der Regel einige schmale Datenmenge, die sie erstellen. Die Daten werden Symbole für eine C#-Quelldatei oder Erstellen der Datei Kontexten für eine _CMakeLists.txt_ Datei. Der Arbeitsbereich wird ein Consumer-Anforderung an den Anbieter, deren Metadaten ausgerichtet, mit der Anforderung, überein. Zweitens können einige Szenarien für viele Anbieter, die auf eine Anforderung, während andere Szenarien beitragen verwenden Sie den Anbieter mit der höchsten Priorität.

Im Gegensatz dazu können Erweiterungen Instanzen abgerufen und direkt mit der Arbeitsbereich Diensten interagieren. Erweiterungsmethoden für `IWorkspace` stehen für die Dienste, die von Visual Studio bereitgestellt, wie z. B. <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Die Erweiterung kann einen Dienst Arbeitsbereich für Komponenten in der Erweiterung oder für andere Erweiterungen Nutzen bieten. Consumer verwenden sollten <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> oder eine Erweiterungsmethode, die Sie bereitstellen, auf die `IWorkspace` Typ.

>[!WARNING]
> Erstellen Sie keine Dienste, die mit Visual Studio in Konflikt stehen. Es kann zu unerwarteten Problemen führen.

## <a name="disposal-on-workspace-closure"></a>Beseitigung Arbeitsbereich schließen

Auf den Abschluss eines Arbeitsbereichs, Extender dispose jedoch asynchronen Aufrufen müssen möglicherweise Code. Die <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Schnittstelle für das Schreiben von Code leicht verfügbar ist.

## <a name="related-types"></a>Verwandte Typen

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> ist die zentrale Entität für eine geöffnete Arbeitsbereich wie einem geöffneten Ordner.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> erstellt einen Anbieter pro Arbeitsbereich instanziiert.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> erstellt einen Dienst pro Arbeitsbereich instanziiert.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> sollte für Anbieter und -Dienste, die zum Ausführen von asynchronen Code während der Freigabe müssen implementiert werden.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Stellt Hilfsmethoden für den Zugriff auf bekannte Dienste oder beliebige Dienste bereit.

## <a name="workspace-settings"></a>Arbeitsbereichseinstellungen

Arbeitsbereiche Einrichten einer <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> Dienst mit einfache, jedoch leistungsstarke Kontrolle über einen Arbeitsbereich. Eine grundlegende Übersicht über die Einstellungen finden Sie unter [anpassen, erstellen und Debuggen von Aufgaben](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Einstellungen für die meisten `SettingsType` Typen sind _.json_ Dateien, wie z. B. _VSWorkspaceSettings.json_ und _tasks.vs.json_.

Die Leistungsfähigkeit von arbeitsbereichseinstellungen dreht sich alles um "Bereiche", einfach Pfade innerhalb des Arbeitsbereichs sind. Wenn ein Consumer ruft <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, werden alle Bereiche, die den angeforderten Pfad und den Typ der Einstellung enthalten aggregiert. Bereich Aggregation Priorität sieht folgendermaßen aus:

1. "Lokale Einstellungen", i. d. r. des Arbeitsbereich Stamms `.vs` Verzeichnis.
1. Der angeforderte Pfad selbst.
1. Das übergeordnete Verzeichnis des angeforderten Pfads.
1. Alle übergeordneten Weitere Verzeichnisse bis zur und einschließlich des Modellstamms Arbeitsbereich.
1. "Globale Einstellungen", die in einem Verzeichnis des Benutzers ist.

Das Ergebnis ist eine Instanz der <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Dieses Objekt enthält die Einstellungen für einen bestimmten Typ, und können abgefragt werden, für Schlüsselnamen festlegen als gespeicherte `string`. Die <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Methoden und <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> Erweiterungsmethoden erwarten, dass den Aufrufer den Typ des angeforderten Einstellungswerts kennen. Die meisten Einstellungsdateien als dauerhafte sind _JSON_ -Dateien verwenden viele Aufrufe `string`, `bool`, `int`, und Arrays dieser Typen. Objekttypen werden ebenfalls unterstützt. In diesen Fällen können Sie `IWorkspaceSettings` selbst als Typargument. Zum Beispiel:

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

Vorausgesetzt, diese Einstellungen wurden in eines Benutzers _VSWorkspaceSettings.json_, die Daten wie möglich:

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
>Diese Einstellungen APIs sind nicht mit der APIs verfügbar, in der `Microsoft.VisualStudio.Settings` Namespace. Arbeitsbereichseinstellungen für die agnostische des Hosts und Arbeitsbereich-spezifische Einstellungsdateien oder Einstellungen für dynamische Anbieter.

### <a name="providing-dynamic-settings"></a>Bereitstellen von Einstellungen für dynamische

Erweiterungen bieten <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Diese in-Memory-Anbieter durch Erweiterungen Einstellungen hinzufügen oder überschreiben andere zulassen.

Exportieren einer `IWorkspaceSettingsProvider` unterscheidet sich von anderen Anbietern Arbeitsbereich. Die Factory ist nicht `IWorkspaceProviderFactory` und kein spezielles Attribut-Typ vorhanden ist. Implementieren Sie stattdessen <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> und `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

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
>Bei der Implementierung von Methoden, die zurückgeben `IWorkspaceSettingsSource` (z. B. `IWorkspaceSettingsProvider.GetSingleSettings`), eine Instanz des zurückgeben `IWorkspaceSettings` statt `IWorkspaceSettingsSource`. `IWorkspaceSettings` enthält weitere Informationen, die während einige Einstellungen Aggregationen hilfreich sein kann.

### <a name="settings-related-apis"></a>Verwandte Einstellungen-APIs

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> liest und Einstellungen für Arbeitsbereich aggregiert.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ruft die `IWorkspaceSettingsManager` für einen Arbeitsbereich angezeigt.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ruft die Einstellungen für einen bestimmten Bereich über alle überlappenden Bereiche aggregiert.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> enthält Einstellungen für einen bestimmten Bereich.

## <a name="workspace-suggested-practices"></a>Arbeitsbereich empfohlene Vorgehensweisen

- Zurückgeben von Objekten aus `IWorkspaceProviderFactory.CreateProvider` oder ähnliche APIs, die merken ihre `Workspace` Kontext beim Erstellen. Anbieter-Schnittstellen geschrieben werden, wird erwartet, dass bei der Erstellung dieses Objekt beibehalten wird.
- Speichern Sie Arbeitsbereich "-spezifische Caches oder im Pfad"Lokale Einstellungen"des Arbeitsbereichs Einstellungen. Erstellen Sie einen Pfad für die Datei mit `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017 15.6 oder höher. Verwenden Sie für Versionen vor Version 15,6 der folgende Codeausschnitt ein:

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

## <a name="solution-events-and-package-auto-load"></a>Projektmappenereignisse und automatisches Laden des Pakets

Geladenen Pakete implementieren können `IVsSolutionEvents7` und Aufrufen von `IVsSolution.AdviseSolutionEvents`. Es enthält Ereignisse für das Öffnen und schließen einen Ordner in Visual Studio.

Ein UI-Kontext kann verwendet werden, um das Paket automatisch geladen. Der Wert ist `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Das SourceExplorerPackage-Paket wurde nicht ordnungsgemäß geladen.

Arbeitsbereich Erweiterbarkeit ist stark MEF-basierten und Zusammensetzung Fehler bewirken, dass das Paket, hostet der Ordner öffnen, um Fehler beim Laden. Wenn eine Erweiterung ein Typs mit exportiert z. B. `ExportFileContextProviderAttribute`, aber nur der Typ implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>`, beim Versuch, einen Ordner in Visual Studio öffnen, wird eine Fehlermeldung angezeigt. Fehlerdetails finden Sie _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Beheben Sie alle Fehler für Typen, die von der Erweiterung implementiert.

## <a name="next-steps"></a>Nächste Schritte

* [Datei Kontexten](workspace-file-contexts.md) -Datei Kontext Anbieter schalten Code Intelligence Arbeitsbereichen geöffneten Ordner. 
* [Indizierung](workspace-indexing.md) -Arbeitsbereich Indizierung erfasst und behält die Informationen über den Arbeitsbereich ".
