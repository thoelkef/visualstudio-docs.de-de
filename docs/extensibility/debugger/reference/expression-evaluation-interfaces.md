---
title: Ausdrucksauswertungsschnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736941"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Im Folgenden finden Sie die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Expression Evaluation Interfaces für das Debugging SDK.

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden verwendet, um Ausdrücke in einer Aufrufliste während des Unterbrechungsmodus auszuwerten. Sie werden nur für Common Language-Laufzeitausdrucksevaluatoren (EE) implementiert.

 Jede Schnittstelle in der Tabelle zeigt die Komponente, die sie implementieren kann, aus der folgenden Liste:

- Debug-Engine (DE)

- Ausdrucksauswertung (EE)

- Visual Studio (VS)

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Stellt einen numerischen Alias für eine Variable dar.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Stellt einen numerischen Alias für eine Variable dar und ermöglicht einem Ausdrucksevaluator (EE) das Abrufen der Anwendungsdomäne für den Alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Stellt ein Arrayobjekt dar.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Stellt ein verwaltetes Arrayobjekt dar und ermöglicht es einem Ausdrucksevaluator (EE), den Basisindex (untere Grenzen) für das Array zu bestimmen.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Stellt einen Bindemittel dar, der Debugsymbole an tatsächliche Adressen im Arbeitsspeicher bindet.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Wie die [IDebugBinder-Schnittstelle,](../../../extensibility/debugger/reference/idebugbinder.md) bietet jedoch Zugriff auf Typen, Aliase und benutzerdefinierte Visualisierungen.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Stellt die Ausdrucksauswertung dar.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Stellt eine erweiterte Version eines Ausdrucksevaluators (EE) dar.|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Stellt einen Ausdrucksevaluator (EE) mit einer erweiterten Parserstruktur dar.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Stellt eine Funktion dar.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Stellt eine Funktion dar und erweitert die [IDebugFunctionObject-Schnittstelle.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Ermöglicht einem Ausdrucksevaluator (EE), eine Meldung im Ausgabefenster des Debuggers anzuzeigen.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Stellt ein verwaltetes Codeobjekt dar.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Basisschnittstelle, die ein beliebiges Symbol darstellt, das an eine Speicheradresse gebunden ist.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Genauso wie die [IDebugObject-Schnittstelle,](../../../extensibility/debugger/reference/idebugobject.md) bietet jedoch Zugriff auf zusätzliche Informationen.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Stellt einen analysierten Ausdruck dar, der ausgewertet werden kann.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Stellt einen Zeiger dar.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Stellt einen Zeiger in einer Analysestruktur dar und erweitert die **IDebugPointerObject-Schnittstelle.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bietet die Möglichkeit, den Wert eines Typs über eine Typvisualisierung zu ändern.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Bietet Zugriff auf benutzerdefinierte Viewer und Typvisualisierer.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bietet die Möglichkeit, ein [IEEVisualizerService-Objekt](../../../extensibility/debugger/reference/ieevisualizerservice.md) zu erstellen.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Stellt eine Auflistung von [IDebugObject-Objekten](../../../extensibility/debugger/reference/idebugobject.md) dar.|

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Schreiben einer CLR-Ausdrucksauswertung](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
