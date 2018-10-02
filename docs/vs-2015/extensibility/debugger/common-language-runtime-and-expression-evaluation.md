---
title: Common Language Runtime und Ausdrucksauswertung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e5a896609d4dc28fb3b320f6d71f0b02b705229
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512610"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime und Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Common Language Runtime und Ausdrucksauswertung](https://docs.microsoft.com/visualstudio/extensibility/debugger/common-language-runtime-and-expression-evaluation).  
  
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiler, kompiliert wie z. B. Visual Basic und c# (ausgesprochen als C-Sharp), die die Common Language Runtime (CLR) abzielen, Microsoft Intermediate Language (MSIL), erzeugt die höher ist in nativen Code. Die CLR bietet eine Debug-Engine (DE), um den sich ergebenden Code Debuggen. Wenn Sie beabsichtigen, Ihre proprietäre Programmiersprache in Visual Studio-IDE integriert, können Sie in MSIL kompiliert wird, und aus diesem Grund müssen nicht Ihren eigenen DE schreiben. Sie müssen jedoch eine ausdrucksauswertung (EE) zu schreiben, die kann der Auswertung von Ausdrücken innerhalb des Kontexts von der Programmiersprache ist.  
  
## <a name="discussion"></a>Diskussion  
 In der Regel werden Computer Sprachausdrücke analysiert, erzeugt einen Satz von Datenobjekten und einen Satz von Operatoren verwendet, um sie zu bearbeiten. Der Ausdruck, der "A + B" analysiert werden, möglicherweise um den Additionsoperator (+) gelten für die Daten z. B. Objekte, "A" und "B", was möglicherweise ein anderes Datenobjekt. Der gesamte Satz von Datenobjekten, Operatoren und ihre Zuordnungen werden meist in einem Programm dargestellt, als eine Struktur, die Operatoren an den Knoten der Struktur und die Datenobjekte an die Branches. Ein Ausdruck, der in Form der Ausdrucksbaumstruktur unterteilt wird häufig eine analysierte Struktur bezeichnet.  
  
 Sobald ein Ausdruck analysiert wurde, ein symbolanbieter (SP) aufgerufen, um die einzelnen Datenobjekte zu bewerten. Angenommen, "A" definiert ist, sowohl in mehr als eine Methode, und klicken Sie dann auf die Frage "Welche A?" müssen beantwortet werden, bevor der Wert von A überprüft werden kann. Die von der gespeicherten Prozedur zurückgegebene Antwort ähnelt den "Das dritte Element auf der fünften Stapelrahmen" oder "Das A, die 50 Bytes hinter dem Anfang des statischen Speichers ist für diese Methode zugeordnet."  
  
 Neben MSIL für das Programm selbst erstellt werden, können CLR-Compiler auch sehr aussagekräftig Debuginformationen zu erzeugen, die in einer Programmdatenbankdatei (.pdb)-Datei geschrieben wird. Solange ein proprietäre Sprache-Compiler Debuginformationen in das gleiche Format wie die CLR-Compiler generiert, kann der CLR SP erkennen, dass die Sprache die Datenobjekte mit dem Namen um. Nachdem ein benanntes Objekt identifiziert wurde, verwendet die EE ein binderobjekt zuzuordnen (oder gebunden) das Datenobjekt, das in den Arbeitsspeicherbereich, der den Wert des Objekts enthält. Die DE kann dann abrufen oder einen neuen Wert für das Datenobjekt, das festlegen.  
  
 Einen proprietären Compilers bieten ein CLR-Debuggen von Informationen durch Aufrufen der `ISymbolWriter` Schnittstelle (definiert in .NET Framework im Namespace `System.Diagnostics.SymbolStore`). Kompilieren in MSIL und beim Schreiben der Debuginformationen über diese Schnittstellen, kann einen proprietären Compilers der CLR DE und SP verwenden. Dies vereinfacht eine proprietäre Sprache in Visual Studio-IDE integrieren.  
  
 Wenn die CLR-DE zum Auswerten eines Ausdrucks den proprietäre EE aufruft, stellt die DE die EE mit Schnittstellen für einen SP und ein binderobjekt. Daher ist das Schreiben einer CLR-basierten Debug-Engine bedeutet, dass es nur notwendig, um die entsprechenden Ausdruck Evaluator-Schnittstellen implementieren; die CLR übernimmt die Bindung und das Symbol für die Sie behandeln.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

