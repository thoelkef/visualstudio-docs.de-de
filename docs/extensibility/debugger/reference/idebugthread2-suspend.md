---
title: 'IDebugThread2:: Suspend | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
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
vorgenommen Gibt den anhaltezähler nach dem Anhaltevorgang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jeder Aufrufe dieser Methode erhöht den anhaltezähler über 0. Diese anhalteanzahl wird im Fenster **Threads** Debuggen angezeigt.

 Für jeden Aufrufe dieser Methode muss ein späterer aufrufbedarf an der [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) -Methode vorhanden sein.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
