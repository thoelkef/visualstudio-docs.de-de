---
title: 'IDebugEngineProgram2:: watchforexpressionevaluationonthread | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730363"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Ermöglicht (oder verweigert) die Ausdrucks Auswertung auf dem angegebenen Thread, auch wenn das Programm beendet wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parameter
`pOriginatingProgram`\
in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, das einen Ausdruck auswertet.

`dwTid`\
in Gibt den Bezeichner des Threads an.

`dwEvalFlags`\
in Eine Kombination von Flags aus der [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung durchgeführt werden soll.

`pExprCallback`\
in Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das zum Senden von Debugereignissen verwendet werden soll, die während der Ausdrucks Auswertung auftreten.

`fWatch`\
in Wenn der Wert ungleich 0 (NULL `TRUE` ) ist, wird die Auswertung von Ausdrücken für den von identifizierten Thread ermöglicht `dwTid` ; andernfalls lässt NULL ( `FALSE` ) die Auswertung von Ausdrücken für diesen Thread nicht zu.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Sitzungs-Debug-Manager (SDM) ein Programm anfordert, das durch den-Parameter identifiziert wird, `pOriginatingProgram` um einen Ausdruck auszuwerten, benachrichtigt er alle anderen angefügten Programme durch Aufrufen dieser Methode.

 Die Ausdrucks Auswertung in einem Programm kann bewirken, dass Code in einem anderen Programm aufgrund einer Funktions Auswertung oder Auswertung von Eigenschaften ausgeführt wird `IDispatch` . Aus diesem Grund ermöglicht diese Methode die Ausführung und den Abschluss der Ausdrucks Auswertung, obwohl der Thread in diesem Programm angehalten werden kann.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
