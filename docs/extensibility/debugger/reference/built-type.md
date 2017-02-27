---
title: "BUILT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "BUILT_TYPE-Struktur"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur enthält Informationen über einen Feldtyp, der aus den Metadaten aufgezeichnet wird.  
  
## Syntax  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### Parameter  
 ulAppDomainID  
 ID der Anwendung, aus der das Symbol stammt.  Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 pUnderlyingField  
 Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das das zugrunde liegende Feld erstellen, die mit diesem Feld identifiziert.  
  
## Hinweise  
 Diese Struktur wird als Teil der Union in der [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur, wenn das `dwKind` Feld der `TYPE_INFO` Struktur in `TYPE_KIND_BUILT` festgelegt wird \(ein Wert aus der [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)\-Enumeration\).  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)