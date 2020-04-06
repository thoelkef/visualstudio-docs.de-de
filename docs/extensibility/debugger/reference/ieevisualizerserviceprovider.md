---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717884"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle ermöglicht den Zugriff auf eine Methode, die einen Visualisierungsdienst erstellen kann, der zum Behandeln von Typvisualisierungsaufgaben für die IDE verwendet wird.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um ein Visualizer-Dienstobjekt zu erstellen,`CLSID`das wiederum verwendet wird, um Klassen-IDs (s) von Typvisualisierern an die Visual Studio-IDE zu liefern.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Der Ausdrucksevaluator (EE) ruft [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) auf, um diese Schnittstelle abzuerhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Erstellt den Visualisierungsdienst|

## <a name="remarks"></a>Bemerkungen
 Die `IEEVisualizerServiceProvider` Schnittstelle wird während der Implementierung von [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)erhalten. Der Visualisierungsdienst, den diese Schnittstelle erstellt, wird verwendet, um einer [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) Funktionalität bereitzustellen, für deren Implementierung der EE verantwortlich ist. Der EE ist auch für die Implementierung einer [IEEVisualizerDataProvider-Schnittstelle](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) verantwortlich, mit der Typvisualisierer den Wert einer Eigenschaft anzeigen und ändern können.

 Weitere Informationen zur Interaktion dieser Schnittstellen finden Sie unter [Visualisieren und Anzeigen von Daten.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
