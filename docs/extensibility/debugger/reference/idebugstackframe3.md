---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719471"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Diese Schnittstelle erweitert [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) um abgefangene Ausnahmen zu behandeln.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugStackFrame2-Schnittstelle](../../../extensibility/debugger/reference/idebugstackframe2.md) implementiert, um abgefangene Ausnahmen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugStackFrame2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)geerbt wurden, `IDebugStackFrame3` werden die folgenden Methoden verfügbar gemacht.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Behandelt eine Ausnahme für den aktuellen Stapelrahmen vor einer regulären Ausnahmebehandlung.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Gibt einen Codekontext zurück, wenn ein Stapelaufwind enden sollte.|

## <a name="remarks"></a>Bemerkungen
 Eine abgefangene Ausnahme bedeutet, dass ein Debugger eine Ausnahme verarbeiten kann, bevor normale Ausnahmebehandlungsroutinen von der Laufzeit aufgerufen werden. Das Abfangen einer Ausnahme bedeutet im Wesentlichen, dass die Laufzeit so tut, als ob ein Ausnahmehandler vorhanden ist, selbst wenn dies nicht der Fall ist.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) wird bei allen normalen Ausnahmerückrufereignissen aufgerufen (die einzige Ausnahme ist, wenn Sie Code im gemischten Modus debuggen (verwalteter und nicht verwalteter Code), in diesem Fall kann die Ausnahme während des Rückrufs der letzten Chance nicht abgefangen werden). Wenn de nicht implementiert `IDebugStackFrame3`wird oder die DE einen Fehler von`InterceptCurrentException` IDebugStackFrame3: (z. B. ) `E_NOTIMPL`zurückgibt, behandelt der Debugger die Ausnahme normal.

 Durch abfangen einer Ausnahme kann der Debugger dem Benutzer erlauben, Änderungen am Status des zu debuggenden Programms vorzunehmen und dann die Ausführung an dem Punkt fortzusetzen, an dem die Ausnahme ausgelöst wurde.

> [!NOTE]
> Abgefangene Ausnahmen sind nur in verwaltetem Code zulässig, d. h. in einem Programm, das unter der Common Language Runtime (CLR) ausgeführt wird.

 Ein Debugmodul gibt an, dass es das Abfangen von Ausnahmen unterstützt, indem "metricExceptions" zur Laufzeit mithilfe der `SetMetric` Funktion auf den Wert 1 gesetzt wird. Weitere Informationen finden Sie unter [SDK-Hilfsprogramme zum Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
