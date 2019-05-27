---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d37ec7c2a81b036c80e7fab30fc794d51f21703
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204277"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Diese Methode ruft ein Objekt, das ermöglicht die Enumeration, der die Liste der persistenten Ports ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`PortNames`\
[in] Ein [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Struktur, die eine Liste der Anschlussnamen gesucht und zurückgegeben, die zwischen der beibehaltenen Ports enthält. Nur die beibehaltenen Ports mit diesen Namen werden zurückgegeben.

`ppEnum`\
[out] Ein Objekt, implementiert die [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Persistente Ports werden geladen, wenn ein portanbieters instanziiert und gespeichert, wenn die anschlusslieferant zerstört wird.

## <a name="see-also"></a>Siehe auch
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)