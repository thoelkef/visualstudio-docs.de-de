---
title: "dwTYPE_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "DwTYPE_KIND-enumeration"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wie der Typ eines Objekts [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interpretiert.  
  
## Syntax  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### Parameter  
 TYPE\_KIND\_METADATA  
 Die [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) Union sollte als [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur interpretiert werden.  
  
 TYPE\_KIND\_PDB  
 Die `TYPE_INFO` Union sollte als [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur interpretiert werden.  
  
 TYPE\_KIND\_BUILT  
 Die `TYPE_INFO` Union sollte als [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur interpretiert werden.  
  
## Hinweise  
 Die Werte dieser Enumeration werden im `dwKind` Feld der [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur und wird verwendet, um zu bestimmen, wie das `type` Gewerkschaftsmitglied interpretiert.  Die `TYPE_INFO` Struktur wird von einem Aufruf der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)