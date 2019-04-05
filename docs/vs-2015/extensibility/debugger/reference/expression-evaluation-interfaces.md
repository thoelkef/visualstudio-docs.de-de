---
title: Schnittstellen für die Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9988e28482f1ed1174658cc9e016fa0eb2f153b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955785"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Im folgenden sind die Schnittstellen für die Ausdrucksauswertung für die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugging-SDK.  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden zum Auswerten von Ausdrücken in einer Aufrufliste während des Unterbrechungsmodus verwendet. Sie sind nur für die common Language Run-Time-ausdrucksauswertungen (EE) implementiert.  
  
 Jede Schnittstelle in der Tabelle zeigt die Komponente, die sie in der folgenden Liste implementieren kann:  
  
-   Debug-Engine (DE)  
  
-   Ausdrucksauswertung (EE)  
  
-   Visual Studio (VS)  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Stellt einen numerischen Alias für eine Variable dar.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Stellt einen numerischen Alias für eine Variable dar und ermöglicht eine ausdrucksauswertung (EE), um die Anwendungsdomäne für den Alias zu erhalten.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Stellt ein Arrayobjekt dar.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Stellt ein verwaltetes Array-Objekt dar und ermöglicht eine ausdrucksauswertung (EE), um zu bestimmen, den Basisindex (untere Grenzen) für das Array.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Stellt einen Binder, bindet die Symbole, die eigentlichen Adressen im Arbeitsspeicher zu debuggen.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identisch mit der [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle ermöglicht jedoch den Zugriff auf Typen, Aliase und benutzerdefinierte Schnellansichten.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Stellt die Ausdrucksauswertung dar.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Stellt eine erweiterte Version eines ausdrucksauswerters (EE) dar.|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Stellt eine ausdrucksauswertung (EE) mit einer erweiterten Parser-Struktur dar.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Stellt eine Funktion dar.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Stellt eine Funktion dar, und verbessert die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Ermöglicht eine ausdrucksauswertung (EE), um eine Meldung im Ausgabefenster des Debuggers anzuzeigen.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Ein Objekt von verwaltetem Code darstellt.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Basisschnittstelle, die alle Symbole darstellt, die an einer Speicheradresse gebunden werden.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identisch mit der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle bietet jedoch Zugriff auf zusätzliche Informationen.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Stellt einen analysierten Ausdruck zur Auswertung bereiter dar.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Stellt einen Zeiger.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Stellt einen Zeiger in eine Analysestruktur und erweitert die **IDebugPointerObject** Schnittstelle.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bietet die Möglichkeit, eines Typs Wert über eine typschnellansicht zu ändern.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Bietet Zugriff auf den benutzerdefinierten Viewer und Typ-Schnellansichten.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bietet die Möglichkeit zum Erstellen einer [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Stellt eine Auflistung von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
