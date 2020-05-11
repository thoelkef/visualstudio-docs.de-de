---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735969"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bindet ein Symbolfeld, das normalerweise vom Symbolanbieter zurückgegeben wird, an einen Speicherkontext oder ein Objekt, das den aktuellen Wert des Symbols enthält.

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle unterstützt die Ausdrucksauswertung und muss vom Debugmodul (DE) implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird bei der Ausexpressionauswertung verwendet und wird in der Regel bei der Implementierung von [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBinder`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft den Speicherkontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Laufzeittyp eines Objekts.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert einen Objektspeicherort oder eine Speicheradresse in einen Speicherkontext.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft ein [IDebugFunctionObject-Objekt](../../../extensibility/debugger/reference/idebugfunctionobject.md) ab, das zum Erstellen von Funktionsparametern verwendet wird.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den genauen Typ für eine Variable ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle gibt Objekte zurück, die vom Ausdrucksevaluator in Analysestrukturen verwendet werden. Der Ausdrucksauswertungswert analysiert einen Ausdruck, indem er den Symbolanbieter verwendet, um die Symbole im Ausdruck in Instanzen von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)zu konvertieren, die jedes Symbol in Bezug auf seinen Typ und seine Position im Quellcode beschreiben. Die [Bind-Methode](../../../extensibility/debugger/reference/idebugbinder-bind.md) konvertiert `IDebugField` Objekte in [IDebugObject-Objekte,](../../../extensibility/debugger/reference/idebugobject.md) die einen Symboltyp mit einem tatsächlichen Wert im Arbeitsspeicher verbinden oder binden. Diese `IDebugObject` Objekte werden dann zur späteren Auswertung in einer Analysestruktur gespeichert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
