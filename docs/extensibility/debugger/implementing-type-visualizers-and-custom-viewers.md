---
title: Implementieren von Typ-Schnellansichten und benutzerdefinierten Viewer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19718425df6f0c8a656db0e3d7ebf0f06937f780
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementieren von Typ-Schnellansichten und benutzerdefinierten Viewer
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Typ-Schnellansichten und benutzerdefinierten Viewer können den Benutzer Daten eines bestimmten Typs in einer Weise anzeigen, die aussagekräftiger sind als ein Speicherabbild der einfache hexadezimalen Zahlen ist. Eine ausdrucksauswertung (EE) kann die benutzerdefinierten Viewer mit bestimmten Arten von Daten oder Variablen zuordnen. Diese benutzerdefinierte Viewer werden durch die EE implementiert. Die EE kann auch externen Typ-Schnellansichten unterstützen, die von einem anderen Drittanbieter oder sogar Endbenutzer stammen können.  
  
## <a name="discussion"></a>Diskussion  
  
### <a name="type-visualizers"></a>Typ-Schnellansichten  
 Visual Studio fordert eine Liste von Schnellansichten Typ und benutzerdefinierten Viewer für jedes Objekt in einem Überwachungsfenster angezeigt werden sollen. Eine ausdrucksauswertung (EE) stellt eine solche Liste für jeden Typ, für die sie die Typ-Schnellansichten und benutzerdefinierten Viewer unterstützen möchte. Aufrufe von [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) starten Sie den gesamten Prozess des Zugriffs auf die Typ-Schnellansichten und benutzerdefinierten Viewer (finden Sie unter [Visualizing und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)ausführliche Informationen über die Aufrufsequenz).  
  
### <a name="custom-viewers"></a>Benutzerdefinierte Viewer  
 Benutzerdefinierte Viewer werden in der EE für einen bestimmten Datentyp implementiert und durch dargestellt werden die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) Schnittstelle. Ein benutzerdefinierter Viewer ist nicht so flexibel wie eine Schnellansicht Typ, da er verfügbar ist, nur, wenn die EE, die dieser spezielle benutzerdefinierten Viewer ausgeführt wird. Implementieren eines benutzerdefinierten Viewers ist einfacher als das Implementieren der Unterstützung für die Typ-Schnellansichten. Allerdings gibt Typ-Schnellansichten unterstützen maximale Flexibilität erhalten Sie die Endbenutzer für seine Daten visualisieren. Die restlichen erläuterungen betrifft nur die Typ-Schnellansichten.  
  
## <a name="interfaces"></a>Schnittstellen  
 Die EE implementiert die folgenden Schnittstellen zur Unterstützung des Typ-Schnellansichten von Visual Studio verwendet wird:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 Die EE nutzt, um die Typ-Schnellansichten unterstützen die folgenden Schnittstellen:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)