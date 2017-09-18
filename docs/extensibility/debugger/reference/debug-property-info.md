---
title: "DEBUG_PROPERTY_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_PROPERTY_INFO"
helpviewer_keywords: 
  - "DEBUG_PROPERTY_INFO-Struktur"
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält Informationen über eine Eigenschaft.  
  
## Syntax  
  
```cpp#  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```c#  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## Mitglieder  
 dwValidFields  
 Eine Kombination von Flags aus der [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)\-Enumeration, die angibt, welche Felder aufgefüllt werden.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 bstrName  
 Der Eigenschaftenname in einem Kontext.  
  
 bstrType  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert als formatierte Zeichenfolge.  
  
 pProperty  
 Das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) von dieser Struktur beschriebenen Objekts.  
  
 dwAttrib  
 Eine Kombination von Flags aus der [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)\-Enumeration, die die Attribute dieser Eigenschaft beschreibt.  
  
## Hinweise  
 Eine Eigenschaft ist ein Objekt einer hierarchischen Natur, die einen Namen, einen Typ und einen Wert verfügt.  Beispielsweise kann eine Eigenschaft lokale Variablen, Parametern, Variablen und Ausdrücke und Überwachen Register beschreiben.  
  
 Diese Struktur wird auf die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\-Methode übergeben, in der er eingetragen wird.  Diese Struktur wird auch als Teil einer Liste dieser Struktur aus der [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)\-Schnittstelle zurückgegeben, die wiederum von einem Aufruf der [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) und [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)\-Methoden zurückgegeben wurde.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)