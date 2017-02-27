---
title: "IDebugDisassemblyStream2::GetScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetScope"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetScope"
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetScope
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bereich des Disassemblysdatenstroms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetScope(   
   DISASSEMBLY_STREAM_SCOPE* pdwScope  
);  
```  
  
```c#  
int GetScope(   
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope  
);  
```  
  
#### Parameter  
 `pdwScope`  
 \[out\]  Gibt einen Wert aus der [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)\-Enumeration zurück, die den Bereich dieses Disassemblys datenstroms beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Gültigkeitsbereich einer Disassemblys kann eine Funktion oder das gesamte Modul befinden, z.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)