---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58967be9befc7061ea8005009b1628966a93de0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349507"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Wird aufgerufen, wenn die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parameter
`pqwCookie`\
[out] Eindeutiger Wert, der der Ausnahme zugeordnet ist, die abgefangen wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Nach der [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode behandeln einer abgefangenen Ausnahme abgeschlossen wurde, sendet er die [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) Ereignis. Der Handler können die `GetInterceptCookie` Methode, um den eindeutigen Wert, der der Ausnahme zugeordnete abzurufen (den gleichen Wert, der zum Übergeben der `InterceptCurrentException` Methode).

## <a name="see-also"></a>Siehe auch
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)