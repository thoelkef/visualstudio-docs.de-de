---
title: "PENDING_BP_STATE | Microsoft Docs"
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
  - "PENDING_BP_STATE"
helpviewer_keywords: 
  - "PENDING_BP_STATE-enumeration"
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# PENDING_BP_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Zustand eines anstehenden Haltepunkts an \(ein Haltepunkt, der noch nicht gebunden wurde\).  
  
## Syntax  
  
```cpp#  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```c#  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## Mitglieder  
 PBPS\_NONE  
 Platzhalter für Nullen.  Dieser Wert wird nie zurückgegeben.  
  
 PBPS\_DELETED  
 Gibt an, dass der ausstehenden Haltepunkt gelöscht wurde.  
  
 PBPS\_DISABLED  
 Gibt an, dass der ausstehenden Haltepunkt deaktiviert ist.  
  
 PBPS\_ENABLED  
 Gibt an, dass der ausstehenden Haltepunkt aktiviert ist.  
  
## Hinweise  
 Verwendung als `state`\-Member der [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)