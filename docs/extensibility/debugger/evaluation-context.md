---
title: Evaluierungskontext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738800"
---
# <a name="evaluation-context"></a>Evaluierungskontext
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn das Debugmodul (DE) den Ausdrucksevaluator (EE) aufruft, bestimmen drei Argumente, die an [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) übergeben werden, den Kontext für das Suchen und Auswerten von Symbolen, wie in der folgenden Tabelle dargestellt.

## <a name="arguments"></a>Argumente

|Argument|BESCHREIBUNG|
|--------------|-----------------|
|`pSymbolProvider`|Eine [IDebugSymbolProvider-Schnittstelle,](../../extensibility/debugger/reference/idebugsymbolprovider.md) die den Symbolhandler (SH) angibt, der zum Identifizieren des Symbols verwendet werden soll.|
|`pAddress`|Eine [IDebugAddress-Schnittstelle,](../../extensibility/debugger/reference/idebugaddress.md) die den aktuellen Ausführungspunkt angibt. Diese Schnittstelle findet die Methode, die den ausgeführten Code enthält.|
|`pBinder`|Eine [IDebugBinder-Schnittstelle,](../../extensibility/debugger/reference/idebugbinder.md) die den Wert und Typ eines Symbols mit dem Namen findet.|

 `IDebugParsedExpression::EvaluateSync`gibt eine [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) zurück, die den resultierenden Wert und seinen Typ darstellt.

## <a name="see-also"></a>Weitere Informationen
- [Schlüsselausdrucksauswertungsschnittstellen](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Anzeigen von Einheimischen](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
