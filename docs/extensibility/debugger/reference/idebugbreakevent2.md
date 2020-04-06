---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735391"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Diese Schnittstelle teilt dem Sitzungsdebug-Manager (SDM) mit, dass ein asynchroner Unterbrechungsfehler erfolgreich abgeschlossen wurde.

## <a name="syntax"></a>Syntax

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um Benutzerunterbrechungen in einem Programm zu unterstützen. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden `IDebugEvent2` (das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die Schnittstelle zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das SDM ruft [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) auf, wenn der Benutzer angefordert hat, dass das zu debuggende Programm angehalten wird. Wenn das Programm erfolgreich angehalten wurde, `IDebugBreakEvent2` sendet die DE das Ereignis. Dieses Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="remarks"></a>Bemerkungen
 Beispielsweise kann ein Benutzer im **Debug-Menü** den Befehl **Alle unterbrechen** auswählen, um aus einem Programm auszubrechen, das eine Endlosschleife ausführt. Das SDM weist das Programm an, durch Aufrufen von [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)aufzuhören. Die DE `IDebugBreakEvent2` sendet, wenn das Programm endlich beendet wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
