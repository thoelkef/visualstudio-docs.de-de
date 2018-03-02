---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8941decfb4e64906c57b719df711ce8779df9c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
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