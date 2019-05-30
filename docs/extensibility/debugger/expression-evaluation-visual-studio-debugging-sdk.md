---
title: Ausdrucksauswertung (Visual Studio Debugging SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e1e09f2302a6bb8401dd8c9f2d7c48810d5ecdc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353816"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ausdrucksauswertung (Visual Studio Debugging SDK)
Die IDE muss während des Unterbrechungsmodus einfache Ausdrücke mit mehreren Programmvariablen ausgewertet werden. Um die Auswertung zu erreichen, muss die Debug-Engine (DE) analysieren und Auswerten eines Ausdrucks, das in eines der Fenster der IDE eingegeben wird.

 Ausdrücke werden erstellt, mit der [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode dargestellt, die vom resultierenden [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.

 Die **IDebugExpression2** Schnittstelle wird implementiert, die DE und ruft seine **EvalAsync** -Methode zur Rückgabe einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, um die IDE, um anzuzeigen die Ergebnisse der Auswertung von Ausdrücken in der IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine Struktur, die verwendet wird, können Sie den Wert eines Ausdrucks in einer **Watch** Fenster oder in der **"lokal"** Fenster.

 Ruft die Debug-Pakets oder einer Sitzung Debug-Manager (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die darstellt Das Ergebnis der Auswertung. `IDebugProperty2` verfügt über Methoden, die den Namen, Typ und Wert des Ausdrucks zurückgeben. Diese Informationen werden in den verschiedenen Debuggerfenstern angezeigt.

## <a name="using-expression-evaluation"></a>Verwenden die Auswertung von Ausdrücken
 Um die Auswertung des Ausdrucks verwenden zu können, müssen Sie implementieren die [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und alle Methoden von der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, wie in der folgenden Tabelle gezeigt.

|Methode|Beschreibung|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron an.|
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone ausdrucksauswertung.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron an.|

 Synchrone und asynchrone Auswertung erfordern, implementieren die [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Asynchrone ausdrucksauswertung erfordert die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Siehe auch
- [Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)