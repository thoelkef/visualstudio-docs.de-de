---
title: DBG_ATTRIB_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 831d1326d88e70ffaba2cc0c242c55d7325be705
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689329"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Beschreibt verschiedene Attribute für eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oder [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Schnittstelle. Mitglied der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.

## <a name="syntax"></a>Syntax

```cpp
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
 DBG_ATTRIB_NONE gibt keine Attribute.

 DBG_ATTRIB_ALL gibt alle Attribute an.

 DBG_ATTRIB_OBJ_IS_EXPANDABLE gibt an, dass der Verweis oder die Eigenschaft über untergeordnete Elemente verfügt.

 DBG_ATTRIB_OBJ_HAS_ID gibt an, dass eine ID für dieses Objekt erstellt wurde.

 DBG_ATTRIB_OBJ_CAN_HAVE_ID gibt an, dass eine ID für dieses Objekt erstellt werden kann.

 DBG_ATTRIB_VALUE_READONLY gibt an, dass der Wert schreibgeschützt ist.

 DBG_ATTRIB_VALUE_ERROR gibt an, dass der Wert einen Fehler.

 DBG_ATTRIB_VALUE_SIDE_EFFECT gibt an, dass es sich bei die Auswertung einen Nebeneffekt haben.

 DBG_ATTRIB_OVERLOADED_CONTAINER gibt an, dass diese Eigenschaft wirklich ein Container für Überladungen.

 DBG_ATTRIB_VALUE_BOOLEAN gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist ein boolescher Wert.

 DBG_ATTRIB_VALUE_BOOLEAN_TRUE gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist ein boolescher Wert und `TRUE`.

 DBG_ATTRIB_VALUE_INVALID gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist ungültig.

 DBG_ATTRIB_VALUE_NAT gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ist "*nicht etwas*" (NAT). NAT wird beschrieben, ein Register-Flag Intel 64-Bit-Prozessoren, der zurückgestellte spekulative Ausnahmen angibt.

 DBG_ATTRIB_VALUE_AUTOEXPANDED gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` wurde möglicherweise automatisch erweitert.

 DBG_ATTRIB_VALUE_TIMEOUT gibt an, die eine Auswertung überschritten hat.

 DBG_ATTRIB_VALUE_RAW_STRING gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` eine unformatierte Zeichenfolge dargestellt werden kann.

 DBG_ATTRIB_VALUE_CUSTOM_VIEWER gibt an, die diese Eigenschaft über mindestens einen benutzerdefinierten Viewer zugeordnet hat.

 DBG_ATTRIB_ACCESS_NONE gibt ein Objekt, das keine `public`, `private`, noch `protected` Geben Sie den Zugriff.

 DBG_ATTRIB_ACCESS_PUBLIC gibt ein Objekt mit öffentlichen Zugriff an.

 DBG_ATTRIB_ACCESS_PRIVATE gibt ein Objekt mit privatem Zugriff an.

 DBG_ATTRIB_ACCESS_PROTECTED gibt ein Objekt, das geschütztem Zugriff an.

 DBG_ATTRIB_ACCESS_FINAL gibt ein Objekt mit endgültigem Zugriff an.

 DBG_ATTRIB_ACCESS_ALL-Maske, die den Zugriff zu extrahieren, Attribute aus `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_STORAGE_NONE gibt an, die es kein Storage-Typ angegeben ist.

 Globaler Speicher DBG_ATTRIB_STORAGE_GLOBAL angibt.

 Gibt an, DBG_ATTRIB_STORAGE_STATIC statischen Speicher.

 Speicher DBG_ATTRIB_STORAGE_REGISTER gibt an, in der Registrierung.

 DBG_ATTRIB_STORAGE_ALL-Maske, die den Speicher extrahieren Attribute `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_TYPE_NONE gibt an, dass keine Typmodifizierer.

 DBG_ATTRIB_TYPE_VIRTUAL gibt an, dass der Typ des Objekts virtuell ist.

 DBG_ATTRIB_TYPE_CONSTANT gibt an, dass der Typ des Objekts konstant ist.

 DBG_ATTRIB_TYPE_SYNCHRONIZED gibt an, dass der Typ des Objekts synchronisiert wird.

 DBG_ATTRIB_TYPE_VOLATILE gibt an, dass der Typ des Objekts "volatile" ist.

 DBG_ATTRIB_TYPE_ALL-Maske, extrahieren Sie den Typ Attribute `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_DATA gibt an, dass dieses Objekt ein Datenfeld ist.

 DBG_ATTRIB_METHOD gibt an, dass dieses Objekt eine Methode.

 DBG_ATTRIB_PROPERTY gibt an, dass dieses Objekt eine Eigenschaft ist.

 DBG_ATTRIB_CLASS gibt an, dass dieses Objekt einer Klasse ist.

 DBG_ATTRIB_BASECLASS gibt an, dass dieses Objekt eine Basisklasse ist.

 DBG_ATTRIB_INTERFACE gibt an, dass dieses Objekt über eine Schnittstelle ist.

 DBG_ATTRIB_INNERCLASS gibt an, dass dieses Objekt den einer inneren Klasse ist.

 DBG_ATTRIB_MOSTDERIVED gibt an, die dieses Objekt ist "*am stärksten abgeleiteten*". Der Begriff "*am stärksten abgeleiteten*" bedeutet, dass der tatsächliche Typ des Objekts und nicht den Typ, der den Verweis.

 DBG_ATTRIB_CHILD_ALL gibt an, der Subnetzmaske `DBG_ATTRIB_DATA` über `DBG_ATTRIB_MOSTDERIVED`.

 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS gibt an, der das Objekt mehrere benutzerdefinierten Viewer zugeordnet ist.

## <a name="remarks"></a>Hinweise

> [!NOTE]
>  Die Werte in dieser Enumeration werden nicht tatsächlich in der Assembly für C#-Code definiert. Stattdessen müssen Sie die Definitionen in der Quelldatei kopieren.

 Diese Flags werden auch verwendet, um die untergeordneten Elemente eines Objekts, z. B. filtern, wenn als Argument übergeben [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Die Werte können kombiniert werden, mit einer bitweisen `OR`.

 Die `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Flag weist darauf hin, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zum Abrufen der [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus der [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle, und rufen [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) eine Liste der benutzerdefinierten Viewer.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)