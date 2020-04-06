---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718675"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Setzt die Ausführung eines Threads fort.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parameter
`pdwSuspendCount`\
[out] Gibt die Suspend-Anzahl nach dem Wiederaufnahmevorgang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jeder Aufruf dieser Methode dekrementiert die Suspend-Anzahl, bis sie 0 erreicht, zu welchem Zeitpunkt die Ausführung tatsächlich fortgesetzt wird. Diese Suspend-Anzahl wird **Threads** im Thread-Debugfenster angezeigt.

 Für jeden Aufruf dieser Methode muss ein vorheriger Aufruf der [Suspend-Methode](../../../extensibility/debugger/reference/idebugthread2-suspend.md) vorhanden sein. Die Suspend-Anzahl bestimmt, `IDebugThread2::Suspend` wie oft die Methode bisher aufgerufen wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Angehalten](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
