---
title: IDebugProgram2::Execute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e1fc6ebaef7f514bf61251aec67554a18db4b0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698585"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Weiterhin die Ausführung dieses Programms aus einem beendeten Zustand. Alle vorherigen Ausführungsstatus (z. B. in einem Schritt) deaktiviert ist, und das Programm gestartet wird, erneut ausführen.

> [!NOTE]
>  Diese Methode ist veraltet. Verwenden der [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) Methode stattdessen.

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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn der Benutzer die Ausführung von Status "beendet" in ein anderes Programm Thread startet, wird diese Methode für dieses Programm aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer wählt die **starten** Befehl die **Debuggen** Menü in der IDE. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode für den aktuellen Thread im Programm.

> [!WARNING]
>  Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)