---
title: Auswerten eines Überwachungsausdrucks | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1704a33abddada9a439786b408a8bc7bceeba0d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711227"
---
# <a name="evaluate-a-watch-expression"></a>Auswerten eines Überwachungsausdrucks
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Wenn Visual Studio für die Anzeige des Wert eines Ausdrucks sehen Sie sich bereit ist, ruft er [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), die wiederum ruft [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Dieser Prozess erzeugt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das den Wert und Typ des Ausdrucks enthält.

In dieser Implementierung der `IDebugParsedExpression::EvaluateSync`, der Ausdruck analysiert und gleichzeitig ausgewertet. Diese Implementierung führt die folgenden Aufgaben:

1. Analysiert und wertet den Ausdruck aus, um ein generisches Objekt zu erstellen, das den Wert und den Typ enthält. In c# wird dies als eine `object` in C++, liegt dies als eine `VARIANT`.

2. Instanziiert die Klasse (namens `CValueProperty` in diesem Beispiel), implementiert die `IDebugProperty2` Schnittstelle, und speichert Sie in der Klasse den Wert zurückgegeben werden.

3. Gibt die `IDebugProperty2` -Schnittstelle aus der `CValueProperty` Objekt.

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

## <a name="unmanaged-code"></a>Nicht verwalteter code
Dies ist eine Implementierung der `IDebugParsedExpression::EvaluateSync` in nicht verwaltetem Code. Die Hilfsfunktion `Evaluate` analysiert und wertet den Ausdruck, der Rückgabe eine `VARIANT` , enthält den resultierenden Wert. Die Hilfsfunktion `VariantValueToProperty` Pakete die `VARIANT` in einem `CValueProperty` Objekt.

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

## <a name="see-also"></a>Siehe auch
- [Auswerten eines überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Beispielimplementierung der ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
