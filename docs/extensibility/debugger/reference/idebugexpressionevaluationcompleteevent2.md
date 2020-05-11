---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35e57e361b59e76e187617b5e528b219e8e47897
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729555"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Session Debug Manager (SDM) gesendet, wenn die asynchrone Ausdrucksauswertung abgeschlossen ist.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um den Abschluss einer Ausdrucksauswertung zu melden, die durch einen Aufruf von [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)gestartet wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um den Abschluss einer Ausdrucksauswertung zu melden. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugExpressionEvaluationCompleteEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Ruft den ursprünglichen Ausdruck ab.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ruft das Ergebnis der Ausdrucksauswertung ab.|

## <a name="remarks"></a>Bemerkungen
 Die DE muss dieses Ereignis senden, unabhängig davon, ob die Auswertung erfolgreich war oder nicht.

 Wenn die Auswertung nicht `DEBUG_PROPINFO_VALUE` erfolgreich `DEBUG_PROPINFO_ATTRIB` war, werden die und Flags nicht in der [DEBUG_PROPERTY_INFO-Struktur](../../../extensibility/debugger/reference/debug-property-info.md) festgelegt, die von [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zurückgegeben wird (das [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) wird von der DE erstellt und im `IDebugExpressionEvaluationCompleteEvent2` Ereignis zurückgegeben, wenn die Auswertung fehlgeschlagen ist).

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
