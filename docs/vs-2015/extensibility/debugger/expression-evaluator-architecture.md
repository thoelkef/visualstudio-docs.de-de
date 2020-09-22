---
title: Architektur der Ausdrucks Auswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0aa8f5cc45e0f6e012ecb3f0a27a22725a259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841049"
---
# <a name="expression-evaluator-architecture"></a>Architektur der Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Das Integrieren einer proprietären Sprache in das Visual Studio-Debugpaket bedeutet, dass die erforderlichen Schnittstellen der Ausdrucks Auswertung (EE) implementiert und die Schnittstellen der Common Language Run-Time Symbol Provider (SP) und Binder aufgerufen werden. Die SP-und Binder Objekte sind zusammen mit der aktuellen Ausführungs Adresse der Kontext, in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen erzeugen und nutzen, stellen die Schlüsselkonzepte in der Architektur eines EE dar.  
  
## <a name="overview"></a>Übersicht  
  
### <a name="parsing-the-expression"></a>Der Ausdruck wird ausgewertet.  
 Wenn Sie ein Programm debuggen, werden Ausdrücke aus einer Reihe von Gründen ausgewertet, aber immer dann, wenn das Programm, das gedebuggt wird, an einem Haltepunkt angehalten wurde (entweder ein Haltepunkt, der vom Benutzer platziert wurde, oder der durch eine Ausnahme verursachte). Zu diesem Zeitpunkt erhält Visual Studio einen Stapel Rahmen, der durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle dargestellt wird, von der Debug-Engine (de). In Visual Studio wird dann [getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aufgerufen, um die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle zu erhalten. Diese Schnittstelle stellt einen Kontext dar, in dem Ausdrücke ausgewertet werden können. " [Parametertext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " ist der Einstiegspunkt des Evaluierungsprozesses. Bis zu diesem Punkt werden alle Schnittstellen von de implementiert.  
  
 Wenn `IDebugExpressionContext2::ParseText` aufgerufen wird, instanziiert der "de" den EE, der der Sprache der Quelldatei zugeordnet ist, in der der Breakpoint aufgetreten ist (der "de" instanziiert ebenfalls die sh an dieser Stelle). Der EE wird durch die [idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) -Schnittstelle dargestellt. Das de-Element [ruft dann](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) die Analyse auf, um den Ausdruck (in Textform) in einen analysierten Ausdruck zu konvertieren, der für die Auswertung bereit ist. Dieser analysierte Ausdruck wird durch die [idebugparameterdexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Schnittstelle dargestellt. Beachten Sie, dass der Ausdruck in der Regel analysiert und zu diesem Zeitpunkt nicht ausgewertet wird.  
  
 Die de erstellt ein Objekt, das die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle implementiert, das- `IDebugParsedExpression` Objekt in das `IDebugExpression2` -Objekt einfügt und das- `IDebugExpression2` Objekt von zurückgibt `IDebugExpressionContext2::ParseText` .  
  
### <a name="evaluating-the-expression"></a>Auswerten des Ausdrucks  
 Visual Studio ruft entweder [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den analysierten Ausdruck auszuwerten. Beide Methoden rufen [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) `IDebugExpression2::EvaluateSync` auf (Ruft die-Methode sofort auf, während `IDebugExpression2::EvaluateAsync` die-Methode über einen Hintergrund Thread aufruft), um den analysierten Ausdruck auszuwerten und eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurückzugeben, die den Wert und den Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync` verwendet die angegebene sh, address und Binder, um den analysierten Ausdruck in einen tatsächlichen Wert zu konvertieren, der durch die- `IDebugProperty2` Schnittstelle dargestellt wird.  
  
### <a name="for-example"></a>Zum Beispiel  
 Nachdem ein Haltepunkt in einem laufenden Programm gedrückt wurde, wählt der Benutzer eine Variable im Dialogfeld **schnell Überwachung** aus. In diesem Dialogfeld werden der Name, der Wert und der Typ der Variablen angezeigt. Der Benutzer kann in der Regel den Wert ändern.  
  
 Wenn das Dialogfeld **schnell Überwachung** angezeigt wird, wird der Name der Variablen, die untersucht wird, als Text an "Parametertext" gesendet. [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Dies gibt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zurück, das den analysierten Ausdruck darstellt, in diesem Fall die-Variable. [Evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird dann aufgerufen, um ein Objekt zu schaffen, `IDebugProperty2` das den Wert und Typ der Variablen sowie den Namen der Variablen darstellt. Diese Informationen werden angezeigt.  
  
 Wenn der Benutzer den Wert der Variablen ändert, wird [setvalueasstring](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) mit dem neuen Wert aufgerufen, der den Wert der Variablen im Arbeitsspeicher ändert, sodass er verwendet wird, wenn das Programm die Ausführung fortsetzt.  
  
 Weitere Informationen zu diesem Prozess der Anzeige der Werte von Variablen finden Sie unter [Anzeigen von lokalen](../../extensibility/debugger/displaying-locals.md) Variablen. Weitere Informationen zur Änderung des Werts einer Variablen finden Sie unter [Ändern des Werts einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) Variablen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Auswertungs Kontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente bereit, die beim Aufrufen von EE an den EE übermittelt werden.  
  
 [Wichtige Schnittstellen für die Ausdrucksauswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Beschreibt die entscheidenden Schnittstellen, die erforderlich sind, wenn ein EE zusammen mit dem Auswertungs Kontext geschrieben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)
