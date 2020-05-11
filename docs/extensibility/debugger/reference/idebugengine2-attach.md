---
title: IDebugEngine2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731216"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Fügt ein Debugmodul (DE) an ein Programm oder Programme an. Wird vom Session Debug Manager (SDM) aufgerufen, wenn die DE in-process zum SDM ausgeführt wird.

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

## <a name="parameters"></a>Parameter
`pProgram`\
[in] Ein Array von [IDebugProgram2-Objekten,](../../../extensibility/debugger/reference/idebugprogram2.md) die Programme darstellen, an die angefügt werden soll. Dies sind Portprogramme.

`rgpProgramNodes`\
[in] Ein Array von [IDebugProgramNode2-Objekten,](../../../extensibility/debugger/reference/idebugprogramnode2.md) die Programmknoten darstellen, eines für jedes Programm. Die Programmknoten in diesem Array stellen `pProgram`dieselben Programme wie in dar. Die Programmknoten werden so angegeben, dass die DE die anfügenden Programme identifizieren kann.

`celtPrograms`\
[in] Anzahl der Programme und/oder Programmknoten in der `pProgram` und `rgpProgramNodes` Arrays.

`pCallback`\
[in] Das [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das zum Senden von Debugereignissen an das SDM verwendet werden soll.

`dwReason`\
[in] Ein Wert [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) aus der ATTACH_REASON-Enumeration, der den Grund für das Anfügen dieser Programme angibt. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es gibt drei Gründe für das Anfügen an ein Programm, wie folgt:

- `ATTACH_REASON_LAUNCH`gibt an, dass die DE an das Programm angefügt wird, da der Benutzer den Prozess gestartet hat, der es enthält.

- `ATTACH_REASON_USER`gibt an, dass der Benutzer die DE explizit aufgefordert hat, an ein Programm (oder den Prozess, der ein Programm enthält) anzufügen.

- `ATTACH_REASON_AUTO`gibt an, dass de an ein bestimmtes Programm angefügt wird, da es bereits andere Programme in einem bestimmten Prozess debuggen. Dies wird auch als Auto-Attach bezeichnet.

  Wenn diese Methode aufgerufen wird, muss die DE diese Ereignisse nacheinander senden:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (wenn es noch nicht für eine bestimmte Instanz des Debugmoduls gesendet wurde)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Wenn der Grund für das `ATTACH_REASON_LAUNCH`Anfügen der Grund ist, muss die DE außerdem das [IDebugEntryPointEvent2-Ereignis](../../../extensibility/debugger/reference/idebugentrypointevent2.md) senden.

   Sobald die DE das [IDebugProgramNode2-Objekt](../../../extensibility/debugger/reference/idebugprogramnode2.md) erhält, das dem zu debuggenden Programm entspricht, kann es für jede private Schnittstelle abgefragt werden.

   Vor dem Aufruf der Methoden eines Programmknotens im Array, das von `pProgram` oder `rgpProgramNodes` `IDebugProgram2` angegeben wird, sollte die Identitätswechselbeifall bei Bedarf auf der Schnittstelle aktiviert werden, die den Programmknoten darstellt. Normalerweise ist dieser Schritt jedoch nicht notwendig. Weitere Informationen finden Sie unter [Sicherheitsprobleme](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
