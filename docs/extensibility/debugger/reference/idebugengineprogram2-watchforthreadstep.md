---
title: IDebugEngineProgram2::WatchForThreadstep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730354"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Beobachtet, ob die Ausführung im angegebenen Thread erfolgt (oder aufhört, die Ausführung zu beobachten).

## <a name="syntax"></a>Syntax

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parameter
`pOriginatingProgram`\
[in] Ein [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das das gestufte Programm darstellt.

`dwTid`\
[in] Gibt den Bezeichner des zu überwachenden Threads an.

`fWatch`\
[in] Un-Null`TRUE`( ) bedeutet, dass Sie `dwTid`die Ausführung des threads, der durch identifiziert wird, einstellen. Andernfalls bedeutet`FALSE`Null ( ) , `dwTid`dass Sie die Ausführung auf beenden.

`dwFrame`\
[in] Gibt einen Rahmenindex an, der den Schritttyp steuert. Wenn dieser Wert Null (0) ist, ist der Schritttyp "Step in" `dwTid` und das Programm sollte beendet werden, wenn der Thread durch Ausgeführt wird. Wenn `dwFrame` es ungleich Null ist, ist der Schritttyp "Schritt über" `dwTid` und das Programm sollte nur beendet werden, wenn `dwFrame`der von ihm identifizierte Thread in einem Frame ausgeführt wird, dessen Index gleich oder höher auf dem Stapel als ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Sitzungsdebug-Manager (SDM) ein `pOriginatingProgram` Programm, das durch den Parameter identifiziert wird, schritte, benachrichtigt er alle anderen angehängten Programme, indem er diese Methode aufruft.

 Diese Methode ist nur für Dasein-Thread-Stepping anwendbar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
