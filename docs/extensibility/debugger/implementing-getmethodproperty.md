---
title: Implementieren von GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738515"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty implementieren
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio ruft die [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)des Debugmoduls (DE) auf, die wiederum [GetMethodProperty aufruft,](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) um Informationen über die aktuelle Methode auf dem Stapelrahmen abzufragen.

Diese Implementierung `IDebugExpressionEvaluator::GetMethodProperty` von führt die folgenden Aufgaben aus:

1. Ruft [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)auf, das das [IDebugAddress-Objekt](../../extensibility/debugger/reference/idebugaddress.md) übergeben wird. Der Symbolanbieter (SP) gibt ein [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) zurück, das die Methode darstellt, die die angegebene Adresse enthält.

2. Ruft das [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField`von der ab.

3. Instanziiert eine Klasse `CFieldProperty` (in diesem Beispiel genannt), die die [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) implementiert und das `IDebugMethodField` vom SP zurückgegebene Objekt enthält.

4. Gibt `IDebugProperty2` die Schnittstelle `CFieldProperty` aus dem Objekt zurück.

## <a name="managed-code"></a>Verwalteter Code
Dieses Beispiel zeigt `IDebugExpressionEvaluator::GetMethodProperty` eine Implementierung von in verwaltetem Code.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
Dieses Beispiel zeigt `IDebugExpressionEvaluator::GetMethodProperty` eine Implementierung von in nicht verwaltetem Code.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Beispielimplementierung von Locals](../../extensibility/debugger/sample-implementation-of-locals.md)
