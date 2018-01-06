---
title: "Auswerten eines Fenster Überwachungsausdrucks | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb109fd91e4c295bf372b14e26bc2a75c3be6b1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-a-watch-window-expression"></a>Bewerten einen Überwachungsausdruck-Fenster
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn die Ausführung angehalten wird, ruft Visual Studio Debugging-Modul (DE) zum Bestimmen des aktuellen Werts jedes Ausdrucks in der Überwachungsliste. Die DE wertet jeden Ausdruck, der über eine ausdrucksauswertung (EE) und Visual Studio zeigt an, dessen Wert in der **Überwachen** Fenster.  
  
 Hier wird eine Übersicht darüber, wie ein Liste Überwachungsausdruck ausgewertet wird:  
  
1.  Visual Studio aufgerufen werden, die DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ein Ausdruckskontext abgerufen, die zum Auswerten von Ausdrücken verwendet werden kann.  
  
2.  Für jeden Ausdruck in der Überwachungsübersicht, ruft Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) den Text des Ausdrucks in einer analysierten Ausdrucks zu konvertieren.  
  
3.  `IDebugExpressionContext2::ParseText`Aufrufe [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , führen Sie die eigentliche Arbeit des Analysieren von Text und erzeugen eine [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
4.  `IDebugExpressionContext2::ParseText`erstellt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt und setzt die `IDebugParsedExpression` -Objekts hinein. Diese ich`DebugExpression2` Objekt dann an Visual Studio zurückgegeben wird.  
  
5.  Visual Studio-Aufrufe [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Auswerten des analysierten Ausdrucks.  
  
6.  `IDebugExpression2::EvaluateSync`übergibt den Aufruf von [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) erstellen und führen Sie die tatsächliche Auswertung ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) zu Visual Studio zurückgegebene Objekt.  
  
7.  Visual Studio-Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) um den Wert des Ausdrucks abzurufen, die dann in der Überwachungsübersicht angezeigt werden.  
  
## <a name="parse-then-evaluate"></a>Analysieren und bewerten  
 Da Analyse einen komplexen Ausdruck wesentlich länger als das Auswerten von es dauern kann, der Prozess der Auswertung eines Ausdrucks ist unterteilt in zwei Schritte: (1) Analysieren des Ausdrucks und (2) den analysierten Ausdruck auswerten. Auf diese Weise kann Auswertung viele Male vorkommen, aber der Ausdruck muss nur einmal analysiert werden. Intermediate analysierten Ausdrucks wird zurückgegeben, aus der AA in ein [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt, das wiederum gekapselt und zurückgegeben, aus dem DE als ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt. Die `IDebugExpression` Objekt orientiert sich auf alle Auswertung der `IDebugParsedExpression` Objekt.  
  
> [!NOTE]
>  Es ist nicht erforderlich für ein EE zu diesen Schritten folgen, obwohl Visual Studio Hierbei wird angenommen; die EE analysieren und bewerten, im gleichen Schritt kann bei [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) aufgerufen wird (Dies ist das Beispiel MyCEE, z. B. Funktionsweise). Wenn Ihre Sprache komplexe Ausdrücke bilden kann, empfiehlt es sich, die Analyse Schritt von der bewertungsschritt zu trennen. Dies kann die Leistung in Visual Studio-Debugger verbessern, wenn viele Ausdrücke zu beobachten sind dargestellt wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beispielimplementierung der Ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Im MyCEE-Beispiel verwendet, um den Prozess der Auswertung von Ausdrücken zu durchlaufen.  
  
 [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Erläutert, was geschieht, nachdem ein Ausdruck erfolgreich analysiert.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente, die übergeben werden, wenn die Debugging-Modul (DE) die ausdrucksauswertung (EE) aufruft.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)