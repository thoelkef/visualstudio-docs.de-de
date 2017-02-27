---
title: "Strategie f&#252;r die Implementierung von Expression Evaluator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Auswertung von Ausdrücken, Implementierungsstrategie"
  - "Debugmodule, Implementierungsstrategien"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Strategie f&#252;r die Implementierung von Expression Evaluator
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ein Ansatz zum Erstellen schnell eine Auswertung eines Ausdrucks \(EE\) ist, implementieren Sie zunächst den mindestens erforderlichen Code für Anzeigen lokaler Variablen in der **Lokal** Fenster. Ist es sinnvoll, erkennen, dass jede Zeile in der **Lokal** Fenster zeigt den Namen, Typ und Wert einer lokalen Variablen, und alle drei dargestellte ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt. Der Name, Typ und Wert einer lokalen Variablen erhalten ein `IDebugProperty2` \-Objekt durch Aufrufen seiner [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Weitere Informationen zur Vorgehensweise beim Anzeigen von lokaler Variablen in der **Lokal** Fenster finden Sie unter [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md).  
  
## Diskussion  
 Eine mögliche Implementierung Sequenz beginnt bei der Implementierung von [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) und [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methoden müssen implementiert werden, um lokale Variablen anzuzeigen. Aufrufen von `IDebugExpressionEvaluator::GetMethodProperty` Gibt ein `IDebugProperty2` \-Objekt, das eine Methode darstellt:, also ein [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Objekt. Methoden selbst werden nicht angezeigt, der **Lokal** Fenster.  
  
 Die [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) \-Methode als Nächstes implementiert werden sollte. Das Debugging\-Modul \(DE\) ruft diese Methode zum Abrufen von einer Liste von lokalen Variablen und Argumenten übergeben `IDebugProperty2::EnumChildren` ein `guidFilter` Argument der `guidFilterLocalsPlusArgs`.`IDebugProperty2::EnumChildren` Ruft [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), kombinieren die Ergebnisse in einer einzelnen Enumeration. Ausführliche Informationen finden Sie unter [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md).  
  
## Siehe auch  
 [Implementieren eine Auswertung eines Ausdrucks](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)