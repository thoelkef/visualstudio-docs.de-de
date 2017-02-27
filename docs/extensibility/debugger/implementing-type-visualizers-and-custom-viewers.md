---
title: "Implementieren von Typ Schnellansichten und benutzerdefinierten Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen von benutzerdefinierten Viewer [Debugging-SDK]"
  - "[Debuggen SDK] Typ Schnellansicht Debuggen"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Implementieren von Typ Schnellansichten und benutzerdefinierten Viewer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Typ Schnellansichten und benutzerdefinierten Viewer können Benutzern das Anzeigen von Daten eines bestimmten Typs auf eine Weise, die aussagekräftiger sind als eine einfache hexadezimale Abbilddatei Zahlen ist. Eine Auswertung eines Ausdrucks \(EE\) kann benutzerdefinierte Viewer mit bestimmten Arten von Daten oder Variablen zuordnen. Diese benutzerdefinierte Viewer werden von der EE implementiert. Die EE kann auch externen Typ\-Schnellansichten unterstützen, die von einem anderen Drittanbieter oder sogar Endbenutzer stammen kann.  
  
## Diskussion  
  
### Typ Schnellansichten  
 Visual Studio fordert eine Liste von Schnellansichten Typ und benutzerdefinierten Viewer für jedes Objekt in einem Überwachungsfenster angezeigt werden. Eine Auswertung eines Ausdrucks \(EE\) stellt eine solche Liste für jeden Typ, für die es Typ Schnellansichten und benutzerdefinierten Viewer unterstützen möchte. Aufrufe von [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Starten Sie den gesamten Prozess der Zugriff auf Typ Schnellansichten und benutzerdefinierten Viewer \(finden Sie unter [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md) ausführliche Informationen über die Aufrufsequenz\).  
  
### Benutzerdefinierte Viewer  
 Benutzerdefinierte Viewer werden in die EE für einen bestimmten Datentyp implementiert und dargestellt werden, durch die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) Schnittstelle. Ein benutzerdefinierter Viewer ist nicht so flexibel wie eine Schnellansicht geben, da es steht nur bei der EE, der diese spezielle benutzerdefinierten Viewer implementiert ausgeführt wird. Implementieren einen benutzerdefinierten Viewer ist einfacher als die Implementierung der Unterstützung für Typ Schnellansichten. Allerdings bietet Typ Schnellansichten unterstützen maximale Flexibilität für den Endbenutzer für seine Daten zu visualisieren. Der Rest dieser Diskussion betrifft nur die Schnellansichten Typ.  
  
## Schnittstellen  
 Die EE implementiert die folgenden Schnittstellen zur Unterstützung von Schnellansichten Typ, von Visual Studio verwendet wird:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 Die EE nutzt die folgenden Schnittstellen zum Typ Schnellansichten unterstützen:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)