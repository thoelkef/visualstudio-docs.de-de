---
title: Architektur der Ausdrucksauswertung | Microsoft-Dokumentation
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
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efb48fdc65fbc8d815c77f6e51e65312d9c93e0d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514904"
---
# <a name="expression-evaluator-architecture"></a>Architektur der Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Architektur der Ausdrucksauswertung](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator-architecture).  
  
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrieren von eine proprietäre Sprache in der Visual Studio-Paket Debuggen bedeutet, dass die erforderlichen Expression Evaluator (EE)-Schnittstellen implementieren und aufrufen, die common Language Run-Time-Symbol-Dienstanbieter (SP) und den Binder-Schnittstellen. Die SP und Binder-Objekte zusammen mit der aktuellen Adresse für die Ausführung stehen für Kontext in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen zu erzeugen und nutzen, stellt die wichtigsten Konzepte in der Architektur eine EE dar.  
  
## <a name="overview"></a>Übersicht  
  
### <a name="parsing-the-expression"></a>Analysieren des Ausdrucks  
 Wenn Sie ein Programm debuggen, werden Ausdrücke ausgewertet, für eine Reihe von Gründen aber immer wenn die zu debuggende Programm wird an einem Haltepunkt (entweder ein Haltepunkt eingefügt, die vom Benutzer oder eine durch eine Ausnahme verursacht hat) wurde beendet. Es ist zu diesem Zeitpunkt an, wenn Visual Studio einen Stapelrahmen erhält, dargestellt durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, von der Debug-Engine (DE). Visual Studio ruft dann [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstelle stellt einen Kontext, in dem Ausdrücke ausgewertet werden können; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ist der Einstiegspunkt für den Prozess der Evaluierung. Bis zu diesem Punkt werden alle Schnittstellen durch die DE implementiert.  
  
 Wenn `IDebugExpressionContext2::ParseText` wird aufgerufen, die DE instanziiert die EE verknüpft ist, mit der Sprache der Quelldatei, in der Haltepunkt aufgetreten ist (die DE instanziiert außerdem die SH an diesem Punkt). Die EE wird dargestellt, durch die [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle. Ruft die DE dann [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Konvertieren des Ausdrucks (in Textform) in einer analysierten Ausdruck bereit, für die Evaluierung. Durch diese analysierten Ausdruck dargestellt wird die [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Beachten Sie, dass der Ausdruck ist in der Regel analysiert und an diesem Punkt nicht ausgewertet.  
  
 Die DE erstellt ein Objekt, das implementiert die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, setzt der `IDebugParsedExpression` -Objekt in der `IDebugExpression2` -Objekt und gibt die `IDebugExpression2` -Objekt aus `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Auswertung des Ausdrucks  
 Visual Studio ruft entweder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) zum Auswerten des analysierten Ausdrucks. Beide Methoden rufen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` Ruft die Methode sofort beendet, während er sich `IDebugExpression2::EvaluateAsync` Ruft die Methode über einen Hintergrundthread) zu den analysierten Ausdruck ausgewertet und zurückgegeben ein [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die den Wert und Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync` verwendet die angegebene SH, Adresse und den Binder zu den analysierten Ausdruck in einen tatsächlichen Wert, dargestellt durch Konvertieren der `IDebugProperty2` Schnittstelle.  
  
### <a name="for-example"></a>Zum Beispiel  
 Nach dem in ein ausgeführtes Programm ein Haltepunkt erreicht wird, wählt des Benutzers an eine Variable in der **Schnellüberwachung** Dialogfeld. Dieses Dialogfeld zeigt den Namen der Variablen, dessen Wert und den Typ an. Der Benutzer kann den Wert in der Regel ändern.  
  
 Wenn die **Schnellüberwachung** Dialogfeld wird angezeigt, der Namen der Variablen, die überprüft wird, wird als Text, der gesendet [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Dies gibt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt, das in diesem Fall den analysierten Ausdruck darstellt, die Variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird aufgerufen, um das Erstellen einer `IDebugProperty2` Objekt, das den Wert der Variable und Typ sowie den Namen darstellt. Es ist diese Informationen, die angezeigt wird.  
  
 Wenn der Benutzer den Wert der Variablen, ändert [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) wird aufgerufen, mit dem neuen Wert, der den Wert der Variablen im Speicher ändert, damit es verwendet wird, wenn das Programm fortgesetzt wird ausgeführt.  
  
 Finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) für Weitere Informationen zu diesem Prozess die Werte der Variablen anzuzeigen. Finden Sie unter [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md) Weitere Einzelheiten, wie der Wert einer Variablen geändert wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Übergibt die Argumente, die übergeben werden, wenn die DE die EE aufruft.  
  
 [Wichtige Schnittstellen für die Ausdrucksauswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Beschreibt die wichtigen Schnittstellen erforderlich, wenn ein EE, zusammen mit den Auswertungskontext zu schreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)

