---
title: Visualisieren von Code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 622655f1ed05ab77b36a3c4756a0176fcad74ac4
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684927"
---
# <a name="visualize-code"></a>Visualisieren von Code

Sie können die Visualisierungs- und Modellierungstools in Visual Studio verwenden, damit diese Ihnen dabei helfen, vorhandenen Code zu verstehen und Ihre Anwendung zu beschreiben. Dies lässt Sie visuell erfahren, wie sich die Änderungen auf den Code auswirken, und Sie können die Arbeit und die Risiken bewerten, die sich von den Änderungen ergeben. Zum Beispiel:

- Ordnen Sie Beziehungen visuell zu, um diese Beziehungen in Ihrem Code besser zu verstehen.

- Um die Architektur des Systems zu beschreiben und den Code auf dem mit dem Entwurf konsistent zu halten, Erstellen von Abhängigkeitsdiagrammen aus, und Überprüfen von Code gegen diese Diagramme.

- Erstellen Sie Klassendiagramme, um Klassenstrukturen zu beschreiben.

Diese Tools erleichtern auch die Kommunikation mit anderen Projektbeteiligten.

Welche Editionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|||
|-|-|
|**Verstehen von Code und seinen Beziehungen:**<br /><br /> Ordnen Sie Beziehungen zwischen bestimmten Codesegmenten zu.<br /><br /> Zeigen Sie eine Übersicht über die Beziehungen im Code für die gesamte Projektmappe an.|- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Verstehen von klassenstrukturen:**<br /><br /> Visualisieren Sie die Struktur von Klassen in einem Projekt, indem Sie aus dem Code Klassendiagramme erstellen.|[Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Beschreiben Sie den allgemeinen Systementwurf, und Überprüfen von Code anhand dieses Entwurfs:**<br /><br /> Beschreiben Sie den allgemeinen Systementwurf und die beabsichtigten Abhängigkeiten, indem Sie Abhängigkeitsdiagramme erstellen. Überprüfen Sie Code anhand dieses Entwurfs, um sicherzustellen, dass die Abhängigkeiten im Code konsistent zum Entwurf verlaufen.|- [Erstellen von Abhängigkeitsdiagrammen aus Ihrem code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Siehe auch

- [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analyse und Modellarchitektur](../modeling/analyze-and-model-your-architecture.md)
- [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)
- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
