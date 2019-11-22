---
title: Visualize code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 955103b6d28e90321fb45c23825f0c2a25362208
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301315"
---
# <a name="visualize-code"></a>Visualisieren von Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Visualisierungs- und Modellierungstools in Visual Studio verwenden, damit diese Ihnen dabei helfen, vorhandenen Code zu verstehen und Ihre Anwendung zu beschreiben. Dies lässt Sie visuell erfahren, wie sich die Änderungen auf den Code auswirken, und Sie können die Arbeit und die Risiken bewerten, die sich von den Änderungen ergeben. Beispiel:

- Ordnen Sie Beziehungen visuell zu, um diese Beziehungen in Ihrem Code besser zu verstehen.

- Um die Architektur des Systems zu beschreiben und den Code konsistent mit dem Entwurf zu halten, erstellen Sie Ebenendiagramme und prüfen den Code gegen diese Diagramme.

- Erstellen Sie Klassendiagramme, um Klassenstrukturen zu beschreiben.

- Zeichnen Sie UML-Diagramme (Unified Modeling Language), um verschiedene Aspekte des Systems zu modellieren und zu kommunizieren. Beispielsweise können Sie die Komponenten, Typen, Interaktionen und Prozesse eines Systems modellieren.

  Diese Tools erleichtern auch die Kommunikation mit anderen Projektbeteiligten. Mithilfe von UML-Klassendiagrammen können Sie z. B. ein allgemeines Glossar zur Erörterung des Systems mit Projektbeteiligten, Benutzern und Teammitgliedern erstellen.

  Informationen dazu, welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|||
|-|-|
|**Understand code and its relationships:**<br /><br /> Ordnen Sie Beziehungen zwischen bestimmten Codesegmenten zu.<br /><br /> Zeigen Sie eine Übersicht über die Beziehungen im Code für die gesamte Projektmappe an.<br /><br /> **Hinweis**: In dieser Version von Visual Studio wird der Begriff *Code Map* anstelle von *Abhängigkeitsdiagramm*verwendet.|-   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Map methods on the call stack while debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Understand class structures:**<br /><br /> Visualisieren Sie die Struktur von Klassen in einem Projekt, indem Sie aus dem Code Klassendiagramme erstellen.|[Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describe the high-level system design and validate code against this design:**<br /><br /> Beschreiben Sie den allgemeinen Systementwurf und die beabsichtigten Abhängigkeiten, indem Sie Ebenendiagramme erstellen. Überprüfen Sie Code anhand dieses Entwurfs, um sicherzustellen, dass die Abhängigkeiten im Code konsistent zum Entwurf verlaufen.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**Communicate the user requirements and architecture:**<br /><br /> Modellieren Sie die Benutzeranforderungen und die Architektur des Softwaresystems, indem Sie die folgenden UML-Diagramme zeichnen: Aktivität, Komponente, Klasse, Sequenz und Anwendungsfall.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|------------------|---------------|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Technische Artikel und Journale**|[MSDN Architecture Forum](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Siehe auch
 [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md) [Model user requirements](../modeling/model-user-requirements.md) [Model your app's architecture](../modeling/model-your-app-s-architecture.md) [Use models in your development process](../modeling/use-models-in-your-development-process.md)
