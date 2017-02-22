---
title: "Beispielimplementierung der Auswertung von Ausdr&#252;cken | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausdrucksauswertungen"
  - "Debuggen [Debugging-SDK] ausdrucksauswertungen"
  - "Auswertung von Ausdrücken, Beispiele"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Beispielimplementierung der Auswertung von Ausdr&#252;cken
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Für eine **Überwachen** Ausdruck, ruft Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erzeugen einer [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt.`IDebugExpressionContext2::ParseText` instanziiert eine Auswertung eines Ausdrucks \(EE\) und ruft [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Abrufen einer [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
 Diese Implementierung der `IDebugExpressionEvaluator::Parse` führt die folgenden Aufgaben:  
  
1.  \[Nur C\+\+\] Analysiert den Ausdruck auf Fehler überprüfen.  
  
2.  Instanziiert eine Klasse \(namens `CParsedExpression` in diesem Beispiel\), implementiert der `IDebugParsedExpression` Schnittstelle und speichert Sie in der Klasse den Ausdruck analysiert werden.  
  
3.  Gibt die `IDebugParsedExpression` \-Schnittstelle aus der `CParsedExpression` Objekt.  
  
> [!NOTE]
>  In den folgenden Beispielen und im Beispiel MyCEE trennt die Auswertung eines Ausdrucks nicht die Analyse bei der Auswertung.  
  
## Verwalteter Code  
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in verwaltetem Code. Beachten Sie, dass diese Version der Methode die Analyse verzögert auf [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) als auch der Code für die Analyse zur gleichen Zeit ausgewertet wird \(finden Sie unter [Evaluieren einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## Nicht verwalteter Code  
 Dies ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in nicht verwaltetem Code. Diese Methode ruft eine Hilfsfunktion `Parse`, um den Ausdruck und die Überprüfung auf Fehler analysiert, aber diese Methode den resultierenden Wert ignoriert. Die formale Bewertung wird verzögert [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) in dem der Ausdruck analysiert wird, während der Auswertung \(siehe [Evaluieren einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## Siehe auch  
 [Evaluieren einen Überwachungsausdruck\-Fenster](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Evaluieren einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)