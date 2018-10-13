---
title: Beispiel für die Implementierung der Ausdrucksauswertung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60582c20e50dbab64dbbfe2cf534337685c064a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182486"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Beispielimplementierung der Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Für eine **Überwachen** Fensters Ausdrucks, Visual Studio-Aufrufe [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erzeugen einer [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt. `IDebugExpressionContext2::ParseText` instanziiert eine ausdrucksauswertung (EE) und ruft [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Abrufen einer [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
 Diese Implementierung der `IDebugExpressionEvaluator::Parse` führt die folgenden Aufgaben:  
  
1.  [Nur für C++] Analysiert den Ausdruck auf Fehler überprüfen.  
  
2.  Instanziiert die Klasse (namens `CParsedExpression` in diesem Beispiel), implementiert die `IDebugParsedExpression` Schnittstelle, und speichert Sie in der Klasse den Ausdruck analysiert werden.  
  
3.  Gibt die `IDebugParsedExpression` -Schnittstelle aus der `CParsedExpression` Objekt.  
  
> [!NOTE]
>  In den folgenden Beispielen und das MyCEE-Beispiel wird trennt die ausdrucksauswertung nicht die Analyse bei der Auswertung.  
  
## <a name="managed-code"></a>Verwalteter Code  
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in verwaltetem Code. Beachten Sie, dass diese Version der Methode die Analyse verzögert zu [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) wie der Code für die Analyse zur gleichen Zeit auch ausgewertet wird (finden Sie unter [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in nicht verwaltetem Code. Diese Methode ruft eine Hilfsfunktion `Parse`, um den Ausdruck und eine Überprüfung auf Fehler zu analysieren, aber diese Methode ignoriert den resultierenden Wert. Die formale Auswertung in Bezug auf verzögert [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , in dem der Ausdruck analysiert wird, während sie ausgewertet wird (finden Sie unter [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
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
 [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)

