---
title: .NET Compiler Platform (&quot;Roslyn&quot;) Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26196b18c6e44ec8f0697fbc656f2934eff1904b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918809"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform (&quot;Roslyn&quot;) Erweiterbarkeit
Der Kernaufgabe von der .NET Compiler Platform ("Roslyn") öffnen Sie die C#- und Visual Basic-Compiler und Tools ermöglichen, und Entwickler in den Compilern umfassende Informationen gemeinsam nutzen müssen Informationen zu Programmen. Tool zur Codeanalyse Verbessern der Codequalität, und code-Generatoren Hilfsmittel bei der Erstellung der Anwendung. Intelligentere Tools erhalten müssen sie Zugriff auf Weitere deep Code wissen, die nur von Compilern besitzen. Anstatt von nicht transparenten Übersetzer (Quellcode und Objektcode out) bieten die Roslyn-Compiler-APIs, die Sie für Aufgaben im Zusammenhang mit Code in Ihren Tools und Anwendungen verwenden können.

 Das beste daran ist, dass die Roslyn-Compiler, ihre APIs, Beispiele und exemplarische Vorgehensweisen und die echten Tools baut auf den diese APIs sind alle vollständig quelloffen auf [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Wechseln Sie zu der OSS-Website, um weitere Informationen und erste Schritte mit Roslyn. Sehen Sie Links auf die neueste Version anzuzeigen C# und Visual Basic-Features, mit denen Sie als ein Endbenutzer als auch Links können als ein Tool-Generator nutzt die Roslyn-APIs beginnen.

## <a name="see-also"></a>Siehe auch
 [Erste Schritte mit Roslyn-Analysetools](../extensibility/getting-started-with-roslyn-analyzers.md)