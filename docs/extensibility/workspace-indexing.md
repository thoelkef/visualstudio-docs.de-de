---
title: Arbeitsbereich Indizierung in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143425"
---
# <a name="workspace-indexing"></a>Arbeitsbereich Indizierung

In einer Projektmappe Projektsystemen sind verantwortlich für die Entwicklung von Funktionen für den Build, Debuggen, **GoTo** Symbol suchen und vieles mehr. Projektsysteme können diese arbeiten daran, dass sie die Beziehung und die Funktionen von Dateien in einem Projekt verstehen. Ein [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Arbeitsbereich benötigt den gleichen einen Einblick in den sowie umfangreiche IDE-Funktionen bieten. Die Sammlung und persistenten Speicherung dieser Daten ist eine sogenannte Arbeitsbereich zu indizieren. Diese indizierten Daten können über eine Reihe von asynchronen APIs abgefragt werden. Extender können durch die Bereitstellung in den Indizierungsprozess einbezogen <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>e, die wissen, wie Sie bestimmte Typen von Dateien zu verarbeiten.

## <a name="types-of-indexed-data"></a>Typen von Daten

Es gibt drei Arten von Daten, die indiziert werden. Notieren Sie den Typ von Dateiscanner erwartet unterscheidet sich von den Typ aus dem Index deserialisiert.

|Daten|Dateityp-scanner|Index Abfrageergebnistyps|Verwandte Typen|
|--|--|--|--|
|Verweise|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> sollte verwendet werden, anstelle von `IIndexWorkspaceService` für Abfragen|
|Datenwerte|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Abfragen von volltextindizierten Daten

Es gibt zwei asynchrone Typen, die auf persistente Daten zuzugreifen. Der erste wird über <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Es bietet grundlegende Zugriff auf einer einzelne Datei `FileReferenceResult` und `FileDataResult` Daten und Ergebnisse zwischenspeichert. Das zweite ist der <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> die caching nicht verwendet werden, jedoch können weitere LINQ-Funktionen.

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

## <a name="participating-in-indexing"></a>Einbeziehung in die Indizierung

Arbeitsbereich Indizierung entspricht in etwa die folgende Reihenfolge:

1. Ermittlung und Dauerhaftigkeit der Datei Systementitäten im Arbeitsbereich (nur auf die erste öffnende-Überprüfung).
1. Pro Datei, wird der entsprechende Anbieter mit der höchsten Priorität zum Überprüfen der gebeten `FileReferenceInfo`s.
1. Pro Datei, wird der entsprechende Anbieter mit der höchsten Priorität zum Überprüfen der gebeten `SymbolDefinition`s.
1. Pro Datei, werden alle Anbieter für aufgefordert `FileDataValue`s.

Erweiterungen können Scanner exportieren, durch die Implementierung `IWorkspaceProviderFactory<IFileScanner>` und Exportieren den Typ mit <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Die `SupportedTypes` Attributargument muss ein oder mehrere Werte aus <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Eine Beispiel-Scanner finden Sie im VS-SDK [Beispiel](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Exportieren Sie einen Dateiscanner, die unterstützt nicht die `FileScannerTypeConstants.FileScannerContentType` Typ. Es wird Microsoft ausschließlich für interne Zwecke, verwendet.

In komplexeren Situationen kann eine Erweiterung dynamisch eine beliebige Gruppe von Dateitypen unterstützt. Anstatt zu MEF exportieren `IWorkspaceProviderFactory<IFileScanner>`, eine Erweiterung kann exportieren `IWorkspaceProviderFactory<IFileScannerProvider>`. Bei der Indizierung begonnen hat, diese Factorytyp wird importiert, instanziiert, und haben die <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> aufgerufene Methode. `IFileScanner` unterstützen einen beliebigen Wert zwischen Instanzen `FileScannerTpeConstants` wird berücksichtigt werden, nicht nur Symbole.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche und Sprachdienste](workspace-language-services.md) -erfahren Sie, wie Sprachdienste in einen Ordner öffnen-Arbeitsbereich zu integrieren.
* [Arbeitsbereich Build](workspace-build.md) -Ordner öffnen unterstützt Buildsysteme wie MSBuild und Makefiles.