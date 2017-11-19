---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator
helpviewer_keywords: IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b7cc2e6c0d25ceebd41648b227405978d1fb67d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt die ausdrucksauswertung dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung muss diese Schnittstelle implementieren.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Um diese Schnittstelle abzurufen, instanziieren Sie die ausdrucksauswertung über die `CoCreateInstance` Methode mit der Klasse-ID (CLSID) der Auswertung. Siehe das Beispiel.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExpressionEvaluator`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Auslesen](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konvertiert eine Ausdruckszeichenfolge auf eine analysierten Ausdrucks.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ruft die lokalen Variablen, Argumente und andere Eigenschaften einer Methode an.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konvertiert einen Methode Speicherort und einen Offset in eine Speicheradresse.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Bestimmt, welche Sprache zum Erstellen von druckbaren Ergebnisse.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Legt den Registrierungsstamm fest. Für das Debuggen von Seite-an-Seite verwendet.|  
  
## <a name="remarks"></a>Hinweise  
 Eine typische Situation instanziiert die Debugging-Modul (DE) die ausdrucksauswertung (EE) infolge eines Aufrufs für [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Da DE bekannt ist, die Sprache und den Hersteller der EE verwenden möchte, ruft die DE die EE CLSID aus der Registrierung (die [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) -Funktion, `GetEEMetric`, können mit diesen Abruf).  
  
 Nach der EE instanziiert wird, ruft die DE [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Analysieren des Ausdrucks und speichern Sie ihn in ein [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt. Später, einen Aufruf von [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) wertet den Ausdruck.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie die ausdrucksauswertung erhält ein Symbol-Anbieter und eine Adresse im Quellcode zu instanziieren. In diesem Beispiel verwendet die Funktion, `GetEEMetric`, aus der [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Library, dbgmetric.lib.  
  
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
            CLSID clsidEE      = { 0 };  
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
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)