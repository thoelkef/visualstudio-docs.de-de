---
title: IDebugProcess3::Ausführen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723682"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Setzt die Ausführung dieses Prozesses von einem angehaltenen Zustand aus fort. Jeder vorherige Ausführungsstatus (z. B. ein Schritt) wird gelöscht, und der Prozess wird erneut ausgeführt.

> [!NOTE]
> Diese Methode sollte anstelle von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread`\
[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den auszuführenden Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Benutzer die Ausführung aus einem angehaltenen Zustand im Thread eines anderen Prozesses startet, wird diese Methode für diesen Prozess aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer den **Befehl Start** aus dem **Debugmenü** in der IDE auswählt. Die Implementierung dieser Methode kann so einfach sein wie das Aufrufen der [Resume-Methode](../../../extensibility/debugger/reference/idebugthread2-resume.md) für den aktuellen Thread im Prozess.

> [!WARNING]
> Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
