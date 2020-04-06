---
title: IDebugProgram2::Schritt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722761"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Führt einen Schritt aus.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) Sie stattdessen die Step-Methode.

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
[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den gestuften Thread darstellt.

`sk`\
[in] Ein Wert [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) aus der STEPKIND-Enumeration, der die Art des Schritts angibt.

`step`\
[in] Ein Wert [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) aus der STEPUNIT-Enumeration, der die Schritteinheit angibt (z. B. durch Anweisung oder Anweisung).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Falls eine Threadsynchronisierung oder -kommunikation zwischen Threads besteht, sollten andere Threads im Programm ausgeführt werden, wenn ein bestimmter Thread schritt.

> [!WARNING]
> Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
