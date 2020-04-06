---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723330"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Mit dieser Schnittstelle kann der Sitzungsdebug-Manager (SDM) einen Prozess benachrichtigen, den er an den Prozess anfügt oder vom Prozess löst.

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle für dasselbe Objekt wie die [IDebugProcess2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprocess2.md) um:

- Unterstützung der Nachverfolgung von Sitzungen, die mit einem Prozess verbunden sind

- Unterstützung der automatischen Anfüdefunktion über mehrere Debug-Engines

  Der benutzerdefinierte Portlieferant kann diese Schnittstelle implementieren, wenn er dies auswählt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer

- Das SDM ruft [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProcess2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProcessEx2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Anfügen](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informiert den Prozess, dass eine Sitzung den Prozess jetzt debuggen.|
|[Trennen](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informiert den Prozess, dass eine Sitzung den Prozess nicht mehr debuggen.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Fügt Programmknoten für eine Liste von Debugmodulen hinzu.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist privat zwischen dem SDM und dem Prozess.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
