---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1edd974c934aab5fe3a5c3679190af5ce6039120
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212564"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Führt das Debugger-Programm. Der Thread wird zurückgegeben, den Debuggerinformationen geben, in welchem, die Thread dem Benutzer angezeigt wird, wenn das Programm ausgeführt, wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread`\
[in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Es gibt drei Möglichkeiten, ein Debugger die Ausführung nach dem Beenden fortgesetzt werden kann:

- Führen Sie aus: Kündigen Sie alle vorherigen Schritt aus, und führen Sie bis zum nächsten Haltepunkt und so weiter.

- Schritt: Brechen Sie alle alten Schritt und ausgeführt, bis der neue Schritt abgeschlossen ist.

- Fahren Sie fort: Führen Sie erneut aus, und lassen Sie alle alten Schritt aktiv.

  Der Thread, die an `ExecuteOnThread` ist nützlich, bei der Entscheidung, wird der entsprechende Schritt abgebrochen. Bricht Sie alle Schritte ab, wenn Sie nicht wissen, dass den Thread ausgeführt wird ausgeführt. Mit Kenntnis des Threads müssen Sie nur den Schritt für den aktiven Thread abzubrechen.

## <a name="see-also"></a>Siehe auch
- [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)