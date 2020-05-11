---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732951"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Versuche, zu ermitteln, warum eine automatische Anfügefunktion fehlgeschlagen ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parameter
`pszUrl`\
[in] Derzeit nicht verwendet; sollte immer auf einen Nullwert festgelegt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Im Folgenden sind andere typische Rückgabecodes:

|Code|BESCHREIBUNG|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Es kann nicht ermittelt werden, warum der Remoteserver das Debuggen nicht gestartet hat.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Das Debuggen auf dem Remoteserver kann nicht ausgeführt werden, möglicherweise aufgrund unzureichender Berechtigungen oder weil das DEBUG-Verb nicht aktiviert ist.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Der Webserver wurde gesperrt und blockiert das DEBUG-Verb, das zum Aktivieren des Debuggens erforderlich ist.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
