---
title: Analyze and model your architecture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297951"
---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellen Sie sicher, dass Ihre App Benutzeranforderungen erfüllt, indem Sie die Visual Studio-Architektur und -Modellierungstools zum Entwerfen und Modellieren Ihrer App verwenden. Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen.

 Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen. Sie können Anforderungen, Aufgaben, Testfälle, Fehler oder andere Arbeitsschritte nachverfolgen, die den Modellen zugeordnet sind, indem Sie Modellelemente mit Team Foundation Server-Arbeitselementen und dem Entwicklungsplan verknüpfen. See [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>Beschreibung

|||
|-|-|
|**Visualisieren von Code**:<br /><br /> -   See the code's organization and relationships by creating code maps. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />-   See the class structure and members for a specific project by creating class diagrams from code.<br />-   Find conflicts between your code and its design by creating layer diagrams to validate code.<br /><br /> **Hinweis**: In dieser Version von Visual Studio wird der Begriff *Code Map* anstelle von *Abhängigkeitsdiagramm*verwendet. Der Begriff *Diagramm* allein bezieht sich in der Regel auf ein gerichtetes Diagramm oder ein DGML-Diagramm (oder -Dokument). Code Maps sind ein spezialisierter Typ von DGML-Diagrammen.|-   [Visualisieren von Code](../modeling/visualize-code.md)<br />-   [Working with Classes and Other Types (Class Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Understand your code dependencies through visualization (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Visualize the impact of a change (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**Beschreiben und Kommunizieren von Benutzeranforderungen**:<br /><br /> -   Clarify user stories, business rules, and other requirements and help ensure their consistency by drawing UML diagrams such as use case, activity, and class diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**Definieren der Architektur**:<br /><br /> -   Model the large-scale structure of your software system and the design patterns by drawing UML component, class, and sequence diagrams.<br />-   Define and enforce constraints on dependencies between the components of your code by creating layer diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Überprüfen des Systems anhand der Anforderungen und des beabsichtigten Entwurfs:**<br /><br /> -   Define acceptance tests or system tests based on the requirements models. Dies schafft eine enge Beziehung zwischen den Tests und den Anforderungen der Benutzer und erleichtert das Aktualisieren des Systems bei geänderten Anforderungen.<br />-   Validate code dependencies with layer diagrams that describe the intended architecture and prevent changes that might conflict with the design.|-   [Validate your system during development](../modeling/validate-your-system-during-development.md)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br /> -   Put code maps, modeling projects, UML diagrams, and layer diagrams under Team Foundation version control so you can share them.|Arbeiten mehrere Benutzer mit diesen Elementen unter Team Foundation-Versionskontrolle, verwenden Sie diese Richtlinien, um Probleme mit der Versionskontrolle zu vermeiden:<br /><br /> -   [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generieren oder Konfigurieren von Teilen der Anwendung aus UML- oder domänenspezifischen Sprachen**:<br /><br /> -   Make your design more responsive to requirements changes and easily variable across a product line.|-   [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md)|
|**Anpassen von Modellen und Diagrammen**:<br /><br /> -   Adapt models to how your project uses them by defining additional properties for UML elements, validation constraints to make sure that your models conform to your business rules, and additional menu commands and toolbox items.<br />-   Create your own domain-specific languages.|-   [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br /> -   Use text blocks and control logic inside templates to generate text-based files.|-   [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Typen von Modellen und deren Anwendungsmöglichkeiten

|**Modelltyp und typische Anwendungsmöglichkeiten**|
|-------------------------------------|
|**Codezuordnungen**<br /><br /> Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -   Examine program code so you can better understand its structure and its dependencies, how to update it, and estimate the cost of proposed changes.<br /><br /> Thema<br /><br /> -   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Layer diagram**<br /><br /> Anhand von Ebenendiagrammen können Sie die Struktur einer Anwendung als einen Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Sie können die Validierung ausführen, um Konflikte zwischen Abhängigkeiten im Code und den in einem Ebenendiagramm beschriebenen Abhängigkeiten zu ermitteln.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -   Stabilize the structure of the application through numerous changes over its life.<br />-   Discover unintentional dependency conflicts before checking in changes to the code.<br /><br /> Thema<br /><br /> -   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**UML model**<br /><br /> Ein UML-Modell beinhaltet mehrere Ansichten, einschließlich Klasse, Komponente, Anwendungsfall sowie Aktivitäts- und Sequenzdiagramme. Sie können UML speziell für Ihre Anwendungsdomäne anpassen. Sie können z. B. Tags, zusätzliche Informationen und Einschränkungen an die Modellelemente anfügen. Außerdem können Sie Tools definieren, mit denen die Modelle bearbeitet werden können. See [Create models for your app](../modeling/create-models-for-your-app.md).<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -   Describe requirements and design. UML lässt sich bei der Entwicklung von Anwendungen schnell anwenden. See [Use models in your development process](../modeling/use-models-in-your-development-process.md).<br />-   Generate or configure tests or parts of an application. Es ist ein wenig Aufwand erforderlich, um die Notation anzupassen und die Generierungsvorlagen oder konfigurierbare Anwendung zu entwickeln. See [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md).<br />-   For general description and for code generation or configuration in smaller projects.|
|**Domänenspezifische Sprache (DSL)**<br /><br /> Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist sie normalerweise eine grafische Darstellung.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -   Generate or configure parts of the application. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.<br />-   For large projects or in product lines where the investment in developing the DSL and its tools is returned by its use in more than one project.<br /><br /> Thema<br /><br /> -   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Wo kann ich weitere Informationen abrufen?

|||
|-|-|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Siehe auch

- [What's new for modeling in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps und Anwendungslebenszyklus-Verwaltung](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
