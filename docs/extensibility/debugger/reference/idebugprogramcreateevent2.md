---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78088d6e5da61c32302c13b08143c9ed902452e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722629"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Session Debug Manager (SDM) gesendet, wenn ein Programm angefügt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE oder der benutzerdefinierte Portlieferant implementiert diese Schnittstelle, um zu melden, dass ein Programm erstellt wurde, in der Regel zum Zeitpunkt der Anade des Programms. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM `QueryInterface` verwendet die `IDebugEvent2` Methode, um auf die Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE oder der benutzerdefinierte Portlieferant erstellt und sendet dieses Ereignisobjekt, um die Erstellung eines Programms zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2-Rückruffunktion,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird. Der benutzerdefinierte Portlieferant sendet dieses Ereignis über die [IDebugPortEvents2-Schnittstelle.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="remarks"></a>Bemerkungen
 Der DE- oder benutzerdefinierte Portlieferant veröffentlicht eine neue [IDebugProgramNode2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprogramnode2.md) indem [er PublishProgramNode aufruft.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
