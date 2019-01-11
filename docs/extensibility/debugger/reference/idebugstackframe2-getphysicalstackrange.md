---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56121c7a0e58d90fd3ab0384a39916c102056c50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958695"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ruft eine Darstellung abhängig vom Computer des Bereichs von physischen Adressen, die einen Stapelrahmen zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `paddrMin`  
 [out] Gibt die niedrigste physische Adresse, die diesen Stapelrahmen zugeordnet.  
  
 `paddrMax`  
 [out] Gibt die höchste physische Adresse, die diesen Stapelrahmen zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Informationen, die von dieser Methode zurückgegebene sitzungsbasierter Debug-Manager (SDM) Dient zum Sortieren der Stapelrahmen.  
  
 Es wird davon ausgegangen, dass die Aufrufliste nach unten, d. h. vergrößert wird, dass es sich bei neuen Stapelrahmen an zunehmend niedrigere Speicheradressen hinzugefügt werden. Eine Laufzeit-Architektur muss physischen Stapel Bereiche angeben, die diese Annahme zu entsprechen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)