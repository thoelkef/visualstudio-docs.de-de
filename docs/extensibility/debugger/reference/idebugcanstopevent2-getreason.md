---
title: IDebugCanStopEvent2::GetReason | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b219973e0fced92a588a87ed472cf7a57d312d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337271"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ruft ab, der Grund, warum die Debug-Engine (DE) beenden möchte.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Parameter
`pcr`\
[out] Gibt einen Wert aus der [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) -Enumeration, die den Grund für dieses Ereignis beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird in der Regel aufgerufen, bevor die [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) Methode, sodass der Aufrufer entscheiden kann, ob ungleich NULL übergeben werden soll (`TRUE`) auf die `IDebugCanStopEvent2::CanStop` Methode.

 Der Grund für beenden kann es sich entweder `CANSTOP_ENTRYPOINT`, was bedeutet, dass die DE ein Einstiegspunkts erreicht hat oder `CANSTOP_STEPIN`, was bedeutet, dass die DE in eine Funktion, abgestuft wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)