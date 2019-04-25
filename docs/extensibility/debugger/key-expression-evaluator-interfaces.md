---
title: Wichtige Schnittstellen für die Ausdrucksauswertung Ausdruck | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f2eeb87bbc0bfef2fa1845fe428a8e178c1d4de
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109963"
---
# <a name="key-expression-evaluator-interfaces"></a>Wichtige Schnittstellen für die ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Beim Schreiben einer ausdrucksauswertung (EE), zusammen mit dem Auswertungskontext sollten Sie mit der folgenden Schnittstellen vertraut sein.

## <a name="interface-descriptions"></a>Schnittstellenbeschreibungen

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Verfügt über eine einzelne Methode, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), die einer Datenstruktur abruft, die dem aktuellen Zeitpunkt der Ausführung darstellt. Diese Datenstruktur ist eines der drei Argumente, die an die Debug-Engine (DE) übergibt die [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Methode zum Auswerten eines Ausdrucks. Diese Schnittstelle wird in der Regel von der symbolanbieter implementiert.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Hat die [binden](../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode, die den Speicherbereich Ruft ab, die den aktuellen Wert eines Symbols enthält. Sowohl der enthaltenden Methode, dargestellt durch ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt und das Symbol, dargestellt durch ein [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt `IDebugBinder::Bind` gibt den Wert des Symbols zurück. `IDebugBinder` wird in der Regel durch die DE implementiert werden.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Stellt einen einfachen Datentyp dar. Verwenden Sie für komplexere Typen wie Arrays und Methoden, die abgeleitete [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) und [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) bzw.-Schnittstellen. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) ist eine andere wichtige abgeleitete Schnittstelle, die Symbole, die mit anderen Symbolen, z. B. Methoden oder Klassen darstellt. Die `IDebugField` -Schnittstelle (und seine ableitungen) werden in der Regel von der symbolanbieter implementiert.

     Ein `IDebugField` Objekt kann verwendet werden, die den Namen und Typ eines Symbols zu finden und, zusammen mit einem [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Objekt, kann verwendet werden, um den Wert zu suchen.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Stellt die eigentlichen Bits des Werts eines Symbols Laufzeit dar. [Binden Sie](../../extensibility/debugger/reference/idebugbinder-bind.md) nimmt eine [IDebugField](../../extensibility/debugger/reference/idebugfield.md) -Objekt, das ein Symbol dargestellt, und gibt ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt. Die ["GetValue"](../../extensibility/debugger/reference/idebugobject-getvalue.md) -Methode gibt den Wert des Symbols in einem Puffer zwischengespeichert. Eine bereitgestellten Kompatibilitätsrichtlinie wird in der Regel implementiert diese Schnittstelle, um den Wert einer Eigenschaft im Speicher darstellen.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Diese Schnittstelle stellt die ausdrucksauswertung selbst. Die Schlüsselmethode ist [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), gibt ein [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Diese Schnittstelle stellt einen analysierten Ausdruck zur Auswertung bereiter dar. Die Schlüsselmethode ist [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gibt eine IDebugProperty2, die den Wert und Typ des Ausdrucks darstellt.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Diese Schnittstelle stellt einen Wert und den Typ dar und ist das Ergebnis der Auswertung eines Ausdrucks.

## <a name="see-also"></a>Siehe auch
- [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)