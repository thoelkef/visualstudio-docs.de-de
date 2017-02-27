---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "PROCESS_INFO_FLAGS-enumeration"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt oder gibt Eigenschaften eines Prozesses an.  
  
## Syntax  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Mitglieder  
 PIFLAG\_SYSTEM\_PROCESS  
 Gibt an, dass der Prozess ein Systemprozess handelt.  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 Gibt an, dass der Prozess von einem Debugger gedebuggt wird.  Es kann ein [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger, oder es ist möglicherweise einen anderen Debugger z. B. WinDbg  
  
 PIFLAG\_PROCESS\_STOPPED  
 Gibt den Prozess wird beendet.  Gültig nur, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben wird.  Verfügbar in [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] und höher.  
  
 PIFLAG\_PROCESS\_RUNNING  
 Gibt den Prozess ausgeführt wird.  Gültig nur, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben wird.  Verfügbar in [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] und höher.  
  
## Hinweise  
 Wird für den `Flags`\-Member der [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)