---
title: Ausdrucksauswertung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738687"
---
# <a name="expression-evaluator"></a>Ausdrucksauswertung
Ausdrucksauswertungen (EE) untersuchen die Syntax einer Sprache, um Variablen und Ausdrücke zur Laufzeit zu analysieren und auszuwerten, sodass sie vom Benutzer angezeigt werden können, wenn sich die IDE im Unterbrechungsmodus befindet.

## <a name="use-expression-evaluators"></a>Verwenden von Ausdrucksauswertungen
 Ausdrücke werden wie folgt mit der [ParseText-Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) erstellt:

1. Das Debugmodul (DE) implementiert die [IDebugExpressionContext2-Schnittstelle.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Das Debugpaket `IDebugExpressionContext2` ruft ein Objekt von einer [IDebugStackFrame2-Schnittstelle](../../extensibility/debugger/reference/idebugstackframe2.md) ab und ruft dann die `IDebugStackFrame2::ParseText` Methode auf, um ein [IDebugExpression2-Objekt](../../extensibility/debugger/reference/idebugexpression2.md) abzubekommen.

3. Das Debugpaket ruft die [EvaluateSync-Methode](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder die [EvaluateAsync-Methode](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den Wert des Ausdrucks abzubekommen. `IDebugExpression2::EvaluateAsync`wird aus dem Fenster Befehl/Sofort aufgerufen. Alle anderen UI-Komponenten rufen auf `IDebugExpression2::EvaluateSync`.

4. Das Ergebnis der Ausdrucksauswertung ist ein [IDebugProperty2-Objekt,](../../extensibility/debugger/reference/idebugproperty2.md) das den Namen, den Typ und den Wert des Ergebnisses der Ausdrucksauswertung enthält.

   Bei der Ausdrucksauswertung benötigt der EE Informationen von der Symbolanbieterkomponente. Der Symbolanbieter stellt die symbolischen Informationen zur Verfügung, die zum Identifizieren und Verstehen des analysierten Ausdrucks verwendet werden.

   Wenn die asynchrone Ausdrucksauswertung abgeschlossen ist, wird ein asynchrones Ereignis von der DE über den Sitzungsdebug-Manager (SDM) gesendet, um die IDE zu benachrichtigen, dass die Ausdrucksauswertung abgeschlossen ist. Und das Ergebnis der Auswertung wird dann vom `IDebugExpression2::EvaluateSync` Aufruf an die Methode zurückgegeben.

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule erwarten, dass sie mit dem Ausdrucksevaluator über CLR-Schnittstellen (Common Language Runtime) sprechen. Daher muss ein Ausdrucksauswertungsgeber, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit den Debugmodulen arbeitet, die CLR unterstützen (eine vollständige Liste aller CLR-Debugging-Schnittstellen finden Sie in debugref.doc, das Teil der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]ist).

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
