---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737528"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Beschreibt verschiedene Arten von Adressen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Member
`dwKind`\
Ein Wert [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) aus der ADDRESS_KIND-Enumeration, der angibt, wie die Union interpretiert werden soll.

`addr.addrNative`\
[Nur C++ Enthält [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) die NATIVE_ADDRESS `dwKind` Struktur, wenn = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Nur C++ Enthält[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) die UNMANAGED_ADDRESS_THIS_RELATIVE `dwKind` Struktur, wenn = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Nur C++ Enthält[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) die UNMANAGED_ADDRESS_PHYSICAL `dwKind` Struktur, wenn = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Nur C++ Enthält[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) die METADATA_ADDRESS_METHOD `dwKind` Struktur if = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Nur C++ Enthält[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) die METADATA_ADDRESS_FIELD `dwKind` Struktur, wenn = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Nur C++ Enthält[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) die METADATA_ADDRESS_LOCAL `dwKind` Struktur if = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Nur C++ Enthält[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) die METADATA_ADDRESS_PARAM `dwKind` Struktur if = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Nur C++ Enthält[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) die METADATA_ADDRESS_ARRAYELEM `dwKind` Struktur if = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Nur C++ Enthält[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) die METADATA_ADDRESS_RETVAL `dwKind` Struktur if = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Nur C++]-Auffüllung.

`addr`\
[Nur C++ Der Name der Vereinigung.

`unionmember`\
[Nur C-Code] Dieser Wert muss basierend auf `dwKind`auf auf den entsprechenden Strukturtyp gemarshallt werden. Siehe Bemerkungen zur `dwKind` Verbindung zwischen und Zur Auslegung der Vereinigung.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist Teil der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur und stellt eine von `DEBUG_ADDRESS` mehreren verschiedenen Arten von Adressen dar (die Struktur wird durch einen Aufruf der [GetAddress-Methode](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ausgefüllt).

 [Nur C-Code] Die folgende Tabelle zeigt, `unionmember` wie das Element für jede Adressart interpretiert wird. Das Beispiel zeigt, wie dies für eine Art von Adresse geschieht.

|`dwKind`|`unionmember`interpretiert als|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt,`METADATA_ADDRESS_ARRAYELEM`wie eine `DEBUG_ADDRESS_UNION` Art von Adresse ( ) der Struktur in C' interpretiert wird. Die übrigen Elemente können genau auf die gleiche Weise interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
