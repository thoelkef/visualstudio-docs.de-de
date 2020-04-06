---
title: IDebugProcess3::Schritt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723552"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Bewirkt, dass der Prozess eine Anweisung oder Anweisung schritt.

> [!NOTE]
> Diese Methode sollte anstelle von [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parameter
`pThread`\
[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den gestuften Thread darstellt.

`sk`\
[in] Einer der [STEPKIND-Werte.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[in] Einer der [STEPUNIT-Werte.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Falls threadsynchronisierung oder -kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Prozess ausgeführt werden, wenn ein bestimmter Thread schritt.

 **Warnung** Senden Sie während der Verarbeitung dieses Aufrufs kein Beenden- oder ein sofortiges (synchrones) Ereignis an [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls kann der Debugger hängen bleiben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
