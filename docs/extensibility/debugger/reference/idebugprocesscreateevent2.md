---
title: IDebugProcessCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfc9b0bbdebde01af48ab1436dbfd17ac0c3241b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723530"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
Diese Schnittstelle wird gesendet, wenn ein Prozess gestartet wird.

## <a name="syntax"></a>Syntax

```
IDebugProcessCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) oder der benutzerdefinierte Portlieferant implementiert diese Schnittstelle, um zu melden, dass ein Prozess erstellt wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE oder der benutzerdefinierte Portlieferant erstellt und sendet dieses Ereignisobjekt, um die Erstellung eines Prozesses zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2-Rückruffunktion,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird. Der benutzerdefinierte Portlieferant sendet dieses Ereignis über die [IDebugPortEvents2-Schnittstelle.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
