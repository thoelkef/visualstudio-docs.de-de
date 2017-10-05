---
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3c1ce8a931ca8687056fcf161d78b7e40260e15f
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Enthält Informationen über eine Debugeigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Member  
 dwValidFields  
 Eine Kombination aus Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) -Enumeration, der angibt, welche Felder ausgefüllt werden.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 bstrName  
 Der Eigenschaftsname in einem Kontext.  
  
 bstrType  
 Der Typ der Eigenschaft als eine formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert als eine formatierte Zeichenfolge.  
  
 pProperty  
 Die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt durch diese Struktur beschrieben.  
  
 dwAttrib  
 Eine Kombination aus Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) -Enumeration, die die Attribute für diese Eigenschaft beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Eine Eigenschaft ist ein Objekt von einer hierarchischen Struktur, die über einen Namen, Typ und Wert verfügt. Eine Eigenschaft kann z. B. lokale Variablen, Parameter, Überwachungsfenster Variablen und Ausdrücke und Register beschreiben.  
  
 Diese Struktur wird zum Übergeben der [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode, wo in gefüllt. Diese Struktur wird auch zurückgegeben, als Teil einer Liste dieser Struktur von den [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) und [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
