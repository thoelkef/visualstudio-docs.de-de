---
title: IDebugExpressionEvaluator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b54b8d4ab6c30bcefe99928409680ed5fa08cb0
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449852"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Diese Schnittstelle stellt die ausdrucksauswertung dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Die ausdrucksauswertung muss diese Schnittstelle implementieren.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Um diese Schnittstelle abzurufen, instanziieren Sie die ausdrucksauswertung über die `CoCreateInstance` Methode mithilfe der Klasse-ID (CLSID) der Auswertung. Siehe das Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDebugExpressionEvaluator`.

|Methode|Beschreibung|
|------------|-----------------|
|[Auslesen](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ruft ab, die lokalen Variablen, Argumente und andere Eigenschaften einer Methode.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konvertiert einen Methode Speicherort und einen Offset, in eine Speicheradresse.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Bestimmt, welche Sprache Sie zum Erstellen von druckbaren Ergebnisse verwenden.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Legt den Registrierungsstamm. Zum Debuggen von Seite-an-Seite verwendet.|

## <a name="remarks"></a>Hinweise
In einer typischen Fall instanziiert die Debug-Engine (DE) die ausdrucksauswertung (EE) aufgrund eines Aufrufs von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Da die DE weiß die Sprache und den Anbieter, der den zu verwendenden EE, ruft die DE die EE CLSID aus der Registrierung (die [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) -Funktion `GetEEMetric`, können Sie mit diesen Abruf).

Nachdem die EE instanziiert wurde, ruft die DE [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Analysieren des Ausdrucks, und speichern Sie sie in einer [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt. Später einen Aufruf von [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) wertet den Ausdruck.

## <a name="requirements"></a>Anforderungen
Header: ee.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie die ausdrucksauswertung, erhalten ein symbolanbieter und eine Adresse im Quellcode zu instanziieren. Dieses Beispiel verwendet eine Funktion, `GetEEMetric`, aus der [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) -Bibliothek, dbgmetric.lib.

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

## <a name="see-also"></a>Siehe auch
[Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)  
[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)  
[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)  
[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)  
[SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
