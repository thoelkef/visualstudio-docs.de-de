---
title: "Typ-Schnellansicht und benutzerdefinierten Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen von benutzerdefinierten Viewer [Debugging-SDK]"
  - "[Debuggen SDK] Typ Schnellansicht Debuggen"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Typ-Schnellansicht und benutzerdefinierten Viewer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Typ schnellansicht ist eine Komponente, die ein Datenelement in einem sehr spezifischen Format anzeigt.  Dieses Format ist vollständig von der Implementierung der Schnellansicht, sei es dem Endbenutzer oder einen Fremdanbieter von Schnellansichten.  
  
 Ein benutzerdefinierter Viewer ist der Teil eines benutzerdefinierten Ausdrucksauswerters, der ein Datenelement in einem sehr spezifischen Format anzeigt.  Dieses Format ist vollständig von der Implementierung des benutzerdefinierten Viewers. Dies bedeutet, dass das Format von der Implementierung des Ausdrucksauswerters \(EE\) ist.  
  
## Unterstützung für Typ\-Schnellansichten in einem Ausdrucksauswertung  
 Eine EE Typ kann schnellansichten unterstützen, indem Sie einen vorhandenen Satz von Schnittstellen unterstützt, die auf den Schnellansichten sind: Schnittstellen wie [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) und [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md).  Beachten Sie jedoch, dass die EE nicht für die Implementierung der Typ schnellansicht selbst verantwortlich ist: Externe nur zulässig EE die Schnellansicht Zugriff auf die Typinformationen.  Solche Schnellansichten werden zusammen mit der EE gelieferten und im entsprechenden Stelle in Visual Studio installiert werden, angegeben von einem anderen Drittanbieter oder sogar vom Endbenutzer.  
  
## Unterstützung für benutzerdefinierte Viewer in einem Ausdrucksauswertung  
 Eine EE benutzerdefinierten Viewer können auch unterstützen, in denen das Zubehör EE auch der Code zum Anzeigen des Datentyps.  Ein benutzerdefinierter Viewer implementiert die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)\-Schnittstelle, die alle Aufgaben zum Anzeigen der Daten behandelt, was im Format erforderlich ist. Der Viewer hat die vollständige Kontrolle über das Anzeigen und kann auch Daten geändert werden können.  Alle benutzerdefinierten Viewer, die von der EE angegeben werden, mit der EE, wenn das Produkt ausgeliefert wird.  
  
## Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)