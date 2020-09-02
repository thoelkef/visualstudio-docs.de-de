---
title: 'IDebugProgram2:: Execute | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af4650b5523595350543ac549ac162247563e418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386744"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Setzt die Ausführung dieses Programms mit dem Status "beendet" fort. Alle vorherigen Ausführungs Zustände (z. b. ein Schritt) werden gelöscht, und die Ausführung des Programms wird erneut gestartet.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden Sie stattdessen die [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) -Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Benutzer die Ausführung von einem beendeten Zustand aus in einem anderen Programm Thread startet, wird diese Methode für dieses Programm aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer den Befehl **Start** im Menü **Debuggen** in der IDE auswählt. Die Implementierung dieser Methode kann so einfach wie das Aufrufen der [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) -Methode für den aktuellen Thread im Programm sein.

> [!WARNING]
> Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
