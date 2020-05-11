---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738151"
---
# <a name="address_kind"></a>ADDRESS_KIND
Gibt die Arten von Adressen an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Felder
`ADDRESS_KIND_NATIVE`\
Eine systemeigene Adresse, die durch die [NATIVE_ADDRESS-Struktur](../../../extensibility/debugger/reference/native-address.md) dargestellt wird.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Eine nicht verwaltete `this` Adresse`Me` relativ zu einem (in Visual Basic) Zeiger und durch die [UNMANAGED_ADDRESS_THIS_RELATIVE-Struktur](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) dargestellt.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Eine nicht verwaltete physische Adresse, die durch die [UNMANAGED_ADDRESS_PHYSICAL-Struktur](../../../extensibility/debugger/reference/unmanaged-address-physical.md) dargestellt wird.

`ADDRESS_KIND_METHOD`\
Eine Methode einer Klasse, die durch die [METADATA_ADDRESS_METHOD-Struktur](../../../extensibility/debugger/reference/metadata-address-method.md) dargestellt wird.

`ADDRESS_KIND_FIELD`\
Ein Feld einer Klasse, dargestellt durch die [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur.

`ADDRESS_KIND_LOCAL`\
Die Adresse ist für eine lokale Variable und wird durch die [METADATA_ADDRESS_LOCAL-Struktur](../../../extensibility/debugger/reference/metadata-address-local.md) dargestellt.

`ADDRESS_KIND_PARAM`\
Ein Methoden- oder Funktionsparameter, der durch die [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur dargestellt wird.

`ADDRESS_KIND_ARRAYELEM`\
Ein Arrayelement, das durch die [METADATA_ADDRESS_ARRAYELEM-Struktur](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) dargestellt wird.

`ADDRESS_KIND_RETVAL`\
Ein Rückgabewert, der durch die [METADATA_ADDRESS_RETVAL-Struktur](../../../extensibility/debugger/reference/metadata-address-retval.md) dargestellt wird.

## <a name="remarks"></a>Bemerkungen
Die [GetAddress-Methode](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) gibt die [DEBUG_ADDRESS-Struktur](../../../extensibility/debugger/reference/debug-address.md) zurück, die eine Vereinigung möglicher Strukturen, die [DEBUG_ADDRESS_UNION-Struktur](../../../extensibility/debugger/reference/debug-address-union.md) enthält. Das `dwKind` Feld `DEBUG_ADDRESS_UNION` der Struktur `ADDRESS_KIND` enthält den Wert und beschreibt, wie das Union-Feld interpretiert wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
