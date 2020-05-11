---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713320"
---
# <a name="type_info"></a>TYPE_INFO
Diese Struktur gibt verschiedene Arten von Informationen über den Typ eines Felds an.

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
 Ein Wert [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) aus der dwTYPE_KIND-Enumeration, die bestimmt, wie die Union interpretiert wird.

 `type.typeMeta`\
 [Nur C++ Enthält [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) eine METADATA_TYPE `dwKind` `TYPE_KIND_METADATA`Struktur, wenn dies ist.

 `type.typePdb`\
 [Nur C++ Enthält [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) eine PDB_TYPE `dwKind` `TYPE_KIND_PDB`Struktur, wenn dies ist.

 `type.typeBuilt`\
 [Nur C++ Enthält [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) eine BUILT_TYPE `dwKind` `TYPE_KIND_BUILT`Struktur, wenn dies der Fall ist.

 `type.unused`\
 Nicht verwendete Polsterung.

 `type`\
 Name der Gewerkschaft.

 `unionmember`\
 [Nur C-Code] Marshallieren Sie dies auf `dwKind`den entsprechenden Strukturtyp basierend auf .

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetTypeInfo-Methode](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) übergeben, bei der sie ausgefüllt wird. Wie der Inhalt der Struktur interpretiert `dwKind` wird, basiert auf dem Feld.

> [!NOTE]
> [Nur C++ Wenn `dwKind` gleich `TYPE_KIND_BUILT`, dann ist es notwendig, das zugrunde `TYPE_INFO` liegende [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) freizugeben, wenn die Struktur zerstört wird. Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()` aufgerufen.

 [Nur C-Code] Die folgende Tabelle zeigt, `unionmember` wie das Element für jede Art von Typ interpretiert wird. Das Beispiel zeigt, wie dies für eine Art von Typ durchgeführt wird.

|`dwKind`|`unionmember`interpretiert als|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Beispiel
 In diesem Beispiel wird `unionmember` gezeigt, `TYPE_INFO` wie das Element der Struktur in C- interpretiert wird. Dieses Beispiel zeigt, wie`TYPE_KIND_METADATA`nur ein Typ interpretiert wird ( ), aber die anderen werden genau auf die gleiche Weise interpretiert.

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

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
