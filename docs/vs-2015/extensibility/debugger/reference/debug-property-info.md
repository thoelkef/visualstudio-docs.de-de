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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143048"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Informationen über eine Debug-Eigenschaft.  
  
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
 dwvalidfields  
 Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, die angibt, welche Felder ausgefüllt werden.  
  
 bstraufullname  
 Der vollständige Name der Eigenschaft.  
  
 bstrName  
 Der Eigenschaftsname innerhalb eines Kontexts.  
  
 bstrintype  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 bstrauvalue  
 Der Eigenschafts Wert als formatierte Zeichenfolge.  
  
 pproperty  
 Das von dieser-Struktur beschriebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt.  
  
 dwattenb  
 Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) -Enumeration, die die Attribute dieser Eigenschaft beschreibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Eigenschaft ist ein Objekt einer hierarchischen Natur, das einen Namen, einen Typ und einen Wert hat. Eine Eigenschaft kann z. b. lokale Variablen, Parameter, Überwachungs Variablen und Ausdrücke beschreiben und registriert werden.  
  
 Diese Struktur wird an die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode übermittelt, wo Sie ausgefüllt ist. Diese Struktur wird auch als Teil einer Liste dieser Struktur von der [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Schnittstelle zurückgegeben, die wiederum von einem Rückruf der [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode und der [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) -Methode zurückgegeben wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [Enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
