---
title: "METADATA_ADDRESS_ARRAYELEM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_ARRAYELEM"
helpviewer_keywords: 
  - "METADATA_ADDRESS_ARRAYELEM-Struktur"
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_ARRAYELEM
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt ein Arrayelement innerhalb eines Arrays dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```c#  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## Ausdrücke  
 tokMethod  
 Die ID des Arrays dieses Element ist ein Part aus.  
  
 \[C\+\+\] `_mdToken``typedef` für 32\-Bit\- `int`.  
  
 dwIndex  
 Der Index des Elements im Array.  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_ARRAYELEM` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)