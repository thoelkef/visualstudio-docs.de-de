---
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9070fcfbf79fb96ecff87a793c221f3e7a65c2ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713289"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
Diese Struktur stellt eine physische Adresse dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Member
 `offset`\
 Ein 64-Bit-Offset in einen physischen Adressraum.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur ist Teil der Union in `dwKind` der `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, `ADDRESS_KIND_UNMANAGED_PHYSICAL` wenn das Feld der Struktur auf (ein Wert aus der ADDRESS_KIND-Enumeration) festgelegt ist. [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
