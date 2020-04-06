---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714103"
---
# <a name="pdb_type"></a>PDB_TYPE

Diese Struktur gibt Informationen zu einem Feldtyp an, der einem PDB-Symbol entnommen wurde.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Member

`ulAppDomainID`\
ID der Anwendung, aus der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.

`guidModule`\
Die GUID des Moduls, das dieses Feld enthält.

`symid`\
Die ID des Symbols, das diesem Feld entspricht.

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur angezeigt, wenn das `dwKind` Feld `TYPE_INFO` der Struktur auf `TYPE_KIND_PDB` (ein Wert aus der [dwTYPE_KIND-Enumeration)](../../../extensibility/debugger/reference/dwtype-kind.md) festgelegt ist.

## <a name="requirements"></a>Requirements (Anforderungen)

Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
