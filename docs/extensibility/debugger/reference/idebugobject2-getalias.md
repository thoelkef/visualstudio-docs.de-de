---
title: IDebugObject2::GetAlias | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db9156e01843e859a2279e43f73c00bee21b3e9c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308742"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ruft den Alias, der dieses Objekt zugeordnete ab, sofern vorhanden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parameter
`ppAlias`\
[out] Gibt eine [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Objekt, das den Alias für dieses Objekt darstellt, andernfalls einen null-Wert.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Erstellt ein Alias für ein Objekt durch einen Aufruf der [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)