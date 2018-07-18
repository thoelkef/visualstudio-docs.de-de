---
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9c72120a4153ed6d0d19a2cf2b7d3a9a9943801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112469"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Vergleicht den Speicherkontext, um jeden Kontext, in dem angegebenen Array in der Weise, angegeben durch Vergleichen-Flags, die einen Index der ersten Kontext, der mit übereinstimmt zurückgeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `compare`  
 [in] Ein Wert aus der [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) -Enumeration, der den Typ des Vergleichs bestimmt.  
  
 `rgpMemoryContextSet`  
 [in] Ein Array von Verweisen auf die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekte, die mit verglichen.  
  
 `dwMemoryContextSetLen`  
 [in] Die Anzahl von Kontexten, die in der `rgpMemoryContextSet` Array.  
  
 `pdwMemoryContext`  
 [out] Gibt den Index des ersten Arbeitsspeicher-Kontexts, die den Vergleich zu erfüllen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_COMPARE_CANNOT_COMPARE` , wenn die beiden Kontexte nicht verglichen werden können.  
  
## <a name="remarks"></a>Hinweise  
 Ein Debugging-Modul (DE) muss nicht alle Typen von vergleichen zu unterstützen, aber es muss mindestens unterstützen `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` und `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)