---
title: Indizierung in Visual Studio Workspace | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956986"
---
# <a name="workspace-indexing"></a>Indizieren von Arbeitsbereich

In einer Projektmappe Projektsystemen sind verantwortlich für das Bereitstellen von Funktionalität für den Build, debug, **GoTo** Symbol suchen und vieles mehr. Projektsysteme können diese Aufgabe übernimmt, da sie die Beziehung und die Funktionen von Dateien in einem Projekt verstehen. Ein ["Ordner öffnen"](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Arbeitsbereichs benötigt, die gleiche Einblicke sowie umfassende IDE-Features angeben. Die Sammlung und die dauerhafte Speicherung von Daten ist ein so genanntes Arbeitsbereich zu indizieren. Diese indizierten Daten können über eine Reihe von asynchronen APIs abgefragt werden. Extender können durch die Bereitstellung in den Indizierungsprozess teilnehmen <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s, die weiß, wie bestimmte Dateitypen zu verarbeiten.

## <a name="types-of-indexed-data"></a>Typen von indizierten Daten

Es gibt drei Arten von Daten, die indiziert werden. Notieren Sie den Typ von Dateiscanner erwartet unterscheidet sich von dem Typ, der aus dem Index deserialisiert.

|Daten|Dateityp-scanner|Index Abfrageergebnistyps|Verwandte Typen|
|--|--|--|--|
|Verweise|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> sollte verwendet werden, anstelle von `IIndexWorkspaceService` für Abfragen|
|Datenwerte|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Abfragen von volltextindizierten Daten

Es gibt zwei asynchrone Typen, die Zugriff auf persistente Daten zur Verfügung. Der erste wird über <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Es bietet einfachen Zugriff auf einer einzelne Datei `FileReferenceResult` und `FileDataResult` Daten und speichert die Ergebnisse. Die zweite ist die <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> das caching nicht verwendet werden, ermöglicht jedoch weitere Funktionen.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Teilnahme an Indizierung

Indizieren von Arbeitsbereich entspricht in etwa die folgende Reihenfolge:

1. Ermittlung und Persistenz File System-Entitäten im Arbeitsbereich "" (nur auf die erste öffnende-Überprüfung).
1. Pro Datei, wird der entsprechende Anbieter mit der höchsten Priorität zum Scannen nach aufgefordert `FileReferenceInfo`s.
1. Pro Datei, wird der entsprechende Anbieter mit der höchsten Priorität zum Scannen nach aufgefordert `SymbolDefinition`s.
1. Pro Datei, werden alle Anbieter aufgefordert, für die `FileDataValue`s.

Erweiterungen können eine Überprüfung durch die Implementierung exportieren `IWorkspaceProviderFactory<IFileScanner>` und Exportieren den Typ mit <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Die `SupportedTypes` Codeattribut-Argument muss einen oder mehrere Werte aus <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Eine Beispiel-Scanner, finden Sie im VS-SDK [Beispiel](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Exportieren Sie einen Dateiscanner, die unterstützt nicht die `FileScannerTypeConstants.FileScannerContentType` Typ. Es wird Microsoft nur zu internen, verwendet.

In komplexeren Situationen kann eine Erweiterung dynamisch eine beliebige Gruppe von Dateitypen unterstützt. Anstatt den MEF-Export `IWorkspaceProviderFactory<IFileScanner>`, eine Erweiterung kann exportieren `IWorkspaceProviderFactory<IFileScannerProvider>`. Indizierung zu Beginn wird dieses Factorytyps wird importiert, werden instanziiert, und haben die <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> aufgerufene Methode. `IFileScanner` unterstützen einen beliebigen Wert zwischen Instanzen `FileScannerTpeConstants` berücksichtigt werden, nicht nur Symbole.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche und Sprachdienste](workspace-language-services.md) -erfahren Sie, wie Sie Sprachdienste in einen Ordner öffnen-Arbeitsbereich zu integrieren.
* [Arbeitsbereich erstellen](workspace-build.md) -Buildsysteme für "Ordner öffnen" unterstützt z.B. MSBuild und Makefiles.