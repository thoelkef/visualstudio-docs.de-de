---
title: "UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UNMANAGED_ADDRESS_THIS_RELATIVE"
helpviewer_keywords: 
  - "UNMANAGED_ADDRESS_THIS_RELATIVE-Struktur"
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# UNMANAGED_ADDRESS_THIS_RELATIVE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt eine Adresse dar, die relativ zu einem `this` Zeiger \(`Me` in Visual Basic\) ist.  
  
## Syntax  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```c#  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## Ausdrücke  
 dwOffset  
 Byteoffset aus einer niedrigen Position \(z. B. zum Starten einer Klasse vtable\).  
  
 dwBitOffset  
 Offset in Bits von einer niedrigen Position \(immer 0, es sei denn, ein Bitfeld ansprechend\).  
  
 dwBitLength  
 Die Anzahl der Bits, die die Adresse darstellen \(immer 0, es sei denn, ein Bitfeld ansprechend\).  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)