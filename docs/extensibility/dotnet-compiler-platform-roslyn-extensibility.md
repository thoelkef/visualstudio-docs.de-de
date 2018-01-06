---
title: .NET Compiler Platform (&quot;Roslyn&quot;) Erweiterbarkeit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b292593c6a6c426bb184acd67a920b5e76e3a51f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform (&quot;Roslyn&quot;) Erweiterbarkeit
Core Mission von .NET Compiler Platform ("Roslyn") ist die C#- und Visual Basic-Compiler öffne und Tools ermöglichen und Entwicklern zur Freigabe in den Compilern umfassende Informationen zu Programmen haben. Codeanalysetools Verbessern der Codequalität und code-Generatoren, die bei der anwendungskonstruktion Ursachenanalyse. Wie Tools intelligentere erhalten, müssen Zugriff auf mehr und mehr Kenntnisse besitzen nur Compiler Tiefe Code. Anstatt deckend Übersetzer (im Quellcode und Objektcode out) bieten die Roslyn-Compiler-APIs, die Sie für Aufgaben im Zusammenhang mit dem Code in die Tools und Anwendungen verwenden können.  
  
 Das beste daran ist, dass die Roslyn-Compiler, zugehörigen APIs, Beispiele und exemplarische Vorgehensweisen und die tatsächlichen Tools baut auf den diese APIs vollständig open-Source am sind [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Wechseln Sie zur OSS-Website, um weitere Informationen und erste Schritte mit Roslyn. Sie werden feststellen, Links zum Abrufen der neuesten c# und VB-Funktionen, die Sie als Endbenutzer verwenden können, sowie Links zu als einen Generator für ein Tool durch die Nutzung der Roslyn-APIs beginnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit Roslyn-Analyzern](../extensibility/getting-started-with-roslyn-analyzers.md)