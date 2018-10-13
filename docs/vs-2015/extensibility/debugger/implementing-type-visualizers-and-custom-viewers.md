---
title: Implementieren von Typschnellansichten und benutzerdefinierten Viewern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6df678c3688008b3367d53046d6ab54ce5279dbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251991"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementieren von Typschnellansichten und benutzerdefinierten Viewern
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Typschnellansichten und benutzerdefinierten Viewer können den Benutzer Daten eines bestimmten Typs in einer Weise anzeigen, die aussagekräftiger sind als ein Speicherabbild der einfachen hexadezimale Zahlen ist. Eine ausdrucksauswertung (EE) kann benutzerdefinierten Viewer bestimmte Typen von Daten oder Variablen zuordnen. Diese benutzerdefinierte Viewer werden durch die EE implementiert. Die EE kann auch externen Typ-Schnellansichten unterstützen, die von einem anderen Drittanbieter oder sogar der Endbenutzer stammen können.  
  
## <a name="discussion"></a>Diskussion  
  
### <a name="type-visualizers"></a>Typ-Schnellansichten  
 Visual Studio fordert eine Liste von typschnellansichten und benutzerdefinierten Viewer für jedes Objekt in einem Fenster "überwachen" angezeigt werden sollen. Eine ausdrucksauswertung (EE) bietet eine solche Liste für jeden Typ, der für die es typschnellansichten und benutzerdefinierten Viewern unterstützen möchte. Aufrufe von [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) starten Sie den gesamten Prozess für den Zugriff auf typschnellansichten und benutzerdefinierten Viewern (finden Sie unter [visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)ausführliche Informationen über die Aufrufsequenz).  
  
### <a name="custom-viewers"></a>Benutzerdefinierten Viewern  
 Benutzerdefinierte Viewer werden in der EE für einen bestimmten Datentyp implementiert und durch dargestellt die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) Schnittstelle. Ein benutzerdefinierter Viewer ist nicht so flexibel wie eine typschnellansicht, da es verfügbar ist, nur, wenn Sie die EE, die diese spezielle benutzerdefinierten Viewer implementiert ausgeführt wird. Implementieren einen benutzerdefinierten Viewer ist einfacher als die Implementierung der Unterstützung für Typ-Schnellansichten. Allerdings bietet Unterstützung von typschnellansichten maximalen Flexibilität für den Endbenutzer zum Visualisieren ihrer Daten. Die restlichen erläuterungen betrifft nur die Typ-Schnellansichten.  
  
## <a name="interfaces"></a>Schnittstellen  
 Die EE implementiert die folgenden Schnittstellen zur Unterstützung von typschnellansichten, von Visual Studio verwendet wird:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 Die EE verwendet, um Typ-Schnellansichten unterstützen die folgenden Schnittstellen:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

