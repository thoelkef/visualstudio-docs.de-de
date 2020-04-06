---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730363"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Ermöglicht die Auswertung (oder Nichtzugerstifsagung) von Ausdrücken für den angegebenen Thread, auch wenn das Programm beendet wurde.

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
[in] Ein [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das das Programm darstellt, das einen Ausdruck auswertet.

`dwTid`\
[in] Gibt den Bezeichner des Threads an.

`dwEvalFlags`\
[in] Eine Kombination von Flags aus der EVALFLAGS-Enumeration, die angeben, wie die Auswertung ausgeführt werden soll. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

`pExprCallback`\
[in] Ein [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das zum Senden von Debugereignissen verwendet werden soll, die während der Ausdrucksauswertung auftreten.

`fWatch`\
[in] Wenn ungleich`TRUE`Null ( ), ermöglicht Die `dwTid`Ausdrucksauswertung für den Thread, der durch identifiziert wird; Andernfalls lässt`FALSE`Null ( ) die Ausdrucksauswertung für diesen Thread nicht zu.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Sitzungsdebug-Manager (SDM) ein `pOriginatingProgram` Programm, das durch den Parameter identifiziert wird, auffordert, einen Ausdruck auszuwerten, benachrichtigt er alle anderen angehängten Programme, indem er diese Methode aufruft.

 Die Ausdrucksauswertung in einem Programm kann dazu führen, dass `IDispatch` Code in einem anderen Programm ausgeführt wird, da die Funktion auswertet oder Eigenschaften ausgewertet werden. Aus diesem Grund ermöglicht diese Methode die Ausführung und Vervollständigung der Ausdrucksauswertung, auch wenn der Thread in diesem Programm angehalten werden kann.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
