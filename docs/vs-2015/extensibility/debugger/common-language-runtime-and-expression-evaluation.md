---
title: Common Language Runtime und Ausdrucks Auswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b75cb1b0604f3611c0e51c6f458939433d2a5470
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841238"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime und Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiler, wie z. b. Visual Basic und c# (ausgesprochen C-Sharp), die auf die Common Language Runtime (CLR) abzielen, erzeugen eine Microsoft Intermediate Language (MSIL), die später in nativem Code kompiliert wird. Die CLR stellt eine Debug-Engine (de) zum Debuggen des resultierenden Codes bereit. Wenn Sie beabsichtigen, ihre proprietäre Programmiersprache in die Visual Studio-IDE zu integrieren, können Sie die Kompilierung in MSIL durchführt, sodass Sie keine eigene de schreiben müssen. Sie müssen jedoch eine Ausdrucks Auswertung (EE) schreiben, mit der Ausdrücke im Kontext der Programmiersprache ausgewertet werden können.  
  
## <a name="discussion"></a>Diskussion (Discussion)  
 Computer sprach Ausdrücke werden in der Regel analysiert, um einen Satz von Datenobjekten und eine Reihe von Operatoren zu entwickeln, die zur Bearbeitung verwendet werden. Beispielsweise kann der Ausdruck "a + B" analysiert werden, um den Additions Operator (+) auf die Datenobjekte "a" und "B" anzuwenden, was möglicherweise zu einem anderen Datenobjekt führt. Der gesamte Satz von Datenobjekten, Operatoren und deren Zuordnungen wird am häufigsten in einem Programm als Struktur dargestellt, mit den Operatoren an den Knoten der Struktur und den Datenobjekten in den Verzweigungen. Ein Ausdruck, der in die Struktur Form aufgeteilt wurde, wird häufig als analysierte Struktur bezeichnet.  
  
 Nachdem ein Ausdruck analysiert wurde, wird ein Symbol Anbieter (SP) aufgerufen, um die einzelnen Datenobjekte auszuwerten. Wenn z. b. "A" sowohl in mehr als einer Methode definiert ist, dann wird die Frage "What A?" muss beantwortet werden, bevor der Wert eines ermittelt werden kann. Die Antwort, die vom SP zurückgegeben wird, ist etwa "das dritte Element im fünften Stapel Rahmen" oder "die A, die nach dem Anfang des statischen Speichers, der dieser Methode zugeordnet ist, 50 Bytes überschreitet."  
  
 Neben der Erstellung von MSIL für das Programm selbst können CLR-Compiler auch sehr beschreibende Debuginformationen erzeugen, die in eine Programm Datenbankdatei (. pdb) geschrieben werden. Solange ein Compiler einer proprietären Sprache Debuginformationen im gleichen Format wie die CLR-Compiler erstellt, kann der CLR-SP die benannten Datenobjekte dieser Sprache identifizieren. Nachdem ein benanntes Datenobjekt identifiziert wurde, verwendet das EE ein Binder Objekt, um das Datenobjekt dem Speicherbereich zuzuordnen (oder zu binden), der den Wert dieses Objekts enthält. Der de kann dann einen neuen Wert für das Datenobjekt erhalten oder festlegen.  
  
 Proprietäre Compiler können CLR-Debuginformationen bereitstellen, indem Sie die- `ISymbolWriter` Schnittstelle aufrufen (die im-.NET Framework im-Namespace definiert ist `System.Diagnostics.SymbolStore` ). Durch Kompilieren in MSIL und Schreiben von Debuginformationen über diese Schnittstellen kann ein proprietärer Compiler die CLR de und SP verwenden. Dies vereinfacht die Integration einer proprietären Sprache in die Visual Studio-IDE erheblich.  
  
 Wenn die CLR de den proprietären EE aufruft, um einen Ausdruck auszuwerten, stellt der de den EE mit Schnittstellen an einen SP-und ein Binder Objekt bereit. Daher bedeutet das Schreiben einer CLR-basierten Debug-Engine, dass nur die entsprechenden Ausdrucks auswerterschnittstellen implementiert werden müssen. die CLR kümmert sich um die Bindung und die Symbol Behandlung für Sie.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
