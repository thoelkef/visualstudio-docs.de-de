---
title: "ATTACH_REASON | Microsoft Docs"
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
  - "ATTACH_REASON"
helpviewer_keywords: 
  - "ATTACH_REASON-enumeration"
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# ATTACH_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Grund für das Debugmodul \(DE\) an Knoten mit einem Programm anzufügen.  
  
## Syntax  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## Mitglieder  
 ATTACH\_REASON\_AUTO  
 Anfügen, da der Prozess derzeit im Debugmodus befindet.  
  
 ATTACH\_REASON\_LAUNCH  
 Anfügen, da der Prozess gestartet wurde.  
  
 ATTACH\_REASON\_USER  
 Anfügen aufgrund einer Benutzeranforderung.  
  
## Hinweise  
 Diese Werte werden als Parameter an den [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) und [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)\-Methoden verwendet.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)