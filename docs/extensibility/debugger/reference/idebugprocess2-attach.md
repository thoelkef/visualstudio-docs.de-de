---
title: IDebugProcess2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724197"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Fügt den Sitzungsdebug-Manager (SDM) an den Prozess an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
[in] Ein [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das für die Debugereignisbenachrichtigung verwendet wird.

`rgguidSpecificEngines`\
[in] Ein Array von GUIDs von Debugmodulen, die zum Debuggen von Programmen verwendet werden sollen, die im Prozess ausgeführt werden. Dieser Parameter kann ein NULL-Wert sein. Einzelheiten finden Sie in den Hinweisen.

`celtSpecificEngines`\
[in] Die Anzahl der Debugmodule im `rgguidSpecificEngines` Array `rghrEngineAttach` und die Größe des Arrays.

`rghrEngineAttach`\
[in, out] Ein Array von HRESULT-Codes, die von den Debugmodulen zurückgegeben werden. Die Größe dieses Arrays `celtSpecificEngines` wird im Parameter angegeben. Jeder Code ist `S_OK` `S_ATTACH_DEFERRED`in der Regel entweder oder . Letzteres weist darauf hin, dass die DE derzeit an keine Programme angeschlossen ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt andere mögliche Werte.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Der angegebene Prozess ist bereits an den Debugger angefügt.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während des Anfügevorgangs ist eine Sicherheitsverletzung aufgetreten.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktopprozess kann nicht an den Debugger angefügt werden.|

## <a name="remarks"></a>Bemerkungen
 Das Anfügen an einen Prozess fügt das SDM an alle Programme an, die in diesem `rgguidSpecificEngines` Prozess ausgeführt werden und von den im Array angegebenen Debugmodulen (DE) gedebuggen werden können. Legen `rgguidSpecificEngines` Sie den Parameter auf `GUID_NULL` einen NULL-Wert fest oder fügen Sie ihn in das Array ein, um ihn an alle Programme im Prozess anzufügen.

 Alle Debugereignisse, die im Prozess auftreten, werden an das angegebene [IDebugEventCallback2-Objekt](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet. Dieses `IDebugEventCallback2` Objekt wird bereitgestellt, wenn das SDM diese Methode aufruft.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
