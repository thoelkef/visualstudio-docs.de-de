---
title: IDebugCanStopEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 012440e03208fab6bc2cde8814781f7b3a64f79d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922998"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Diese Schnittstelle wird verwendet, die sitzungsbasierter Debug-Manager (SDM) an, ob an der aktuellen Codeposition beendet bitten.

## <a name="syntax"></a>Syntax

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um die Unterstützung der Source-Code schrittweise durchlaufen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden (wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle).

 Die Implementierung dieser Schnittstelle muss das SDM Aufruf kommunizieren [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) an die Debug-Engine. Z. B. dazu mit der Meldung an die Debug-Engine-Meldungsbehandlung Thread gesendet oder das Objekt, das diese Schnittstelle implementiert, enthalten einen Verweis auf die Debug-Engine und einen Rückruf in die Debug-Engine mit dem übergebenen Kennzeichen konnte `IDebugCanStopEvent2::CanStop`.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Methode jedes Mal, wenn die DE aufgefordert, Ausführung und die DE weiterhin den Code durchlaufen werden kann die DE senden. Dieses Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM angegeben wird, wenn diese an die zu debuggende Programm wird angefügt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugCanStopEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob die zu debuggende Programm wird an der Position der dieses Ereignis (und das Senden eines Ereignisses, das den Grund für Beenden beschreibt) beendet werden soll, oder nur die Ausführung wird fortgesetzt.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft ab, der Dokumentenkontext, der den Speicherort der dieses Ereignis beschreibt.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft ab, der Codekontext, der den Speicherort der dieses Ereignis beschreibt.|

## <a name="remarks"></a>Hinweise
 Die DE sendet diese Schnittstelle auf, wenn die Benutzer schrittweise eine Funktion und die DE findet keine Debuginformationen vorhanden oder Debuginformationen vorhanden ist, aber die DE weiß nicht, wenn der Quellcode für diesen Standort angezeigt werden kann.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)