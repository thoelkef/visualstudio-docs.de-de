---
title: DEBUG_ADDRESS | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
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
> Dieser Wert ist spezifisch für einen Symbolanbieter und hat daher keine andere allgemeine Bedeutung als als Bezeichner für einen Klassentyp.

`addr`\
Eine [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, die eine Vereinigung von Strukturen enthält, die die einzelnen Adresstypen beschreiben. Der `addr`Wert .`dwKind` stammt aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Aufzählung, in der erklärt wird, wie die Gewerkschaft zu interpretieren ist.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetAddress-Methode](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) übergeben, die ausgefüllt werden soll.

**Warnung [nur C++**

Wenn `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` dies `addr.addr.addrLocal.pLocal` der Fall ist und wenn `Release` es sich nicht um einen Nullwert handelt, müssen Sie den Tokenzeiger aufrufen:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
