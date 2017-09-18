---
title: "BP_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_STATE"
helpviewer_keywords: 
  - "BP_STATE-enumeration"
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt das Vorhandensein eines gebundenen Haltepunkte an und gibt außerdem an, wenn er aktiviert ist.  
  
## Syntax  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```c#  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## Mitglieder  
 BPS\_NONE  
 Gibt an, dass kein Haltepunkt vorhanden ist.  
  
 BPS\_DELETED  
 Gibt an, dass der Haltepunkt gelöscht wurde.  
  
 BPS\_DISABLED  
 Gibt an, dass der Haltepunkt deaktiviert ist.  
  
 BPS\_ENABLED  
 Gibt an, dass der Haltepunkt aktiviert ist.  
  
## Hinweise  
 Wird zurückgegeben von der [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)