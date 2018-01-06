---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f10efd1e9a06ca8425d972f43736b49e6ef4a83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Schreibt die angegebene Anzahl von Bytes an Arbeitsspeicher, ab der angegebenen Adresse an.  
  
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
 [in] Die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das angibt, wo Sie beginnen, Schreiben von Bytes.  
  
 `dwCount`  
 [in] Die Anzahl der zu schreibenden Bytes.  
  
 `rgbMemory`  
 [in] Der zu schreibenden Bytes. Dieses Array wird davon ausgegangen, dass mindestens `dwCount` Byte lang.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` Wenn nicht alle Bytes geschrieben werden konnte oder wird ein Fehlercode zurückgegeben (üblicherweise `E_FAIL`).  
  
## <a name="remarks"></a>Hinweise  
 Ist die Startadresse nicht in das Fenster "Arbeitsspeicher" dargestellt, die von diesem [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt, ohne das Schreiben von tritt auf, und einem Fehlercode von `E_FAIL` zurückgegeben – selbst wenn der Betrag, um das Schreiben in den Speicherbereich überschneidet sich.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)