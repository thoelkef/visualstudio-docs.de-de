---
title: IDebugEngineProgram2::Stop | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3cb9627ba11bdec5729383bd6a31e4a338f3ef9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686768"
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