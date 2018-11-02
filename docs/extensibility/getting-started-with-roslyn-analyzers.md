---
title: Erste Schritte mit Roslyn-Analysetools | Microsoft-Dokumentation
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d89cd2f7ff1be28ac9d96578ba5ce57f653cc65e
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750909"
---
# <a name="get-started-with-roslyn-analyzers"></a>Erste Schritte mit Roslyn-Analysetools

Mit live-projektbasierten codeanalysemodulen in Visual Studio können die API-Autoren domänenspezifische Codeanalyse als Teil ihrer NuGet-Pakete schicken. Da diese Analysemodule durch das .NET Compiler Platform (Codename "Roslyn") unterstützt werden, können sie Warnungen in Ihrem Code führen, während der Eingabe, bevor Sie die Zeile (nicht mehr darauf warten, erstellen Sie Ihren Code, um Probleme zu ermitteln) abgeschlossen haben. Analyzer können auch auftreten, einen automatischen Codefix über die Visual Studio-Glühbirne-Eingabeaufforderung, bereinigen Sie Ihren Code sofort zu können.

## <a name="get-started"></a>Erste Schritte

[Einführung in Roslyn live Code-Analyzer und exemplarische Vorgehensweise](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Hinzufügen von codefehlerbehebungen Exemplarische Vorgehensweise: bieten Sie Benutzern Korrekturen für Analyzer-Probleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Einführung und exemplarische Vorgehensweise des Analyzers der realen Welt kommunizieren.](https://channel9.msdn.com/events/Build/2015/3-725)

[Roslyn-Analyzer realen](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , die Sie können außerdem sehen Sie sich als ein [sprechen](https://channel9.msdn.com/events/Build/2015/3-725)

[Beispiele auf GitHub an, gruppiert drei Arten von Analysen](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Einführung und Überblick über einige Analysen kommunizieren.](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analyzer](../code-quality/roslyn-analyzers-overview.md)
- [Weitere-Dokumentation auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [FxCop-Regeln, die mit Roslyn-Analysetools auf GitHub implementiert](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
