---
title: .NET Compiler Platform (&quot;Roslyn&quot;) Erweiterbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de01ec4f857042c6eaaaa70632b28cfc830886cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817086"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Erweiterbarkeit der .NET-Compilerplattform (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Kernaufgabe von der .NET Compiler Platform ("Roslyn") öffnen Sie die C#- und Visual Basic-Compiler und Tools ermöglichen, und Entwickler in den Compilern umfassende Informationen gemeinsam nutzen müssen Informationen zu Programmen. Tool zur Codeanalyse Verbessern der Codequalität, und code-Generatoren Hilfsmittel bei der Erstellung der Anwendung. Intelligentere Tools erhalten müssen sie Zugriff auf Weitere deep Code wissen, die nur von Compilern besitzen. Anstatt von nicht transparenten Übersetzer (Quellcode und Objektcode out) bieten die Roslyn-Compiler-APIs, die Sie für Aufgaben im Zusammenhang mit Code in Ihren Tools und Anwendungen verwenden können.  
  
 Das beste daran ist, dass die Roslyn-Compiler, ihre APIs, Beispiele und exemplarische Vorgehensweisen und die echten Tools baut auf den diese APIs sind alle vollständig quelloffen auf [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Wechseln Sie zu der OSS-Website, um weitere Informationen und erste Schritte mit Roslyn. Sie werden feststellen, Links, um die neueste c# und VB-Features, mit denen Sie als Endbenutzer zu erhalten sowie Links zu als ein Tool-Generator nutzt die Roslyn-APIs beginnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit Roslyn-Analyzern](../extensibility/getting-started-with-roslyn-analyzers.md)

