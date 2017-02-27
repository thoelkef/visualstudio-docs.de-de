---
title: "FIELD_KIND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FIELD_KIND_EX-enumeration"
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet zusätzliche Arten von Feldern, die ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt enthalten kann.  Diese Enumeration wird die [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)\-Enumeration.  
  
## Syntax  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```c#  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## Mitglieder  
 FIELD\_KIND\_EX\_NONE  
 Feld enthält keinen erweiterten Typ.  
  
 FIELD\_TYPE\_EX\_METHODVAR  
 Feld enthält eine Variable Methoden.  
  
 FIELD\_TYPE\_EX\_CLASSVAR  
 Feld enthält eine Klassenvariablen.  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)