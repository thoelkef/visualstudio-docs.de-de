---
title: IDebugProgramDestroyEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd9f7b97dc7479b90801ebcd07966a0058fa6476
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343539"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Diese Schnittstelle wird von der Debug-Engine (DE) für die Sitzung Debug-Manager (SDM) gesendet, wenn ein Programm bis zum Abschluss ausgeführt wurde.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE oder den benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle zum Bericht, dass ein Programm ist nicht mehr verfügbar ist, für das Debuggen wurde beendet. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE oder den benutzerdefinierten Port Lieferanten erstellt und sendet dieses Ereignisobjekt, um die Beendigung eines Programms zu melden. Die DE sendet dieses Ereignis mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt. Der benutzerdefinierten Port Lieferanten sendet dieses Ereignis mit der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methode der `IDebugProgramDestroyEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Ruft Exitcode des Programms ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)