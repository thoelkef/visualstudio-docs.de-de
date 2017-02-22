---
title: "Auswerten von Ausdr&#252;cken | Microsoft Docs"
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
  - "Ausdrücke [Debugging-SDK], auswerten"
  - "Debuggen die Auswertung von Ausdrücken [Debugging-SDK]"
  - "Ausdrucksauswertung"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Auswerten von Ausdr&#252;cken
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ausdrücke werden von Zeichenfolgen erstellt, die von den Automobilen, der die Überwachung, von der Schnellüberwachung oder den Direktfenstern übergeben werden.  Wenn ein Ausdruck ausgewertet wird, wird eine druckbare Zeichenfolge, die den Namen und die Variablenart oder Argument und sein Wert enthält.  Diese Zeichenfolge wird im richtigen IDE\-Fenster angezeigt.  
  
## Implementierung  
 Ausdrücke ausgewertet werden, wenn ein Programm bei einem Haltepunkt angehalten wurde.  Der Ausdruck selbst wird durch eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle dargestellt, die einen analysierten Ausdruck darstellt, der zum Binden und zur Auswertung innerhalb des angegebenen Ausdrucksauswertungs kontexts bereit ist.  Der Stapelrahmen bestimmt den Ausdrucksauswertungs, der das Debuggen des Moduls \(DE\) durch das Implementieren der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle.  
  
 Bei können eine Benutzerzeichenfolge und eine [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle, ein Modul \(Debug\) DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) erhalten eine Schnittstelle, indem sie die Benutzerzeichenfolge zur [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode übergeben.  Die Schnittstelle IDebugExpression2, die zurückgegeben wird, enthält den analysierten Ausdruck, der zur Auswertung bereit ist.  
  
 Mit der `IDebugExpression2`\-Schnittstelle kann DE den Wert des Ausdrucks durch synchrone oder asynchrone Ausdrucksauswertung unter Verwendung [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)abrufen.  Dieser Wert zusammen mit dem Namen und Typ der Variable oder eines Arguments wird an die IDE für die Anzeige gesendet.  Der Wert, der Name und Typ werden durch eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle dargestellt.  
  
 Um Ausdrucksauswertung zu aktivieren, muss der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) DE [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) und Schnittstellen implementieren.  Auswertung erfordern synchrone und asynchrone Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\-Methode.  
  
## Siehe auch  
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Ausdruckskontext\-Evaluierung](../../extensibility/debugger/expression-evaluation-context.md)   
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)