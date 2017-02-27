---
title: "BP_UNBOUND_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "BP_UNBOUND_REASON-enumeration"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Grund für den ein Haltepunkt aufgehoben wurde.  
  
## Syntax  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## Mitglieder  
 BPUR\_UNKNOWN  
 Der Grund ist unbekannt.  
  
 BPUR\_CODE\_UNLOADED  
 Der Code, der den Haltepunkt enthält, wird entladen wurde.  
  
 BPUR\_BREAKPOINT\_REBIND  
 Der Haltepunkt wird an einem anderen Speicherort erneut gebunden.  Dies kann geschehen nachdem Bearbeiten und setzt Vorgänge fort, wenn der Haltepunkt befindet oder wenn der Haltepunkt in einer Datei mit einem Pfad gebunden ist, der nicht mehr gültig ist.  
  
 BPUR\_ BREAKPOINT\_ERROR  
 Der Haltepunkt wird festgelegt, um Fehler geschlossen werden soll, nachdem er gebunden ist.  Dies geschieht auf verwaltete Haltepunkte, deren Bedingungen nicht mehr gültig sind.  
  
## Hinweise  
 Wird zurückgegeben von der [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)