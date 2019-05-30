---
title: IDebugBinder::GetFunctionObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03078a09de94b886a659059192a5b67430cb5137
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337664"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Diese Methode ruft eine [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Objekt verwendet, um Funktionsparameter zu erstellen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parameter
`ppFunction`\
[out] Gibt die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle, die verwendet wird, um Funktionsparameter zu erstellen.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)