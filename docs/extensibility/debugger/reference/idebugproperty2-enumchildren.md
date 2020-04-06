---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721513"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Ruft eine Liste der untergeordneten Elemente der Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Flags aus der DEBUGPROP_INFO_FLAGS-Enumeration, die angibt, welche Felder in den aufgezählten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen ausgefüllt werden sollen. [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)

`dwRadix`\
[in] Gibt den Radix an, der beim Formatieren numerischer Informationen verwendet werden soll.

`guidFilter`\
[in] GUID des Filters, `dwAttribFilter` der `pszNameFilter` mit dem `DEBUG_PROPERTY_INFO` und Parametern verwendet wird, um auszuwählen, welche untergeordneten Elemente aufgezählt werden sollen. `guidFilterLocals` Filtert beispielsweise nach lokalen Variablen.

`dwAttribFilter`\
[in] Eine Kombination von Flags aus der DBG_ATTRIB_FLAGS-Enumeration, die angibt, `DBG_ATTRIB_METHOD` welcher Objekttyp aufgezählt werden soll, z. B. für alle Methoden, die untergeordnete Methoden dieser Eigenschaft sein könnten. [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Wird in Kombination `guidFilter` `pszNameFilter` mit den und Parametern verwendet.

`pszNameFilter`\
[in] Der Name des Filters, `guidFilter` `dwAttribFilter` der mit `DEBUG_PROPERTY_INFO` dem und den Parametern verwendet wird, um auszuwählen, welche untergeordneten Elemente aufgezählt werden sollen. Wenn Sie diesen Parameter beispielsweise auf "MyX"-Filter für alle untergeordneten Elemente mit dem Namen "MyX" festlegen.

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`ppEnum`\
[out] Gibt ein [IEnumDebugPropertyInfo2-Objekt](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zurück, das eine Liste der untergeordneten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
