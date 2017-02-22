---
title: "LAUNCH_FLAGS | Microsoft Docs"
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
  - "LAUNCH_FLAGS"
helpviewer_keywords: 
  - "LAUNCH_FLAGS-enumeration"
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# LAUNCH_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Programmdebuginformationen Startflags an.  
  
## Syntax  
  
```cpp#  
enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
typedef DWORD LAUNCH_FLAGS;  
```  
  
```c#  
public enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
```  
  
## Mitglieder  
 LAUNCH\_DEBUG  
 Startet den Prozess zu Debugzwecken.  
  
 LAUNCH\_NODEBUG  
 Startet den Prozess, ohne sie zu debuggen.  
  
 LAUNCH\_ENABLE\_ENC  
 VERALTET. USE, TUN NOT  
  
 LAUNCH\_MERGE\_ENV  
 Startet den Prozess und übergibt dem Start der Umgebung zusammen hostet.  
  
## Hinweise  
 Diese Werte werden als Argument an die [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)\-Methode übergeben.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)