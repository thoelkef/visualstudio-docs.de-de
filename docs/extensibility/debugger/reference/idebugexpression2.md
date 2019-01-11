---
title: IDebugExpression2 | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: 9d493da63aaac406ea1fef0f33abbcef528ead61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866987"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Diese Schnittstelle stellt eine einsatzbereite analysierten Ausdruck für die Bindung und auswerten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um einen analysierten Ausdruck zur Auswertung bereiter darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) dieser Schnittstelle zurück. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstellen sind zugegriffen werden kann, nur, wenn das derzeit debuggte Programm angehalten wurde und ein Stapelrahmen verfügbar ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExpression2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet diesen Ausdruck asynchron aus.|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone ausdrucksauswertung.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet diesen Ausdruck synchron aus.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Programm angehalten wurde, erhält der sitzungsbasierter Debug-Manager (SDM) einen Stapelrahmen aus dem DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Klicken Sie dann aufruft, das SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Darauf folgt ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erstellen der `IDebugExpression2` -Schnittstelle, die den analysierten Ausdruck zur Auswertung bereiter darstellt.  
  
 Das SDM Ruft entweder [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) wertet den Ausdruck und Wert erzeugen kann.  
  
 In einer Implementierung der `IDebugExpressionContext2::ParseText`, die DE verwendet COM `CoCreateInstance` -Funktion zum Instanziieren einer ausdrucksauswertung und erhalten eine [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle (Siehe das Beispiel in der `IDebugExpressionEvaluator` Schnittstelle). Ruft die DE dann [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Abrufen einer [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Diese Schnittstelle wird verwendet, bei der Implementierung der `IDebugExpression2::EvaluateSync` und `IDebugExpression2::EvaluateAsync` um die Auswertung auszuführen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)