---
title: Key Expression Evaluator-Schnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738488"
---
# <a name="key-expression-evaluator-interfaces"></a>Schlüsselausdrucksauswertungsschnittstellen
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Beim Schreiben eines Ausdrucksevaluators (EE) und des Auswertungskontexts sollten Sie mit den folgenden Schnittstellen vertraut sein.

## <a name="interface-descriptions"></a>Schnittstellenbeschreibungen

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Verfügt über eine einzelne Methode, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), die eine Datenstruktur abruft, die den aktuellen Ausführungspunkt darstellt. Diese Datenstruktur ist eines der drei Argumente, die das Debugmodul (DE) an die [EvaluateSync-Methode](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) zum Auswerten eines Ausdrucks übergibt. Diese Schnittstelle wird in der Regel vom Symbolanbieter implementiert.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Hat [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) die Bind-Methode, die den Speicherbereich abruft, der den aktuellen Wert eines Symbols enthält. Da sowohl die enthaltende Methode, die durch ein [IDebugObject-Objekt](../../extensibility/debugger/reference/idebugobject.md) dargestellt wird, als auch das Symbol selbst, dargestellt durch ein [IDebugField-Objekt,](../../extensibility/debugger/reference/idebugfield.md) `IDebugBinder::Bind` den Wert des Symbols zurückgibt. `IDebugBinder`wird in der Regel von der DE implementiert.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Stellt einen einfachen Datentyp dar. Für komplexere Typen, z. B. Arrays und Methoden, verwenden Sie die abgeleiteten [IDebugArrayField-](../../extensibility/debugger/reference/idebugarrayfield.md) bzw. [IDebugMethodField-Schnittstellen.](../../extensibility/debugger/reference/idebugmethodfield.md) [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) ist eine weitere wichtige abgeleitete Schnittstelle, die Symbole darstellt, die andere Symbole enthalten, wie Methoden oder Klassen. Die `IDebugField` Schnittstelle (und ihre Derivate) wird in der Regel vom Symbolanbieter implementiert.

     Ein `IDebugField` Objekt kann verwendet werden, um den Namen und Typ eines Symbols zu finden und zusammen mit einem [IDebugBinder-Objekt](../../extensibility/debugger/reference/idebugbinder.md) seinen Wert zu finden.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Stellt die tatsächlichen Bits des Laufzeitwerts eines Symbols dar. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) nimmt ein [IDebugField-Objekt,](../../extensibility/debugger/reference/idebugfield.md) das ein Symbol darstellt, und gibt ein [IDebugObject-Objekt](../../extensibility/debugger/reference/idebugobject.md) zurück. Die [GetValue-Methode](../../extensibility/debugger/reference/idebugobject-getvalue.md) gibt den Wert des Symbols in einem Speicherpuffer zurück. Eine DE implementiert diese Schnittstelle in der Regel, um den Wert einer Eigenschaft im Arbeitsspeicher darzustellen.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Diese Schnittstelle stellt den Ausdrucksevaluator selbst dar. Die Schlüsselmethode ist [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), die eine [IDebugParsedExpression-Schnittstelle](../../extensibility/debugger/reference/idebugparsedexpression.md) zurückgibt.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Diese Schnittstelle stellt einen analysierten Ausdruck dar, der ausgewertet werden kann. Die Key-Methode ist [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) die eine IDebugProperty2 zurückgibt, die den Wert und Typ des Ausdrucks darstellt.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Diese Schnittstelle stellt einen Wert und seinen Typ dar und ist das Ergebnis einer Ausdrucksauswertung.

## <a name="see-also"></a>Weitere Informationen
- [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)
