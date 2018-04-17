---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5b991a877f91b9324b6535fb3b79b082cd901c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Ruft den Disassembly-Datenstrom für dieses Programm oder einen Teil dieses Programm an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwScope`  
 [in] Gibt einen Wert aus der [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) -Enumeration, der den Bereich des Datenstroms Disassembly definiert.  
  
 `pCodeContext`  
 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das die Position, an dem die Disassembly-Stream gestartet darstellt.  
  
 `ppDisassemblyStream`  
 [out] Gibt eine [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) -Objekt, das den Disassembly-Stream darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_DISASM_NOTSUPPORTED` Wenn Disassembly für diese bestimmte Architektur nicht unterstützt wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `dwScopes` Parameter hat die `DSS_HUGE` flag von der [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) -Enumeration festgelegt, und klicken Sie dann die Disassembly wird erwartet, dass eine große Anzahl von Disassembly-Anweisungen, z. B. für eine gesamte Datei zurückgegeben oder das Modul. Wenn die `DSS_HUGE` Flag nicht festgelegt ist, und klicken Sie dann die Disassembly wird erwartet, dass auf einen kleinen Bereich beschränkt werden in der Regel, die von einer einzelnen Funktion.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)