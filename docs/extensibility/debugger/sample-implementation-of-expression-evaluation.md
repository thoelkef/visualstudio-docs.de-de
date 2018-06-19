---
title: Beispiel der Implementierung der Auswertung von Ausdrücken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edc31a8bc403f4f6dfcb16847d3cfce5d99b526
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127836"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Beispielimplementierung der Auswertung von Ausdrücken
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Für eine **Überwachen** Ausdruck, Visual Studio ruft [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) erzeugt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt. `IDebugExpressionContext2::ParseText` instanziiert eine ausdrucksauswertung (EE) und ruft [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Abrufen einer [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
 Diese Implementierung der `IDebugExpressionEvaluator::Parse` führt die folgenden Aufgaben:  
  
1.  [Nur C++] Analysiert den Ausdruck auf Fehler überprüfen.  
  
2.  Instanziiert eine Klasse (aufgerufen `CParsedExpression` in diesem Beispiel), implementiert die `IDebugParsedExpression` Schnittstelle, und speichert Sie in der Klasse den Ausdruck analysiert werden soll.  
  
3.  Gibt die `IDebugParsedExpression` -Schnittstelle aus dem `CParsedExpression` Objekt.  
  
> [!NOTE]
>  In den folgenden Beispielen und im MyCEE Beispiel ist die ausdrucksauswertung nicht trennen Sie die Analyse bei der Auswertung.  
  
## <a name="managed-code"></a>Verwalteter Code  
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in verwaltetem Code. Beachten Sie, dass diese Version der Methode die Analyse verzögert zu [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) als auch der Code für die Analyse gleichzeitig ausgewertet wird (finden Sie unter [auswerten einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in nicht verwaltetem Code. Diese Methode ruft eine Hilfsfunktion `Parse`, um den Ausdruck und die Überprüfung auf Fehler zu analysieren, aber diese Methode ignoriert den resultierenden Wert. Die formale Auswertung wird verzögert [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , in dem der Ausdruck analysiert wird, während sie ausgewertet wird (finden Sie unter [auswerten einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Bewerten einen Überwachungsausdruck-Fenster](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)