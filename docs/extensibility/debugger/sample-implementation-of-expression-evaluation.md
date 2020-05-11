---
title: Beispielimplementierung der Ausdrucksbewertung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713102"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Beispielimplementierung der Ausdrucksauswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und Beispiel für [managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Für einen **Watch-Fensterausdruck** ruft Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) auf, um ein [IDebugExpression2-Objekt](../../extensibility/debugger/reference/idebugexpression2.md) zu erstellen. `IDebugExpressionContext2::ParseText`instanziiert einen Ausdrucksevaluator (EE) und ruft [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf, um ein [IDebugParsedExpression-Objekt](../../extensibility/debugger/reference/idebugparsedexpression.md) abzuruft.

 Der `IDebugExpressionEvaluator::Parse` führt die folgenden Aufgaben aus:

1. [Nur C++ Analysiert den Ausdruck, um nach Fehlern zu suchen.

2. Instanziiert eine Klasse `CParsedExpression` (in diesem Beispiel `IDebugParsedExpression` aufgerufen), die die Schnittstelle ausführt und in der Klasse den zu analysierenden Ausdruck speichert.

3. Gibt `IDebugParsedExpression` die Schnittstelle `CParsedExpression` aus dem Objekt zurück.

> [!NOTE]
> In den folgenden Beispielen und im MyCEE-Beispiel trennt der Ausdrucksbewerter die Analyse nicht von der Auswertung.

## <a name="managed-code"></a>Verwalteter Code
 Der folgende Code zeigt `IDebugExpressionEvaluator::Parse` eine Implementierung von in verwaltetem Code. Diese Version der Methode verschiebt die Analyse auf [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) da der Code für die Analyse gleichzeitig ebenfalls ausgewertet wird (siehe [Auswerten eines Watch-Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
Der folgende Code ist `IDebugExpressionEvaluator::Parse` eine Implementierung von in nicht verwaltetem Code. Diese Methode ruft eine `Parse`Hilfsfunktion auf, um den Ausdruck zu analysieren und nach Fehlern zu suchen, aber diese Methode ignoriert den resultierenden Wert. Die formale Auswertung wird auf [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) verschoben, wo der Ausdruck analysiert wird, während er ausgewertet wird (siehe [Bewerten eines Watch-Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Auswerten eines Watch-Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)
