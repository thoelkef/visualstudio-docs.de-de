---
title: Geben Sie Schnellansicht und den benutzerdefinierten Viewer | Microsoft Docs
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
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 91aa122c96230c7fd34ce2b65925b9166883def6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>Typ-Schnellansicht und den benutzerdefinierten Viewer
Eine Typ-Schnellansicht ist eine Komponente, die einen Teil der Daten in einem sehr spezifischen Format angezeigt. Dieses Format wird vom Implementierer der Schnellansicht vollständig, die es dem Endbenutzer oder einem Drittanbieter von Schnellansichten werden.  
  
 Ein benutzerdefinierter Viewer ist der Teil einer benutzerdefinierten ausdrucksauswertung, die einen Teil der Daten in einem sehr spezifischen Format angezeigt. Dieses Format ist vollständig vom Implementierer der benutzerdefinierten Viewer, was bedeutet, dass das Format der Implementierer der ausdrucksauswertung (EE) ist.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Unterstützung für die Typ-Schnellansichten in eine Ausdrucksauswertung  
 Ein EE kann Typ-Schnellansichten unterstützen, indem Sie einen Satz von Schnittstellen zugänglich Schnellansichten unterstützen: Schnittstellen wie [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) und [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Beachten Sie jedoch, dass die EE nicht für die Implementierung der Typ-Schnellansicht selbst verantwortlich ist: die EE lediglich externe Schnellansichten ermöglicht den Zugriff auf die Typinformationen. Solche Schnellansichten möglicherweise zusammen mit der EE ausgeliefert und an der entsprechenden Stelle in Visual Studio bereitgestellt werden, von einem anderen Drittanbieter oder auch von der Endbenutzer installiert werden.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Unterstützung für den benutzerdefinierten Viewer in eine Ausdrucksauswertung  
 Ein EE kann auch benutzerdefinierten Viewer unterstützen, in denen die EE selbst den Code für den Datentyp anzeigen bereitstellt. Implementiert ein benutzerdefinierter Viewer die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) -Schnittstelle, die alle Aufgaben für das Anzeigen von Daten in dem Format behandelt gewünscht; im Viewer verfügt über Vollzugriff auf die Anzeige und kann auch die Daten geändert werden. Alle benutzerdefinierten Viewer, die von der EE bereitgestellten verfügen über die EE, bei der Auslieferung des Produkts.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)