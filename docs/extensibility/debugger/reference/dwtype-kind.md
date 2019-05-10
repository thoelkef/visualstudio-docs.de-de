---
title: DwTYPE_KIND | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a33bdf1875426898a6db72831bee4d1d7ac1f9a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689251"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Gibt an, wie den Typ des interpretieren eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.

## <a name="syntax"></a>Syntax

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

#### <a name="parameters"></a>Parameter
TYPE_KIND_METADATA der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Union interpretiert werden soll, als eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur.

TYPE_KIND_PDB der `TYPE_INFO` Union interpretiert werden soll, als eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur.

TYPE_KIND_BUILT der `TYPE_INFO` Union interpretiert werden soll, als eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur.

## <a name="remarks"></a>Hinweise
Die Werte dieser Enumeration werden in der `dwKind` Feld der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strukturieren und werden verwendet, um zu bestimmen, wie zum Interpretieren der `type` union-Member. Die `TYPE_INFO` Struktur wird zurückgegeben, durch einen Aufruf der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
