---
title: "Auswertung von Ausdrücken (Visual Studio debuggen SDK) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c66a6eac74b3d1494a1e98bcb95112c43c4c1bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Auswertung von Ausdrücken (Visual Studio debuggen SDK)
Während der sich im Unterbrechungsmodus befinden muss die IDE können einfache Ausdrücke mit mehreren Variablen des Programms. Um dies zu erreichen, muss die Debugging-Modul (DE) vorliegen, zu analysieren und Auswerten eines Ausdrucks, das in einem Fenster der IDE eingegeben wurde.  
  
 Ausdrücke werden erstellt, mit der [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und sind durch das resultierende dargestellt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.  
  
 Der **IDebugExpression2** Schnittstelle wird implementiert, die DE und ruft seine **EvalAsync** -Methode zur Rückgabe einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, um die IDE, um anzuzeigen der Ergebnisse der Auswertung von Ausdrücken in der IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine Struktur, die mit der Wert eines Ausdrucks in einem Überwachungsfenster oder das Fenster "lokal" eingefügt werden kann.  
  
 Der Debug-Paket oder Sitzung Debug-Manager (SDM) Ruft [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die darstellt Das Ergebnis der Auswertung. `IDebugProperty2`verfügt über Methoden, die den Namen, Typ und Wert des Ausdrucks zurückgeben. Diese Informationen werden in den verschiedenen Debuggerfenstern angezeigt.  
  
## <a name="using-expression-evaluation"></a>Verwenden die Auswertung von Ausdrücken  
 Um Auswertung von Ausdrücken zu verwenden, müssen Sie implementieren die [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und alle Methoden von der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle ein, wie in der folgenden Tabelle dargestellt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron an.|  
|[Abbrechen](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone ausdrucksauswertung.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron an.|  
  
 Synchrone und asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Asynchrone ausdrucksauswertung erfordert die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)