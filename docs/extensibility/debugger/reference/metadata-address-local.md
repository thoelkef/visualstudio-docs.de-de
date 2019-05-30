---
title: METADATA_ADDRESS_LOCAL | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8500d7ad1e03e08fa852afe9b8b77e49562f355
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345635"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL

Diese Struktur stellt die Adresse einer lokalen Variablen in einem Gültigkeitsbereich (in der Regel eine Funktion oder Methode) dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Member

`tokMethod`\
Die ID der Methode oder der Funktion ist die lokale Variable Teil.

[C++] `_mdToken` ist eine `typedef` für eine 32-Bit- `int`.

`pLocal`\
Das Token, dessen Adresse dieser Struktur darstellt.

`dwIndex`\
Der Index dieser lokalen Variablen in der Methode oder Funktion oder einen anderen Wert (sprachspezifischen) kann sein.

## <a name="remarks"></a>Hinweise

Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Kontostruktur, wenn die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur nastaven NA hodnotu `ADDRESS_KIND_LOCAL` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) die Enumeration).

> [!WARNING]
> [C++ nur] Wenn `pLocal` nicht null ist, dann Sie aufrufen müssen `Release` für den token auf (`addr` ist ein Feld in der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Anforderungen

Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch

- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
