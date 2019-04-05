---
title: Auswerten von Ausdrücken | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946164"
---
# <a name="evaluating-expressions"></a>Auswerten von Ausdrücken
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ausdrücke werden von Zeichenfolgen, die von der "Auto", sehen Sie sich, Schnellüberwachung oder direkt übergeben erstellt. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen "oder" Argument "und" den Wert enthält. Diese Zeichenfolge wird in den zugehörigen IDE-Fenster angezeigt.  
  
## <a name="implementation"></a>Implementierung  
 Ausdrücke werden ausgewertet, wenn ein Programm an einem Haltepunkt beendet wurde. Der Ausdruck selbst wird durch dargestellt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die einen analysierten Ausdruck darstellt, die für die Bindung und der Auswertung innerhalb des Kontexts des angegebenen Ausdrucks Auswertung bereit ist. Bestimmt Kontexts für die ausdrucksauswertung, die die Debug-Engine (DE) durch die Implementierung bereitstellt, der Stapelrahmen der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.  
  
 Erhalten eine Benutzerzeichenfolge und ein [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle, eine Debug-Engine (DE) erhalten eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, übergeben Sie die Benutzerzeichenfolge, die die [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode. Zurückgegebene Schnittstelle IDebugExpression2 enthält den analysierten Ausdruck, der zur Evaluierung bereit.  
  
 Mit der `IDebugExpression2` -Schnittstelle, die DE erhalten den Wert des Ausdrucks durch synchrone oder asynchrone ausdrucksauswertung mit [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Dieser Wert zusammen mit dem Namen und Typ der Variablen oder des Arguments, wird für die Anzeige der IDE gesendet. Der Wert, Name und Typ werden durch dargestellt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
 Um die Auswertung des Ausdrucks zu aktivieren, muss eine bereitgestellten Kompatibilitätsrichtlinie implementieren die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstellen. Synchrone und asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
