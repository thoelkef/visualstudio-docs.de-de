---
title: "IDebugEngine2::CauseBreak | Microsoft Docs"
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
  - "IDebugEngine2::CauseBreak"
helpviewer_keywords: 
  - "IDebugEngine2::CauseBreak"
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Anforderungen, die alle Programme, die von diesem Debugmodul \(Debuggen\) DE das nächste Mal eine ihrer Ausführung von Threads zu beenden versucht, auszuführen.  
  
## Syntax  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ist asynchron: Ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)\-Ereignis wird gesendet, wenn das Programm auszuführen versucht auf Weiter, nachdem diese Methode aufgerufen wurde.  
  
## Siehe auch  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)