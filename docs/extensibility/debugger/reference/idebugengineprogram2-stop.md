---
title: IDebugEngineProgram2::Stop | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba93c88eb3d7e996b2a5f19dda605653af090c94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345217"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Beendet alle Threads, die in diesem Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, wenn dieses Programm in einer Umgebung mit mehreren Anwendung gedebuggt wird. Wenn eine Beenden-Ereignis in ein anderes Programm empfangen wird, wird diese Methode für dieses Programm aufgerufen. Die Implementierung dieser Methode sollten asynchron sein; nicht alle Threads sollte, also erforderlich, um vor dem Beenden dieser Methode beendet werden. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) Methode für dieses Programm.

 Kein Debugereignis wird als Reaktion auf diese Methode gesendet.

## <a name="see-also"></a>Siehe auch
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)