---
title: Common Language Runtime und Ausdrucksauswertung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739114"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime und Ausdrucksauswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Compiler, wie z. B. Visual Basic und C-Sharp, die auf die Common Language Runtime (CLR) abzielen, erzeugen Microsoft Intermediate Language (MSIL), das später in systemeigenem Code kompiliert wird. Die CLR stellt ein Debugmodul (DE) bereit, um den resultierenden Code zu debuggen. Wenn Sie Ihre proprietäre Programmiersprache in die Visual Studio-IDE integrieren möchten, können Sie die Kompilierung in MSIL auswählen und müssen daher keine eigene DE schreiben. Sie müssen jedoch einen Ausdrucksevaluator (EE) schreiben, der in der Lage ist, Ausdrücke im Kontext Ihrer Programmiersprache auszuwerten.

## <a name="discussion"></a>Diskussion
 Computersprachausdrücke werden im Allgemeinen analysiert, um eine Reihe von Datenobjekten und eine Reihe von Operatoren zu erzeugen, die zum Bearbeiten verwendet werden. Beispielsweise kann der Ausdruck "A+B" analysiert werden, um den Additionsoperator (+) auf die Datenobjekte "A" und "B" anzuwenden, was möglicherweise zu einem anderen Datenobjekt führt. Der gesamte Satz von Datenobjekten, Operatoren und deren Zuordnungen werden in einem Programm am häufigsten als Struktur dargestellt, wobei die Operatoren an den Knoten der Struktur und die Datenobjekte an den Zweigen angezeigt werden. Ein Ausdruck, der in Baumform unterteilt wurde, wird häufig als analysierter Baum bezeichnet.

 Nachdem ein Ausdruck analysiert wurde, wird ein Symbolanbieter (SP) aufgerufen, um jedes Datenobjekt auszuwerten. Wenn z. B. "A" in mehr als einer Methode definiert ist, lautet die Frage "Welches A?" muss beantwortet werden, bevor der Wert von A festgestellt werden kann. Die Antwort, die vom SP zurückgegeben wird, ist so etwas wie "Das dritte Element auf dem fünften Stapelrahmen" oder "Das A, das 50 Byte über dem Anfang des statischen Speichers liegt, der dieser Methode zugewiesen ist."

 Neben der Erstellung von MSIL für das Programm selbst können CLR-Compiler auch sehr beschreibende Debugging-Informationen erzeugen, die in eine Program DataBase -*.pdb*) Datei geschrieben werden. Solange ein proprietärer Compiler Debuginformationen im gleichen Format wie die CLR-Compiler erstellt, ist der CLR-SP in der Lage, die benannten Datenobjekte dieser Sprache zu identifizieren. Nachdem ein benanntes Datenobjekt identifiziert wurde, verwendet der EE ein Binderobjekt, um das Datenobjekt dem Speicherbereich zuzuordnen (oder zu binden), der den Wert dieses Objekts enthält. Die DE kann dann einen neuen Wert für das Datenobjekt abrufen oder festlegen.

 Ein proprietärer Compiler kann CLR-Debuginformationen bereitstellen, indem er die `ISymbolWriter` Schnittstelle aufruft (die im .NET Framework im Namespace `System.Diagnostics.SymbolStore`definiert ist). Durch das Kompilieren in MSIL und das Schreiben von Debuginformationen über diese Schnittstellen kann ein proprietärer Compiler DIE CLR DE und SP verwenden. Dies vereinfacht die Integration einer proprietären Sprache in die Visual Studio-IDE erheblich.

 Wenn die CLR DE den proprietären EE aufruft, um einen Ausdruck auszuwerten, stellt die DE dem EE Schnittstellen zu einem SP und einem Binderobjekt bereit. Das Schreiben eines CLR-basierten Debugmoduls bedeutet daher, dass nur die entsprechenden Expression evaluator-Schnittstellen implementiert werden müssen. Die CLR kümmert sich um die Bindung und die Symbolhandhabung für Sie.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
