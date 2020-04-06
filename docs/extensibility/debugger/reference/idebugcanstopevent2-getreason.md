---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734523"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ruft den Grund ab, warum das Debugmodul (DE) beendet werden soll.

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
[out] Gibt einen Wert [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) aus der CANSTOP_REASON-Enumeration zurück, die den Grund für dieses Ereignis beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird in der Regel vor der [CanStop-Methode](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) aufgerufen,`TRUE`damit `IDebugCanStopEvent2::CanStop` der Aufrufer bestimmen kann, ob die Methode ungleich Null ( ) übergeben werden soll.

 Der Grund für das `CANSTOP_ENTRYPOINT`Anhalten kann entweder sein, was `CANSTOP_STEPIN`bedeutet, dass die DE einen Einstiegspunkt erreicht hat, oder , was bedeutet, dass die DE in eine Funktion eingetreten ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
