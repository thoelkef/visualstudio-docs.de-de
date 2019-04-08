---
title: Auswerten eines Überwachungsausdrucks | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4eb1ee2048a5e5580cbeb8320ba573c85b92183
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957295"
---
# <a name="evaluating-a-watch-expression"></a>Auswerten eines Überwachungsausdrucks
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn Visual Studio für die Anzeige des Wert eines Ausdrucks sehen Sie sich bereit ist, ruft er [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wiederum ruft [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Dies führt zu einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das den Wert und Typ des Ausdrucks enthält.  
  
 In dieser Implementierung der `IDebugParsedExpression::EvaluateSync`, der Ausdruck analysiert und gleichzeitig ausgewertet. Diese Implementierung führt die folgenden Aufgaben:  
  
1.  Analysiert und wertet den Ausdruck aus, um ein generisches Objekt zu erstellen, das den Wert und den Typ enthält. In C# wird dies als eine `object` während C++ dies als dargestellt wird ein `VARIANT`.  
  
2.  Instanziiert die Klasse (namens `CValueProperty` in diesem Beispiel), implementiert die `IDebugProperty2` Schnittstelle, und speichert Sie in der Klasse den Wert zurückgegeben werden.  
  
3.  Gibt die `IDebugProperty2` -Schnittstelle aus der `CValueProperty` Objekt.  
  
## <a name="managed-code"></a>Verwalteter Code  
 Dies ist eine Implementierung der `IDebugParsedExpression::EvaluateSync` in verwaltetem Code. Die Hilfsmethode `Tokenize` analysiert den Ausdruck in eine Analysestruktur. Die Hilfsfunktion `EvalToken` das Token auf einen Wert konvertiert. Die Hilfsfunktion `FindTerm` rekursiv durchläuft die Analysestruktur Aufrufen `EvalToken` für jeden Knoten, die einen Wert darstellt, und alle Vorgänge (Addition oder Multiplikation) im Ausdruck anwenden.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Nicht verwalteter Code  
 Dies ist eine Implementierung der `IDebugParsedExpression::EvaluateSync` in nicht verwaltetem Code. Die Hilfsfunktion `Evaluate` analysiert und wertet den Ausdruck, der Rückgabe eine `VARIANT` , enthält den resultierenden Wert. Die Hilfsfunktion `VariantValueToProperty` Pakete die `VARIANT` in einem `CValueProperty` Objekt.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Beispielimplementierung der Ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
