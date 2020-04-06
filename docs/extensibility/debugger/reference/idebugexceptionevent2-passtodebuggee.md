---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729830"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Gibt an, ob die Ausnahme an das Programm übergeben werden soll, das gedebuggt wird, wenn die Ausführung fortgesetzt wird, oder ob die Ausnahme verworfen werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parameter
`fPass`\
[in] Ein Wert`TRUE`ungleich Null ( ), wenn die Ausnahme an das Programm übergeben`FALSE`werden soll, das beim Fortsetzen der Ausführung gedebuggt wird, oder Null ( ), wenn die Ausnahme verworfen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das Aufrufen dieser Methode bewirkt eigentlich nicht, dass Code in dem zu debuggenden Programm ausgeführt wird. Der Aufruf besteht lediglich darin, den Status für die nächste Codeausführung festzulegen. Beispielsweise können Aufrufe der [CanPassToDebuggee-Methode](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) mit dem `S_OK` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)zurückgegeben werden.`dwState` Feld auf `EXCEPTION_STOP_SECOND_CHANCE`.

 Die IDE empfängt möglicherweise das [IDebugExceptionEvent2-Ereignis](../../../extensibility/debugger/reference/idebugexceptionevent2.md) und ruft die [Continue-Methode](../../../extensibility/debugger/reference/idebugprogram2-continue.md) auf. Das Debugmodul (DE) sollte ein Standardverhalten aufweisen, um die Anfrage zu behandeln, wenn die `PassToDebuggee` Methode nicht aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
