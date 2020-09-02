---
title: 'IDebugStackFrame2:: getexpressioncontext | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7aea3543401faa1e7a6fd3ab2d3de073b5e6b3bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164731"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft einen Auswertungs Kontext für die Ausdrucks Auswertung innerhalb des aktuellen Kontexts eines Stapel Rahmens und Threads ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppExprCxt`  
 vorgenommen Gibt ein [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Objekt zurück, das einen Kontext für die Ausdrucks Auswertung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Im Allgemeinen kann ein Ausdrucks Auswertungs Kontext als Bereich zum Durchführen der Ausdrucks Auswertung betrachtet werden. Aufrufen der [Methode "](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode", um einen Ausdruck zu analysieren und dann die resultierenden [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) -oder [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methoden aufzurufen, um den analysierten Ausdruck auszuwerten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [Parametertext](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
