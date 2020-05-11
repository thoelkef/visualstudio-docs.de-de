---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718052"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet die Möglichkeit, den Wert eines Objekts durch eine Typvisualisierung zu ändern.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksauswertungswert implementiert diese Schnittstelle, um das Ändern von Daten für ein Eigenschaftsobjekt über eine Typvisualisierung zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird beim Erstellen des [IEEVisualizerService-Objekts](../../../extensibility/debugger/reference/ieevisualizerservice.md) über einen Aufruf von [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)verwendet. Weitere Informationen finden Sie [unter Visualisieren und Anzeigen von Daten.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bestimmt, ob es möglich ist, das Objekt (und anschließend seinen Wert) zu aktualisieren, das von dieser Visualisierung dargestellt wird.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Erzwingt eine Neubewertung des Objekts für diese Visualisierung.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ruft ein vorhandenes Objekt für diese Visualisierung ab (es wird keine Auswertung durchgeführt).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualisiert das Objekt für diese Visualisierung, wodurch der Wert der Visualisierung geändert wird.|

## <a name="remarks"></a>Bemerkungen
 Der Visualisierungsdienst (wie von der [IEEVisualizerService-Schnittstelle](../../../extensibility/debugger/reference/ieevisualizerservice.md) dargestellt und von [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)zurückgegeben) enthält einen Verweis auf das Objekt, das die `IEEVisualizerDataProvider` Schnittstelle implementiert. Daher sollte die `IEEVisualizerDataProvider` Schnittstelle nicht für dasselbe Objekt implementiert werden, das die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, wenn dieses Objekt einen Verweis auf das `IEEVisualizerService` Objekt beibehält: Ein Zirkelverweis resultiert und ein Deadlock tritt auf, wenn die Objekte zerstört werden. Der empfohlene Ansatz `IEEVisualizerDataProvider` besteht darin, für `IDebugProperty2` ein separates `IUnknown::AddRef` Objekt zu implementieren, an das das Objekt delegiert, ohne es aufzurufen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
