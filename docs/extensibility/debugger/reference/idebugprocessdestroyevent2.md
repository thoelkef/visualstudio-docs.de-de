---
title: IDebugProcessDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d7c93c1e5811ec3aed5d44f3c306de1c09cced9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723448"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Diese Schnittstelle wird gesendet, wenn ein Prozess beendet, atypisch beendet oder getrennt wird.

## <a name="syntax"></a>Syntax

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) oder der benutzerdefinierte Portlieferant implementieren diese Schnittstelle, um zu melden, dass ein Prozess beendet wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE oder der benutzerdefinierte Portlieferant erstellt und sendet dieses Ereignisobjekt, um die Beendigung eines Prozesses zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2-Rückruffunktion,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird. Der benutzerdefinierte Portlieferant sendet dieses Ereignis über die [IDebugPortEvents2-Schnittstelle.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
