---
title: "BSTR_ARRAY | Microsoft Docs"
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
  - "BSTR_ARRAY"
helpviewer_keywords: 
  - "BSTR_ARRAY-Struktur"
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BSTR_ARRAY
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Eine Struktur, die ein Array von Zeichenfolgen beschreibt.  
  
## Syntax  
  
```cpp#  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```c#  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## Ausdrücke  
 dwCount  
 Die Anzahl der Zeichenfolgen in `Members` Array.  
  
 Mitglieder  
 Zeichenfolgenarray.  
  
## Hinweise  
 Diese Struktur wird von der [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)\-Methode zurückgegeben.  
  
 \[C\+\+\] Es muss jede einzelne Zeichenfolge mit `SysFreeString`freigegeben werden, und das `Members` Array muss mit `CoTaskMemFree`freigegeben werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)