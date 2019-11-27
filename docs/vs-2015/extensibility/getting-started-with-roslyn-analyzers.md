---
title: Ersten Einstieg in Roslyn-Analyzers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300011"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Erste Schritte mit Roslyn-Analyzern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Live, projektbasierten Code Analysemodulen in Visual Studio können API-Autoren eine domänenspezifische Code Analyse als Teil ihrer nuget-Pakete versenden.  Da diese Analysen von der .NET Compiler Platform (Codename "Roslyn") unter werden, können Sie während der Typisierungs Warnung Warnungen in Ihrem Code erstellen (ohne mehr darauf warten, Ihren Code zu erstellen, um Probleme zu ermitteln).  Analyzers können auch über die Eingabeaufforderung von Visual Studio eine automatische Code Korrektur durchlaufen, damit Sie Ihren Code sofort bereinigen können.

## <a name="getting-started"></a>Erste Schritte
[Einführung und Exemplarische Vorgehensweise für Roslyn-Live Code-Analyzers](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Hinzufügen von Code Korrekturen Exemplarische Vorgehensweise: Bereitstellen von Benutzer Korrekturen für Analyse Probleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Einführung und Exemplarische Vorgehensweise für Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Echte Roslyn-Analyse](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) Tool, das Sie auch als [Gespräch](https://channel9.msdn.com/events/Build/2015/3-725) ansehen können

[Mehrere Beispiele auf GitHub, die in drei Arten von Analyzern gruppiert sind.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Einführung und Tour durch einige Analyzers Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Weitere Ressourcen
[Weitere Dokumente auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Mit Roslyn-Analysen implementierte FxCop-Regeln auf GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
