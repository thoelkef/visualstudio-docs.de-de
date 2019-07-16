---
title: IDebugParsedExpression | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56c0547d348c4fb3de387ac0ffce465b7bf5e90
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311777"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt einen analysierten Ausdruck zur Auswertung bereiter dar.

## <a name="syntax"></a>Syntax

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine ausdrucksauswertung implementiert diese Schnittstelle einen analysierten Ausdruck darstellt, der für die Evaluierung bereit ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) dieser Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methode der `IDebugParsedExpression`.

|Methode|Beschreibung|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Wertet den analysierten Ausdruck.|

## <a name="remarks"></a>Hinweise
 Wenn der Aufrufer zum Auswerten des Ausdrucks bereit ist, ruft er [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) zurückzugebenden ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , die das Ergebnis der Auswertung enthält. Dieser Ansatz mit dem zweiteiligen Auswertung, analysieren und dann auswerten, können den analysierten Ausdruck mehrmals ausgewertet werden soll, die zeitaufwändig Analysieren des Ausdrucks zu umgehen.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Auslesen](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)