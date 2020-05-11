---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717944"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle implementiert wichtige Methoden, die Funktionen für die [Schnittstellen IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) bereitstellen.

## <a name="syntax"></a>Syntax

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um einem Ausdrucksevaluator (EE) die Unterstützung von Typvisualisierungen zu ermöglichen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Der EE ruft [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) auf, um diese Schnittstelle als Teil seiner Unterstützung für Typvisualisierer zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Ruft die Anzahl der benutzerdefinierten Viewer ab, über die dieser Dienst Bescheid weiß.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Ruft die Liste der benutzerdefinierten Viewer ab.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Gibt ein Proxyobjekt für eine Eigenschaft zurück.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Ruft die Anzahl der Wertzeichenfolgen ab, die für die angegebene Eigenschaft oder das angegebene Feld angezeigt werden sollen.|

## <a name="remarks"></a>Bemerkungen
 Die IDE verwendet die [IDebugProperty3-Schnittstelle,](../../../extensibility/debugger/reference/idebugproperty3.md) um zu bestimmen, ob benutzerdefinierte Viewer oder Typvisualisierer für die Eigenschaft vorhanden sind. Durch das Erstellen eines Visualizer-Service (mit [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) `IDebugProperty3` kann der EE die Funktionalität für die und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (die das Anzeigen und Ändern des Werts einer Eigenschaft unterstützt) bereitstellen und dadurch Typvisualisierungen unterstützen.

 Wenn ein EE über benutzerdefinierte Viewer verfügt, die `CLSID`selbst implementiert werden, kann der EE die s dieser benutzerdefinierten Viewer an das Ende der von [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)zurückgegebenen Liste anhängen. Dadurch kann ein EE sowohl Typvisualisierer als auch eigene benutzerdefinierte Viewer unterstützen. Stellen Sie sicher, dass [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) die Hinzufügung von benutzerdefinierten Viewern widerspiegelt.

 Eine Erläuterung des Unterschieds zwischen Visualisierern und Betrachtern finden Sie unter [Typvisualisierung und benutzerdefinierter Viewer.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
