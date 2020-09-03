---
title: Typvisualizer und Custom Viewer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185311"
---
# <a name="type-visualizer-and-custom-viewer"></a>Typschnellansicht und benutzerdefinierter Viewer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine typschnell Ansicht ist eine Komponente, die ein Datenelement in einem sehr spezifischen Format anzeigt. Dieses Format ist vollständig für den Implementierer der Schnellansicht, d. h. der Endbenutzer oder ein Drittanbieter von Visualisierungen.  
  
 Ein benutzerdefinierter Viewer ist der Teil einer benutzerdefinierten Ausdrucks Auswertung, der ein Datenelement in einem sehr spezifischen Format anzeigt. Dieses Format ist vollständig auf die Implementierung des benutzerdefinierten Viewers fest, was bedeutet, dass das Format dem Implementierer der Ausdrucks Auswertung (EE) entspricht.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Unterstützung für typvisualisierungen in einer Ausdrucks Auswertung  
 Ein EE kann typvisualisierungen unterstützen, indem er eine Reihe von Schnittstellen unterstützt, auf die Visualisierungen zugreifen können: Schnittstellen wie [ieevisualizerservice](../../extensibility/debugger/reference/ieevisualizerservice.md) und [ieevisualizerdataprovider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Beachten Sie jedoch, dass der EE nicht für die Implementierung der typschnell Ansicht selbst zuständig ist: der EE ermöglicht externen visualisierern lediglich den Zugriff auf die Typinformationen. Solche schnell Ansichten werden möglicherweise zusammen mit dem EE geliefert und an der entsprechenden Stelle in Visual Studio installiert, die von einem Drittanbieter oder sogar vom Endbenutzer bereitgestellt wird.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Unterstützung für benutzerdefinierte Viewer in einer Ausdrucks Auswertung  
 Ein EE kann auch benutzerdefinierte Viewer unterstützen, in denen der EE selbst den Code zum Anzeigen des Datentyps bereitstellt. Ein benutzerdefinierter Viewer implementiert die [idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md) -Schnittstelle, die alle Aufgaben zum Anzeigen der Daten in einem beliebigen Format verarbeitet. der Viewer verfügt über die vollständige Kontrolle über die Anzeige und kann sogar das Ändern der Daten zulassen. Alle benutzerdefinierten Viewer, die von der EE bereitgestellt werden, erhalten den EE, wenn das Produkt ausgeliefert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [Ieevisualizerservice](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
