---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719445"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Das Debugmodul (DE) kann dieses optionale Ereignis an den Sitzungsdebug-Manager (SDM) senden, wenn ein Programm beendet wurde.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer

Diese Schnittstelle wurde mit Visual Studio 2005 eingeführt. Frühere Versionen unterstützten kein asynchrones Beenden.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird vom SDM in Multiprozess- oder Multi-Programm-Szenarien aufgerufen. Wenn ein Programm ein Beenden-Ereignis an das SDM sendet, fordert das SDM auch andere Programme auf, die beendet werden.

Stop wird verwendet, um das SDM asynchron darüber zu informieren, dass ein Programm beendet wurde. Die Information des SDM ist nützlich für ein Interpreter-Debugmodul, bei dem manchmal kein Code innerhalb des debuggen Programms ausgeführt wird, sodass [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nicht synchron abgeschlossen werden kann. Wenn ein Debugmodul diese asynchrone Benachrichtigung verwenden `S_ASYNC_STOP` möchte, muss es von [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)zurückgegeben werden.

## <a name="requirements"></a>Requirements (Anforderungen)

Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
