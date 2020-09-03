---
title: Ersten Einstieg in Roslyn-Analyzers | Microsoft-Dokumentation
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711273"
---
# <a name="get-started-with-roslyn-analyzers"></a>Einstieg in Roslyn-Analysen

Mit Live, projektbasierten Code Analysemodulen in Visual Studio können API-Autoren eine domänenspezifische Code Analyse als Teil ihrer nuget-Pakete versenden. Da diese Analysen von der .NET Compiler Platform (Codename "Roslyn") unter werden, können Sie während der Typisierungs Warnung Warnungen in Ihrem Code erstellen (ohne mehr darauf warten, Ihren Code zu erstellen, um Probleme zu ermitteln). Analyzers können auch über die Eingabeaufforderung von Visual Studio eine automatische Code Korrektur durchlaufen, damit Sie den Code sofort bereinigen können.

## <a name="get-started"></a>Erste Schritte

[Übersicht über Roslyn-Analysen](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Schreiben Ihres ersten Analysetools und Codefixes](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Hinzufügen von Code Korrekturen Exemplarische Vorgehensweise: Bereitstellen von Benutzer Korrekturen für Analyse Probleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Echte Roslyn-Analyse](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) Tool, das Sie auch als [Gespräch](https://channel9.msdn.com/events/Build/2015/3-725) ansehen können

[Mehrere Beispiele auf GitHub, die in drei Arten von Analyzern gruppiert sind.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Weitere Informationen

- [.Net-compilerplattform-Paket Versions Referenz](roslyn-version-support.md)
- [Weitere Dokumente auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Mit Roslyn-Analyzern implementierte FxCop-Regeln](../code-quality/fxcop-rule-port-status.md)
