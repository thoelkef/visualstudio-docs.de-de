---
title: IDebugProgram2::Ausführen | Microsoft Docs
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
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722984"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Setzt die Ausführung dieses Programms unter einem angehaltenen Zustand fort. Alle vorherigen Ausführungsstatus (z. B. ein Schritt) werden gelöscht, und das Programm beginnt erneut mit der Ausführung.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) Sie stattdessen die Execute-Methode.

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
 Wenn der Benutzer die Ausführung aus einem angehaltenen Zustand im Thread eines anderen Programms startet, wird diese Methode für dieses Programm aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer den **Befehl Start** aus dem **Debugmenü** in der IDE auswählt. Die Implementierung dieser Methode kann so einfach sein wie das Aufrufen der [Resume-Methode](../../../extensibility/debugger/reference/idebugthread2-resume.md) für den aktuellen Thread im Programm.

> [!WARNING]
> Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
