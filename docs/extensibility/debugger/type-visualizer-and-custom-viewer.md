---
title: Typ Visualizer und custom Viewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712465"
---
# <a name="type-visualizer-and-custom-viewer"></a>Typvisualisierung und benutzerdefinierter Viewer
Eine Typvisualisierung ist eine Komponente, die ein Datenelement in einem bestimmten Format anzeigt. Das Format hängt ganz davon ab, wer die Visualisierung implementiert, sei es der Endbenutzer oder ein Drittanbieter von Visualisierern.

 Ein benutzerdefinierter Viewer ist der Teil eines benutzerdefinierten Ausdrucksauswertungswerts, der ein Datenelement in einem bestimmten Format anzeigt. Dieses Format ist vollständig dem Implementierer des benutzerdefinierten Viewers überlassen, was bedeutet, dass das Format dem Implementierer des Ausdrucksevaluators (EE) entspricht.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Unterstützung für Typvisualisierer in einem Ausdrucksevaluator
 Ein EE unterstützt Typvisualisierungen, indem es eine Reihe von Schnittstellen unterstützt, auf die Visualizer zugreifen können: Schnittstellen wie [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) und [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Der EE ist jedoch nicht für die Implementierung der Typvisualisierung selbst verantwortlich: Der EE ermöglicht lediglich externen Visualisierern den Zugriff auf seine Typinformationen. Solche Visualisierungen können zusammen mit dem EE ausgeliefert und an der entsprechenden Stelle in Visual Studio installiert werden, die von einem anderen Drittanbieter oder sogar vom Endbenutzer bereitgestellt wird.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Unterstützung für benutzerdefinierte Viewer in einem Ausdrucksbewerter
 Ein EE kann auch benutzerdefinierte Viewer unterstützen, bei denen der EE selbst den Code zum Anzeigen des Datentyps bereitstellt. Ein benutzerdefinierter Viewer implementiert die [IDebugCustomViewer-Schnittstelle,](../../extensibility/debugger/reference/idebugcustomviewer.md) die alle Aufgaben übernimmt, die Daten in jedem gewünschten Format anzuzeigen. Der Betrachter hat die volle Kontrolle über das Display und kann sogar die Daten ändern lassen. Alle kundenspezifischen Viewer, die von der EE geliefert werden, werden mit dem EE geliefert, wenn das Produkt ausgeliefert wird.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
