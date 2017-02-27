---
title: "Auswertung des Ausdrucks (Visual Studio Debugging-SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen die Auswertung von Ausdrücken [Debugging-SDK]"
  - "Ausdrucksauswertung"
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Auswertung des Ausdrucks (Visual Studio Debugging-SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Während des Unterbrechungsmodus muss die IDE in der Lage sein, die einfachen Ausdrücke auswerten, die mehrere Variablen des Programms.  Um dies zu erreichen, muss das Debugmodul \(DE\) in der Lage sein, einen Ausdruck auszuwerten und zu analysieren, der in eines der Fenster der IDE eingegeben wird.  
  
 Ausdrücke werden mithilfe der [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode erstellt und werden durch die resultierende [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle dargestellt.  
  
 Die **IDebugExpression2**\-Schnittstelle wird von DE implementiert, und zeigt dessen **EvalAsync**\-Methode aufruft, um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle zur IDE zurück, um die Ergebnisse der Ausdrucksauswertung in der IDE angezeigt.  [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine Struktur zurück, das verwendet werden kann, um auf den Wert eines Ausdrucks in einem Überwachungsfenster oder das Fenster Lokal zu setzen.  
  
 Die Aufrufe Debuggen auf Debuggen [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) des Managers des Pakets oder der Sitzung \(SDM\), um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle abzurufen, die das Ergebnis der Auswertung darstellt.  `IDebugProperty2` verfügt über Methoden, die den Namen, den Typ und den Wert des Ausdrucks zurückgeben.  Diese Informationen werden in verschiedenen Debuggerfenstern angezeigt.  
  
## Verwenden der Ausdrucksauswertung  
 Um Ausdrucksauswertung zu verwenden, müssen Sie die [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode und alle Methoden der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle, wie in der folgenden Tabelle gezeigt implementieren.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron aus.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucksauswertung.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron aus.|  
  
 Synchrone und asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\-Methode.  Asynchrone Ausdrucksauswertung benötigt die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## Siehe auch  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)