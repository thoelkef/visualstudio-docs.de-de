---
title: "IDebugThread2::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::CanSetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::CanSetNextStatement"
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugThread2::CanSetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob der aktuelle Anweisungszeiger auf die angegebene Stapelrahmen festgelegt werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Parameter  
 `pStackFrame`  
 Für zukünftige Verwendung reserviert. Auf einem NULL\-Wert.  Wenn dies ein NULL\-Wert ist, verwenden Sie den aktuellen Stapelrahmen.  
  
 `pCodeContext`  
 \[in\]  Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das den auszuführenden Code ungefähr beschreibt Speicherort und der Kontext.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn diese Methode `S_OK`zurückgibt, rufen Sie die [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)\-Methode auf, um die nächste Anweisung tatsächlich festzulegen.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)