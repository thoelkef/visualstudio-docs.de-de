---
title: "Implementieren eine Auswertung eines Ausdrucks | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausdrucksauswertungen"
  - "Debuggen [Debugging-SDK] ausdrucksauswertungen"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Implementieren eine Auswertung eines Ausdrucks
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die Auswertung eines Ausdrucks ist ein komplexes Zusammenspiel zwischen dem Debugging\-Modul \(DE\), den Symbol\-Anbieter \(SP\), der Binder\-Objekt und der Auswertung eines Ausdrucks \(EE\) selbst. Diese vier Komponenten werden durch Schnittstellen verbunden, die von einer Komponente implementiert und von einem anderen genutzt werden.  
  
 Die EE nimmt einen Ausdruck aus der DE in Form einer Zeichenfolge analysiert und wertet ihn. Die EE implementiert die folgenden Schnittstellen, die von der DE genutzt werden:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 Die EE ruft der binderobjekt, das vom DE, um den Wert von Symbolen und Objekten abzurufen. Die EE nutzt die folgenden Schnittstellen, die durch die DE implementiert werden:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementiert die EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md).`IDebugProperty2` Stellt den Mechanismus zum Beschreiben des Ergebnis der Auswertung eines Ausdrucks, z. B. eine lokale Variable, ein primitiver Typ oder ein Objekt, um Visual Studio zeigt dann die entsprechende Informationen in der **Lokal**, **Überwachen**, oder **sofort** Fenster.  
  
 Der SP wird auf die EE durch die DE zugewiesen, wenn nach Informationen gefragt wird. Der SP implementiert Schnittstellen, die Adressen und Felder, z. B. die folgenden Schnittstellen und ihre Derivate beschreiben:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 Die EE nutzt alle diese Schnittstellen.  
  
## In diesem Abschnitt  
 [Strategie für die Implementierung von Expression Evaluator](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiert einen dreistufigen Prozess für die Implementierungsstrategie für Expression Evaluator \(EE\).  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)