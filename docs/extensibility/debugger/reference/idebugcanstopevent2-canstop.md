---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734589"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Benachrichtigt das Debugmodul (DE), ob es am aktuellen Codespeicherort anhalten oder einfach die Ausführung fortsetzen soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parameter
`fCanStop`\
[in] Ungleich Null`TRUE`( ), wenn die DE an der aktuellen Codeposition anhalten soll; andernfalls Null`FALSE`( ).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Empfänger dieses Ereignisses ruft in der Regel die [GetReason-Methode](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) auf, um den Grund zu bestimmen, warum die DE beendet werden soll, und ruft dann die `IDebugCanStopEvent2::CanStop` Methode mit der entsprechenden Antwort auf.

 Wenn die DE beendet wird, sendet sie ein Ereignis, das den Grund für das Beenden beschreibt. Es gibt in der Regel zwei Ereignisse, die gesendet werden, einen Benutzer oder eine Signalunterbrechung, die durch die [IDebugBreakEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakevent2.md) dargestellt wird, und ein Haltepunktereignis, das durch die [IDebugBreakpointEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) dargestellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
