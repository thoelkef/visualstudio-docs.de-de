---
title: Implementieren von Typvisualisierern und benutzerdefinierten Viewern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738507"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementieren von Typvisualisierern und benutzerdefinierten Viewern
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Mithilfe von Typvisualisierungen und benutzerdefinierten Viewern können Benutzer Daten eines bestimmten Typs auf eine Sinnvollkeit anzeigen als ein einfaches hexadezimales Dump von Zahlen. Ein Ausdrucksauswertungswerter (EE) kann benutzerdefinierte Betrachter bestimmten Datentypen oder Variablen zuordnen. Diese benutzerdefinierten Viewer werden von der EE implementiert. Der EE kann auch externe Typ-Visualisierungen unterstützen, die von einem anderen Drittanbieter oder sogar vom Endbenutzer stammen können.

## <a name="discussion"></a>Diskussion

### <a name="type-visualizers"></a>Typ-Visualisierungen
 Visual Studio fragt nach einer Liste von Typvisualisierungen und benutzerdefinierten Viewern für jedes Objekt, das in einem Überwachungsfenster angezeigt werden soll. Ein Ausdrucksauswertungswerter (EE) stellt eine solche Liste für jeden Typ bereit, für den er Typvisualisierungen und benutzerdefinierte Viewer unterstützen möchte. Aufrufe von [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) starten den gesamten Prozess des Zugriffs auf Typvisualisierungs- und benutzerdefinierte Viewer (Details zur aufrufenden Sequenz finden Sie unter [Visualisieren und Anzeigen von Daten).](../../extensibility/debugger/visualizing-and-viewing-data.md)

### <a name="custom-viewers"></a>Benutzerdefinierte Zuschauer
 Benutzerdefinierte Viewer werden im EE für einen bestimmten Datentyp implementiert und durch die [IDebugCustomViewer-Schnittstelle](../../extensibility/debugger/reference/idebugcustomviewer.md) dargestellt. Ein benutzerdefinierter Viewer ist nicht so flexibel wie ein Typvisualizer, da er nur verfügbar ist, wenn der EE, der diesen bestimmten benutzerdefinierten Viewer implementiert, ausgeführt wird. Das Implementieren eines benutzerdefinierten Viewers ist einfacher als die Implementierung von Unterstützung für Typvisualisierer. Die Unterstützung von Typvisualisierern bietet dem Endbenutzer jedoch maximale Flexibilität bei der Visualisierung seiner Daten. Der Rest dieser Diskussion betrifft nur Typvisualisierer.

## <a name="interfaces"></a>Schnittstellen
 Der EE implementiert die folgenden Schnittstellen zur Unterstützung von Typvisualisierern, die von Visual Studio verwendet werden:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  Der EE verwendet die folgenden Schnittstellen, um Typvisualizer zu unterstützen:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
