---
title: "Ausdrucksauswertung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausdrücke [SDK-Debuggen]"
  - "Debuggen die Auswertung von Ausdrücken [Debugging-SDK]"
  - "Ausdrucksauswertung"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ausdrucksauswertung \(EE\) überprüfen Sie die Syntax einer Programmiersprache, um Variablen und Ausdrücke analysieren und zur Laufzeit ausgewertet und vom Benutzer ermöglichen, die angezeigt werden soll, wenn die IDE im Unterbrechungsmodus befindet.  
  
## Verwenden der Ausdrucksauswertung  
 Ausdrücke werden mithilfe der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode erstellt wie folgt:  
  
1.  Das Debugmodul \(DE\) implementiert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle.  
  
2.  Das Debuggen in ein Paket `IDebugExpressionContext2`\-Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)\-Schnittstelle ab und ruft dann die `IDebugStackFrame2::ParseText`\-Methode dafür aufrufen, um ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Objekt abzurufen.  
  
3.  Das Debuggen von Paket ruft die [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)\-Methode oder die [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)\-Methode auf, um den Wert des Ausdrucks abzurufen.  `IDebugExpression2::EvaluateAsync` wird vom Befehl\/vom Direktfenster aufgerufen.  Weitere Benutzeroberfläche\-Komponenten gesamte Aufruf `IDebugExpression2::EvaluateSync`.  
  
4.  Das Ergebnis der Ausdrucksauswertung ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt, das den Namen, den Typ und den Wert des Ergebnisses der Ausdrucksauswertung enthält.  
  
 Während der Ausdrucksauswertung fordert die EE Anbieter Symbol Informationen aus der Komponente.  Das Symbol für stellt das die symbolischen Informationen zum Identifizieren und das Verständnis des analysierten Ausdruck frei.  
  
 Wenn die asynchrone Ausdrucksauswertung abgeschlossen ist, wird ein asynchrones Ereignis durch DE Debuggen durch den Manager der Sitzung \(SDM\) gesendet, damit die IDE zu benachrichtigen, dass Ausdrucksauswertung abgeschlossen ist.  Bei synchronen Ausdrucksauswertung abgeschlossen ist, wird das Ergebnis der Auswertung `IDebugExpression2::EvaluateSync` vom Aufruf der Methode zurückgegeben.  
  
## Implementierungs\-Hinweise  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule zu erwarten, mit dem der Ausdrucksauswertung zu verweisen, mit Schnittstellen der Common Language Runtime \(CLR\).  Daher muss der Ausdrucksauswertung, der den Debug\- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Modulen kann die CLR unterstützen \(eine vollständige Liste aller CLR\-Debugschnittstellen kann in debugref.doc gefunden werden, das Teil [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]ist\).  
  
## Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)