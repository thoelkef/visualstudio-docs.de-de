---
title: IDebugExceptionEvent2::GetException | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 691df8f5a212f1d854d87076a215402c7ce0053c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310509"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ruft eine ausführliche Beschreibung der Ausnahme, die dieses Ereignis ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parameter
`pExceptionInfo`\
[in, out] Ein [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die mit der Beschreibung der Ausnahme gefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise

 [C++ nur] Der Aufrufer ist verantwortlich für das Freigeben von Zeichenfolgen in die [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur sowie die Freigabe der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt in der Struktur.

## <a name="see-also"></a>Siehe auch
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)