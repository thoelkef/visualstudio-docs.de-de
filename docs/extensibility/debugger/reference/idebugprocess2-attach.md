---
title: IDebugProcess2::Attach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: de41c3f611383afabfd6fe051edb8dbe83d266b4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202764"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Fügt der Sitzung Debug-Manager (SDM) an den Prozess an.

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
[in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das verwendet wird, für die Debug-ereignisbenachrichtigung.

`rgguidSpecificEngines`\
[in] Ein Array von GUIDs von Debug-Engines verwendet werden, zum Debuggen von Programmen, die im Prozess ausgeführt werden soll. Dieser Parameter kann ein null-Wert sein. Einzelheiten finden Sie unter "Hinweise".

`celtSpecificEngines`\
[in] Die Anzahl der Debug-engines in die `rgguidSpecificEngines` Array und die Größe der `rghrEngineAttach` Array.

`rghrEngineAttach`\
[in, out] Ein Array von HRESULT-Codes, die von der Debug-Engines zurückgegeben. Die Größe dieses Arrays wird angegeben, der `celtSpecificEngines` Parameter. Jeder Code ist in der Regel entweder `S_OK` oder `S_ATTACH_DEFERRED`. Letztere gibt an, dass die DE derzeit keine Programme hinzugefügt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt weitere mögliche Werte.

|Wert|Beschreibung|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Der angegebene Prozess ist bereits an den Debugger angefügt.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während dieses Vorgangs Anfügen ist ein Sicherheitsverstoß aufgetreten.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein desktop-Prozess kann nicht an den Debugger angefügt werden.|

## <a name="remarks"></a>Hinweise
 Anfügen an einen Prozess, das SDM auf alle Programme, die ausgeführt wird, in diesem Prozess, der durch die Debug-Engines (DE), die im angegebenen gedebuggt werden, kann fügt die `rgguidSpecificEngines` Array. Legen Sie die `rgguidSpecificEngines` Parameter ein NULL-Wert Wert oder enthalten `GUID_NULL` in das Array, das auf alle Programme im Prozess anfügen.

 Alle Debug-Ereignisse, die im Prozess auftreten, werden gesendet, um die angegebenen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt. Dies `IDebugEventCallback2` Objekt wird bereitgestellt, wenn das SDM diese Methode aufruft.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)