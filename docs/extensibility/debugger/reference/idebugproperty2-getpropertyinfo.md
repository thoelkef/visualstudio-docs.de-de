---
title: IDebugProperty2::GetPropertyInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ec1c3e29e0dbb6ca069dec696e6645a159ec7e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721364"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Ruft die [DEBUG_PROPERTY_INFO-Struktur](../../../extensibility/debugger/reference/debug-property-info.md) ab, die eine Eigenschaft beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Werten aus der DEBUGPROP_INFO_FLAGS-Enumeration, die angibt, welche Felder in der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) `pPropertyInfo` Struktur ausgefüllt werden sollen.

`nRadix`\
[in] Radix, das zum Formatieren numerischer Informationen verwendet werden soll.

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`rgpArgs`\
[in, out] Reserviert für die zukünftige Verwendung; auf einen NULL-Wert festgelegt.

`dwArgCount`\
[in] Reserviert für die zukünftige Verwendung; auf Null gesetzt.

`pPropertyInfo`\
[out] Eine [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur, die mit der Beschreibung der Eigenschaft ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
