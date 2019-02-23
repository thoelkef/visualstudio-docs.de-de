---
title: IDebugEngine2::Attach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab1ea05511369d36b881afcaf7c161f796fd4925
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678253"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Fügt eine Debug-Engine (DE) an ein Programm oder Programme. Aufgerufen von der Sitzungs-Manager (SDM) ein, wenn die DE ausgeführten in-Process an das SDM befindet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

#### <a name="parameters"></a>Parameter
 `pProgram`

 [in] Ein Array von [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Programme anzufügenden darstellende – Objekte. Hierbei handelt es sich um Anschluss-Programme.

 `rgpProgramNodes`

 [in] Ein Array von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekte, die programmknoten, einen für jedes Programm darstellen. Die programmknoten in diesem Array darstellen derselben Programme wie in `pProgram`. Die programmknoten erhalten, damit die DE die Programme zum Anfügen an identifizieren kann.

 `celtPrograms`

 [in] Anzahl der Programme und/oder programmknoten in der `pProgram` und `rgpProgramNodes` Arrays.

 `pCallback`

 [in] Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt, das verwendet werden, das SDM-Debug-Ereignissen an.

 `dwReason`

 [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, die den Grund für das Anfügen von diesen Programmen angibt. Weitere Informationen finden Sie im Abschnitt "Hinweise".

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Es gibt drei Gründe für das Anfügen an ein Programm, wie folgt:

- `ATTACH_REASON_LAUNCH` Gibt an, dass die DE für das Programm angefügt wird, da der Benutzer, der Prozess gestartet, der sie enthält.

- `ATTACH_REASON_USER` Gibt an, dass der Benutzer explizit die DE zum Anfügen an ein Programm (oder den Prozess, der ein Programm enthält) angefordert hat.

- `ATTACH_REASON_AUTO` Gibt an, dass die DE an ein bestimmtes Programm angefügt wird, da sie bereits andere Programme in einem bestimmten Prozess Debuggen ist. Dies wird auch bezeichnet das automatische Anhängen.

  Wenn diese Methode aufgerufen wird, muss die DE senden, diese Ereignisse in Reihenfolge:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (sofern es nicht bereits für eine bestimmte Instanz der Debug-Engine gesendet wurden)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Darüber hinaus ist der Grund für das Anfügen von `ATTACH_REASON_LAUNCH`, muss die DE senden die [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) Ereignis.

   Nach DE Ruft die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das zu debuggende Programm wird, entspricht für alle private Schnittstelle abgefragt werden kann.

   Vor dem Aufrufen der Methoden eines Knotens für die Anwendung in das Array, das vom `pProgram` oder `rgpProgramNodes`, Identitätswechsel bei Bedarf aktiviert werden soll die `IDebugProgram2` -Schnittstelle, die Programm-Knoten darstellt. In der Regel ist jedoch, diesen Schritt nicht erforderlich. Weitere Informationen finden Sie unter [Sicherheitsprobleme](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)