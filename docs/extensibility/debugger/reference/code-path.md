---
title: "CODE_PATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODE_PATH"
helpviewer_keywords: 
  - "CODE_PATH-Struktur"
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CODE_PATH
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt eine Methode oder einen Funktionsaufruf.  
  
## Syntax  
  
```cpp#  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```c#  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## Mitglieder  
 bstrName  
 Der Name des Codepfads.  
  
 pCode  
 Das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das angibt, an welcher Stelle im Code in einer Funktion wird.  
  
## Hinweise  
 Diese Struktur wird verwendet, um das schrittweise Durchlaufen in eine Funktion zu implementieren.  [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) gibt alle Aufrufe von der aktuellen Position im Programm, das gedebuggt wird.  Diese Struktur stellt einen solchen Aufruf dar.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)