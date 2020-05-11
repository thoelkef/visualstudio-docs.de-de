---
title: IDebugThread2::Suspend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718642"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Hält einen Thread an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parameter
`pdwSuspendCount`\
[out] Gibt die Suspend-Anzahl nach dem Suspend-Vorgang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Bei jedem Aufruf dieser Methode wird die Suspend-Anzahl über 0 erhöht. Diese Suspend-Anzahl wird **Threads** im Thread-Debugfenster angezeigt.

 Für jeden Aufruf dieser Methode muss ein neuer Aufruf der [Resume-Methode](../../../extensibility/debugger/reference/idebugthread2-resume.md) erfolgen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
