---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719482"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Wird vom Debugger auf dem aktuellen Stapelrahmen aufgerufen, wenn er die aktuelle Ausnahme abfangen möchte.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parameter
`dwFlags`\
[in] Gibt verschiedene Aktionen an. Derzeit wird [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) nur `IEA_INTERCEPT` der INTERCEPT_EXCEPTION_ACTION Wert unterstützt und muss angegeben werden.

`pqwCookie`\
[out] Eindeutiger Wert, der eine bestimmte Ausnahme identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

 Im Folgenden finden Sie die häufigsten Fehlerrückgaben.

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Die aktuelle Ausnahme kann nicht abgefangen werden.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Der aktuelle Ausführungsframe wurde noch nicht nach einem Handler durchsucht.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Diese Methode wird für diesen Frame nicht unterstützt.|

## <a name="remarks"></a>Bemerkungen
 Wenn eine Ausnahme ausgelöst wird, erhält der Debugger die Kontrolle über die Laufzeit an Schlüsselpunkten während des Ausnahmebehandlungsvorgangs. In diesen Schlüsselmomenten kann der Debugger den aktuellen Stapelrahmen fragen, ob der Frame die Ausnahme abfangen möchte. Auf diese Weise ist eine abgefangene Ausnahme im Wesentlichen ein spontaner Ausnahmehandler für einen Stapelrahmen, auch wenn dieser Stapelframe keinen Ausnahmehandler hat (z. B. ein try/catch-Block im Programmcode).

 Wenn der Debugger wissen möchte, ob die Ausnahme abgefangen werden soll, ruft er diese Methode für das aktuelle Stapelframeobjekt auf. Diese Methode ist für die Behandlung aller Details der Ausnahme verantwortlich. Wenn die [IDebugStackFrame3-Schnittstelle](../../../extensibility/debugger/reference/idebugstackframe3.md) nicht `InterceptStackException` implementiert ist oder die Methode einen Fehler zurückgibt, setzt der Debugger die normale Verarbeitung der Ausnahme fort.

> [!NOTE]
> Ausnahmen können nur in verwaltetem Code abgefangen werden, d. h., wenn das zu debuggende Programm unter der .NET-Laufzeit ausgeführt wird. Natürlich können Sprachimplementierer von Drittanbietern `InterceptStackException` in ihren eigenen Debug-Engines implementieren, wenn sie dies wünschen.

 Nachdem das Abfangen abgeschlossen ist, wird ein [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalisiert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
