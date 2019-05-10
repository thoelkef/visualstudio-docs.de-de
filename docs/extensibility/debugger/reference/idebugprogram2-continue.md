---
title: IDebugProgram2::Continue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd13d67917a395eb33e26a53e0db1fed7340c9c6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412870"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Weiterhin die Ausführung dieses Programms aus einem beendeten Zustand. Alle vorherigen Ausführungsstatus (z. B. in einem Schritt) wird beibehalten, und das Programm gestartet wird, erneut ausführen.

> [!NOTE]
> Diese Methode ist veraltet. Verwenden der [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md) Methode stattdessen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

#### <a name="parameters"></a>Parameter
 `pThread`

 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, für dieses Programm unabhängig davon, wie viele Programme debuggt werden oder welches Programm das Stopping-Ereignis generiert. Die Implementierung muss behalten den vorherigen Ausführungsstatus (z. B. in einem Schritt) und die Ausführung wird fortgesetzt, als wären es nie vor dem Abschluss der vorherigen Ausführung beendet haben. Wenn ein Thread in diesem Programm einen Schritt-für-Vorgang durchführen wurde und wurde beendet, weil ein anderes Programm beendet werden soll, und klicken Sie dann diese Methode aufgerufen wurde, muss die Anwendung, also der ursprüngliche Prozedurschritten-Vorgang abgeschlossen.

> [!WARNING]
> Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.

## <a name="see-also"></a>Siehe auch
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)