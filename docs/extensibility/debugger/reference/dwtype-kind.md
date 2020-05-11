---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737195"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Gibt an, wie der Typ eines [IDebugField-Objekts](../../../extensibility/debugger/reference/idebugfield.md) interpretiert werden soll.

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

## <a name="fields"></a>Felder
`TYPE_KIND_METADATA`\
Die [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Union sollte als [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur interpretiert werden.

`TYPE_KIND_PDB`\
Die `TYPE_INFO` Union sollte als [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur interpretiert werden.

`TYPE_KIND_BUILT`\
Die `TYPE_INFO` Union sollte als [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur interpretiert werden.

## <a name="remarks"></a>Bemerkungen
Die Werte dieser Enumeration `dwKind` werden im Feld der [TYPE_INFO-Struktur](../../../extensibility/debugger/reference/type-info.md) angezeigt `type` und werden verwendet, um zu bestimmen, wie das Union-Mitglied interpretiert wird. Die `TYPE_INFO` Struktur wird durch einen Aufruf der [GetTypeInfo-Methode](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
