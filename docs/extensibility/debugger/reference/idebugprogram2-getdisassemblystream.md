---
title: "IDebugProgram2::GetDisassemblyStream | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
helpviewer_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Disassemblys datenstrom für dieses Programm oder einen Teil des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```c#  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### Parameter  
 `dwScope`  
 \[in\]  Gibt einen Wert aus der [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)\-Enumeration, die den Bereich des Disassemblys datenstroms definiert.  
  
 `pCodeContext`  
 \[in\]  Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das die Position darstellt, wo der Disassemblys datenstrom beginnt.  
  
 `ppDisassemblyStream`  
 \[out\]  Gibt ein [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)\-Objekt zurück, das den Disassemblysdatenstrom darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_DISASM_NOTSUPPORTED` zurück, wenn die Disassembly nicht für diese bestimmte Architektur unterstützt wird.  
  
## Hinweise  
 Wenn der Parameter `dwScopes``DSS_HUGE` das Flag der festgelegten [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)\-Enumeration hat, dann ist die Disassembly Demontagevorschriften viele erwartet, z. B. für eine gesamte Datei oder ein Modul zurückzugeben.  Wenn das `DSS_HUGE`\-Flag nicht festgelegt wurde, wird die Disassembly erwartet, auf einem kleinen Bereich, in der Regel der begrenzt werden aus einer einzelnen Funktion.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)