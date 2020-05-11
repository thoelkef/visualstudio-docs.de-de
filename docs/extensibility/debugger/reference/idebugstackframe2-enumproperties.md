---
title: IDebugStackFrame2::EnumProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719901"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Erstellt einen Enumerator für Eigenschaften, die dem Stapelrahmen zugeordnet sind, z. B. lokale Variablen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
[in] Eine Kombination von Flags aus der DEBUGPROP_INFO_FLAGS-Enumeration, die angibt, welche Felder in den aufgezählten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen ausgefüllt werden sollen. [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)

`nRadix`\
[in] Der Radix, der zum Formatieren numerischer Informationen verwendet werden soll.

`refiid`\
[in] Eine GUID eines Filters, [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) der verwendet wird, um auszuwählen, `guidFilterLocals`welche DEBUG_PROPERTY_INFO Strukturen aufgezählt werden sollen, z. B. .

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`pcelt`\
[out] Gibt die Anzahl der aufgezählten Eigenschaften zurück. Dies ist dasselbe wie das Aufrufen der [GetCount-Methode.](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)

`ppEnum`\
[out] Gibt ein [IEnumDebugPropertyInfo2-Objekt](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zurück, das eine Liste der gewünschten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Da diese Methode das Abrufen aller ausgewählten Eigenschaften mit einem einzelnen Aufruf ermöglicht, ist sie schneller als der sequenzielle Aufruf der [GetDebugProperty-](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) und [EnumChildren-Methoden.](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
