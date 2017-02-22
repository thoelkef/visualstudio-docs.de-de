---
title: "METADATA_ADDRESS_PARAM | Microsoft Docs"
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
  - "METADATA_ADDRESS_PARAM"
helpviewer_keywords: 
  - "METADATA_ADDRESS_PARAM-Struktur"
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_PARAM
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt einen Parameter einer Methode oder Funktion dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_PARAM {  
   _mdToken tokMethod;  
   _mdToken tokParam;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_PARAM;  
```  
  
```c#  
public struct METADATA_ADDRESS_PARAM {  
   public int  tokMethod;  
   public int  tokParam;  
   public uint dwIndex;  
}  
```  
  
## Ausdrücke  
 tokMethod  
 Die ID der Parameter der Methode ist ein Part aus.  
  
 tokParam  
 Die ID des Parameters.  
  
 dwIndex  
 Der Index des Parameters in einer Liste mit Parametern.  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_PARAM` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)