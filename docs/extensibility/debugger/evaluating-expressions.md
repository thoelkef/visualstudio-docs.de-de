---
title: Auswerten von Ausdrücken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738830"
---
# <a name="evaluate-expressions"></a>Ausdrücken auswerten
Ausdrücke werden aus Zeichenfolgen erstellt, die aus den Fenstern **Autos**, **Watch**, **QuickWatch**oder **Immediate** übergeben werden. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen oder des Arguments und ihren Wert enthält. Diese Zeichenfolge wird im entsprechenden IDE-Fenster angezeigt.

## <a name="implementation"></a>Implementierung
 Ausdrücke werden ausgewertet, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst wird durch eine [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) dargestellt, die einen analysierten Ausdruck darstellt, der für die Bindung und Auswertung innerhalb des angegebenen Ausdrucksauswertungskontexts bereit ist. Der Stapelrahmen bestimmt den Ausdrucksauswertungskontext, den das Debugmodul (DE) durch Implementieren der [IDebugExpressionContext2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressioncontext2.md) bereitstellt.

 Bei einer Benutzerzeichenfolge und einer [IDebugExpressionContext2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressioncontext2.md) kann ein Debugmodul (DE) eine [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) abrufen, indem es die Benutzerzeichenfolge an die [IDebugExpressionContext2::ParseText-Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) übergibt. Die zurückgegebene IDebugExpression2-Schnittstelle enthält den analysierten Ausdruck, der für die Auswertung bereit ist.

 Mit `IDebugExpression2` der Schnittstelle kann die DE den Wert des Ausdrucks durch synchrone oder asynchrone Ausdrucksauswertung mithilfe von [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)abrufen. Dieser Wert wird zusammen mit dem Namen und Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet. Der Wert, der Name und der Typ werden durch eine [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) dargestellt.

 Um die Ausdrucksauswertung zu aktivieren, muss eine DE die Schnittstellen [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) implementieren. Sowohl die synchrone als auch die asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo-Methode.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Weitere Informationen
- [Stapelrahmen](../../extensibility/debugger/stack-frames.md)
- [Ausdrucksbewertungskontext](../../extensibility/debugger/expression-evaluation-context.md)
- [Debug-Aufgaben](../../extensibility/debugger/debugging-tasks.md)
