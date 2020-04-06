---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729376"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Diese Schnittstelle stellt den Ausdrucksevaluator dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Der Ausdrucksauswertungsor muss diese Schnittstelle implementieren.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Um diese Schnittstelle zu erhalten, instanziieren Sie `CoCreateInstance` den Ausdrucksevaluator über die Methode mithilfe der Klassen-ID (CLSID) des Evaluators. Siehe Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt `IDebugExpressionEvaluator`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ruft die lokalen Variablen, Argumente und andere Eigenschaften einer Methode ab.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konvertiert eine Methodenposition und versetzt in eine Speicheradresse.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Bestimmt, welche Sprache zum Erstellen druckbarer Ergebnisse verwendet werden soll.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Legt den Registrierungsstamm fest. Wird für das side-by-side-Debugging verwendet.|

## <a name="remarks"></a>Bemerkungen
In einer typischen Situation instanziiert das Debugmodul (DE) den Ausdrucksevaluator (EE) als Ergebnis eines Aufrufs von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Da die DE die Sprache und den Anbieter des EE kennt, die sie verwenden möchte, ruft die DE die `GetEEMetric`CLSID des EE aus der Registrierung ab (die [SDK-Hilfsfunktion hilft bei](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) diesem Abruf).

Nachdem der EE instanziiert wurde, ruft die DE [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf, um den Ausdruck zu analysieren und in einem [IDebugParsedExpression-Objekt](../../../extensibility/debugger/reference/idebugparsedexpression.md) zu speichern. Später wertet ein Aufruf von [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) den Ausdruck aus.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: ee.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie der Ausdrucksauswertungswert instanziiert wird, der einen Symbolanbieter und eine Adresse im Quellcode erhält. In diesem Beispiel `GetEEMetric`wird eine Funktion verwendet, , aus der [SDK-Hilfsbibliothek "Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib".

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
