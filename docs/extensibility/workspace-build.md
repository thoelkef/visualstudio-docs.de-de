---
title: Arbeitsbereich Builds in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143926"
---
# <a name="workspace-build"></a>Arbeitsbereich erstellen

Build-Unterstützung [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Szenarien erfordert keinen Extender angeben [indiziert](workspace-indexing.md) und [Kontext](workspace-file-contexts.md) Daten für die [Arbeitsbereich](workspaces.md), als sowie den Buildvorgang ausgeführt werden soll.

Es folgt ein Überblick darüber, was die Erweiterung benötigen.

## <a name="build-file-context"></a>Erstellen Sie die Dateikontext

- Anbieterfactory
  - `ExportFileContextProviderAttribute` -Attribut mit `supportedContextTypeGuids` wie alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Kontext-dateianbieter
    - Zurückgeben einer `FileContext` erstellen Sie für jeden Vorgang und Konfiguration wird unterstützt
      - `contextType` Von <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementiert <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> mit der `Configuration` -Eigenschaft, wie die Build-Konfiguration (z. B. `"Debug|x86"`, `"ret"`, oder `null` Falls nicht zutreffend). Alternativ können Sie mit einer Instanz der <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Der Konfigurationswert **müssen** mit der Konfiguration aus der indizierten Datenwert übereinstimmt.

## <a name="indexed-build-file-data-value"></a>Indizierte Build Datei Datenwert

- Anbieterfactory
  - `ExportFileScannerAttribute` -Attribut mit `IReadOnlyCollection<FileDataValue>` als unterstützten Typ
  - Implementiert `IWorkspaceProviderFactory<IFileScanner>`
- Dateiscanner auf `ScanContentAsync<T>`
  - Gibt Daten zurück, wenn `FileScannerTypeConstants.FileDataValuesType` entspricht dem Typargument
  - Gibt einen Wert des Datei-Daten für jede Konfiguration, die mit erstellt:
    - `type` as `BuildConfigurationContext.ContextTypeGuid`
    - `context` als der Buildkonfiguration (z. B. `"Debug|x86"`, `"ret"`, oder `null` Falls nicht zutreffend). Dieser Wert **müssen** mit der Konfiguration aus dem Dateikontext übereinstimmt.

## <a name="build-file-context-action"></a>Datei-Kontext Buildvorgang

- Anbieterfactory
  - `ExportFileContextActionProvider` -Attribut mit `supportedContextTypeGuids` wie alle anwendbaren `string` Konstanten aus `BuildContextTypes`
  - Implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Aktionsanbieter auf `IFileContextActionProvider.GetActionsAsync`
  - Zurückgeben einer `IFileContextAction` , entspricht der angegebenen `FileContext.ContextType` Wert
- Datei Kontext Aktion
  - Implementiert `IFileContextAction` und <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` -Eigenschaft gibt `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` ist `0x1000` für Build-, `0x1010` für die Wiederherstellung oder `0x1020` für bereinigen

>[!NOTE]
>Da die `FileDataValue` indiziert werden, muss eine gewissen Zeit zwischen dem Öffnen des Arbeitsbereichs und den Punkt, an dem die Datei wird für die vollständige Erstellung Funktionalität gescannt, werden. Auf der ersten Öffnen eines Ordners, da kein zuvor zwischengespeicherte Index vorhanden ist, wird die Verzögerung angezeigt werden.

## <a name="reporting-messages-from-a-build"></a>Reporting-Nachrichten aus einem build

Der Build kann Informations-, Warn- und Fehlermeldungen für Benutzer auf zwei Arten Oberfläche. Die einfache Möglichkeit ist die Verwendung der <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> , und geben Sie einen <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, wie folgt:

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

`BuildMessage.Type` und `BuildMessage.LogMessage` steuern das Verhalten der, in denen Informationen, die dem Benutzer angezeigt wird. Alle `BuildMessage.TaskType` anderen Wert als `None` erzeugt eine **Fehlerliste** Eintrag mit den angegebenen Details. `LogMessage` wird immer ausgegeben werden, der **erstellen** im Bereich der **Ausgabe** Toolfenster.

Erweiterungen können auch direkt interagieren, mit der **Fehlerliste** oder **erstellen** Bereich. Ein Fehler ist in Versionen vor Visual Studio 2017 Version 15.7 vorhanden, in denen die `pszProjectUniqueName` Argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> wird ignoriert.

>[!WARNING]
>Der Aufrufer `IFileContextAction.ExecuteAsync` bieten beliebige zugrunde liegenden Implementierungen für die `IProgress<IFileContextActionProgressUpdate>` Argument. Rufen Sie nie `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direkt. Es gibt derzeit keine allgemeingültigen Richtlinien für die Verwendung dieses Arguments, aber diese Richtlinien können jederzeit geändert werden.

## <a name="build-related-apis"></a>Erstellen von verwandten APIs

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> bietet Details zur Konfiguration von Builds.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Zeigt <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s für Benutzer.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON und launch.vs.json

Informationen über das Entwickeln einer tasks.vs.json oder launch.vs.json-Datei finden Sie unter [anpassen, erstellen und Debuggen von Aufgaben](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Nächste Schritte

* [Language-Serverprotokolls](language-server-protocol.md) -erfahren Sie, wie Server Sprache in Visual Studio integrieren.