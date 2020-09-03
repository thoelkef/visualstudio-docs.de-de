---
title: .NET Compiler Platform ( &quot; Roslyn &quot; )-Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712079"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; Roslyn &quot; )-Erweiterbarkeit
Die Hauptaufgabe des .NET Compiler Platform ("Roslyn") besteht darin, die c#-und Visual Basic Compiler zu öffnen und Tools und Entwickler zu ermöglichen, die umfassenden Informationen zu Programmen zu verwenden. Code Analysetools verbessern die Codequalität, und Code-Generatoren helfen bei der Anwendungs Erstellung. Da Tools intelligenter werden, benötigen Sie Zugriff auf mehr und mehr von Deep Code-wissen, das nur Compiler besitzen. Anstatt nicht transparente Konvertierer (Quellcode in und Objektcode out) zu werden, bieten die Roslyn-Compiler APIs, die Sie für Code bezogene Aufgaben in ihren Tools und Anwendungen verwenden können.

 Der beste Teil besteht darin, dass die Roslyn-Compiler, ihre APIs, Beispiele und Exemplarische Vorgehensweisen und die echten Tools, die auf diesen APIs basieren, vollständig Open Source unter [GitHub.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn)sind. Besuchen Sie die OSS-Website, um weitere Informationen zu erhalten, und beginnen Sie mit Roslyn. Links zum Abrufen der neuesten c#-und Visual Basic Features, die Sie als Endbenutzer verwenden können, sowie Links zu den ersten Schritten als Tool Generator, der die Roslyn-APIs nutzt.

## <a name="see-also"></a>Siehe auch
- [Einstieg in Roslyn-Analysen](../extensibility/getting-started-with-roslyn-analyzers.md)
