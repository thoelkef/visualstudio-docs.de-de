---
title: "Schlüssel Expression Evaluator Schnittstellen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1e0d655f18ec7ec50dffa52e3ac4ce363fb02fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="key-expression-evaluator-interfaces"></a>Schlüsselausdruck Evaluator-Schnittstellen
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn Sie eine ausdrucksauswertung (EE), zusammen mit den Auswertungskontext zu schreiben, sollten Sie die folgenden Schnittstellen vertraut sein.  
  
## <a name="interface-descriptions"></a>Schnittstellenbeschreibungen  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Verfügt über eine einzelne Methode [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), die einer Datenstruktur Ruft den aktuellen Zeitpunkt der Ausführung darstellt. Diese Datenstruktur ist eines der drei Argumente, die an die Debugging-Modul (DE) übergibt die [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Methode zum Auswerten eines Ausdrucks. Diese Schnittstelle wird normalerweise von der Symbol-Anbieter implementiert.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Hat die [binden](../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode, die den Speicherbereich abruft, die den aktuellen Wert eines Symbols enthält. Sowohl der enthaltenden Methode, dargestellt durch eine [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt und dem Symbol selbst, dargestellt durch eine [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt `IDebugBinder::Bind` gibt den Wert des Symbols zurück. `IDebugBinder`wird normalerweise von der DE implementiert.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Stellt einen einfachen Datentyp dar. Verwenden Sie für komplexe Typen, z. B. Arrays und Methoden, die abgeleitete [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) und [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) bzw. Schnittstellen. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) ist eine andere wichtige abgeleitete Schnittstelle, Symbole, die mit anderen Symbolen, z. B. Methoden oder Klassen darstellt. Die `IDebugField` -Schnittstelle (und die Ableitung) werden in der Regel von der Symbol-Anbieter implementiert.  
  
     Ein `IDebugField` Objekt kann sein, um den Namen und den Typ eines Symbols zu finden und verwendet, zusammen mit einem [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Objekt, kann verwendet werden, um seinen Wert zu ermitteln.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Stellt die tatsächliche Bits des Werts eines Symbols zur Laufzeit dar. [Binden](../../extensibility/debugger/reference/idebugbinder-bind.md) akzeptiert ein [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt, das ein Symbol dargestellt, und gibt eine [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt. Die [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) -Methode gibt den Wert des Symbols in einem Puffer. Ein DE implementiert in der Regel diese Schnittstelle, um die Darstellung des Werts einer Eigenschaft im Arbeitsspeicher.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Diese Schnittstelle stellt die ausdrucksauswertung selbst dar. Ist die Hauptmethode [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), welche gibt eine [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Diese Schnittstelle stellt einen analysierten Ausdruck zur Auswertung bereiter dar. Ist die Hauptmethode [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) welche gibt ein IDebugProperty2, die den Wert und Typ des Ausdrucks darstellt.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Diese Schnittstelle stellt einen Wert und dessen Typ dar und ist das Ergebnis der Auswertung von Ausdrücken.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)