---
title: IDebugStopCompleteEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d080b3073ffc13b90870b40a16a353634f4aa0cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352010"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Die Debug-Engine (DE) kann dieses optionale Ereignis für die Sitzung Debug-Manager (SDM) senden, wenn ein Programm beendet wurde.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer

Diese Schnittstelle wurde mit Visual Studio 2005 eingeführt. Asynchrones beenden wurde von frühere Versionen nicht unterstützt.

- [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, durch die SDM mit mehreren Prozessen oder mit mehreren Programm Szenarios. Wenn ein Programm eine Beenden-Ereignis, das SDM sendet, fordert das SDM andere Programme zu beenden.

Beenden wird verwendet, um asynchron die SDM zu informieren, die ein Programm beendet wurde. Informiert das SDM eignet sich für ein Interpreter-Debug-Engine, dem manchmal innerhalb der debuggten kein Code ausgeführt wird programmieren, also [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nicht synchron abgeschlossen werden kann. Wenn eine Debug-Engine diese asynchrone Benachrichtigung einsetzen will, muss es zurückgeben `S_ASYNC_STOP` aus [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Anforderungen

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll