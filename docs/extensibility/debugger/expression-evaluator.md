---
title: Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c33fff3d8b5bd30ecec1b566e550d14e4cb68c11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925803"
---
# <a name="expression-evaluator"></a>Ausdrucksauswertung
Ausdrucksauswertungen (EE) überprüfen die Syntax einer Sprache zum Analysieren und Auswerten von Variablen und Ausdrücke zur Laufzeit, sodass sie vom Benutzer angezeigt werden, wenn die IDE im Unterbrechungsmodus befindet.

## <a name="use-expression-evaluators"></a>Ausdrucksauswertungen verwenden
 Ausdrücke werden erstellt, mit der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode wie folgt:

1. Die Debug-Engine (DE) implementiert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.

2. Ruft ab, das debugpaket ein `IDebugExpressionContext2` -Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle und ruft dann die `IDebugStackFrame2::ParseText` Methode darauf, um die erste ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt.

3. Ruft die Debug-Paket der [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) Methode oder der [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methode, um den Wert des Ausdrucks zu erhalten. `IDebugExpression2::EvaluateAsync` wird vom Befehl/Direktfenster aufgerufen. Alle anderen UI-Komponenten aufrufen `IDebugExpression2::EvaluateSync`.

4. Das Ergebnis der Auswertung des Ausdrucks ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Namen, Typ und Wert das Ergebnis der Auswertung des Ausdrucks enthält.

   Beim Auswerten des Ausdrucks erfordert die EE Informationen aus der Symbol-Anbieter-Komponente. Der symbolanbieter stellt die symbolische Informationen zum Identifizieren und Grundlegendes zu den analysierten Ausdruck.

   Wenn asynchrone ausdrucksauswertung abgeschlossen ist, wird ein asynchrones Ereignis per die DE über die sitzungsbasierter Debug-Manager (SDM) der IDE benachrichtigt, dass die Auswertung des Ausdrucks abgeschlossen ist. Und das Ergebnis der Auswertung wird dann zurückgegeben, durch den Aufruf der `IDebugExpression2::EvaluateSync` Methode.

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-Engines für die Kommunikation mit der Auswertung eines Ausdrucks mithilfe der Common Language Runtime (CLR)-Schnittstellen zu erwarten. Daher eine ausdrucksauswertung, die funktioniert mit den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-Engines müssen die CLR unterstützt (eine vollständige Liste der alle CLR-Debugschnittstellen befinden sich debugref.doc, gehört der der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).

## <a name="see-also"></a>Siehe auch
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)