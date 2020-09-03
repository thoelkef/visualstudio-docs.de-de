---
title: 'IDebugInterceptExceptionCompleteEvent2:: getinterceptcookie | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9065c0b7868efaeb70c10a3ab921a8764694662e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727779"
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
vorgenommen Eindeutiger Wert, der der abgefangenen Ausnahme zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem die [interceptaccesstexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode die Verarbeitung einer abgefangenen Ausnahme abgeschlossen hat, sendet Sie das [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) -Ereignis. Der-Handler kann die- `GetInterceptCookie` Methode verwenden, um den eindeutigen Wert abzurufen, der der Ausnahme zugeordnet ist (derselbe Wert, der an die-Methode übertragen wird `InterceptCurrentException` ).

## <a name="see-also"></a>Weitere Informationen
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
