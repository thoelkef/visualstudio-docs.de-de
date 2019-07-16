---
title: IDebugProcess3::Execute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b4b854c752bc7b1f66687074fbfe86286fc48fb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314001"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Wird fortgesetzt, das Ausführen dieses Prozesses vom Status "beendet". Alle vorherigen Ausführungsstatus (z. B. in einem Schritt) deaktiviert ist, und der Prozess gestartet wird, erneut ausführen.

> [!NOTE]
> Diese Methode sollte verwendet werden, anstelle von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

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
[in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt, das Ausführen des Threads darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Wenn der Benutzer die Ausführung von Status "beendet" im Thread von einem anderen Prozess startet, wird diese Methode zu diesem Vorgang aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer wählt die **starten** Befehl die **Debuggen** Menü in der IDE. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode für den aktuellen Thread im Prozess.

> [!WARNING]
> Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)