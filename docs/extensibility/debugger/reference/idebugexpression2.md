---
title: IDebugExpression2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2"></a>IDebugExpression2
Diese Schnittstelle stellt eine analysierten Ausdrucks kann jetzt für die Bindung und auswerten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine analysierten Ausdrucks zur Auswertung bereiter darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) gibt diese Schnittstelle. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstellen sind zugegriffen werden kann, nur, wenn das Programm, der debuggt angehalten wurde und ein Stapelrahmen verfügbar ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExpression2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet diesen Ausdruck asynchron aus.|  
|[Abbrechen](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone ausdrucksauswertung.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet diesen Ausdruck synchron aus.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Programm angehalten wurde, erhält der Sitzungs-Manager (SDM) einen Stapelrahmen aus DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Ruft die SDM dann [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Durch einen Aufruf von darauf [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erstellen der `IDebugExpression2` -Schnittstelle, die zur Auswertung bereiter analysierten Ausdrucks darstellt.  
  
 Ruft die SDM [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) tatsächlich wertet den Ausdruck und einen Wert zu erzeugen.  
  
 In einer Implementierung von `IDebugExpressionContext2::ParseText`, DE verwendet COM `CoCreateInstance` Funktion, um eine ausdrucksauswertung instanziieren und Abrufen einer [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle (Siehe das Beispiel in der `IDebugExpressionEvaluator` Schnittstelle). Die DE ruft dann [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Abrufen einer [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Diese Schnittstelle wird verwendet, in der Implementierung der `IDebugExpression2::EvaluateSync` und `IDebugExpression2::EvaluateAsync` eine Auswertung durchgeführt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)