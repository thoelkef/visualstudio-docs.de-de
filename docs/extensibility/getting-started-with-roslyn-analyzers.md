---
title: Erste Schritte mit Roslyn Analyzern | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711273"
---
# <a name="get-started-with-roslyn-analyzers"></a>Erste Schritte mit Roslyn-Analysatoren

Mit Live-, projektbasierten Codeanalysatoren in Visual Studio können API-Autoren domänenspezifische Codeanalysen als Teil ihrer NuGet-Pakete versenden. Da diese Analysatoren von der .NET Compiler Platform (Codename "Roslyn") unterstützt werden, können sie Warnungen in Ihrem Code erzeugen, während Sie die Zeile eingeben, noch bevor Sie die Zeile beendet haben (keine Wartezeiten mehr auf den Erstellen des Codes, um Probleme zu beheben). Analyzer können auch eine automatische Codekorrektur über die Visual Studio-Glühbirnesaufforderung aufstellen, damit Sie den Code sofort bereinigen können.

## <a name="get-started"></a>Erste Schritte

[Roslyn-Analysatoren im Überblick](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Schreiben Ihres ersten Analysetools und Codefixes](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Hinzufügen von Codefixes Walkthrough: Bereitstellen von Benutzerkorrekturen für Analyseprobleme](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Real World Roslyn Analyzer,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) den Sie auch als [Vortrag](https://channel9.msdn.com/events/Build/2015/3-725) sehen können

[Mehrere Beispiele auf GitHub, gruppiert in drei Arten von Analysatoren](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Weitere Informationen

- [.NET Compilerplattformpaketversionsreferenz](roslyn-version-support.md)
- [Weitere Dokumente auf der GitHub OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [FxCop-Regeln mit Roslyn-Analysatoren implementiert](../code-quality/fxcop-rule-port-status.md)
