---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 332cbb28bd175aa5c3b4187ae735a479ba9de6b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729862"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ruft eine detaillierte Beschreibung der Ausnahme ab, die dieses Ereignis ausgelöst hat.

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
[in, out] Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, die mit der Beschreibung der Ausnahme ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

 [Nur C++ Der Aufrufer ist dafür verantwortlich, alle Zeichenfolgen in der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur freizugeben und das [IDebugProgram2-Objekt](../../../extensibility/debugger/reference/idebugprogram2.md) in der Struktur freizugeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
