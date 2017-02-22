---
title: "BP_FLAGS | Microsoft Docs"
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
  - "BP_FLAGS"
helpviewer_keywords: 
  - "BP_FLAGS-enumeration"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt optionale Flags bereit, die möglicherweise zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen.  
  
## Syntax  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Mitglieder  
 BP\_FLAG\_NONE  
 Gibt kein Haltepunkt flag an.  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 Gibt an, dass das Debugmodul \(DE\) den Haltepunkt mit der Position der Dokumente zugeordnet werden soll.  Dies ist nur für Haltepunkte anwendbar, die in Skript\-ausgerichteten Quelldateien z. B. ASP \(Active Server Pages\) festgelegt werden.  
  
 \_STOPP BP\_FLAG\_DO NOT  
 Gibt an, dass der Haltepunkt vom Debugmodul verarbeitet werden soll, aber, dass das Debugmodul es letztlich nicht beendet werden soll \(das heißt ein [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)\-Ereignisobjekt nicht übermittelt werden soll\).  Dieses Flag ist hauptsächlich mit Ablaufverfolgungspunkten vorgesehen.  
  
## Hinweise  
 Wird für den `dwFlags`\-Member der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)