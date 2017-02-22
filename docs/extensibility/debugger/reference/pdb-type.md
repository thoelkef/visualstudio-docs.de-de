---
title: "PDB_TYPE | Microsoft Docs"
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
  - "PDB_TYPE"
helpviewer_keywords: 
  - "PDB_TYPE-Struktur"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur enthält Informationen über einen Feldtyp, der von einem PDB\-Symbol belegt wird.  
  
## Syntax  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### Parameter  
 ulAppDomainID  
 ID der Anwendung, aus der das Symbol stammt.  Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 symid  
 Die ID des Symbols, das auf dieses Feld entspricht.  
  
## Hinweise  
 Diese Struktur wird als Teil der Union in der [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur, wenn das `dwKind` Feld der `TYPE_INFO` Struktur in `TYPE_KIND_PDB` festgelegt wird \(ein Wert aus der [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)