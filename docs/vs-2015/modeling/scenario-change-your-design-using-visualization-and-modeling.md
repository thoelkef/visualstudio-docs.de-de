---
title: 'Szenario: Ändern Sie Ihren Entwurf mithilfe von Visualisierung und Modellierung | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301236"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellen Sie sicher, dass das Softwaresystem die Anforderungen der Benutzer erfüllt, indem Sie die Visualisierungs- und Modellierungstools in Visual Studio verwenden. Verwenden Sie Tools wie z. B. UML-Diagramme (Unified Modeling Language), Code Maps, Ebenendiagramme und Klassendiagramme für folgende Aufgaben:

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Tools unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Ermitteln der Anforderungen und Geschäftsprozesse von Benutzern

- Visualisieren und Untersuchen von vorhandenem Code

- Beschreiben der Änderungen an einem vorhandenen System

- Sicherstellen, dass das System die Anforderungen erfüllt

- Sicherstellen, dass der Code konsistent mit dem Entwurf ist

  Diese exemplarische Vorgehensweise:

- Beschreibt den Nutzen dieser Tools für Ihr Softwareprojekt

- Zeigt, wie Sie diese Tools unabhängig von Ihrem Entwicklungsansatz in einem Beispielszenario verwenden können

  Weitere Informationen zu diesen Tools und den Szenarien, die sie unterstützen, finden Sie unter:

- [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)

- [Visualisieren von Code](../modeling/visualize-code.md)

- [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>Szenarioübersicht
 Dieses Szenario beschreibt Episoden in den Lebenszyklen der Softwareentwicklung von zwei fiktiven Unternehmen: Dinner Now und Lucerne Publishing. Dinner Now bietet einen webbasierten Essenslieferdienst in Seattle an. Kunden können Essen bestellen auf der Dinner Now-Website bezahlen. Die Bestellungen werden dann an das entsprechende örtliche Restaurant für die Lieferung gesendet. Lucerne Publishing, ein Unternehmen in New York, unterhält mehrere Geschäfte sowohl im Internet als auch außerhalb des Internets. Beispielsweise wird eine Website betrieben, auf der Kunden Restaurantkritiken veröffentlichen können.

 Lucerne hat vor kurzem Dinner Now übernommen und möchte die folgenden Änderungen vornehmen:

- Integrieren der Websites durch Hinzufügen von Restaurantkritikfunktionen zu Dinner Now

- Ersetzen des Zahlungssystems von Dinner Now durch das System von Lucerne

- Ausweiten der Dienstleistung von Dinner Now auf die gesamte Region.

  Dinner Now verwendet SCRUM- und eXtreme-Programmierung. Sie verfügen über eine sehr hohe Testabdeckung und nur wenig nicht unterstützten Code. Risiken werden minimiert, indem kleine, funktionierende Versionen eines Systems erstellt und dann schrittweise Funktionen hinzugefügt werden. Der Code wird über kurze und regelmäßige Iterationen entwickelt. Dadurch werden Änderungen auf sichere Weise eingeführt, der Code wird häufig umgestaltet, und ein "Big Design Up Front" wird vermieden.

  Lucerne unterhält eine überaus umfangreichere und komplexe Auflistung von Systemen, die teilweise über 40 Jahre alt sind. Aufgrund von Komplexität und Umfang des älteren Codes werden Änderungen nur mit größter Vorsicht vorgenommen. Lucerne verfolgt einen rigoroseren Entwicklungsprozess und zieht es vor, detaillierte Lösungen zu entwerfen und den Entwurf und sowie während der Entwicklung auftretende Änderungen zu dokumentieren.

  Beide Teams verwenden Modellierungsdiagramme in Visual Studio, die sie dabei unterstützen, Systeme zu entwickeln, die die Anforderungen der Benutzer erfüllen. Sie verwenden Team Foundation Server zusammen mit anderen Tools zum Planen, Organisieren und Verwalten ihrer Arbeit.

  Weitere Informationen über Team Foundation Server finden Sie unter:

- [Planen und Nachverfolgen der Arbeit](#PlanningTracking)

- [Testen, Überprüfen und Einchecken von aktualisiertem Code](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Rollen von Architektur- und Modellierungsdiagrammen in der Softwareentwicklung
 In der folgenden Tabelle werden Rollen beschrieben, die diese Tools während verschiedener Phasen des Lebenszyklus der Softwareentwicklung spielen können:

||**Modellieren von Benutzeranforderungen**|**Modellierung von Geschäftsprozessen**|**Systemarchitektur und -entwurf**|**Visualisieren und Untersuchen von Code**|**Überprüfung**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Anwendungsfalldiagramm (UML)|√|√|||√|
|Aktivitätsdiagramm (UML)|√|√|√||√|
|Klassendiagramm (UML)|√|√|√||√|
|Komponentendiagramm (UML)|√|√|√||√|
|Sequenzdiagramm (UML)|√|√|√||√|
|DSL-Diagramm (domänenspezifische Sprache)|√|√|√|||
|Ebenendiagramm, Ebenenvalidierung|||√|√|√|
|Code Map|||√|√|√|
|Klassen-Designer (codebasiert)||||√||

 Um UML-Diagramme und Ebenendiagramme zu zeichnen, müssen Sie ein Modellierungsprojekt als Teil einer vorhandenen oder einer neuen Lösung erstellen. Diese Diagramme müssen im Modellierungsprojekt erstellt werden. Elemente in UML-Diagrammen sind Teil eines allgemeinen Modells, und die UML-Diagramme sind Ansichten dieses Modells. Elemente in Ebenendiagrammen befinden sich im Modellierungsprojekt, sie werden jedoch nicht im allgemeinen Modell gespeichert. Code Maps und .NET-Klassendiagramme, die aus Code erstellt werden, sind außerhalb des Modellierungsprojekts vorhanden.

 Siehe:

- [Erstellen von UML-Modellierungsprojekten und -Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

- [Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Um alternative Ansichten der Architektur anzuzeigen, können Sie bestimmte Elemente aus demselben Modell in verschiedenen Diagrammen wiederverwenden. Beispielsweise können Sie eine Komponente in ein anderes Komponentendiagramm oder in ein Sequenzdiagramm ziehen, damit es als Akteur fungieren kann. Siehe [Bearbeiten von UML-Modellen und -Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

  Beide Teams verwenden außerdem Ebenenvalidierung, um sicherzustellen, dass Code in der Entwicklung mit dem Entwurf konsistent bleibt.

  Siehe:

- [Halten Sie Code mit dem Design konsistent](#ValidatingCode)

- [Beschreiben der logischen Architektur: Ebenendiagramme](#DescribeLayers)

- [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Einige Versionen von Visual Studio unterstützen Ebenenvalidierung und schreibgeschützte Versionen von Code Maps und UML-Diagrammen zur Visualisierung und Modellierung. Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a> Verstehen und Kommunizieren von Informationen zum System
 Es gibt keine vorgeschriebene Reihenfolge zum Verwenden der Visual Studio-Modellierungsdiagramme. Daher können Sie sie ganz Ihren Anforderungen oder dem Ansatz entsprechend verwenden. Normalerweise rufen Teams ihre Modelle im Verlauf des Projekts wiederholt und häufig auf. Jedes Diagramm bietet bestimmte Vorteile, um verschiedene Aspekte des Systems in der Entwicklung zu verstehen, zu beschreiben und zu kommunizieren.

 Dinner Now und Lucerne kommunizieren untereinander sowie mit Projektbeteiligten anhand von Diagrammen als einheitliche Sprache. Beispielsweise verwendet Dinner Now Diagramme, um folgende Aufgaben auszuführen:

- Visualisieren von vorhandenem Code

- Kommunizieren mit Lucerne über neue oder aktualisierte User Storys

- Identifizieren von Änderungen, die für die Unterstützung neuer oder aktualisierter User Storys erforderlich sind

  Lucerne verwendet Diagramme, um folgende Aufgaben auszuführen:

- Aneignung von Kenntnissen über den Geschäftsprozess von Dinner Now

- Verstehen des Systementwurfs

- Kommunizieren mit Dinner Now über neue oder aktualisierte Benutzeranforderungen

- Dokumentieren von Aktualisierungen am System

  Die Diagramme sind in Team Foundation Server integriert, sodass die Teams ihre Arbeit leichter planen, verwalten und verfolgen können. Beispielsweise verwenden sie Modelle, um Testfälle und Entwicklungsaufgaben zu identifizieren und ihre Arbeit einzuschätzen. Lucerne verknüpft Team Foundation Server-Arbeitselemente mit Modellelementen, sodass sie den Fortschritt überwachen sowie sicherstellen können, dass das System die Anforderungen der Benutzer erfüllt. Beispielsweise werden Anwendungsfälle mit Testfallarbeitselementen verknüpft, um sehen zu können, dass Anwendungsfälle erfüllt werden, wenn alle Tests erfolgreich verlaufen.

  Bevor Teams ihre Änderungen einchecken, überprüfen sie den Code anhand der Tests und des Entwurfs durch das Ausführen von Builds, die Ebenenvalidierung und automatisierte Tests beinhalten. Dadurch wird sichergestellt, dass der aktualisierte Code dem Entwurf nicht widerspricht und Funktionen, die bereits funktionieren, nicht beeinträchtigt werden.

  Siehe:

- [Grundlegendes zur Rolle des Systems im Geschäftsprozess](#UnderstandingBPMandSystemDesign)

- [Beschreiben neuer oder aktualisierter Benutzeranforderungen](#DescribingURM)

- [Erstellen von Tests aus Modellen](#CreatingTests)

- [Identifizieren von Änderungen am bestehenden System](#DeterminingChanges)

- [Sicherstellen der Konsistenz von Code und Entwurf](#ValidatingCode)

- [Allgemeine Tipps zum Erstellen und Verwenden von Modellen](#GeneralTips)

- [Planen und Nachverfolgen der Arbeit](#PlanningTracking)

- [Testen, Überprüfen und Einchecken von aktualisiertem Code](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>Verständnis der Rolle des Systems im Geschäftsprozess
 Lucerne möchte mehr über den Geschäftsprozess von Dinner Now erfahren. Die folgenden Diagramme werden erstellt, um den Kenntnisstand mit Dinner Now leichter abzuklären:

|**Diagramm**|**Beschreibt**|
|-----------------|-------------------|
|*Anwendungsfalldiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|- Die Aktivitäten, die das Dinner Now-System unterstützt<br />- Die Personen und externen Systeme, die die Aktivitäten ausführen<br />- Die wichtigsten Komponenten des Systems, die jede Aktivität unterstützen<br />- Die Teile des Geschäftsprozesses, die außerhalb des Rahmens des aktuellen Systems liegen, z. B.|
|*Aktivitätsdiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|Der Ablauf von Schritten, wenn ein Kunde eine Bestellung aufgibt|
|*Klassendiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|Die bei Besprechungen verwendeten Geschäftsentitäten und Begriffe sowie die Beziehungen zwischen ihnen Beispielsweise sind "Bestellung" und "Menüelement" Teil des Vokabulars in diesem Szenario.|

 Lucerne erstellt z. B. das folgende Anwendungsfalldiagramm, um zu verstehen, welche Aufgaben auf der Dinner Now-Website ausgeführt werden und von wem sie ausgeführt werden:

 ![UML-Anwendungsfalldiagramm](../modeling/media/uml-usecase.png "UML_UseCase")

 **UML-Anwendungsfalldiagramm**

 Das folgende Aktivitätsdiagramm beschreibt den Ablauf von Schritten, wenn ein Kunde auf der Dinner Now-Website eine Bestellung aufgibt. In dieser Version identifizieren Kommentarelemente die Rollen, und mit Linien werden *Verantwortlichkeitsbereiche*erstellt, die die Schritte nach Rolle organisieren:

 ![UML-Aktivitätsdiagramm](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **UML-Aktivitätsdiagramm**

 Das folgende Klassendiagramm beschreibt die Entitäten, die am Bestellvorgang beteiligt sind:

 ![UML-Klassendiagramm](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **UML-Klassendiagramm**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>Beschreiben neuer oder aktualisierter Benutzeranforderungen
 Lucerne will dem Dinner Now-System Funktionen hinzufügen, damit Kunden Restaurantkritiken lesen und veröffentlichen können. Die folgenden Diagramme werden aktualisiert, um diese neue Anforderung mit Dinner Now zu besprechen:

|**Diagramm**|**Beschreibt**|
|-----------------|-------------------|
|*Anwendungsfalldiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|Ein neuer Anwendungsfall für "Restaurantkritik verfassen"|
|*Aktivitätsdiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|Die Schritte, die auftreten, wenn ein Kunde eine Restaurantkritik schreiben möchte|
|*Klassendiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|Die Daten, die zum Speichern einer Kritik erforderlich sind|

 Beispielsweise enthält das folgende Anwendungsfalldiagramm den neuen Anwendungsfall "Kritik verfassen", um die neue Anforderung darzustellen. Zur leichteren Erkennung wird es im Diagramm orangefarben hervorgehoben:

 ![UML-Anwendungsfalldiagramm](../modeling/media/uml-writerev.png "UML_WriteRev")

 **UML-Anwendungsfalldiagramm**

 Das folgende Aktivitätsdiagramm enthält neue Elemente in orange, um den Ablauf von Schritten im neuen Anwendungsfall zu beschreiben:

 ![UML-Aktivitätsdiagramm](../modeling/media/uml-writereview.png "UML_WriteReview")

 **UML-Aktivitätsdiagramm**

 Das folgende Klassendiagramm enthält die neue Klasse "Review" (Kritik) sowie zugehörige Beziehungen zu anderen Klassen, sodass die Teams die Einzelheiten erläutern können. Beachten Sie, dass ein Kunde und ein Restaurant über mehrere Kritiken verfügen können:

 ![UML-Klassendiagramm](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **UML-Klassendiagramm**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>Erstellen von Tests aus Modellen
 Beide Teams stimmen darin überein, dass sie einen vollständigen Satz von Tests für das System und seine Komponenten benötigen, bevor sie Änderungen vornehmen können. Lucerne verfügt über ein spezialisiertes Team, das Tests auf System- und Komponentenebene durchführt. Die von Dinner Now erstellten Tests werden wiederverwendet und mithilfe von UML-Diagrammen strukturiert:

- Jeder Anwendungsfall wird durch einen oder mehrere Tests dargestellt. Die Elemente im Anwendungsfalldiagramm sind mit Testfallarbeitselementen in Team Foundation Server verknüpft.

- Jeder Ablauf in einem Aktivitätsdiagramm oder einem Sequenzdiagramm auf Systemebene wird mindestens mit einem Test verknüpft. Das Testteam stellt systematisch sicher, dass jeder mögliche Pfad durch das Aktivitätsdiagramm getestet wird.

- Die zum Beschreiben der Tests verwendeten Begriffe basieren auf den Begriffen, die durch Anwendungsfall-, Klassen- und Aktivitätsdiagramme definiert werden.

  Mit der Änderung von Anforderungen und der entsprechenden Aktualisierung der Diagramme werden auch die Tests aktualisiert. Eine Anforderung wird nur als erfüllt betrachtet, wenn die Tests bestanden werden. Wenn es möglich oder praktikabel ist, werden die Tests auf Grundlage von UML-Diagrammen definiert, bevor mit der Implementierung begonnen wird.

  Siehe:

- [Entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)

- [Überprüfen des UML-Modells](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a> Identifying Changes to the Existing System
 Dinner Now muss die Kosten für die Erfüllung der neuen Anforderung schätzen. Diese hängen teilweise davon ab, wie sehr sich diese Änderung auf andere Teile des Systems auswirkt. Zur Verdeutlichung erstellt einer der Dinner Now-Entwickler die folgenden Code Maps und Diagramme aus vorhandenem Code:

|**Code Map oder Diagramm**|**Zeigt**|
|------------------------|---------------|
|*Code Map*<br /><br /> Siehe:<br /><br /> -   [Zuordnen von Abhängigkeiten in Ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Durchsuchen und Neuanordnen von Codezuordnungen](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Anpassen von Codezuordnungen durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Abhängigkeiten und andere Beziehungen im Code.<br /><br /> Dinner Now könnte z. B. damit beginnen, Assembly-Code Maps zu überprüfen, um eine Übersicht der Assemblys und ihrer Abhängigkeiten zu erhalten. Sie können in den Code Maps einen Drilldown durchführen, um die Namespaces und Klassen in diesen Assemblys zu untersuchen.<br /><br /> Dinner Now kann auch Code Maps erstellen, um bestimmte Bereiche und andere Arten von Beziehungen im Code zu untersuchen. Sie verwenden den Projektmappen-Explorer, um relevante Bereiche und Beziehungen zu finden und auszuwählen.|
|*Codebasiertes Klassendiagramm*<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Vorhandene Klassen in Code|

 Beispiel: Die Entwicklerin erstellt eine Code Map. Sie passt den Umfang an, um sich auf die Bereiche zu konzentrieren, die von dem neuen Szenario betroffen sind. Diese Bereiche werden ausgewählt und auf der Code Map hervorgehoben:

 ![Abhängigkeitsdiagramm für Namespaces](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Namespace-Code Map**

 Die Entwicklerin erweitert die ausgewählten Namespaces, um die zugehörigen Klassen, Methoden und Beziehungen anzuzeigen:

 ![Erweitertes Abhängigkeitsdiagramm für Namespaces](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Erweiterte Code Map für Namespaces mit sichtbaren gruppenübergreifenden Links**

 Die Entwicklerin untersucht den Code, um nach den betroffenen Klassen und Methoden zu suchen. Um die Auswirkungen der einzelnen Änderungen sofort anzuzeigen, generieren Sie Code Maps nach jeder Änderung neu. Siehe [Visualisieren](../modeling/visualize-code.md)von Code .

 Um Änderungen an anderen Teilen des Systems zu beschreiben, wie z. B. Komponenten oder Interaktionen, kann das Team diese Elemente bei Bedarf auf Whiteboards zeichnen. Sie können auch die folgenden Diagramme in Visual Studio zeichnen, sodass die Details von beiden Teams erfasst, verwaltet und verstanden werden können:

|**Diagramme**|**Beschreibt**|
|------------------|-------------------|
|*Aktivitätsdiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|Der Ablauf von Schritten, wenn das System erkennt, dass ein Kunde erneut eine Bestellung bei einem Restaurant aufgibt, und der Kunden aufgefordert wird, eine Kritik zu schreiben|
|*Klassendiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|Logische Klassen und ihre Beziehungen Beispielsweise wird eine neue Klasse hinzugefügt, um eine **Kritik** und die Beziehungen mit anderen Entitäten zu beschreiben, wie z. B. **Restaurant**, **Menü**und **Kunde**.<br /><br /> Um Kritiken einem Kunden zuzuordnen, muss das System Kundendetails speichern. Ein UML-Klassendiagramm kann helfen, diese Details zu klären.|
|*Codebasiertes Klassendiagramm*<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Vorhandene Klassen in Code|
|*Komponentendiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|Die Teile des Systems auf höherer Ebene, wie z. B. die Dinner Now-Website und ihre Schnittstellen Diese Schnittstellen definieren, wie Komponenten untereinander durch die Methoden oder Dienste interagieren, die sie bereitstellen und nutzen.|
|*Sequenzdiagramm (UML)*<br /><br /> Siehe:<br /><br /> -   [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)|Die Sequenz der Interaktionen zwischen Instanzen|

 Das folgende Komponentendiagramm zeigt z. B. die neue Komponente an, die Teil der Dinner Now-Websitekomponente ist. Die Komponente "ReviewProcessing" behandelt die Funktionalität zum Erstellen von Kritiken und wird orangefarben angezeigt:

 ![UML-Komponentendiagramm](../modeling/media/uml-internal.png "UML_Internal")

 **UML-Komponentendiagramm**

 Das folgende Sequenzdiagramm zeigt die Reihenfolge von Interaktionen an, die auftreten, wenn von der Dinner Now-Website überprüft wird, ob der Kunde schon einmal eine Bestellung bei einem Restaurant aufgegeben hat. Wenn dies zutrifft, wird der Kunde aufgefordert, eine Kritik zu erstellen, die an das Restaurant gesendet und auf der Website veröffentlicht wird:

 ![UML-Sequenzdiagramm](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **UML-Sequenzdiagramm**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Halten Sie Code mit dem Design konsistent
 Dinner Now muss sicherstellen, dass der aktualisierte Code konsistent mit dem Entwurf bleibt. Es werden Ebenendiagramme erstellt, die die Funktionsebenen im System beschreiben, die erlaubten Abhängigkeiten zwischen ihnen angeben und diesen Ebenen Lösungsartefakte zuordnen.

|**Diagramm**|**Beschreibt**|
|-----------------|-------------------|
|*Ebenendiagramm*<br /><br /> Siehe:<br /><br /> -   [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer-Diagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Layer-Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|Die logische Architektur des Codes<br /><br /> Mit einem Ebenendiagramm werden die Artefakte in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projektmappe organisiert und abstrakten Gruppen, genannt *Ebenen*, zugeordnet. Diese Ebenen identifizieren die Rollen, Aufgaben oder Funktionen, die diese Artefakte im System spielen.<br /><br /> Ebenendiagramme sind hilfreich, um den beabsichtigten Entwurf des Systems zu beschreiben und in der Entwicklung befindlichen Code anhand des Entwurfs zu validieren.<br /><br /> Um Ebenen zu erstellen, ziehen Sie Elemente aus dem Projektmappen-Explorer, Code Maps, der Klassenansicht und dem Objektkatalog. Verwenden Sie die Toolbox, oder klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, um neue Ebenen zu zeichnen.<br /><br /> Um vorhandene Abhängigkeiten anzuzeigen, klicken Sie mit der rechten Maustaste auf die Ebenendiagrammoberfläche, und klicken Sie dann auf **Abhängigkeiten generieren**. Um beabsichtigte Abhängigkeiten anzugeben, zeichnen Sie neue Abhängigkeiten.|

 Das folgende Ebenendiagramm beschreibt z. B. Abhängigkeiten zwischen Ebenen sowie die Anzahl der Artefakte, die jeder Ebene zugeordnet sind:

 ![Ebenendiagramm für integriertes Zahlungssystem](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Layer-Diagramm**

 Um sicherzustellen, dass während der Codeentwicklung keine Konflikte mit dem Entwurf auftreten, verwenden die Teams Ebenenvalidierung in Builds, die unter Team Foundation Build ausgeführt werden. Außerdem erstellen sie eine benutzerdefinierte MSBuild-Aufgabe, um Ebenenvalidierung bei den Eincheckvorgängen zu erfordern. Mithilfe von Buildberichten werden Validierungsfehler erfasst.

 Siehe:

- [Definieren des Buildprozesses](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Verwenden eines abgegrenzten Eincheckbuildprozesses zur Überprüfung von Änderungen](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Anpassen der Buildprozessvorlage](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Allgemeine Tipps zum Erstellen und Verwenden von Modellen

- Die meisten Diagramme bestehen aus Knoten, die durch Linien verbunden sind. Für jeden Diagrammtyp stellt die Toolbox verschiedene Arten von Knoten und Linien bereit.

   Zum Öffnen der Toolbox klicken Sie im Menü **Ansicht** auf **Toolbox**.

- Um einen Knoten zu erstellen, ziehen Sie ihn von der Toolbox in das Diagramm. Bestimmte Arten von Knoten müssen auf vorhandene Knoten gezogen werden. In einem Komponentendiagramm muss einer vorhandenen Komponente z. B. ein neuer Port hinzugefügt werden.

- Um eine Linie oder Verbindung zu erstellen, klicken Sie in der Toolbox auf das entsprechende Tool, klicken Sie auf den Quellknoten und dann auf den Zielknoten. Einige Linien können nur zwischen bestimmten Arten von Knoten erstellt werden. Wenn Sie den Mauszeiger über mögliche Quellen oder Ziele bewegen, wird angezeigt, ob Sie eine Verbindung erstellen können.

- Wenn Sie Elemente in UML-Diagrammen erstellen, werden diese auch einem allgemeinen Modell hinzugefügt. Die UML-Diagramme in einem Modellierungsprojekt sind Ansichten dieses Modells. Elemente in einem Ebenendiagramm sind Teil des Modellierungsprojekts, obwohl sie nicht im allgemeinen Modell gespeichert werden.

   Um das Modell anzuzeigen, zeigen Sie im Menü **Architektur** auf  **Fenster**, und klicken Sie dann auf **UML-Modell-Explorer**.

- In einigen Fällen können Sie bestimmte Elemente aus dem **UML-Modell-Explorer** in ein UML-Diagramm ziehen. Einige Elemente innerhalb des gleichen Modells können in verschiedenen Diagrammen verwendet werden, um alternative Ansichten der Architektur anzuzeigen. Sie können z. B. eine Komponente in ein anderes Komponentendiagramm oder ein Sequenzdiagramm ziehen, um sie als Akteur zu verwenden.

- Visual Studio unterstützt UML 2.1.2. In dieser Übersicht werden nur die Hauptfunktionen der UML-Diagramme in dieser Version beschrieben. Es gibt jedoch viele Bücher, die UML und dessen Verwendung im Detail behandeln.

  Weitere Informationen finden Sie unter [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md).

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>Planungs- und Nachverfolgungsarbeiten
 Visual Studio-Modellierungsdiagramme sind in Team Foundation Server integriert, sodass Sie Arbeit leichter planen, verwalten und nachverfolgen können. Beide Teams verwenden Modelle, um Testfälle und Entwicklungsaufgaben zu identifizieren und ihre Arbeit einzuschätzen. Lucerne erstellt und verknüpft Team Foundation Server-Arbeitselemente mit Modellelementen, wie z. B. Anwendungsfälle oder Komponenten. Auf diese Weise kann der Status überwacht werden, und die Arbeit kann bis zu den Benutzeranforderungen zurückverfolgt werden. Somit wird sichergestellt, dass die Änderungen stets den Anforderungen entsprechen.

 Im Verlauf ihrer Arbeit aktualisieren die Teams die Arbeitselemente, um die Zeit zu berücksichtigen, die sie mit ihren Aufgaben verbracht haben. Außerdem wird eine Überwachung und Berichterstellung des Status der Arbeit mithilfe der folgenden Team Foundation Server-Funktionen durchgeführt:

- Tägliche *Burndownberichte* , die angeben, ob die geplante Arbeit in der erwarteten Zeit angeschlossen wird. Es werden andere ähnliche Berichte in Team Foundation Server generiert, um den Status von Fehlern zu verfolgen.

- Ein *Iterationsarbeitsblatt* , das Microsoft Excel verwendet, mit dem das Team die Arbeitsauslastung überwachen und zwischen den Mitgliedern ausgleichen kann. Dieses Arbeitsblatt ist mit Team Foundation Server verknüpft und bietet eine Diskussionsbasis bei den regelmäßigen Statusbesprechungen.

- Ein *Entwicklungsdashboard* , das Office Project verwendet, um das Team mit wichtigen Projektinformationen auf dem neuesten Stand zu halten.

  Siehe:

- [Nachverfolgen von Arbeit mit Visual Studio Team Services oder Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Verknüpfen von Modellelementen und Arbeitselementen](../modeling/link-model-elements-and-work-items.md)

- [Diagramme, Dashboards und Berichte für Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Erstellen von Backlog und Aufgaben mit Project](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a> Testen, Überprüfen und Einchecken von Code
 Beim Abschließen der einzelnen Aufgaben wird der Code von den Teams in der Team Foundation-Versionskontrolle eingecheckt. Wird dies vergessen, werden von Team Foundation Server entsprechende Erinnerungen angezeigt. Bevor Team Foundation Server das Einchecken akzeptiert, führen die Teams Komponententests und Ebenenvalidierung aus, um den Code anhand der Testfälle und des Entwurfs zu überprüfen. Mit Team Foundation Server werden regelmäßig Builds, automatisierte Komponententests und eine Ebenenvalidierung ausgeführt. Dadurch wird sichergestellt, dass der Code die folgenden Kriterien erfüllt:

- Er funktioniert.

- Bereits funktionierender Code wird dadurch nicht beeinträchtigt.

- Er steht nicht in Konflikt mit dem Entwurf.

  Dinner Now verfügt über eine große Auflistung automatisierter Tests, die Lucerne wiederverwenden kann, da fast alle weiterhin gültig sind. Lucerne kann außerdem auf diesen Tests aufbauen und neue hinzufügen, um neue Funktionen abzudecken. Beide verwenden auch Visual Studio, um manuelle Tests auszuführen.

  Um sicherzustellen, dass der Code dem Entwurf entspricht, konfigurieren die Teams ihre Builds zum Einbinden der Ebenenvalidierung in Team Foundation Build. Wenn Konflikte auftreten, wird ein Bericht mit den Details generiert.

  Siehe:

- [Testen der Anwendung](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)

- [Verwenden von Versionskontrolle](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Erstellen der Anwendung](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Aktualisieren des Systems mithilfe von Visualisierung und Modellierung
 Lucerne und Dinner Now müssen ihre Zahlungssysteme integrieren. Die folgenden Abschnitte zeigen die Modellierungsdiagramme in Visual Studio, die beim Ausführen dieser Aufgabe helfen:

- [Verstehen der Benutzeranforderungen: Anwendungsfalldiagramme](#UnderstandUseCases)

- [Verstehen des Geschäftsprozesses: Aktivitätsdiagramme](#UnderstandActivities)

- [Beschreiben der Systemstruktur: Komponentendiagramme](#DescribeComponents)

- [Beschreiben der Interaktionen: Sequenzdiagramme](#DescribeSequence)

- [Visualisieren von vorhandenem Code: Code Maps](#VisualizeCode)

- [Definieren eines Glossars von Typen: Klassendiagramme](#DefineClasses)

- [Beschreiben der logischen Architektur: Ebenendiagramme](#DescribeLayers)

  Siehe:

- [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)

- [Visualisieren von Code](../modeling/visualize-code.md)

- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

- [Modellieren von Benutzeranforderungen](../modeling/model-user-requirements.md)

- [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>Verstehen der Benutzeranforderungen: Anwendungsfalldiagramme
 Anwendungsfalldiagramme fassen zusammen, welche Aktivitäten ein System unterstützt und von wem diese ausgeführt werden. Lucerne verwendet ein Anwendungsfalldiagramm, um die folgenden Informationen über das Dinner Now-System zu erhalten:

- Kunden geben Bestellungen auf.

- Restaurants empfangen Bestellungen.

- Das externe Zahlungsverarbeitungsgateway, das vom Dinner Now-Zahlungssystem zum Überprüfen von Zahlungen verwendet wird, liegt außerhalb des Projektumfangs der Website.

  Das Diagramm zeigt auch, wie einige der Hauptanwendungsfälle in kleinere Anwendungsfälle unterteilt sind. Lucerne möchte sein eigenes Zahlungssystem verwenden. Der Anwendungsfall "Process Payment" (Zahlung verarbeiten) wird in einer anderen Farbe hervorgehoben, um auf erforderliche Änderungen hinzuweisen:

  ![Hervorheben von "Process Payment" (Zahlung verarbeiten) im Anwendungsfalldiagramm](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Hervorheben von "Process Payment" (Zahlung verarbeiten) im Anwendungsfalldiagramm**

  Wenn die Entwicklungszeit knapp wäre, könnte das Team erwägen, dass Kunden die Restaurants direkt bezahlen. Um dies zu verdeutlichen, würden sie den Anwendungsfall "Process Payment" (Zahlung verarbeiten) durch einen Anwendungsfall außerhalb der Dinner Now-Systemgrenze ersetzen. Anschließend würde der Kunde direkt mit dem Restaurant verknüpft, um anzugeben, dass Dinner Now nur die Bestellungen verarbeitet:

  ![Neudefinition des Projektumfangs zum Bezahlen der Restaurants im Anwendungsfalldiagramm](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Neudefinition des Projektumfangs zum Bezahlen der Restaurants im Anwendungsfalldiagramm**

  Siehe:

- [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)

- [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Zeichnen eines Anwendungsfalldiagramms
 Ein Anwendungsfalldiagramm umfasst die folgenden Hauptfunktionen:

- *Akteure* stellen Rollen dar, die Personen, Organisationen, Maschinen oder Softwaresysteme spielen. Bespielsweise sind Kunde, Restaurant und das Dinner Now-Zahlungssystem Akteure.

- *Anwendungsfälle* stellen Interaktionen zwischen Akteuren und dem System in der Entwicklung dar.  Sie können eine beliebige Skala der Interaktion von einem einzelnen Mausklick oder einer Meldung bis hin zu einer mehrtägigen Transaktion darstellen.

- *Zuordnungen* verknüpfen Akteure mit Anwendungsfällen.

- Ein größerer Anwendungsfall kann kleinere *einschließen* , z. B. ist "Select Restaurant" (Restaurant auswählen) in "Create Order" (Bestellung aufgeben) enthalten. Sie können einen Anwendungsfall *erweitern* . Einem erweiterten Anwendungsfall werden Ziele und Schritte hinzugefügt, um anzugeben, dass der Anwendungsfall nur unter bestimmten Bedingungen auftritt. Anwendungsfälle können auch voneinander erben.

- Ein *Subsystem* stellt das Softwaresystem dar, das sich in der Entwicklung befindet, oder eine seiner Komponenten. Dabei handelt es sich um ein großes Feld, das Anwendungsfälle enthält. Ein Anwendungsfalldiagramm klärt ab, was sich innerhalb oder außerhalb der Subsystemgrenze befindet. Um anzugeben, dass der Benutzer bestimmte Ziele auf andere Weise erreichen muss, zeichnen Sie diese Anwendungsfälle außerhalb der Subsystemgrenze.

- *Artefakte* verknüpfen Elemente im Diagramm mit anderen Diagrammen oder Dokumenten.

  Siehe:

- [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)

- [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Zusammenfassung: Vorteile von Anwendungsfalldiagrammen
 Mit Anwendungsfalldiagrammen können Sie Folgendes visualisieren:

- Die Aktivitäten, die ein System unterstützt bzw. nicht unterstützt

- Die Personen und externen Systeme, von denen diese Aktivitäten ausgeführt werden

- Die Hauptkomponenten des Systems, die die einzelnen Aktivitäten unterstützen und die Sie als im übergeordneten System geschachtelte Subsysteme darstellen können

- Wie ein Anwendungsfall in kleinere Anwendungsfälle oder Variationen unterteilt sein kann

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibt**|
|-----------------|-------------------|
|Aktivitätsdiagramm|Der Ablauf von Schritten in einem Anwendungsfall und die Personen, die diese Schritte in diesem Anwendungsfall ausführen.<br /><br /> Die Namen von Anwendungsfällen spiegeln häufig die Schritte in einem Aktivitätsdiagramm wider. Aktivitätsdiagramme unterstützen Elemente wie z. B. Entscheidungen, Zusammenführungen, Eingaben und Ausgaben, gleichzeitige Abläufe usw.<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|
|Sequenzdiagramm|Die Reihenfolge der Interaktionen zwischen den Teilnehmern in einem Anwendungsfall.<br /><br /> Siehe:<br /><br /> -   [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)|
|Klassendiagramm (UML)|Die am Anwendungsfall beteiligten Entitäten oder Typen.<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>Verstehen des Geschäftsprozesses: Aktivitätsdiagramme
 Aktivitätsdiagramme beschreiben den Ablauf von Schritten in einem Geschäftsprozess und bieten eine einfache Möglichkeit, den Workflow zu kommunizieren. Ein Entwicklungsprojekt kann mehrere Aktivitätsdiagramme umfassen. Normalerweise umfasst eine Aktivität alle Aktionen, die sich aus einer externen Aktion ergeben, wie z. B. das Bestellen einer Mahlzeit, das Aktualisieren eines Menüs oder das Hinzufügen eines neuen Restaurants zum Geschäft. Eine Aktivität kann auch die Details einer komplexen Aktion beschreiben.

 Lucerne aktualisiert das folgende Aktivitätsdiagramm, um zu zeigen, dass Lucerne die Zahlung verarbeitet und das Restaurant bezahlt. Das Dinner Now-Zahlungssystem wird durch das Lucerne-Zahlungssystem ersetzt, wie hervorgehoben wird:

 ![Lucerne-Zahlungssystem in Aktivitätsdiagramm](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Ersetzen des Dinner Now-Zahlungssystems im Aktivitätsdiagramm**

 Mit dem aktualisierten Diagramm können Lucerne und Dinner Now darstellen, an welcher Stelle das Zahlungssystem von Lucerne in den Geschäftsprozess passt. In dieser Version werden Kommentare zum Identifizieren der Rollen verwendet, die die Schritte ausführen. Mithilfe von Linien werden *Verantwortlichkeitsbereiche*erstellt, mit denen die Schritte nach Rolle organisiert werden.

 Die Teams könnten auch einen alternativen Textabschnitt in Erwägung ziehen, bei dem der Kunde das  Restaurant bezahlt, nachdem die Bestellung geliefert wurde. Dies würde zu anderen Anforderungen an das Softwaresystem führen.

 Zuvor hat Dinner Now diese Diagramme auf ein Whiteboard oder in PowerPoint gezeichnet. Jetzt werden diese Diagramme auch mit Visual Studio gezeichnet, sodass beide Teams die Details erfassen, verstehen und verwalten können.

 Siehe:

- [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)

- [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Zeichnen eines Aktivitätsdiagramms
 Ein Aktivitätsdiagramm umfasst die folgenden Hauptfunktionen:

- Einen *Startknoten* , der die erste Aktion der Aktivität angibt.

   Das Diagramm sollte immer einen dieser Knoten enthalten.

- *Aktionen* , die Schritte beschreiben, bei denen der Benutzer oder die Software eine Aufgabe ausführt.

- *Kontrollflüsse* , die den Ablauf zwischen Aktionen anzeigen.

- *Entscheidungsknoten* , die bedingte Verzweigungen im Ablauf darstellen.

- *Gabelungsknoten* , die einzelne Abläufe in gleichzeitige Abläufe teilen.

- *Aktivitätsendknoten* , die Enden der Aktivität anzeigen.

   Obwohl diese Knoten optional sind, ist deren Aufnahme in das Diagramm nützlich, um zu verdeutlichen, wo die Aktivität endet.

  Siehe:

- [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)

- [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Zusammenfassung: Vorteile von Aktivitätsdiagrammen
 Mit Aktivitätsdiagrammen können Sie den Steuerungsablauf und die Informationen zwischen den Aktionen eines Geschäfts, Systems oder Programms visuell darstellen und beschreiben. Dabei handelt es sich um eine einfache und hilfreiche Möglichkeit, anderen Personen den Workflow zu erläutern.

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-----------------|---------------------|
|Anwendungsfalldiagramm|Fassen Sie die Aktivitäten zusammen, die jeder Akteur ausführt.<br /><br /> Siehe:<br /><br /> -   [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|
|Komponentendiagramm|Visualisieren Sie das System als Auflistung von wiederverwendbaren Komponenten, die durch einen genau definierten Satz von Schnittstellen Verhaltensweisen bereitstellen oder nutzen.<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>Beschreiben der Systemstruktur: Komponentendiagramme
 Komponentendiagramme beschreiben ein System als Auflistung trennbarer Komponenten, die durch einen genau definierten Satz von Schnittstellen Verhaltensweisen bereitstellen oder nutzen. Die Komponenten können einen beliebigen Umfang aufweisen und auf beliebige Art miteinander verbunden sein.

 Damit Lucerne und Dinner Now die Komponenten und Schnittstellen des Systems leichter visualisieren und besprechen können, werden die folgenden Komponentendiagramme erstellt:

 ![Externe Komponenten im Zahlungssystem](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Komponenten des Zahlungssystems von Dinner Now**

 Dieses Diagramm zeigt verschiedene Komponententypen und ihre *Abhängigkeiten*. Sowohl die Dinner Now-Website als auch das Zahlungssystem von Lucerne erfordern z. B. das externe Zahlungsverarbeitungsgateway zum Überprüfen von Zahlungen. Die Pfeile zwischen Komponenten stellen die Abhängigkeiten dar, mit denen angegeben wird, welche Komponenten die Funktionen anderer Komponenten erfordern.

 Um das Zahlungssystem von Lucerne zu verwenden, muss die Dinner Now-Website für die Verwendung der Schnittstellen "PaymentApproval" und "PayableInsertion" des Zahlungssystems von Lucerne aktualisiert werden.

 Das folgende Diagramm zeigt eine spezielle Konfiguration der Komponenten für die Dinner Now-Website. Diese Konfiguration gibt an, dass jede Instanz der Website aus vier *Teilen*besteht:

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  Diese Teile sind Instanzen der angegebenen Komponententypen und sind wie folgt verbunden:

  ![Komponenten innerhalb der Dinner Now-Website](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Komponenten innerhalb der Dinner Now-Website**

  Die Dinner Now-Website delegiert sein Verhalten an diese Teile, die die Funktionen der Website behandeln. Die Pfeile zwischen der übergeordneten Komponente und ihren Mitgliedskomponenten weisen auf *Delegierungen* hin, mit denen angegeben wird, welche Teile die Nachricht behandeln, die das übergeordnete Element über die Schnittstellen empfängt oder sendet.

  In dieser Konfiguration werden die Kundenzahlungen von der PaymentProcessing-Komponente verarbeitet. Daher muss sie für die Integration mit dem Zahlungssystem von Lucerne aktualisiert werden. In anderen Szenarien können mehrere Instanzen eines Komponententyps in derselben übergeordneten Komponente vorhanden sein.

  Siehe:

- [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)

- [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Zeichnen eines Komponentendiagramms
 Ein Komponentendiagramm umfasst die folgenden Hauptfunktionen:

- *Komponenten* , die trennbare Stücke der Systemfunktionalität darstellen.

- *Bereitgestellte Schnittstellenports* , die Gruppen von Nachrichten oder Aufrufen darstellen, die von Komponenten implementiert und von anderen Komponenten oder externen Systemen verwendet werden.

- *Erforderliche Schnittstellenports* , die Gruppen von Nachrichten oder Aufrufen darstellen, die von Komponenten an andere Komponenten oder externe Systeme gesendet werden. Diese Art von Port beschreibt die Vorgänge, die eine Komponente von anderen Komponenten oder externen Systemen mindestens erwartet.

- *Teile* sind Elemente von Komponenten und üblicherweise Instanzen anderer Komponenten. Ein Teil ist ein Stück des internen Entwurfs der übergeordneten Komponente.

- *Abhängigkeiten* , die angeben, dass Komponenten die Funktionalität anderer Komponenten erfordern.

- *Delegierungen* , die angeben, dass Teile einer Komponente Nachrichten behandeln, die von der übergeordneten Komponente gesendet oder empfangen werden.

  Siehe:

- [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)

- [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Zusammenfassung: Vorteile von Komponentendiagrammen
 Mit Komponentendiagramme können Sie Folgendes visualisieren:

- Das System als Auflistung trennbarer Teile, unabhängig von ihrer Implementierungssprache oder ihres Formats.

- Komponenten mit genau definierten Schnittstellen, um den Entwurf leichter verstehen und aktualisieren zu können, wenn sich die Anforderungen ändern.

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-----------------|---------------------|
|Code Map|Visualisieren Sie die Organisation und Beziehungen in vorhandenem Code.<br /><br /> Um Kandidaten für Komponenten zu identifizieren, erstellen Sie eine Code Map, und gruppieren Sie Elemente nach ihrer Funktion im System.<br /><br /> Siehe:<br /><br /> -   [Zuordnen von Abhängigkeiten in Ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)|
|Sequenzdiagramm|Visualisieren Sie die Sequenz der Interaktionen zwischen Komponenten oder den Teilen innerhalb einer Komponente.<br /><br /> Um aus einer Komponente eine Lebenslinie in einem Sequenzdiagramm zu erstellen, klicken Sie mit der rechten Maustaste auf die Komponente, und klicken Sie dann auf **Lebenslinie erstellen**.<br /><br /> Siehe:<br /><br /> -   [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)|
|Klassendiagramm (UML)|Definieren Sie die Schnittstellen an den bereitgestellten oder angeforderten Ports sowie die Klassen, die die Funktionalität der Komponenten implementieren.<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|
|Ebenendiagramm|Beschreiben Sie die logische Architektur des Systems in Bezug auf die Komponenten. Stellen Sie durch Ebenenvalidierung sicher, dass der Code konsistent mit dem Entwurf bleibt.<br /><br /> Siehe:<br /><br /> -   [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer-Diagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Layer-Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|
|Aktivitätsdiagramm|Visualisieren Sie die interne Verarbeitung, die Komponenten als Reaktion auf eingehende Nachrichten durchführen.<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Visualisieren vorhandener Code: Codezuordnungen
 Code Maps zeigen die aktuelle Organisation und die Beziehungen im Code. Elemente werden auf der Code Map durch *Knoten* und Beziehungen durch *Links*dargestellt. Mit Code Maps können Sie die folgenden Arten von Aufgaben ausführen:

- Untersuchen von unbekanntem Code

- Verstehen, wo und wie sich eine vorgeschlagene Änderung auf vorhandenen Code auswirken könnte

- Auffinden von Bereichen mit Komplexität, natürlichen Ebenen oder Mustern sowie anderen Bereichen, die von Verbesserungen profitieren könnten

  Dinner Now muss z. B. die Kosten für die Aktualisierung der PaymentProcessing-Komponente schätzen. Diese hängen teilweise davon ab, wie sehr sich diese Änderung auf andere Teile des Systems auswirkt. Zur Verdeutlichung erstellt einer der Dinner Now-Entwickler Code Maps aus dem Code und richtet den Fokus des Projektumfangs auf die Bereiche aus, die durch die Änderung betroffen sein könnten.

  Die folgende Code Map zeigt die Abhängigkeiten zwischen der PaymentProcessing-Klasse und anderen Teilen des Dinner Now-Systems, die markiert dargestellt werden:

  ![Abhängigkeitsdiagramm für das Zahlungssystem von Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Code Map für das Zahlungssystem von Dinner Now**

  Der Entwickler untersucht die Code Map, indem er die PaymentProcessing-Klasse erweitert und die zugehörigen Member auswählt, um die potenziell betroffenen Bereiche anzuzeigen:

  ![Methoden in der PaymentProcessing-Klasse und ihre Abhängigkeiten](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Methoden in der PaymentProcessing-Klasse und ihre Abhängigkeiten**

  Für das Zahlungssystem von Lucerne wird die folgende Code Map generiert, um die zugehörigen Klassen, Methoden und Abhängigkeiten zu untersuchen. Das Team erkennt, dass das Lucerne-System auch Arbeit erfordern könnte, damit es mit anderen Teilen von Dinner Now interagieren kann:

  ![Abhängigkeitsdiagramm für das Zahlungssystem von Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Code Map für das Zahlungssystem von Lucerne**

  Beide Teams arbeiten zusammen, um die Änderungen zu ermitteln, die zum Integrieren der beiden Systeme erforderlich sind. Es wird entschieden, einen Teil des Codes umzugestalten, damit er einfacher zu aktualisieren ist. Die PaymentApprover-Klasse wird in den DinnerNow.Business-Namespace verschoben und erfordert einige neue Methoden. Die Dinner Now-Klassen, die Transaktionen behandeln, erhalten einen eigenen Namespace. Die Teams erstellen und verwenden Arbeitselemente, um ihre Arbeit zu planen, zu organisieren und nachzuverfolgen. Wo sinnvoll, werden Arbeitselemente mit Modellelementen verknüpft.

  Nach der Neuorganisation des Codes generieren die Teams eine neue Code Map, um die aktualisierte Struktur und die Beziehungen anzuzeigen:

  ![Abhängigkeitsdiagramm mit neu organisiertem Code](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Code Map mit neu organisiertem Code**

  Diese Code Map zeigt, dass sich die PaymentApprover-Klasse jetzt im DinnerNow.Business-Namespace befindet und über ein paar neue Methoden verfügt. Die Dinner Now-Transaktionsklassen verfügen jetzt über einen eigenen PaymentSystem-Namespace, mit dem der Code später leichter behandelt werden kann.

#### <a name="creating-a-code-map"></a>Erstellen einer Code Map

- Folgen Sie den folgenden Schritten zum Generieren einer Code Map, um eine schnelle Übersicht über Quellcode zu erhalten:

     Klicken Sie im Menü **Architektur** auf **Code Map für Projektmappe generieren**.

     Erstellen Sie für eine schnelle Übersicht über kompilierten Code eine leere Code Map, und ziehen Sie dann Assemblydateien oder Binärdateien auf die Oberfläche der Code Map.

- Um bestimmte Code- oder Projektmappenelemente zu untersuchen, wählen Sie im Projektmappen-Explorer die Elemente und Beziehungen aus, die Sie visualisieren möchten. Sie können dann entweder eine neue Code Map generieren oder einer vorhandenen Code Map ausgewählte Elemente hinzufügen. Siehe [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Um die Code Map einfacher zu untersuchen, können Sie das Layout den auszuführenden Aufgaben entsprechend neu anordnen.

     Wählen Sie beispielsweise ein Strukturlayout aus, um die Ebenen im Code zu visualisieren. Siehe [Durchsuchen und Neuanordnen von Codezuordnungen](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Zusammenfassung: Vorteile von Code Maps
 Mit Code Maps können Sie Folgendes durchführen:

- Verdeutlichen der Organisation und Beziehungen in vorhandenem Code

- Identifizieren der Bereiche, die von einer vorgeschlagenen Änderung betroffen sein könnten

- Auffinden von Bereichen mit Komplexität, Mustern oder Ebenen sowie andere Bereichen, die Sie optimieren könnten, um den Code leichter verwalten, ändern und wiederverwenden zu können

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibt**|
|-----------------|-------------------|
|Ebenendiagramm|Die logische Architektur des Systems Stellen Sie durch Ebenenvalidierung sicher, dass der Code konsistent mit dem Entwurf bleibt.<br /><br /> Erstellen Sie eine Code Map, und gruppieren Sie zugehörige Elemente, um vorhandene oder beabsichtigte Ebenen besser identifizieren zu können. Informationen zum Erstellen eines Ebenendiagramms finden Sie unter:<br /><br /> -   [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer-Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)|
|Komponentendiagramm|Komponenten, ihre Schnittstellen und ihre Beziehungen<br /><br /> Um Komponenten zu identifizieren, erstellen Sie eine Code Map, und gruppieren Sie Elemente nach ihrer Funktion im System.<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|
|Klassendiagramm (UML)|Klassen, ihre Attribute und Vorgänge und ihre Beziehungen<br /><br /> Um diese Elemente leichter zu identifizieren, erstellen Sie ein UML-Klassendiagramm, das die betreffenden Elemente zeigt.<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|
|Klassendiagramm (codebasiert)|Vorhandene Klassen in Code für ein bestimmtes Projekt<br /><br /> Verwenden Sie den Klassen-Designer, um eine vorhandene Klasse in Code zu visualisieren und zu ändern.<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>Beschreiben der Interaktionen: Sequenzdiagramme
 Sequenzdiagramme beschreiben eine Reihe von Interaktionen zwischen Teilen eines Systems. Die Teile können beliebig skaliert sein. Sie können z. B. von einzelnen Objekten in einem Programm bis hin zu großen Subsystemen oder externen Akteuren reichen. Skala und Typ der Interaktionen können beliebig sein. Sie können z. B. von einzelnen Nachrichten bis hin zu erweiterten Transaktionen reichen, und es kann sich um Funktionsaufrufe oder Webdienstmeldungen handeln.

 Um die Schritte im Anwendungsfall "Process Payment" (Zahlung verarbeiten) besser besprechen und erläutern zu können, erstellen Lucerne und Dinner Now das folgende Sequenzdiagramm aus dem Komponentendiagramm. Die Lebenslinien spiegeln die Dinner Now-Websitekomponente und seine Teile wider. Die Meldungen, die zwischen Lebenslinien auftreten, folgen den Verbindungen in den Komponentendiagrammen:

 ![Sequenzdiagramm für den Anwendungsfall "Process Payment" (Zahlung verarbeiten)](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Sequenzdiagramm für den Anwendungsfall "Process Payment" (Zahlung verarbeiten)**

 Das Sequenzdiagramm zeigt, dass die Dinner Now-Website "ProcessOrder" in einer Instanz von "OrderProcessing" aufruft, wenn der Kunde eine Bestellung aufgibt. Anschließend wird "ProcessPayment" in "PaymentProcessing" von "OrderProcessing" aufgerufen. Dies wird fortgeführt, bis die Zahlung vom externen Zahlungsverarbeitungsgateway überprüft wird. Erst dann wird die Kontrolle an die Dinner Now-Website zurückgegeben.

 Lucerne muss die Kosten für die Integration ihres Zahlungssystem in das Dinner Now-System schätzen. Zur Verdeutlichung können die Entwickler auch Code Maps erstellen, um den betroffenen Code zu visualisieren.

 Siehe:

- [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)

- [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Zeichnen eines Sequenzdiagramms
 Ein Sequenzdiagramm umfasst die folgenden Hauptfunktionen:

- Vertikale *Lebenslinien* stellen Akteure oder Instanzen von Softwareobjekten dar.

   Klicken Sie auf die Lebenslinie, um ein Akteursymbol hinzuzufügen, mit dem angegeben wird, dass sich ein Teilnehmer außerhalb des Systems in der Entwicklung befindet. Legen Sie im Fenster **Eigenschaftenfenster** die Option **Akteur** auf **Wahr**fest. Wenn das Fenster **Eigenschaften** nicht angezeigt wird, drücken Sie **F4**.

- Horizontale *Meldungen* stellen Methodenaufrufe, Webdienstmeldungen oder eine andere Kommunikationsarten dar. *Vorkommnisausführungen* sind vertikal schraffierte Rechtecke, die auf Lebenslinien angezeigt werden und die Zeiträume darstellen, in denen Objektprozessaufrufe empfangen werden.

- Während einer *synchronen* Nachricht wartet das Absenderobjekt \<darauf, dass die Steuerung>> wie bei einem regulären Funktionsaufruf zurückgegeben <. Bei einer *asynchronen* Meldung kann der Absender unmittelbar fortfahren.

- Verwenden \<Sie <>> Nachrichten erstellen, um die Konstruktion von Objekten durch andere Objekte anzuzeigen. Dies sollte die erste an das Objekt gesendete Meldung sein.

  Siehe:

- [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)

- [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Zusammenfassung: Vorteile von Sequenzdiagrammen
 Mit Sequenzdiagrammen können Sie Folgendes visualisieren:

- Der Kontrollfluss, der während der Ausführung eines Anwendungsfalls zwischen Akteuren oder Objekten übertragen wird.

- Die Implementierung eines Methodenaufrufs oder einer Meldung

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-----------------|---------------------|
|Klassendiagramm (UML)|Definieren Sie die Klassen, die Lebenslinien darstellen, sowie die Parameter und Rückgabewerte, die in zwischen Lebenslinien gesendeten Meldungen verwendet werden.<br /><br /> Um eine Klasse aus einer Lebenslinie zu erstellen, klicken Sie mit der rechten Maustaste auf die Lebenslinie, und klicken Sie dann auf **Klasse erstellen** oder **Schnittstelle erstellen**. Um eine Lebenslinie aus einem Typ in einem Klassendiagramm zu erstellen, klicken Sie mit der rechten Maustaste auf den Typ, und klicken Sie dann auf **Lebenslinie erstellen**erstellen.<br /><br /> Siehe:<br /><br /> -   [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)<br />-   [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)|
|Komponentendiagramm|Beschreiben Sie die Komponenten, die Lebenslinien darstellen, sowie die Schnittstellen, die das von Meldungen dargestellte Verhalten bereitstellen und nutzen.<br /><br /> Um eine Lebenslinie aus einem Komponentendiagramm zu erstellen, klicken Sie mit der rechten Maustaste auf die Komponente, und klicken Sie dann auf **Lebenslinie erstellen**.<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|
|Anwendungsfalldiagramm|Fassen Sie die Interaktionen zwischen Benutzern und Komponenten in einem Sequenzdiagramm als Anwendungsfall zusammen, der das Ziel eines Benutzers darstellt.<br /><br /> Siehe:<br /><br /> -   [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Definieren eines Glossars der Typen: Klassendiagramme
 Klassendiagramme definieren die am System beteiligten Entitäten, Begriffe oder Konzepte sowie ihre Beziehungen untereinander. Beispielsweise können Sie diese Diagramme während der Entwicklung verwenden, um die Attribute und Vorgänge für jede Klasse unabhängig von Implementierungssprache oder Format zu beschreiben.

 Um die am Anwendungsfall "Process Payment" (Zahlung verarbeiten) beteiligten Entitäten zu erläutern und zu besprechen, zeichnet Lucerne das folgende Klassendiagramm:

 ![Process Payment-Entitäten in einem Klassendiagramm](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Process Payment-Entitäten in einem Klassendiagramm**

 Dieses Diagramm zeigt, dass ein Kunde über viele Bestellungen und verschiedene Methoden zum Bezahlen der Bestellungen verfügen kann. "BankAccount" und "CreditCard" erben beide von "Payment".

 Während der Entwicklung verwendet Lucerne das folgende Klassendiagramm, um die Details der einzelnen Klassen zu beschreiben und zu besprechen:

 ![Process Payment-Entitätsdetails in einem Klassendiagramm](../modeling/media/uml-payment.png "UML_Payment")

 **Process Payment-Details im Klassendiagramm**

 Siehe:

- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)

- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Zeichnen eines Klassendiagramms
 Ein Klassendiagramm umfasst die folgenden Hauptfunktionen:

- Typen wie z. B. Klassen, Schnittstellen und Enumerationen:

  - Eine *Klasse* ist die Definition von Objekten, die gemeinsame strukturelle Merkmale oder Verhaltensmerkmale aufweisen.

  - Eine *Schnittstelle* definiert einen Teil des extern sichtbaren Verhaltens eines Objekts.

  - Eine *Enumeration* ist eine Klassifizierung, die eine Liste von literalen Werten enthält.

- *Attribute* sind Werte eines bestimmten Typs, der die einzelnen Instanzen einer *Klassifizierung*beschreiben. Eine Klassifizierung ist ein allgemeiner Name für Typen, Komponenten, Anwendungsfälle und sogar Akteure.

- *Vorgänge* sind Methoden oder Funktionen, die Instanzen einer Klassifizierung ausführen können.

- Eine *Zuordnung* gibt eine Art von Beziehung zwischen zwei Klassifizierern an.

  - Eine *Aggregation* ist eine Zuordnung, die einen gemeinsamen Besitz zwischen Klassifizierungen angibt.

  - Eine *Komposition* ist eine Zuordnung, die eine ganzteilige Beziehung zwischen Klassifizierungen angibt.

    Um Aggregationen oder Kompositionen anzuzeigen, legen Sie die Eigenschaft **Aggregation** für eine Zuordnung fest. Mit**Freigegeben** werden Aggregationen und mit **Verbund** werden Kompositionen angezeigt.

- Eine *Abhängigkeit* gibt an, dass durch Änderungen an der Definition einer Klassifizierung möglicherweise auch die Definition einer anderen Klassifizierung geändert wird.

- Eine *Generalisierung* gibt an, dass eine bestimmte Klassifizierung einen Teil ihrer Definition von einer allgemeinen Klassifizierung erbt. Eine *Realisierung* gibt an, dass eine Klasse die Vorgänge und Attribute implementiert, die von einer Schnittstelle bereitgestellt werden.

   Verwenden Sie das Tool **Vererbung** , um diese Beziehungen zu erstellen. Alternativ kann eine Realisierung als *Lollipop*dargestellt werden.

- *Pakete* sind Gruppen von Klassifizierern, Zuordnungen, Lebenslinien, Komponenten und anderen Paketen. *Importbeziehungen* geben an, dass ein Paket alle Definitionen eines anderen Pakets enthält.

  Als Ausgangspunkt für die Untersuchung und Besprechung bestehender Klassen können Sie mit dem Klassen-Designer Klassendiagramme aus Code erstellen.

  Siehe:

- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)

- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)

- [Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Zusammenfassung: Vorteile von Klassendiagrammen
 Mit Klassendiagrammen können Sie Folgendes definieren:

- Ein allgemeines Glossar von Begriffen, die zum Erläutern der Benutzeranforderungen und der am System beteiligten Entitäten verwendet werden. Siehe [Modellbenutzeranforderungen](../modeling/model-user-requirements.md).

- Typen, die von Teilen des Systems verwendet werden, wie z. B. Komponenten, unabhängig von ihrer Implementierung. Weitere Informationen finden Sie unter [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md).

- Beziehungen, wie z. B. Abhängigkeiten zwischen Typen. Sie können z. B. anzeigen, dass ein Typ mehreren Instanzen eines anderen Typs zugeordnet sein kann.

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-----------------|---------------------|
|Anwendungsfalldiagramm|Definieren Sie die Typen, mit denen die Ziele und Schritte in Anwendungsfällen beschreiben werden.<br /><br /> Siehe:<br /><br /> -   [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)|
|Aktivitätsdiagramm|Definieren Sie die Typen von Daten, die Objektknoten, Eingabepins, Ausgabepins und Aktivitätsparameterknoten durchlaufen.<br /><br /> Siehe:<br /><br /> -   [UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md)|
|Komponentendiagramm|Beschreiben Sie Komponenten, ihre Schnittstellen und ihre Beziehungen. Eine Klasse kann auch eine vollständige Komponente beschreiben.<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|
|Ebenendiagramm|Definieren Sie die logische Architektur des Systems in Bezug auf Klassen.<br /><br /> Stellen Sie durch Ebenenvalidierung sicher, dass der Code konsistent mit dem Entwurf bleibt.<br /><br /> Siehe:<br /><br /> -   [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer-Diagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Layer-Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|
|Sequenzdiagramm|Definieren Sie die Typen von Lebenslinien sowie die Vorgänge, Parameter und Rückgabewerte für alle Meldungen, die die Lebenslinie empfangen kann.<br /><br /> Um eine Lebenslinie aus einem Typ in einem Klassendiagramm zu erstellen, klicken Sie mit der rechten Maustaste auf den Typ, und klicken Sie dann auf **Lebenslinie erstellen**erstellen.<br /><br /> Siehe:<br /><br /> -   [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)|
|Code Map|Visualisieren Sie die Organisation und Beziehungen in vorhandenem Code.<br /><br /> Um Klassen, ihre Beziehungen und ihre Methoden zu identifizieren, erstellen Sie eine Code Map, in der diese Elemente angezeigt werden.<br /><br /> Siehe:<br /><br /> -   [Zuordnen von Abhängigkeiten in Ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>Beschreiben der logischen Architektur: Layer-Diagramme
 Ebenendiagramme beschreiben die logische Architektur eines Systems, indem die Artefakte in der Projektmappe in abstrakten Gruppen bzw. *Ebenen*organisiert werden. Artefakte können viele Dinge sein, z. B. Namespaces, Projekte, Klassen, Methoden usw. Ebenen stellen die Rollen oder Aufgaben dar, die die Artefakte im System ausführen. Sie können auch eine Ebenenvalidierung in die Build- und Eincheckvorgänge einschließen, um sicherzustellen, dass der Code konsistent mit dem Entwurf bleibt.

 Um den Code mit dem Entwurf konsistent zu halten, überprüfen Dinner Now und Lucerne ihren Code während der Entwicklung mit dem folgenden Ebenendiagramm:

 ![Ebenendiagramm für integriertes Zahlungssystem](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Ebenendiagramm für Dinner Now nach der Integration mit Lucerne**

 Die Ebenen in diesem Diagramm sind mit den entsprechenden Lösungsartefakten von Dinner Now und Lucerne verknüpft. Die Business-Ebene ist z. B. mit dem DinnerNow.Business-Namespace und seinen Membern verknüpft, die nun die PaymentApprover-Klasse einschließen. Die Resource Access-Ebene ist mit dem DinnerNow.Data-Namespace verknüpft. Die Pfeile (bzw. *Abhängigkeiten*) geben an, dass die Funktionen in der Resource Access-Ebene nur von der Business-Ebene verwendet werden können. Beim Aktualisieren des Codes durch die Teams wird regelmäßig eine Ebenenvalidierung ausgeführt, um Konflikte bei ihrer Entstehung sofort erkennen und beheben zu können.

 Die Teams arbeiten zusammen, um die beiden Systeme schrittweise zu integrieren und zu testen. Zuerst wird sichergestellt, dass "PaymentApprover" und der Rest von Dinner Now erfolgreich miteinander funktionieren, bevor "PaymentProcessing" behandelt wird.

 Die folgende Code Map zeigt die neuen Aufrufe zwischen Dinner Now und "PaymentApprover":

 ![Aktualisiertes Abhängigkeitsdiagramm mit integriertem System](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Code Map mit aktualisierten Methodenaufrufen**

 Nachdem bestätigt wurde, dass das System wie erwartet funktioniert, wird der PaymentProcessing-Code von Dinner Now auskommentiert. Die Ebenenvalidierungsberichte sind einwandfrei, und die resultierende Code Map zeigt, dass keine PaymentProcessing-Abhängigkeiten mehr vorhanden sind:

 ![Abhängigkeitsdiagramm ohne PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Code Map ohne "PaymentProcessing"**

#### <a name="drawing-a-layer-diagram"></a>Zeichnen eines Ebenendiagramms
 Ein Ebenendiagramm umfasst die folgenden Hauptfunktionen:

- *Ebenen* beschreiben logische Gruppen von Artefakten.

- Ein *Link* ist eine Zuordnung zwischen einer Ebene und einem Artefakt.

   Um Ebenen aus Artefakten zu erstellen, ziehen Sie Elemente aus dem Projektmappen-Explorer, aus Code Maps, der Klassenansicht oder dem Objektkatalog. Um neue Ebenen zu zeichnen und sie dann mit Artefakten zu verknüpfen, verwenden Sie die Toolbox, oder klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, um die Ebenen zu erstellen, und ziehen Sie dann Elemente in diese Ebenen.

   Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein. Beachten Sie folgendes, wenn Sie die Anzahl der Artefakte in einer Ebene interpretieren:

  - Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

  - Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

    Klicken Sie mit der rechten Maustaste auf die Ebene, um die mit der Ebene verknüpften Artefakte anzuzeigen, und klicken Sie dann auf **Links anzeigen** , um den **Ebenen-Explorer**zu öffnen.

- Eine *Abhängigkeit* gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt. Eine *bidirektionale Abhängigkeit* gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.

   Um vorhandene Abhängigkeiten in einem Ebenendiagramm anzuzeigen, klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, und klicken Sie dann auf **Abhängigkeiten generieren**. Um beabsichtigte Abhängigkeiten zu beschreiben, zeichnen Sie neue.

  Siehe:

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)

- [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Zusammenfassung: Vorteile von Ebenendiagrammen
 Mit Ebenendiagrammen können Sie Folgendes ausführen:

- Beschreiben der logischen Architektur eines Systems entsprechend den Funktionen der zugehörigen Artefakte

- Sicherstellen, dass dieser Code in der Entwicklung dem vorgegebenen Entwurf entspricht

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-----------------|---------------------|
|Code Map|Visualisieren Sie die Organisation und Beziehungen in vorhandenem Code.<br /><br /> Um Ebenen zu erstellen, generieren Sie eine Code Map, und gruppieren Sie dann die Elemente auf der Code Map als potenzielle Ebenen. Ziehen Sie die Gruppen aus der Code Map in das Ebenendiagramm.<br /><br /> Siehe:<br /><br /> -   [Zuordnen von Abhängigkeiten in Ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Durchsuchen und Neuanordnen von Codezuordnungen](../modeling/browse-and-rearrange-code-maps.md)|
|Komponentendiagramm|Beschreiben Sie Komponenten, ihre Schnittstellen und ihre Beziehungen.<br /><br /> Um Ebenen zu visualisieren, erstellen Sie ein Komponentendiagramm, das die Funktionalität verschiedener Komponenten im System beschreibt.<br /><br /> Siehe:<br /><br /> -   [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)<br />-   [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|------------------|---------------|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Weitere Informationen
 [Code visualisieren](../modeling/visualize-code.md) [Modelle für Ihre App](../modeling/create-models-for-your-app.md) Verwenden Sie Modelle in Ihrem [Entwicklungsprozess](../modeling/use-models-in-your-development-process.md) [Verwenden Sie Modelle in der agilen Entwicklung](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [Validieren Sie Ihr System während der Entwicklung](../modeling/validate-your-system-during-development.md) Erweitern Sie [UML-Modelle und -Diagramme erweitern](../modeling/extend-uml-models-and-diagrams.md)
