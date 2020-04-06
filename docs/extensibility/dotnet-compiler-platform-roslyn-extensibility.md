---
title: .NET Compilerplattform&quot;(&quot;Roslyn ) Erweiterbarkeit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712079"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler&quot;Platform (&quot;Roslyn ) Erweiterbarkeit
Die Kernaufgabe der .NET Compiler Platform ("Roslyn") besteht darin, die Compiler von C- und Visual Basic zu öffnen und Tools und Entwicklern die gemeinsame Nutzung der umfangreichen Informationen zu ermöglichen, die Compiler über Programme haben. Codeanalysetools verbessern die Codequalität, und Codegeneratoren unterstützen die Anwendungserstellung. Wenn Tools intelligenter werden, benötigen sie Zugriff auf immer mehr des tiefen Codewissens, über das nur Compiler verfügen. Anstatt undurchsichtige Übersetzer zu sein (Quellcode in und Objektcode aus), bieten die Roslyn-Compiler APIs, die Sie für codebezogene Aufgaben in Ihren Tools und Anwendungen verwenden können.

 Das Beste daran ist, dass die Roslyn-Compiler, ihre APIs, Beispiele und exemplarischen Vorgehensweisen sowie die auf diesen APIs basierenden echten Tools alle vollständig Open Source bei [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)sind. Bitte gehen Sie auf die OSS-Website, um mehr zu erfahren und beginnen Sie mit Roslyn. Sie finden Links, um die neuesten Funktionen von C- und Visual Basic zu erhalten, die Sie als Endbenutzer verwenden können, sowie Links, um als Werkzeugbauer zu beginnen, der die Roslyn-APIs nutzt.

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte mit Roslyn-Analysatoren](../extensibility/getting-started-with-roslyn-analyzers.md)
