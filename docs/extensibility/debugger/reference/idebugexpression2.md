---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729691"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Diese Schnittstelle stellt einen analysierten Ausdruck dar, der zum Binden und Auswerten bereit ist.

## <a name="syntax"></a>Syntax

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um einen analysierten Ausdruck darzustellen, der ausgewertet werden kann.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) gibt diese Schnittstelle zurück. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die [IDebugExpressionContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) zurück. Auf diese Schnittstellen kann nur zugegriffen werden, wenn das zu debuggende Programm angehalten wurde und ein Stapelrahmen verfügbar ist.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugExpression2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet diesen Ausdruck asynchron aus.|
|[Abbrechen](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucksauswertung.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bewertet diesen Ausdruck synchron.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Programm angehalten wurde, ruft der Sitzungsdebug-Manager (SDM) einen Stackframe von der DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)ab. Das SDM ruft dann [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die [IDebugExpressionContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) abruft. Es folgt ein Aufruf von [ParseText,](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) um die `IDebugExpression2` Schnittstelle zu erstellen, die den analysierten Ausdruck darstellt, der ausgewertet werden kann.

 Das SDM ruft entweder [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den Ausdruck tatsächlich auszuwerten und einen Wert zu erzeugen.

 In einer `IDebugExpressionContext2::ParseText`Implementierung von verwendet die `CoCreateInstance` DE die Funktion von COM, um einen Ausdrucksevaluator zu instanziieren `IDebugExpressionEvaluator` und eine [IDebugExpressionEvaluator-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) abzubekommen (siehe Beispiel in der Schnittstelle). Die DE ruft dann [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf, um eine [IDebugParsedExpression-Schnittstelle](../../../extensibility/debugger/reference/idebugparsedexpression.md) zu erhalten. Diese Schnittstelle wird bei `IDebugExpression2::EvaluateSync` der `IDebugExpression2::EvaluateAsync` Implementierung und Durchführung der Auswertung verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
