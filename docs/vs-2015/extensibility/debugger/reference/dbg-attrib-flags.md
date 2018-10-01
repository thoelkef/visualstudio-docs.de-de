---
title: DBG_ATTRIB_FLAGS | Microsoft-Dokumentation
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
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b34dbc0caa75ee33d19df51e5dcefce3f7f40601
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513148"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DBG_ATTRIB_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/dbg-attrib-flags).  
  
Beschreibt verschiedene Attribute für eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oder [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Schnittstelle. Mitglied der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```csharp  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## <a name="members"></a>Member  
 DBG_ATTRIB_NONE  
 Gibt keine Attribute an.  
  
 DBG_ATTRIB_ALL  
 Gibt alle Attribute an.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 Gibt an, dass der Verweis oder die Eigenschaft über untergeordnete Elemente verfügt.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 Gibt an, dass eine ID für dieses Objekt erstellt wurde.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 Gibt an, dass eine ID für dieses Objekt erstellt werden kann.  
  
 DBG_ATTRIB_VALUE_READONLY  
 Gibt an, dass der Wert schreibgeschützt ist.  
  
 DBG_ATTRIB_VALUE_ERROR  
 Gibt an, dass der Wert einen Fehler.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 Gibt an, dass es sich bei die Auswertung einen Nebeneffekt haben.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 Gibt an, dass diese Eigenschaft wirklich ein Container für Überladungen.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist ein boolescher Wert.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist ein boolescher Wert und `TRUE`.  
  
 DBG_ATTRIB_VALUE_INVALID  
 Gibt an, dass der Wert im `DEBUG_PROPERTY_INFO::bstrValue` ungültig ist.  
  
 DBG_ATTRIB_VALUE_NAT  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist "*nicht etwas*" (NAT). NAT wird beschrieben, ein Register-Flag Intel 64-Bit-Prozessoren, der zurückgestellte spekulative Ausnahmen angibt.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` wurde möglicherweise automatisch erweitert.  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 Gibt an, dass eine Auswertung überschritten hat.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` eine unformatierte Zeichenfolge dargestellt werden kann.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 Gibt an, dass diese Eigenschaft über mindestens einen benutzerdefinierten Viewer zugeordnet ist.  
  
 DBG_ATTRIB_ACCESS_NONE  
 Gibt ein Objekt, das keine `public`, `private`, noch `protected` Geben Sie den Zugriff.  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 Gibt ein Objekt mit öffentlichem Zugriff an.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 Gibt ein Objekt mit privatem Zugriff an.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 Gibt ein Objekt mit geschütztem Zugriff an.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 Gibt ein Objekt mit endgültigem Zugriff an.  
  
 DBG_ATTRIB_ACCESS_ALL  
 Maske, die die Zugriffsattribute aus extrahieren `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_STORAGE_NONE  
 Gibt an, dass kein Storage-Typ angegeben.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 Zeigt einen globalen Speicher an.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 Zeigt einen statischen Speicher an.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 Gibt an, Speicher, in der Registrierung.  
  
 DBG_ATTRIB_STORAGE_ALL  
 Maske zum Extrahieren der Attribute des vom `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_TYPE_NONE  
 Gibt an, dass keine Typmodifizierer.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 Gibt an, dass der Typ des Objekts virtuell ist.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 Gibt an, dass der Objekttyp konstant ist.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 Gibt an, dass der Typ des Objekts synchronisiert wird.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 Gibt an, dass der Typ des Objekts "volatile" ist.  
  
 DBG_ATTRIB_TYPE_ALL  
 Maske, die die Attribute des Typs von extrahieren `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_DATA  
 Gibt an, dass dieses Objekt ein Datenfeld ist.  
  
 DBG_ATTRIB_METHOD  
 Gibt an, dass dieses Objekt eine Methode.  
  
 DBG_ATTRIB_PROPERTY  
 Gibt an, dass dieses Objekt eine Eigenschaft ist.  
  
 DBG_ATTRIB_CLASS  
 Gibt an, dass dieses Objekt einer Klasse ist.  
  
 DBG_ATTRIB_BASECLASS  
 Gibt an, dass dieses Objekt eine Basisklasse ist.  
  
 DBG_ATTRIB_INTERFACE  
 Gibt an, dass dieses Objekt über eine Schnittstelle ist.  
  
 DBG_ATTRIB_INNERCLASS  
 Gibt an, dass dieses Objekt den einer inneren Klasse ist.  
  
 DBG_ATTRIB_MOSTDERIVED  
 Gibt an, dass dieses Objekt ist "*am stärksten abgeleiteten*". Der Begriff "*am stärksten abgeleiteten*" bedeutet, dass der tatsächliche Typ des Objekts und nicht den Typ, der den Verweis.  
  
 DBG_ATTRIB_CHILD_ALL  
 Gibt eine Maske von `DBG_ATTRIB_DATA` über `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 Gibt an, dass das Objekt mehrere benutzerdefinierten Viewer zugeordnet ist.  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Die Werte in dieser Enumeration werden nicht tatsächlich in der Assembly für C#-Code definiert. Stattdessen müssen Sie die Definitionen in der Quelldatei kopieren.  
  
 Diese Flags werden auch verwendet, um die untergeordneten Elemente eines Objekts, z. B. filtern, wenn als Argument übergeben [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Die Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
 Die `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Flag weist darauf hin, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zum Abrufen der [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus der [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle, und rufen [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) eine Liste der benutzerdefinierten Viewer.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

