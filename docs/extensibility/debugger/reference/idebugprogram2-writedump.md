---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
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
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Schreibt einen Dump in einer Datei.  
  
## Syntax  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### Parameter  
 `DumpType`  
 \[in\]  Ein Wert aus der [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)\-Enumeration, der den Typ des Dumps z. B. lang oder direkt angeben  
  
 `pszDumpUrl`  
 \[in\]  Die URL, an die der Dumps geschrieben werden soll.  In der Regel ist dies ist in Form von `file://c: Pfad \ \ " filename.ext`, aber jedes gültige URL.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Programm dump wird in der Regel den aktuellen Stapelrahmen, den Stapel selbst eine Liste der Threads enthalten, die im Programm aus, und ggf. jeden beliebigen Speicher, der vom Programm besitzt.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)