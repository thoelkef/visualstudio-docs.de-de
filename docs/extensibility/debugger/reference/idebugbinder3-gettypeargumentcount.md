---
title: IDebugBinder3::GetTypeArgumentCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b34cbc89874110712ea1d630a27bd709d21894b3
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614984"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Diese Methode gibt die Anzahl von Argumenttypen, die diesem Objekt zugeordnet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>Parameter
`uCount`\
[out] Die Anzahl von Argumenttypen, die diesem Objekt zugeordnet.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der von dieser Methode zurückgegebene Wert kann verwendet werden, für die Verwendung mit einem Array Zuweisen der [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)