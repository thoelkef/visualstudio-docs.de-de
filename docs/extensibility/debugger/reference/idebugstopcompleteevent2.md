---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Debugging-Modul (DE) kann die Sitzung Debug-Manager (SDM) dieses optionale Ereignis senden, Beendigung ein Programms.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer

Diese Schnittstelle wurde mit Visual Studio 2005 eingeführt. Asynchrone beenden wurde von frühere Versionen nicht unterstützt.

[Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) durch die SDM in Prozessen oder ein Programm mit mehreren Szenarien aufgerufen wird. Wenn ein Programm, das SDM Stopping-Ereignis gesendet wird, fordert die SDM andere Programme zu beenden.

Beenden wird verwendet, um asynchron die SDM informiert werden, die eine Anwendung beendet wurde. Informiert die SDM eignet sich für ein Interpreter-Debugmodul, dem manchmal innerhalb der debuggten kein Code ausgeführt wird-Programm so [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) kann nicht synchron abgeschlossen werden. Wenn ein Debugmodul diese asynchrone Benachrichtigung verwendet möchte, muss er zurück `S_ASYNC_STOP` aus [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Anforderungen

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll