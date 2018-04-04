---
title: Erste Schritte mit Roslyn-Analyzern | Microsoft Docs
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0546604c60a310531fb101515b08bf18ed3d98e6
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="getting-started-with-roslyn-analyzers"></a>Erste Schritte mit Roslyn-Analyzern

Mit live-projektbasierten Code-Analyzer in Visual Studio können API Autoren domänenspezifische Codeanalyse in ihre NuGet-Pakete enthalten sind. Da diese Analyzer durch die .NET Compiler Platform (mit dem Codenamen "Roslyn") unterstützt werden, können sie Warnungen in Ihrem Code erzeugen, während der Eingabe, bevor Sie die Zeile (nicht mehr wartet auf den Code zum Ermitteln von Problemen zu erstellen) abgeschlossen haben. Analysen können auch über die Visual Studio Glühbirne Eingabeaufforderung, um Ihnen das Bereinigen von Code ermöglichen, sofort eine automatische Codekorrektur Oberfläche.

## <a name="getting-started"></a>Erste Schritte

[Roslyn Live Code-Analyzer – Einführung und exemplarische Vorgehensweise](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Hinzufügen, Dass Code Walkthrough behebt: Geben Sie Benutzer Korrekturen für Analyzer-Probleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Einführung und exemplarische Vorgehensweise der realen Welt Analyzer Talk](http://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , die Sie können außerdem sehen Sie sich als ein [sprechen](http://channel9.msdn.com/events/Build/2015/3-725)

[Beispielen auf Github, die in drei Arten von Analysen gruppiert](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Einführung und Überblick über einige Analysen zu sprechen.](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analyzern](../code-quality/roslyn-analyzers-overview.md)
- [Weitere Dokumente auf Github OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Implementiert mit Roslyn-Analyzer auf Github FxCop-Regeln](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)