---
title: IDebugProgramDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722592"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Session Debug Manager (SDM) gesendet, wenn ein Programm bis zum Abschluss ausgeführt wurde.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE oder der benutzerdefinierte Portlieferant implementiert diese Schnittstelle, um zu melden, dass ein Programm beendet wurde und nicht mehr für das Debuggen verfügbar ist. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE oder der benutzerdefinierte Portlieferant erstellt und sendet dieses Ereignisobjekt, um die Beendigung eines Programms zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2-Rückruffunktion,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird. Der benutzerdefinierte Portlieferant sendet dieses Ereignis über die [IDebugPortEvents2-Schnittstelle.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgramDestroyEvent2`die Methode von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Ruft den Exit-Code des Programms ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
