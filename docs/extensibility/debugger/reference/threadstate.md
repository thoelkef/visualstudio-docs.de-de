---
title: "THREADSTATE | Microsoft Docs"
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
  - "THREADSTATE"
helpviewer_keywords: 
  - "THREADSTATE-enumeration"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADSTATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Zustand des Threads an.  
  
## Syntax  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## Mitglieder  
 THREADSTATE\_RUNNING  
 Gibt an, dass der Thread ausgeführt wird.  
  
 THREADSTATE\_STOPPED  
 Gibt an, dass der Thread aufgrund eines Haltepunkts angehalten wurde.  
  
 THREADSTATE\_FRESH  
 Gibt an, dass der Thread erstellt wurde, aber noch nicht führt Code aus.  
  
 THREADSTATE\_DEAD  
 Gibt an, dass der Thread tot ist.  
  
 THREADSTATE\_FROZEN  
 Gibt an, dass der Thread eingefroren ist \(keine Ausführung kann ausgeführt werden\).  
  
## Hinweise  
 Wird zum `dwThreadState` Feld der [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)