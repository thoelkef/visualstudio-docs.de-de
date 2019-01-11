---
title: IDebugMemoryBytes2::WriteAt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7d9cbd621b24db26316cc7fca48352a7d97df6e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873183"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Schreibt die angegebene Anzahl von Bytes des Arbeitsspeichers, ab der angegebenen Adresse an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStartContext`  
 [in] Die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das angibt, wo Sie anfangen, Schreiben von Bytes.  
  
 `dwCount`  
 [in] Die Anzahl der zu schreibenden Bytes kennzeichnet.  
  
 `rgbMemory`  
 [in] Der zu schreibenden Bytes. Dieses Array wird davon ausgegangen, dass mindestens `dwCount` Bytes groß.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` Wenn nicht alle Bytes geschrieben werden kann, oder ein Fehlercode zurückgegeben (in der Regel `E_FAIL`).  
  
## <a name="remarks"></a>Hinweise  
 Ist die Startadresse nicht in das Fenster "Arbeitsspeicher" von diesem dargestellt [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Objekt, ohne das Schreiben von tritt ein, und einem Fehlercode von `E_FAIL` zurückgegeben – selbst wenn der Betrag, um das Schreiben in den Speicherbereich überschneidet sich mit.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)