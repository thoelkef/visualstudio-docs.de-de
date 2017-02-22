---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
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
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "METADATA_ADDRESS_METHOD-Struktur"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur enthält die Adresse einer Methode einer Klasse dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## Ausdrücke  
 tokMethod  
 Die ID der Methode.  
  
 \[C\+\+\] `_mdToken``typedef` für 32\-Bit\- `int`.  
  
 dwOffset  
 Der Offset vom Klassen, wobei dieser Methode \(kann den Offset in der vtable darstellen\).  
  
 dwVersion  
 Die Version der Methode \(dieser Wert entspricht dem Symbol für eindeutig\).  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_METHOD` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)