---
title: Auswerten eines Überwachungsausdrucks | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738854"
---
# <a name="evaluate-a-watch-expression"></a>Auswerten eines Uhrausdrucks
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Wenn Visual Studio bereit ist, den Wert eines Watch-Ausdrucks anzuzeigen, ruft es [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)auf, das wiederum [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)aufruft. Dieser Prozess erzeugt ein [IDebugProperty2-Objekt,](../../extensibility/debugger/reference/idebugproperty2.md) das den Wert und Typ des Ausdrucks enthält.

In dieser `IDebugParsedExpression::EvaluateSync`Implementierung von wird der Ausdruck analysiert und gleichzeitig ausgewertet. Diese Implementierung führt die folgenden Aufgaben aus:

1. Analysiert und wertet den Ausdruck aus, um ein generisches Objekt zu erzeugen, das den Wert und seinen Typ enthält. In C- wird dies `object` als eine While in C++ dargestellt, dies wird als eine `VARIANT`dargestellt.

2. Instanziiert eine Klasse `CValueProperty` (in diesem Beispiel genannt), die die `IDebugProperty2` Schnittstelle implementiert und den zurückzugebenden Wert in der Klasse speichert.

3. Gibt `IDebugProperty2` die Schnittstelle `CValueProperty` aus dem Objekt zurück.

## <a name="managed-code"></a>Verwalteter Code
Dies ist eine `IDebugParsedExpression::EvaluateSync` Implementierung des in verwalteten Codes. Die Hilfsmethode `Tokenize` analysiert den Ausdruck in einer Analysestruktur. Die Hilfsfunktion `EvalToken` konvertiert das Token in einen Wert. Die Hilfsfunktion `FindTerm` durchläuft rekursiv die Analysestruktur, `EvalToken` ruft jeden Knoten auf, der einen Wert darstellt, und wendet alle Operationen (Addition oder Subtraktion) im Ausdruck an.

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
Dies ist eine `IDebugParsedExpression::EvaluateSync` Implementierung des nicht verwalteten Codes. Die Hilfsfunktion `Evaluate` analysiert und wertet den `VARIANT` Ausdruck aus und gibt einen Haltewert zurück. Die Hilfsfunktion `VariantValueToProperty` bündelt `VARIANT` die `CValueProperty` in einem Objekt.

```cpp
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

## <a name="see-also"></a>Weitere Informationen
- [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Beispielimplementierung der Ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
