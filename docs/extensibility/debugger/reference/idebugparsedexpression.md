---
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725995"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt einen analysierten Ausdruck dar, der ausgewertet werden kann.

## <a name="syntax"></a>Syntax

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksauswertungswert implementiert diese Schnittstelle, um einen analysierten Ausdruck darzustellen, der für die Auswertung bereit ist.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugParsedExpression`die Methode von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Wertet den analysierten Ausdruck aus.|

## <a name="remarks"></a>Bemerkungen
 Wenn der Aufrufer bereit ist, den Ausdruck auszuwerten, ruft er [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) auf, um eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) zurückzugeben, die das Ergebnis der Auswertung enthält. Dieser zweiteilige Ansatz für die Auswertung und anschließende Auswertung ermöglicht die mehrfache Auswertung des analysierten Ausdrucks, wodurch der zeitaufwändige Prozess der Analyse des Ausdrucks umgangen wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
