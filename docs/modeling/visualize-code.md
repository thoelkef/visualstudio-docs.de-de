---
title: Visualisieren von Code
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9886ea905a4997d5735e4dd2cabbfc4798a5c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535875"
---
# <a name="visualize-code"></a>Visualisieren von Code

Sie können die Visualisierungs- und Modellierungstools in Visual Studio verwenden, damit diese Ihnen dabei helfen, vorhandenen Code zu verstehen und Ihre Anwendung zu beschreiben. Dies lässt Sie visuell erfahren, wie sich die Änderungen auf den Code auswirken, und Sie können die Arbeit und die Risiken bewerten, die sich von den Änderungen ergeben. Beispiel:

- Ordnen Sie Beziehungen visuell zu, um diese Beziehungen in Ihrem Code besser zu verstehen.

- Um die Architektur des Systems zu beschreiben und den Code mit dem Entwurf konsistent zu halten, erstellen Sie Abhängigkeits Diagramme, und überprüfen Sie den Code anhand dieser Diagramme.

- Erstellen Sie Klassendiagramme, um Klassenstrukturen zu beschreiben.

Diese Tools erleichtern auch die Kommunikation mit anderen Projektbeteiligten.

Welche Editionen von Visual Studio die einzelnen Features unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|Szenario|Artikel|
|-|-|
|**Verstehen von Code und seinen Beziehungen:**<br /><br /> Ordnen Sie Beziehungen zwischen bestimmten Codesegmenten zu.<br /><br /> Zeigen Sie eine Übersicht über die Beziehungen im Code für die gesamte Projektmappe an.|- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analysen](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Zuordnen von Methoden in der aufrufsstapel beim Debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Verstehen von Klassenstrukturen:**<br /><br /> Visualisieren Sie die Struktur von Klassen in einem Projekt, indem Sie aus dem Code Klassendiagramme erstellen.|[Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Beschreiben Sie den allgemeinen Systementwurf, und überprüfen Sie den Code anhand dieses Entwurfs:**<br /><br /> Beschreiben Sie den System Entwurf auf hoher Ebene und die beabsichtigten Abhängigkeiten, indem Sie Abhängigkeits Diagramme erstellen. Überprüfen Sie Code anhand dieses Entwurfs, um sicherzustellen, dass die Abhängigkeiten im Code konsistent zum Entwurf verlaufen.|- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Weitere Informationen

- [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analyse und Modell Architektur](../modeling/analyze-and-model-your-architecture.md)
- [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)
- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
