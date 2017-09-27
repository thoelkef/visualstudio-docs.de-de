---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
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
ms.openlocfilehash: f4633730a3dbe09f356c3731cd48c9428b9e8890
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Gibt an, welche Informationen für eine Debug-Property-Objekt abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Die Initialisierung/verwenden die `bstrFullName` Feld.  
  
 DEBUGPROP_INFO_NAME  
 Die Initialisierung/verwenden die `bstrName` Feld.  
  
 DEBUGPROP_INFO_TYPE  
 Die Initialisierung/verwenden die `bstrType` Feld.  
  
 DEBUGPROP_INFO_VALUE  
 Die Initialisierung/verwenden die `bstrValue` Feld.  
  
 DEBUGPROP_INFO_ATTRIB  
 Die Initialisierung/verwenden die `dwAttrib` Feld.  
  
 DEBUGPROP_INFO_PROP,  
 Die Initialisierung/verwenden die `pProperty` Feld, enthält ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Gibt an, dass das Feld "Wert" den Wert automatisch erweitert für diesen Objekttyp enthalten soll.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Veraltet.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Führen Sie keine beautified Werte zurückgeben oder Mitglieder (d. h. nicht formatieren die Werte).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Führen Sie keine spezielle gebildeter Werte zurückgegeben (z. B. nicht aufrufen `ToString()` für ein Objekt zur Erzeugung eines Werts).  
  
 DEBUGPROP_INFO_NONE  
 Gibt an, dass keine Flags festgelegt sind.  
  
 DEBUGPROP_INFO_STANDARD  
 Die Initialisierung/verwenden die `dwAttrib`, `bstrName`, `bstrType`, und `bstrValue` Felder.  
  
 DEBUGPROP_INFO_All  
 Gibt eine Maske aller Flags an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden zum Übergeben der [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), und [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) Methoden angegeben, welche Felder zu initialisierenden der [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.  
  
 Diese Werte werden auch verwendet, für die `dwFields` Mitglied der `DEBUG_PROPERTY_INFO` Struktur, um anzugeben, welche Felder der Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
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
