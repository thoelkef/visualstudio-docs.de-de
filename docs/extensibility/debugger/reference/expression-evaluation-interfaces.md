---
title: Ausdruck Auswertung Schnittstellen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6a9d1d63b4fb15a920f175013af8a05cb38beb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-interfaces"></a>Ausdruck Auswertung Schnittstellen
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Im folgenden sind die Schnittstellen der Auswertung Ausdruck für die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging-SDK.  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden zum Auswerten von Ausdrücken in einer Aufrufliste im Unterbrechungsmodus. Sie sind nur für common Language Run-Time-ausdrucksauswertungen (EE) implementiert.  
  
 Jede Schnittstelle in der Tabelle wird die Komponente, die sie, in der folgenden Liste implementieren kann gezeigt:  
  
-   Debuggen des Datenbankmoduls (DE)  
  
-   Ausdrucksauswertung (EE)  
  
-   Visual Studio (VS)  
  
|Schnittstelle|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Stellt einen numerische Alias für eine Variable dar.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Stellt einen numerische Alias für eine Variable dar und ermöglicht eine ausdrucksauswertung (EE), um die Anwendungsdomäne für den Alias zu erhalten.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Stellt ein Arrayobjekt.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Stellt ein verwaltetes Array-Objekt dar und ermöglicht eine ausdrucksauswertung (EE), um zu bestimmen, den Basisindex (Untergrenze) für das Array.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Stellt einen Binder, bindet die Symbole, die eigentlichen Adressen im Arbeitsspeicher zu debuggen.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identisch mit der [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle bietet jedoch Zugriff auf Typen, Aliase und benutzerdefinierte Schnellansichten.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Stellt die Ausdrucksauswertung dar.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Stellt eine erweiterte Version des eine ausdrucksauswertung (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Stellt eine ausdrucksauswertung (EE) mit einer verbesserten Parser-Struktur dar.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Stellt eine Funktion dar.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Stellt eine Funktion dar und verbessert die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Ermöglicht eine ausdrucksauswertung (EE), um eine Meldung im Ausgabefenster des Debuggers anzuzeigen.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Stellt ein Objekt für verwalteten Code dar.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Basisschnittstelle, die alle Symbole darstellt, die an einer Speicheradresse gebunden werden.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identisch mit der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle bietet jedoch den Zugriff auf zusätzliche Informationen.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Stellt einen analysierten Ausdruck zur Auswertung bereiter.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Stellt einen Zeiger.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Stellt einen Zeiger in einen Analysestruktur und erweitert die **IDebugPointerObject** Schnittstelle.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bietet die Möglichkeit, einen Typ als Wert in einer Schnellansicht Typ zu ändern.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Bietet Zugriff auf den benutzerdefinierten Viewer und Typ-Schnellansichten.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bietet die Möglichkeit zum Erstellen einer [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Stellt eine Auflistung von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)