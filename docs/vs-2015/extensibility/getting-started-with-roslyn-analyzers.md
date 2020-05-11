---
title: Erste Schritte mit Roslyn Analyzern | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444979"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Erste Schritte mit Roslyn-Analyzern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Live-, projektbasierten Codeanalysatoren in Visual Studio können API-Autoren domänenspezifische Codeanalysen als Teil ihrer NuGet-Pakete versenden.  Da diese Analysatoren von der .NET Compiler Platform (Codename "Roslyn") unterstützt werden, können sie Warnungen in Ihrem Code erzeugen, während Sie die Zeile eingeben, noch bevor Sie die Zeile beendet haben (keine Wartezeiten mehr auf den Erstellen des Codes, um Probleme zu beheben).  Analysatoren können auch eine automatische Codekorrektur über die Visual Studio-Glühbirnesaufforderung erstellen, damit Sie den Code sofort bereinigen können.

## <a name="getting-started"></a>Erste Schritte
[Roslyn Live Code Analyzers Einführung und exemplarische Vorgehensweise](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Hinzufügen von Codefixes Walkthrough: Bereitstellen von Benutzerkorrekturen für Analyzer-Probleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Einführung und Exemplarung von Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) den Sie auch als [Vortrag](https://channel9.msdn.com/events/Build/2015/3-725) sehen können

[Mehrere Beispiele auf GitHub, gruppiert in drei Arten von Analysatoren](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Einführung und Tour of a Few Analyzers Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Weitere Ressourcen
[Weitere Dokumente auf der GitHub OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[FxCop-Regeln mit Roslyn-Analysatoren auf GitHub implementiert](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
