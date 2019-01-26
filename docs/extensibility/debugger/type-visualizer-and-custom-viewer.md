---
title: Typ der Schnellansicht und den benutzerdefinierten Viewer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b09dc2d578ade421d35bb17dfbdf01e93313bbdb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926865"
---
# <a name="type-visualizer-and-custom-viewer"></a>Typschnellansicht und benutzerdefinierter viewer
Eine typschnellansicht ist eine Komponente, die einen Teil der Daten in einem bestimmten Format angezeigt. Das Format ist vollständig bis zu, die die Schnellansicht implementiert, sei es dem Endbenutzer oder einem Drittanbieter von Schnellansichten.  
  
 Ein benutzerdefinierter Viewer ist der Teil einer benutzerdefinierten ausdrucksauswertung, der ein Datenelement in einem bestimmten Format angezeigt. Dieses Format ist vollständig hängt von der Implementierung der benutzerdefinierten Viewer, was bedeutet, dass das Format hängt von der Implementierung von der ausdrucksauswertung (EE) ist.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Unterstützung für Typ-Schnellansichten in einer ausdrucksauswertung  
 Ein EE unterstützt die Typ-Schnellansichten unterstützt einen Satz von Schnittstellen für Schnellansichten verfügbar: z. B. [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) und [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Die EE ist jedoch nicht für die Implementierung der typschnellansicht selbst verantwortlich: die EE lediglich externe Schnellansichten ermöglicht den Zugriff auf die Typinformationen. Solche Schnellansichten wäre zusammen mit den EE geliefert und installiert in der entsprechenden Stelle in Visual Studio, die von einem anderen Drittanbieter oder sogar durch den Endbenutzer bereitgestellt.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Unterstützung für benutzerdefinierten Viewern in einer ausdrucksauswertung  
 Ein EE kann auch benutzerdefinierten Viewer unterstützen, in denen die EE selbst den Code für den Datentyp anzeigen bereitstellt. Implementiert ein benutzerdefinierter Viewer die [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) -Schnittstelle, die alle Aufgaben des zeigt die Daten im benötigten Format behandelt erwünscht ist; der Viewer verfügt über Vollzugriff auf die Anzeige und kann auch die Daten geändert werden. Alle benutzerdefinierten Viewer, die von der EE bereitgestellt verfügen über die EE, wenn das Produkt ausgeliefert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Debug-engine](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)