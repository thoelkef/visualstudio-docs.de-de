---
title: "METADATA_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_TYPE"
helpviewer_keywords: 
  - "METADATA_TYPE-Struktur"
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# METADATA_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur gibt Informationen zu einem Feld Metadaten entnommen.  
  
## Syntax  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```c#  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### Parameter  
 ulAppDomainID  
 ID der Anwendung, von der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 tokClass  
 Die Metadaten token\-ID dieses Typs.  
  
 \[C\+\+\] `_mdToken` ist eine `typedef` für 32\-Bit\- `int`.  
  
## Hinweise  
 Diese Struktur wird als Teil der Vereinigung der [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) beim Strukturieren der `dwKind` Feld der `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_METADATA` \(ein Wert aus der [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration\).  
  
 Die `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Weitere Informationen zum Interpretieren der höherwertigen Bits der Metadaten\-token\-ID finden Sie unter der `CorTokenType` Enumeration in der Datei "corhdr.h" in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)