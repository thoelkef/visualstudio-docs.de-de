---
title: TYPE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86212a5ef6f417dae2ae345b1367e041c3cf9095
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316132"
---
# <a name="typeinfo"></a>TYPE_INFO
Diese Struktur gibt die verschiedenen Arten von Informationen zum Typ des Felds an.

## <a name="syntax"></a>Syntax

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Member
 `dwKind`\
 Ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) -Enumeration, der bestimmt, wie die Union zu interpretieren.

 `type.typeMeta`\
 [C++ nur] Enthält eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_METADATA`.

 `type.typePdb`\
 [C++ nur] Enthält eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_PDB`.

 `type.typeBuilt`\
 [C++ nur] Enthält eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_BUILT`.

 `type.unused`\
 Nicht verwendete Abstand.

 `type`\
 Die Namen der Union.

 `unionmember`\
 [C# nur] Marshallen, die diese Option, um den entsprechenden Strukturtyp basierend auf `dwKind`.

## <a name="remarks"></a>Hinweise
 Diese Struktur wird zum Übergeben der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) Methode, in denen es ausgefüllt wird. Wie der Inhalt der Struktur interpretiert werden basiert auf der `dwKind` Feld.

> [!NOTE]
> [C++ nur] Wenn `dwKind` gleich `TYPE_KIND_BUILT`, ist es erforderlich, um den zugrunde liegenden freizugeben [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt beim Zerstören der `TYPE_INFO` Struktur. Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()` aufgerufen.

 [C# nur] Die folgende Tabelle zeigt die Interpretation der `unionmember` Element für jede Art von Typ. Im Beispiel wird gezeigt, wie dies für eine Art von Typ erfolgt.

|`dwKind`|`unionmember` interpretiert als|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Beispiel
 In diesem Beispiel wird gezeigt, wie zum Interpretieren der `unionmember` Mitglied der `TYPE_INFO` Struktur in C# geschrieben. Dieses Beispiel zeigt nur eine Art interpretieren (`TYPE_KIND_METADATA`), aber die anderen auf genau die gleiche Weise interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)