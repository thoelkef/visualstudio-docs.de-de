---
title: Arbeitsbereich-Builds in Visual Studio | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553327"
---
# <a name="workspace-build"></a>Arbeitsbereich erstellen

Buildunterstützung ["Ordner öffnen"](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Szenarien erfordert, geben Sie einen Extender [indiziert](workspace-indexing.md) und [Dateikontext](workspace-file-contexts.md) Daten für die [Arbeitsbereich](workspaces.md), als sowie der Buildvorgang ausgeführt werden soll.

Im folgenden finden Sie ein Überblick darüber, was die Erweiterung benötigen.

## <a name="build-file-context"></a>Erstellen von Kontext

- Anbieterfactory
  - `ExportFileContextProviderAttribute` -Attribut mit `supportedContextTypeGuids` wie alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dateianbieter-Kontext
    - Zurückgeben einer `FileContext` erstellen Sie für jedes Verwendungsweise und die Konfiguration unterstützt
      - `contextType` Von <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementiert <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> mit der `Configuration` -Eigenschaft, wie die Build-Konfiguration (z. B. `"Debug|x86"`, `"ret"`, oder `null` Falls nicht zutreffend). Verwenden Sie alternativ eine Instanz der <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Der Konfigurationswert **müssen** mit der Konfiguration aus der indizierte Wert für die Daten übereinstimmen.

## <a name="indexed-build-file-data-value"></a>Daten-Wert der indizierten Build-Datei

- Anbieterfactory
  - `ExportFileScannerAttribute` -Attribut mit `IReadOnlyCollection<FileDataValue>` als unterstützten Typ
  - Implementiert `IWorkspaceProviderFactory<IFileScanner>`
- Dateiscanner auf `ScanContentAsync<T>`
  - Gibt Daten zurück, wenn `FileScannerTypeConstants.FileDataValuesType` ist das Typargument
  - Gibt einen Wert des Datei-Daten für jede Konfiguration, die mit erstellt:
    - `type` as `BuildConfigurationContext.ContextTypeGuid`
    - `context` als der Buildkonfiguration (z. B. `"Debug|x86"`, `"ret"`, oder `null` Falls nicht zutreffend). Dieser Wert **müssen** mit der Konfiguration aus dem Dateikontext übereinstimmen.

## <a name="build-file-context-action"></a>Dateikontextaktion erstellen

- Anbieterfactory
  - `ExportFileContextActionProvider` -Attribut mit `supportedContextTypeGuids` wie alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Aktionsanbieter auf `IFileContextActionProvider.GetActionsAsync`
  - Zurückgeben einer `IFileContextAction` , entspricht der angegebenen `FileContext.ContextType` Wert
- Dateikontextaktion
  - Implementiert `IFileContextAction` und <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` -Eigenschaft gibt `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` ist `0x1000` für Build-, `0x1010` für die Neuerstellung oder `0x1020` für bereinigen

>[!NOTE]
>Da die `FileDataValue` indiziert werden, fallen in eine bestimmte Zeit zwischen dem Öffnen des Arbeitsbereichs und der Punkt, an dem die Datei vollständiger Build-Funktion überprüft wird. Auf der ersten Öffnen eines Ordners, da kein zuvor zwischengespeicherten Index vorhanden ist, wird die Verzögerung angezeigt werden.

## <a name="reporting-messages-from-a-build"></a>Berichterstellung von Nachrichten aus einem build

Der Build kann Informationen, Warnung und Fehlermeldungen für Benutzer auf zwei Arten auftreten. Die einfachste Möglichkeit ist die Verwendung der <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> und geben Sie einen <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, etwa so:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` und `BuildMessage.LogMessage` Steuerung des Verhaltens, in dem Informationen für den Benutzer angezeigt wird. Alle `BuildMessage.TaskType` anderen Wert als `None` erzeugt eine **Fehlerliste** Eintrag mit den angegebenen Details. `LogMessage` wird immer ausgegeben werden, der **erstellen** im Bereich der **Ausgabe** Toolfenster.

Erweiterungen können auch direkt interagieren, mit der **Fehlerliste** oder **erstellen** Bereich. Ein Fehler ist in Versionen vor Visual Studio 2017 Version 15.7 vorhanden, in denen die `pszProjectUniqueName` Argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> wird ignoriert.

>[!WARNING]
>Aufrufer `IFileContextAction.ExecuteAsync` bieten beliebige zugrunde liegende Implementierungen für die `IProgress<IFileContextActionProgressUpdate>` Argument. Rufen Sie nie `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direkt. Es gibt derzeit keine allgemeingültigen Richtlinien für die Verwendung dieses Arguments, aber diese Richtlinien können geändert werden.

## <a name="build-related-apis"></a>Erstellen von verknüpften APIs

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> enthält ausführliche Informationen zur Build-Konfiguration.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Zeigt <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s für Benutzer.

## <a name="tasksvsjson-and-launchvsjson"></a>"Tasks.VS.JSON" und "Launch.VS.JSON"

Weitere Informationen zum Erstellen einer Datei "Tasks.VS.JSON" oder "Launch.VS.JSON", finden Sie unter [Anpassen von Build- und debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Nächste Schritte

* [Sprachserverprotokoll](language-server-protocol.md) -erfahren Sie, wie Sie Language-Server in Visual Studio zu integrieren.