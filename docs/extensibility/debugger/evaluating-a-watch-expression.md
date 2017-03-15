---
title: "Evaluieren einen &#220;berwachungsausdruck | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Auswertung von Ausdrücken, Überwachungsausdrücke"
  - "Ansehen von Ausdrücken"
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Evaluieren einen &#220;berwachungsausdruck
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn Visual Studio bereit, um den Wert eines Ausdrucks überwachen anzuzeigen ist, ruft er [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wiederum aufruft [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Dies erzeugt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) \-Objekt, das den Wert und Typ des Ausdrucks enthält.  
  
 In dieser Implementierung der `IDebugParsedExpression::EvaluateSync`, der Ausdruck analysiert und gleichzeitig ausgewertet. Diese Implementierung führt die folgenden Aufgaben:  
  
1.  Analysiert und wertet den Ausdruck aus, um ein generisches Objekt zu erstellen, das den Wert und den Typ enthält. In c\# wird dies als ein `object` und in C\+\+ dies als dargestellt eine `VARIANT`.  
  
2.  Instanziiert eine Klasse \(namens `CValueProperty` in diesem Beispiel\), implementiert der `IDebugProperty2` Schnittstelle und speichert Sie in der Klasse den Wert zurückgegeben werden.  
  
3.  Gibt die `IDebugProperty2` \-Schnittstelle aus der `CValueProperty` Objekt.  
  
## Verwalteter Code  
 Dies ist eine Implementierung der `IDebugParsedExpression::EvaluateSync` in verwaltetem Code. Die Hilfsmethode `Tokenize` analysiert den Ausdruck in eine Analysestruktur. Die Hilfsfunktion `EvalToken` das Token in einen\-Wert konvertiert. Die Hilfsfunktion `FindTerm` rekursiv durchsucht die Analysestruktur Aufrufen `EvalToken` für jeden Knoten, die einen Wert darstellt, und alle Operationen \(Addition oder Multiplikation\) im Ausdruck angewendet.  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT EvaluateSync( uint evalFlags, uint timeout, IDebugSymbolProvider provider, IDebugAddress address, IDebugBinder binder, string resultType, out IDebugProperty2 result) { HRESULT retval = COM.S_OK; this.evalFlags = evalFlags; this.timeout = timeout; this.provider = provider; this.address = address; this.binder = binder; this.resultType = resultType; try { IDebugField field = null; // Tokenize, then parse. tokens = Tokenize(expression); result = new CValueProperty( expression, (int) FindTerm(EvalToken(tokens[0], out field),1), field, binder); } catch (ParseException) { result = new CValueProperty(expression, "Huh?"); retval = COM.E_INVALIDARG; } return retval; } } }  
```  
  
## Nicht verwalteter Code  
 Dies ist eine Implementierung der `IDebugParsedExpression::EvaluateSync` in nicht verwaltetem Code. Die Hilfsfunktion `Evaluate` analysiert und wertet den Ausdruck Zurückgeben einer `VARIANT` halten den resultierenden Wert. Die Hilfsfunktion `VariantValueToProperty` Pakete der `VARIANT` in einem `CValueProperty` Objekt.  
  
```  
[C++] STDMETHODIMP CParsedExpression::EvaluateSync( in  DWORD                 evalFlags, in  DWORD                 dwTimeout, in  IDebugSymbolProvider* pprovider, in  IDebugAddress*        paddress, in  IDebugBinder*         pbinder, in  BSTR                  bstrResultType, out IDebugProperty2**     ppproperty ) { // dwTimeout parameter is ignored in this implementation. if (pprovider == NULL) return E_INVALIDARG; if (paddress == NULL) return E_INVALIDARG; if (pbinder == NULL) return E_INVALIDARG; if (ppproperty == NULL) return E_INVALIDARG; else *ppproperty = 0; HRESULT hr; VARIANT value; BSTR    bstrErrorMessage = NULL; hr = ::Evaluate( pprovider, paddress, pbinder, m_expr, &bstrErrorMessage, &value ); if (hr != S_OK) { if (bstrErrorMessage == NULL) return hr; //we can display better messages ourselves. HRESULT hrLocal = S_OK; VARIANT varType; VARIANT varErrorMessage; VariantInit( &varType ); VariantInit( &varErrorMessage ); varErrorMessage.vt      = VT_BSTR; varErrorMessage.bstrVal = bstrErrorMessage; CValueProperty* valueProperty = new CValueProperty(); if (valueProperty != NULL) { hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage); if (SUCCEEDED(hrLocal)) { hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2, reinterpret_cast<void**>(ppproperty) ); } } VariantClear(&varType); VariantClear(&varErrorMessage); //frees BSTR if (!valueProperty) return hr; valueProperty->Release(); if (FAILED(hrLocal)) return hr; } else { if (bstrErrorMessage != NULL) SysFreeString(bstrErrorMessage); hr = VariantValueToProperty( pprovider, paddress, pbinder, m_radix, m_expr, value, ppproperty ); VariantClear(&value); if (FAILED(hr)) return hr; } return S_OK; }  
```  
  
## Siehe auch  
 [Evaluieren einen Überwachungsausdruck\-Fenster](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Beispielimplementierung der Auswertung von Ausdrücken](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)