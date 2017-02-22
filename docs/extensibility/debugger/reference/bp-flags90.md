---
title: "BP_FLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BP_FLAGS90-enumeration"
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_FLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet gültigen Werten für optionale Flags aufgelistet.  Die optionalen Flags verwendet werden, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt.  Diese Enumeration wird die [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)\-Enumeration.  
  
## Syntax  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```c#  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### Parameter  
 BP90\_FLAG\_NONE  
 Gibt kein Haltepunkt flag an.  
  
 BP90\_FLAG\_MAP\_DOCPOSITION  
 Gibt an, dass das Debugmodul \(DE\) den Haltepunkt mithilfe der Position Dokumenten zugeordnet werden soll.  Dies ist nur für Haltepunkte anwendbar, die in Skript\-ausgerichteten Quelldateien z. B. ASP \(Active Server Pages\) festgelegt werden.  
  
 \_STOPP BP90\_FLAG\_DO NOT  
 Gibt an, dass der Haltepunkt vom Debugmodul verarbeitet werden soll, sondern dass das Debugmodul es letztlich nicht beendet werden soll. Dies bedeutet, dass ein [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)\-Ereignisobjekt nicht gesendet werden.  Dieses Flag ist hauptsächlich mit Ablaufverfolgung punkten vorgesehen.  
  
 BP90\_FLAG\_TRACEPOINT\_CONTINUE  
 Wird vom systemeigenen Debugmodul, um zu bestimmen, ob der tretende Zustand gelöscht werden soll.  Er unterscheidet sich von BP90\_FLAG\_DONT\_STOP, da BP90\_FLAG\_DONT\_STOP nicht festgelegt wird, wenn der Ablaufverfolgung mit einem Makro ausführt.  
  
## Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)