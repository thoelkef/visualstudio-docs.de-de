---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722149"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Wird vom Debugmodul (DE) an den Sitzungsdebug-Manager (SDM) gesendet, wenn sich der Name eines Programms ändert.

## <a name="syntax"></a>Syntax

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass sich der Name des Programms geändert hat. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die **IDebugEvent2-Schnittstelle** zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um eine Programmnamensänderung zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2-Rückruffunktion,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird. Der benutzerdefinierte Portlieferant sendet dieses Ereignis über die I-Schnittstelle.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
