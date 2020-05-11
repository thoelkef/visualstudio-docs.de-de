---
title: Implementieren eines Ausdrucksevaluators | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738540"
---
# <a name="implement-an-expression-evaluator"></a>Implementieren eines Ausdrucksevaluators
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Das Auswerten eines Ausdrucks ist ein komplexes Zusammenspiel zwischen dem Debugmodul (DE), dem Symbolanbieter (SP), dem Binderobjekt und dem Ausdrucksevaluator (EE). Diese vier Komponenten sind über Schnittstellen verbunden, die von einer Komponente implementiert und von einer anderen verwendet werden.

 Der EE nimmt einen Ausdruck aus der DE in Form einer Zeichenfolge an und analysiert oder wertet ihn aus. Der EE verfügt über die folgenden Schnittstellen, die von der DE genutzt werden:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  Der EE ruft das von der DE bereitgestellte Binderobjekt auf, um den Wert von Symbolen und Objekten abzubekommen. Die EE verbraucht die folgenden Schnittstellen, die von der DE implementiert werden:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Die EE führt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)aus. `IDebugProperty2`stellt den Mechanismus zum Beschreiben des Ergebnisses einer Ausdrucksauswertung bereit, z. B. einer lokalen Variablen, einem Primitiv oder einem Objekt für Visual Studio, das dann die entsprechenden Informationen im Fenster **"Lokale",** **"Uhr"** oder **"Unmittelbar"** anzeigt.

  Der SP wird der EE von der DE gegeben, wenn sie um Informationen bittet. Der SP führt Schnittstellen aus, die Adressen und Felder beschreiben, z. B. die folgenden Schnittstellen und deren Ableitungen:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  Der EE verbraucht alle diese Schnittstellen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementierungsstrategie für Ausdrucksevaluator](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definiert einen dreistufigen Prozess für die Implementierungsstrategie für Ausdrucksevaluator (EE).

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
