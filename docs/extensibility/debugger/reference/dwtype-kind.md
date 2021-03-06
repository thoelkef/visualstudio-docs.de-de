---
title: dwTYPE_KIND | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737195"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Gibt an, wie der Typ eines [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekts interpretiert werden soll.

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
Die Werte dieser Enumeration `dwKind` werden im-Feld der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur angezeigt und werden verwendet, um zu bestimmen, wie das `type` Unionmember interpretiert werden soll. Die- `TYPE_INFO` Struktur wird durch einen Aufrufen der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
