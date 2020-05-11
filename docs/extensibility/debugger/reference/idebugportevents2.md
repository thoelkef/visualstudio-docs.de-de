---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725178"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Diese Schnittstelle benachrichtigt einen Listener (in der Regel den Sitzungsdebug-Manager [SDM] oder ein Debugmodul) über die Prozess- und Programmerstellung und -zerstörung auf einem bestimmten Port. Diese Informationen können verwendet werden, um eine Echtzeitansicht der Prozesse und Programme zu präsentieren, die auf dem Port ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle in der Regel, um Benachrichtigungen über die Programmerstellung und -zerstörung zu erhalten. Ein Debugmodul kann diese Schnittstelle auch implementieren, um auf solche Portereignisse zu warten.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Alle [IDebugPort2-Schnittstellen](../../../extensibility/debugger/reference/idebugport2.md) können für <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> eine Schnittstelle abgefragt werden. Dann <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> wird `IDebugPortEvents2` die Methode <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> für in <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> der Schnittstelle aufgerufen, um eine Schnittstelle zu erhalten. Schließlich wird <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Methode in der Schnittstelle aufgerufen, um die Ereignisse über die [Event-Methode](../../../extensibility/debugger/reference/idebugportevents2-event.md) zu senden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPortEvents2`die Methode von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Sendet Ereignisse, die die Erstellung und Zerstörung von Prozessen und Programmen auf dem Port beschreiben.|

## <a name="remarks"></a>Bemerkungen
 `IDebugPortEvents2`wird auch vom SDM zum Debuggen von Programmen verwendet, die in einem Prozess ausgeführt werden, der bereits gedebuggen wird.

 Portereignisse werden über diese Schnittstelle an das SDM übergeben.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
