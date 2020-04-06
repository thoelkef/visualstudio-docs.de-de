---
title: IDebugProgram2::Weiter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723075"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Setzt die Ausführung dieses Programms unter einem angehaltenen Zustand fort. Alle vorherigen Ausführungsstatus (z. B. ein Schritt) bleiben erhalten, und das Programm beginnt erneut mit der Ausführung.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) Sie stattdessen die Continue-Methode.

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

## <a name="parameters"></a>Parameter
`pThread`[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird für dieses Programm aufgerufen, unabhängig davon, wie viele Programme gedebuggen werden oder welches Programm das Stoppereignis generiert hat. Die Implementierung muss den vorherigen Ausführungsstatus (z. B. einen Schritt) beibehalten und die Ausführung so fortsetzen, als ob sie nie beendet worden wäre, bevor die vorherige Ausführung abgeschlossen wurde. Das heißt, wenn ein Thread in diesem Programm einen Stepover-Vorgang ausführt und angehalten wurde, weil ein anderes Programm angehalten wurde, und dann diese Methode aufgerufen wurde, muss das Programm den ursprünglichen Stepovervorgang abschließen.

> [!WARNING]
> Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
