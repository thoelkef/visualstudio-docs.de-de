---
title: "UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL"
helpviewer_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL-Struktur"
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt eine physische Adresse dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```c#  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## Ausdrücke  
 Offset  
 Ein 64\-Bit\-Offset in den Adressbereich physische Adresse.  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_UNMANAGED_PHYSICAL` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)