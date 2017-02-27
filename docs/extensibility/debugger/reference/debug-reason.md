---
title: "DEBUG_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "DEBUG_REASON-enumeration"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, dass der Prozess zu Debugzwecken gestartet wurde.  
  
## Syntax  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### Parameter  
 DEBUG\_REASON\_ERROR  
 Ein unspezifischer Fehler aufgetreten \(dies wird als Standardbedingung verwendet, wenn keine anderen Gründen angepasst\).  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 Der Prozess wurde mit der Benutzeranforderung gestartet.  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 Der Bereits RUNNING\-Prozess wurde von dem Benutzer angefügt.  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 Der Prozess wurde automatisch angefügt, als er gestartet wurde.  
  
 DEBUG\_REASON\_CAUSALITY  
 Der Vorgang wurde aufgrund eines Ereignisses des *Just\-In\-Time* \(JIT\) \- Debuggen gestartet.  
  
## Hinweise  
 Wird zurückgegeben von der [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)