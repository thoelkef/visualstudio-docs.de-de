---
title: IDebugProgram2::Step | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8030bd45850a2b81e3cfb03a83497bba77c4515c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325282"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Führt einen Schritt aus.

> [!NOTE]
> Diese Methode ist veraltet. Verwenden der [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode stattdessen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parameter
`pThread`\
[in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread wird abgestuften darstellt.

`sk`\
[in] Ein Wert aus der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der den Typ des Schritts angibt.

`step`\
[in] Ein Wert aus der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Enumeration, die die Einheit des Schritts (beispielsweise von einer Anweisung oder der Anweisung) angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Für den Fall, dass alle Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Programm ausführen, wird ein Prozedurschritt ein bestimmter Thread ausgeführt.

> [!WARNING]
> Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)