---
title: IDebugEngineCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a964f1e08fc2e88ac9a1d211e4b3e36b32c5b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730594"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Das Debugmodul (DE) sendet diese Schnittstelle an den Session Debug Manager (SDM), wenn eine Instanz der DE erstellt wird.

## <a name="syntax"></a>Syntax

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle als Teil ihrer normalen Operationen. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle `QueryInterface` implementiert werden `IDebugEvent2` (das SDM verwendet die Methode, um auf die Schnittstelle zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn die DE instanziiert wurde. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEngineCreateEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Ruft das Objekt ab, das das neu erstellte Debugmodul (DE) darstellt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
