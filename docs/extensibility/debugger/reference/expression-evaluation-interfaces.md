---
title: "Ausdruck Evaluation-Schnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Auswertung von Ausdrücken, Schnittstellen"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ausdruck Evaluation-Schnittstellen
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Im folgenden sind die Ausdruck\-Bewertung\-Schnittstellen für die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging\-SDK.  
  
## Diskussion  
 Diese Schnittstellen werden zum Auswerten von Ausdrücken in einer Aufrufliste während des Unterbrechungsmodus verwendet. Sie sind nur für common Language Runtime\-Ausdruck Bewerter \(EE\) implementiert.  
  
 Jede Schnittstelle in der Tabelle wird die Komponente, die sie, aus der folgenden Liste implementieren kann gezeigt:  
  
-   Debug\-Modul \(DE\)  
  
-   Expression Evaluator \(EE\)  
  
-   Visual Studio \(VS\)  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|-------------------|-------------------------|------------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Stellt einen numerischen Alias für eine Variable dar.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Stellt einen numerischen Alias für eine Variable dar und ermöglicht eine Auswertung eines Ausdrucks \(EE\), um die Anwendungsdomäne für den Alias zu erhalten.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Stellt ein Arrayobjekt.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Stellt ein verwaltetes Array\-Objekt dar und ermöglicht eine Auswertung eines Ausdrucks \(EE\), um den Basisindex \(Untergrenze\) für das Array zu bestimmen.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Stellt einen Binder, bindet die Symbole verwenden, um die eigentlichen Adressen im Arbeitsspeicher Debuggen.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identisch mit der [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) \-Schnittstelle bietet jedoch Zugriff auf Typen, Aliase und benutzerdefinierte Schnellansichten.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Stellt die ausdrucksauswertung dar.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Stellt eine erweiterte Version einer Auswertung eines Ausdrucks \(EE\) dar.|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Stellt eine ausdrucksauswertung \(EE\) mit einer verbesserten Parser\-Struktur dar.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Stellt eine Funktion dar.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Stellt eine Funktion dar und verbessert die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Ermöglicht eine Auswertung eines Ausdrucks \(EE\) eine Meldung im Ausgabefenster des Debuggers angezeigt.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Stellt eine verwaltete Codeobjekt dar.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Basisschnittstelle, die alle Symbole darstellt, die an einer Speicheradresse gebunden werden.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identisch mit der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) \-Schnittstelle bietet jedoch Zugriff auf Weitere Informationen.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Stellt einen analysierten Ausdruck ausgewertet werden kann.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Stellt einen Zeiger.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Stellt einen Zeiger in eine Analysestruktur und erweitert die **IDebugPointerObject** Schnittstelle.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bietet die Möglichkeit zum Ändern des Typs Werts mithilfe einer Schnellansicht Typ.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VISUAL STUDIO|Bietet Zugriff auf den benutzerdefinierten Viewer und Typ Schnellansichten.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VISUAL STUDIO|Bietet die Möglichkeit zum Erstellen einer [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Stellt eine Auflistung von[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekten dar.|  
  
## Siehe auch  
 [API\-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)