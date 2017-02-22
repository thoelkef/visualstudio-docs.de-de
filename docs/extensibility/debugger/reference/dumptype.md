---
title: "DUMPTYPE | Microsoft Docs"
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
  - "DUMPTYPE"
helpviewer_keywords: 
  - "DUMPTYPE-enumeration"
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DUMPTYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wie viel von einem Zustand des Programms \(z. B. ausgeführte Threads, Stapelrahmen und aktuelle Anweisungsadresse\), um Dumps.  
  
## Syntax  
  
```cpp#  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```c#  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## Mitglieder  
 DUMP\_MINIDUMP  
 Gibt einen kleinen, kompakten Dump an.  
  
 DUMP\_FULLDUMP  
 Gibt einen großen, vollständigen Dump an.  
  
## Hinweise  
 Übergabe als Argument an die [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)