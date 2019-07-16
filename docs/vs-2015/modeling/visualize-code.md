---
title: Visualisieren von Code | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2d5803544e4e7279179929c7c04a3792e4dd9318
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183872"
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
|**Verstehen von Code und seinen Beziehungen:**<br /><br /> Ordnen Sie Beziehungen zwischen bestimmten Codesegmenten zu.<br /><br /> Zeigen Sie eine Übersicht über die Beziehungen im Code für die gesamte Projektmappe an.<br /><br /> **Hinweis:** In dieser Version von Visual Studio den Begriff *codezuordnung* dient anstelle von *Abhängigkeitsdiagramm*.|-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Verstehen von klassenstrukturen:**<br /><br /> Visualisieren Sie die Struktur von Klassen in einem Projekt, indem Sie aus dem Code Klassendiagramme erstellen.|[Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Beschreiben Sie den allgemeinen Systementwurf, und Überprüfen von Code anhand dieses Entwurfs:**<br /><br /> Beschreiben Sie den allgemeinen Systementwurf und die beabsichtigten Abhängigkeiten, indem Sie Ebenendiagramme erstellen. Überprüfen Sie Code anhand dieses Entwurfs, um sicherzustellen, dass die Abhängigkeiten im Code konsistent zum Entwurf verlaufen.|-   [Erstellen von Ebenendiagrammen aus Ihrem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|  
|**Kommunizieren der benutzeranforderungen und die Architektur:**<br /><br /> Modellieren Sie die Benutzeranforderungen und die Architektur des Softwaresystems, indem Sie die folgenden UML-Diagramme zeichnen: Aktivität, Komponente, Klasse, Sequenz und Anwendungsfall.|-   [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)<br />-   [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md)<br />-   [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
|**Kategorie**|**Links**|  
|------------------|---------------|  
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technische Artikel und Journale**|[MSDN-Forum für Architektur](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Siehe auch  
 [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)   
 [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)   
 [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md)   
 [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md)   
 [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
