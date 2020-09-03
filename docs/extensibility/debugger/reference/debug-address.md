---
title: DEBUG_ADDRESS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737522"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Diese Struktur stellt eine Adresse dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Member
`ulAppDomainID`\
Die Prozess-ID.

`guidModule`\
Die GUID des Moduls, das diese Adresse enthält.

`tokClass`\
Das Token, das die Klasse oder den Typ dieser Adresse identifiziert.

> [!NOTE]
> Dieser Wert ist für einen Symbol Anbieter spezifisch und hat daher keine allgemeine Bedeutung, außer als Bezeichner für einen Klassentyp.

`addr`\
Eine [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, die eine Union von-Strukturen enthält, die die einzelnen Adresstypen beschreiben. Der-Wert `addr` .`dwKind` stammt aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) -Enumeration, in der die Interpretation der Union erläutert wird.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) -Methode, die ausgefüllt werden soll, übermittelt.

**Warnung [nur C++]**

Wenn `addr.dwKind` ist `ADDRESS_KIND_METADATA_LOCAL` und wenn `addr.addr.addrLocal.pLocal` kein NULL-Wert ist, müssen Sie `Release` für den tokenzeiger aufzurufen:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Anforderungen
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
