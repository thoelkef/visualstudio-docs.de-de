---
title: "PROGRAM_DESTROY_FLAGS | Microsoft Docs"
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
  - "PROGRAM_DESTROY_FLAGS-enumeration"
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# PROGRAM_DESTROY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet die gültigen Werte des Programms zerstört Flags aufgelistet.  
  
## Syntax  
  
```cpp#  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```c#  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## Ausdrücke  
 PROGRAM\_DESTROY\_CONTINUE\_DEBUGGING  
 Zerstören Sie Programms, sondern fahren Sie fort, um zu debuggen.  
  
## Hinweise  
 Die Enumeration wird von der [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)