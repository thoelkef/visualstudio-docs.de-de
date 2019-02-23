---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cae097b5ce02993fc125aafaffded32a35dde0a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679356"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Gibt an, ob die Ausnahme übergeben werden soll, die zu debuggende Programm wird bei der Ausführung fortgesetzt wird, oder die Ausnahme verworfen werden sollen.

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

#### <a name="parameters"></a>Parameter
 `fPass`

 [in] Ungleich Null (`TRUE`), wenn die Ausnahme übergeben werden soll, die zu debuggende Programm wird bei der Ausführung fortgesetzt wird, oder 0 (null) (`FALSE`) ob die Ausnahme verworfen werden sollen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Das Aufrufen dieser Methode bewirkt nicht tatsächlich Code in das derzeit debuggte Programm ausgeführt werden soll. Der Aufruf ist lediglich zum Festlegen des Status für die nächste codeausführung. Z. B. Aufrufe von der [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) Methodenrückgabewert möglicherweise `S_OK` mit der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` Feld festgelegt, um `EXCEPTION_STOP_SECOND_CHANCE`.

 Die IDE wird möglicherweise die [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) Ereignis, und rufen die [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Methode. Die Debug-Engine (DE) müssen ein Standardverhalten zum Behandeln der Fall, wenn die `PassToDebuggee` Methode wird nicht aufgerufen.

## <a name="see-also"></a>Siehe auch
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)