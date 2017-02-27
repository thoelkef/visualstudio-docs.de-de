---
title: "IDebugExpressionEvaluator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator-Schnittstelle"
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt die Auswertung eines Ausdrucks.  
  
## Syntax  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks muss diese Schnittstelle implementieren.  
  
## Hinweise für Aufrufer  
 Um diese Schnittstelle zu erhalten, instanziieren Sie die Auswertung eines Ausdrucks durch die `CoCreateInstance` Methode, indem Sie mithilfe der Klassen\-ID \(CLSID\), der die Auswertung. Siehe das Beispiel.  
  
## Methoden in Vtable\-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExpressionEvaluator`.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konvertiert eine Ausdruckszeichenfolge zu einer analysierten Ausdrucks.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ruft die lokalen Variablen, Argumenten und andere Eigenschaften einer Methode.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konvertiert einen Methode Speicherort und einen Offset in eine Speicheradresse.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Bestimmt, welche Sprache zum Erstellen von druckbaren Ergebnisse.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Legt den Registrierungsstamm. Zum Debuggen von Seite\-an\-Seite verwendet.|  
  
## Hinweise  
 Erziehungsberechtigte, instanziiert die Debugging\-Modul \(DE\) der Auswertung eines Ausdrucks \(EE\) aufgrund eines Aufrufs von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Da die DE kennt die Sprache und den Hersteller der EE verwenden möchte, ruft die DE die EE CLSID aus der Registrierung \(die [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) \-Funktion, `GetEEMetric`, hilft bei diesen Abruf\).  
  
 Nachdem die EE instanziiert wurde, ruft die DE [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Analysieren des Ausdrucks, und speichern Sie sie in ein [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt. Später, einen Aufruf von [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) wird der Ausdruck ausgewertet.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die Auswertung eines Ausdrucks erhält ein Symbol\-Anbieter und eine Adresse im Quellcode zu instanziieren. Dieses Beispiel verwendet die Funktion, `GetEEMetric`, aus der [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Library, dbgmetric.lib.  
  
```cpp#  
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
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)