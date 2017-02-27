---
title: "DEBUG_REFERENCE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REFERENCE_INFO"
helpviewer_keywords: 
  - "DEBUG_REFERENCE_INFO-Struktur"
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt einen Verweis.  
  
## Syntax  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```c#  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## Mitglieder  
 dwFields  
 Eine Kombination von Flags aus der [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)\-Enumeration, die angibt, welche Felder geändert werden.  
  
 bstrName  
 Der vom Benutzer angegebene Name des [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekts.  
  
 bstrType  
 Der Verweistyp als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Verweiswert als formatierte Zeichenfolge  
  
 dwAttrib  
 Eine Kombination von Flags aus der [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)\-Enumeration, die die Flags für die Debug\- Attribute Eigenschaft angibt.  
  
 dwRefType  
 Ein Wert aus der [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)\-Enumeration, die angibt, ob der schwach oder stark Verweistyp ist.  
  
 m\_pReference  
 Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekt, das die Verweisinformationen angibt.  
  
## Hinweise  
 Diese Struktur wird auf einen Aufruf an die Methode übergeben [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) ausgefüllt werden soll.  Diese Struktur wird auch als Teil einer Liste der [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)\-Schnittstelle zurückgegeben, die wiederum von einem Aufruf der [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)\-Methode zurückgegeben wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)