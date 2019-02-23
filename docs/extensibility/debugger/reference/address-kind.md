---
title: ADDRESS_KIND | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71888e4e0b339b9b9b94946e8d9c49f8ffb1f84c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696819"
---
# <a name="addresskind"></a>ADDRESS_KIND
Gibt die Arten der Adressen.

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

## <a name="terms"></a>Begriffe
ADDRESS_KIND_NATIVE eine native Adresse, dargestellt durch die [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur.

ADDRESS_KIND_UNMANAGED_THIS_RELATIVE eine nicht verwaltete, relativ zur Adresse einer `this` (`Me` in Visual Basic) Zeiger und dargestellt werden, indem die [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur.

ADDRESS_KIND_UNMANAGED_PHYSICAL eine nicht verwaltete physische Adresse, dargestellt durch die [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur.

ADDRESS_KIND_METHOD eine Methode einer Klasse, dargestellt durch die [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur.

ADDRESS_KIND_FIELD ein Feld einer Klasse, dargestellt durch die [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur.

ADDRESS_KIND_LOCAL die Adresse wird für eine lokale Variable und wird durch die [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur.

ADDRESS_KIND_PARAM eine Methode oder Funktion Parameters, dargestellt durch die [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur.

ADDRESS_KIND_ARRAYELEM ein Arrayelement, dargestellt durch die [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur.

ADDRESS_KIND_RETVAL ein Rückgabewert, dargestellt durch die [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur.

## <a name="remarks"></a>Hinweise
Die [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Methode gibt die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die eine Union mit Strukturen zu möglich, enthält die [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur. Die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur enthält die `ADDRESS_KIND` Wert ein, und beschreibt, wie Sie das Feld der union zu interpretieren.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
