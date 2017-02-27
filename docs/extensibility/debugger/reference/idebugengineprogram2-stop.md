---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beendet die für alle Threads in diesem Programm ausgeführt werden sollen.  
  
## Syntax  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird aufgerufen, wenn das Programm in einer Multiprogrammierungs Umgebungen gedebuggt wird.  Wenn ein aufhörendes Ereignis von einem anderen Programm empfangen wird, wird diese Methode für das Programm aufgerufen.  Die Implementierung dieser Methode sollte asynchron sein. Das heißt, sollten nicht alle Threads beendet werden, erforderlich sein, bevor diese Methode beendet wird.  Die Implementierung dieser Methode kann so einfach wie das die [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)\-Methode für dieses Programm aufgerufen wird.  
  
 Kein Debuggen Ereignis wird als Reaktion auf diese Methode gesendet.  
  
## Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)