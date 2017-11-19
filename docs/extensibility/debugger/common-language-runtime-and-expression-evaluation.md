---
title: "Common Language Runtime und Auswertung von Ausdrücken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba9a9a6b406ad5a94cced7820e6b4581db56eb2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime und Auswertung von Ausdrücken
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiler, kompiliert wie z. B. Visual Basic und c# (ausgesprochen C-Sharp), die die Common Language Runtime (CLR) abzielen, Microsoft Intermediate Language (MSIL), erzeugen die höher ist in nativen Code. Die CLR bietet eine Debugging-Modul (DE), um die resultierende Code zu debuggen. Wenn Sie beabsichtigen, Ihre eigene Programmiersprache in Visual Studio-IDE integrieren, können Sie in MSIL kompiliert und daher werden keine eigene DE schreiben. Allerdings müssen Sie eine ausdrucksauswertung (EE) schreiben, die der Auswertung von Ausdrücken innerhalb des Kontexts der Programmiersprache entspricht.  
  
## <a name="discussion"></a>Diskussion  
 Computer-Sprachausdrücke sind im Allgemeinen analysiert, um erzeugen einen Satz von Datenobjekten und eine Reihe von Operatoren verwendet, um sie zu bearbeiten. Objekte z. B. der Ausdruck, der "A + B" möglicherweise zum Anwenden von des Additionsoperators (+) auf die Daten analysiert werden, "A" und "B", was zu einem anderen Datenobjekt. Gesamtsatz Datenobjekte, Operatoren und ihre Zuordnungen werden am häufigsten in einem Programm als eine Struktur, die Operatoren auf den Knoten der Struktur und die Datenobjekte an die Verzweigungen dargestellt. Ein Ausdruck, der in Strukturansicht unterteilt wurde wird eine analysierte Struktur häufig aufgerufen werden.  
  
 Nachdem ein Ausdruck analysiert wurde, wird ein Symbol-Anbieter (SP) aufgerufen, um jedes Datenobjekt auswerten. Angenommen, wenn "A" definiert ist, sowohl in mehr als eine Methode, und klicken Sie dann auf die Frage "Welches A?" müssen beantwortet werden, bevor der Wert von A ermittelt werden kann. Die Antwort des SP ist z.B. "Das dritte Element im fünften Stapelrahmen" oder "A, die 50 Byte nach dem Start des statischen Arbeitsspeichers sind für diese Methode zugeordnet."  
  
 Neben dem, der für das Programm selbst MSIL erzeugt, können CLR-Compiler auch sehr aussagekräftig Debuginformationen zu erzeugen, die in eine Programmdatenbank (PDB-Format)-Datei geschrieben wird. Solange ein proprietäre Sprache-Compiler Debuginformationen in das gleiche Format wie die CLR-Compiler erzeugt, ist die CLR-SP zu erkennen, dass der Sprache Datenobjekte Namens. Nach einem benannten Datenobjekt identifiziert wurde, verwendet die EE ein binderobjekt das Datenobjekt zuordnen (oder Binden), um den Speicherbereich, der den Wert für dieses Objekt enthält. Die DE kann dann abrufen oder einen neuen Wert für das Datenobjekt festlegen.  
  
 Ein proprietärer Compiler bieten CLR Debuginformationen durch Aufrufen der `ISymbolWriter` Schnittstelle (in .NET Framework im Namespace definiert sind `System.Diagnostics.SymbolStore`). Kompilieren in MSIL und Schreiben von Debuginformationen über diese Schnittstellen, kann einen proprietärer Compiler der CLR-Code und SP verwenden. Dies vereinfacht eine proprietäre Sprache in Visual Studio-IDE integrieren.  
  
 Wenn die CLR-DE zum Auswerten eines Ausdrucks der proprietäre EE aufruft, stellt die DE die EE mit Schnittstellen ein SP und ein binderobjekt bereit. Folglich besteht im Schreiben von einer CLR-basierten Debug-Modul bedeutet, dass es nur notwendig, um die entsprechenden Ausdruck Evaluator-Schnittstellen implementieren; die CLR übernimmt die Bindung und dem Symbol, das Sie behandeln.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)