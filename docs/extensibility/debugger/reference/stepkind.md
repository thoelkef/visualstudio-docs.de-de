---
title: "STEPKIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPKIND"
helpviewer_keywords: 
  - "STEPKIND-enumeration"
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPKIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Art der Schritt für die schrittweise Ausführung an.  
  
## Syntax  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```c#  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## Mitglieder  
 STEP\_INTO  
 Schritte in eine benutzerdefinierte Funktion.  
  
 STEP\_OVER  
 Überspringt eine Funktion.  
  
 STEP\_OUT  
 Schritte aus einer Funktion heraus.  
  
 STEP\_BACKWARDS  
 rückwärts Schritte in eine benutzerdefinierte Funktion.  
  
## Hinweise  
 Übergabe als Argument an die [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)