---
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a07f2808c1aaeca3c1631fce658fdf6e8da32d60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727767"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Session Debug Manager (SDM) gesendet, wenn die DE die Behandlung eines abgefangenen Ereignisses abgeschlossen hat.

## <a name="syntax"></a>Syntax

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um den Abschluss einer abgefangenen Ausnahme zu melden. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die `IDebugInterceptExceptionCompleteEvent2` Schnittstelle implementiert die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Gibt den eindeutigen Wert zurück, der der behandelten Ausnahme zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Dieses Ereignis wird von [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) gesendet, wenn diese Methode die Behandlung einer abgefangenen Ausnahme erfolgreich abgeschlossen hat.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
