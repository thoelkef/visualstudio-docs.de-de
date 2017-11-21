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
ms.openlocfilehash: cb9b887ff8501516ea063dccf0247b0915de1d63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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