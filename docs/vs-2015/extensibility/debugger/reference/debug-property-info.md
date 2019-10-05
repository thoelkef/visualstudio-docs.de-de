---
title: DEBUG_PROPERTY_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4c4200cb5a44e185d50158829fe44152707ee459
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143048"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Informationen über ein Debug-Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
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
 Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder ausgefüllt werden.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 bstrName  
 Der Eigenschaftenname in einem Kontext.  
  
 bstrType  
 Der Typ der Eigenschaft als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert als formatierte Zeichenfolge.  
  
 pProperty  
 Die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) von dieser Struktur beschriebenen Objekts.  
  
 dwAttrib  
 Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die die Attribute für diese Eigenschaft beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Eine Eigenschaft ist ein Objekt von einer hierarchischen Wesens, die über einen Namen, Typ und Wert verfügt. Eine Eigenschaft kann z. B. lokale Variablen, Parameter, überwachen Sie Variablen und Ausdrücken und Registern beschrieben.  
  
 Diese Struktur wird zum Übergeben der [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode, in denen es ausgefüllt wird. Diese Struktur wird auch zurückgegeben, als Teil einer Liste der Struktur aus der [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) und [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) Methoden.  
  
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
