---
title: DEBUGPROP_INFO_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 999b9af039513782439ca89826f54c94da79546f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511132"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DEBUGPROP_INFO_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debugprop-info-flags).  
  
Gibt an, welche Informationen Sie über ein Debug-Eigenschaft-Objekt abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 DEBUGPROP_INFO_FULLNAME  
 Initialisieren und Verwenden der `bstrFullName` Feld.  
  
 DEBUGPROP_INFO_NAME  
 Initialisieren und Verwenden der `bstrName` Feld.  
  
 DEBUGPROP_INFO_TYPE  
 Initialisieren und Verwenden der `bstrType` Feld.  
  
 DEBUGPROP_INFO_VALUE  
 Initialisieren und Verwenden der `bstrValue` Feld.  
  
 DEBUGPROP_INFO_ATTRIB  
 Initialisieren und Verwenden der `dwAttrib` Feld.  
  
 DEBUGPROP_INFO_PROP,  
 Initialisieren und Verwenden der `pProperty` Feld mit einem [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Gibt an, dass das Feld "Wert" den Wert automatisch erweitert, für diesen Objekttyp enthalten soll.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Veraltet.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Alle Werte verschönert bzw. die Elemente keine zurück (d. h. nicht formatieren die Werte).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Ist keine spezielle synthetischen Werte zurückgegeben (rufen Sie z. B. nicht `ToString()` auf ein Objekt, das einen Wert zu erzeugen).  
  
 DEBUGPROP_INFO_NONE  
 Gibt an, dass keine Flags festgelegt sind.  
  
 DEBUGPROP_INFO_STANDARD  
 Initialisieren und Verwenden der `dwAttrib`, `bstrName`, `bstrType`, und `bstrValue` Felder.  
  
 DEBUGPROP_INFO_All  
 Gibt eine Maske aller Flags an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden übergeben, um die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), und [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) Methoden, um anzugeben, welche Felder initialisiert werden, werden die [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.  
  
 Diese Werte werden auch verwendet, für die `dwFields` Mitglied der `DEBUG_PROPERTY_INFO` Struktur, um anzugeben, welche Felder der Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

