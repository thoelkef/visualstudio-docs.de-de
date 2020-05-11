---
title: Ausdrucksauswertung (Visual Studio Debugging SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738714"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ausdrucksauswertung (Visual Studio Debugging SDK)
Während des Unterbrechungsmodus muss die IDE einfache Ausdrücke auswerten, die mehrere Programmvariablen betreffen. Um die Auswertung durchzuführen, muss das Debugmodul (DE) einen Ausdruck analysieren und auswerten, der in eines der Fenster der IDE eingegeben wurde.

 Ausdrücke werden mit der [IDebugExpressionContext2::ParseText-Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) erstellt und durch die resultierende [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) dargestellt.

 Die **IDebugExpression2-Schnittstelle** wird von der DE implementiert und ruft ihre **EvalAsync-Methode** auf, um eine [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) an die IDE zurückzugeben, um die Ergebnisse der Ausdrucksauswertung in der IDE anzuzeigen. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine Struktur zurück, die verwendet wird, um den Wert eines Ausdrucks in ein **Watch-Fenster** oder in das **Locals-Fenster** zu setzen.

 Das Debugpaket oder der Sitzungsdebug-Manager (SDM) ruft [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) auf, um eine [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) abzuerhalten, die das Ergebnis der Auswertung darstellt. `IDebugProperty2`hat Methoden, die den Namen, den Typ und den Wert des Ausdrucks zurückgeben. Diese Informationen werden in verschiedenen Debuggerfenstern angezeigt.

## <a name="using-expression-evaluation"></a>Verwenden der Ausdrucksauswertung
 Um die Ausdrucksauswertung zu verwenden, müssen Sie die [IDebugExpressionContext2::ParseText-Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) und alle Methoden der [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) implementieren, wie in der folgenden Tabelle dargestellt.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron aus.|
|[Abbrechen](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucksauswertung.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron aus.|

 Für die synchrone und asynchrone Auswertung ist die [IDebugProperty2::GetPropertyInfo-Methode](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) implementiert. Die Asynchrone Ausdrucksauswertung erfordert die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Weitere Informationen
- [Ausführungskontrolle und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
