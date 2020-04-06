---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734511"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Diese Schnittstelle wird verwendet, um den Sitzungsdebug-Manager (SDM) zu fragen, ob er am aktuellen Codespeicherort anhalten soll.

## <a name="syntax"></a>Syntax

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle, um das Durchlaufen des Quellcodes zu unterstützen. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden `IDebugEvent2` (das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die Schnittstelle zuzugreifen).

 Die Implementierung dieser Schnittstelle muss den Aufruf von [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) durch das SDM an das Debugmodul übermitteln. Dies kann z. B. mit einer Nachricht erfolgen, die an den Nachrichtenbehandlungsthread des Debugmoduls gesendet wird, oder das Objekt, das diese Schnittstelle implementiert, kann einen Verweis auf das Debugmodul enthalten und mit dem an `IDebugCanStopEvent2::CanStop`übergebenen Flag in das Debugmodul zurückrufen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE kann diese Methode jedes Mal senden, wenn die DE aufgefordert wird, die Ausführung fortzusetzen, und die DE durch den Code tritt. Dieses Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugCanStopEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob das gedebuggte Programm am Speicherort dieses Ereignisses beendet werden soll (und ein Ereignis sendet, das den Grund für das Beenden beschreibt) oder einfach die Ausführung fortsetzen soll.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft den Dokumentkontext ab, der den Speicherort dieses Ereignisses beschreibt.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft den Codekontext ab, der den Speicherort dieses Ereignisses beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Die DE sendet diese Schnittstelle, wenn der Benutzer in eine Funktion einsteigt und die DE dort keine Debuginformationen findet oder Debuginformationen vorhanden sind, aber die DE weiß nicht, ob der Quellcode für diesen Speicherort angezeigt werden kann.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
