---
title: IDebugProcess3::Weiter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723781"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Setzt die Ausführung dieses Prozesses von einem angehaltenen Zustand aus fort. Alle vorherigen Ausführungsstatus (z. B. ein Schritt) bleiben erhalten, und der Prozess wird erneut ausgeführt.

> [!NOTE]
> Diese Methode sollte anstelle von [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)verwendet werden.

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
`pThread`\
[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, der fortgesetzt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird für diesen Prozess aufgerufen, unabhängig davon, wie viele Prozesse gedebughandelt werden oder welcher Prozess das Stoppereignis generiert hat. Die Implementierung muss den vorherigen Ausführungsstatus (z. B. einen Schritt) beibehalten und die Ausführung so fortsetzen, als ob sie nie beendet worden wäre, bevor die vorherige Ausführung abgeschlossen wurde. Das heißt, wenn ein Thread in diesem Prozess einen Stepovervorgang ausführt und `Continue` angehalten wurde, weil ein anderer Prozess angehalten wurde und dann aufgerufen wurde, muss der angegebene Thread den ursprünglichen Stepovervorgang abschließen.

 **Warnung** Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
