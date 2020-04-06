---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729777"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Das Debugmodul (DE) sendet diese Schnittstelle an den Session Debug Manager (SDM), wenn eine Ausnahme in dem aktuell ausgeführten Programm ausgelöst wird.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Ausnahme in dem zu debuggenden Programm aufgetreten ist. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um eine Ausnahme zu melden. Das Ereignis wird mit der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugExceptionEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ruft detaillierte Informationen über die Ausnahme ab, die dieses Ereignis ausgelöst hat.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ruft eine vom Menschen lesbare Beschreibung für die ausgelöste Ausnahme ab, die dieses Ereignis ausgelöst hat.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Legt fest, ob das Debugmodul (DE) die Option unterstützt, diese Ausnahme an das zu debuggende Programm zu übergeben, wenn die Ausführung fortgesetzt wird.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Gibt an, ob die Ausnahme an das Programm übergeben werden soll, das gedebuggt wird, wenn die Ausführung fortgesetzt wird, oder ob die Ausnahme verworfen werden soll.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Bemerkungen
 Vor dem Senden des Ereignisses überprüft die DE, ob dieses Ausnahmeereignis durch einen vorherigen Aufruf von [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)als Ausnahme der ersten oder zweiten Chance festgelegt wurde. Wenn es als Ausnahme der ersten Chance `IDebugExceptionEvent2` festgelegt wurde, wird das Ereignis an das SDM gesendet. Ist dies nicht der Fall, gibt die DE der Anwendung die Möglichkeit, die Ausnahme zu behandeln. Wenn kein Ausnahmehandler bereitgestellt wird und die Ausnahme als Ausnahme der `IDebugExceptionEvent2` zweiten Chance festgelegt wurde, wird das Ereignis an das SDM gesendet. Andernfalls nimmt die DE die Ausführung des Programms wieder auf, und das Betriebssystem oder die Laufzeit behandelt die Ausnahme.

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
