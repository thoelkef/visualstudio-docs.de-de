---
title: 'Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 371eadd1438d33601b90ebfae0432c20841c313c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591982"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung

Stellen Sie sicher, dass das Softwaresystem die Anforderungen der Benutzer erfüllt, indem Sie die Visualisierungs- und Modellierungstools in Visual Studio verwenden.
Verwenden Sie Tools wie Code Maps, Abhängigkeits Diagramme und Klassendiagramme für folgende Aktionen:

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

## <a name="scenario-overview"></a>Übersicht über das Szenario

Dieses Szenario beschreibt Episoden in den Lebenszyklen der Softwareentwicklung von zwei fiktiven Unternehmen: Dinner Now und Lucerne Publishing. Dinner Now bietet einen webbasierten Essenslieferdienst in Seattle an. Kunden können auf der Dinner now-Website Mahlzeiten bestellen und für diese bezahlen. Die Bestellungen werden dann an das entsprechende örtliche Restaurant für die Lieferung gesendet. Lucerne Publishing, ein Unternehmen in New York, unterhält mehrere Geschäfte sowohl im Internet als auch außerhalb des Internets. Sie führen beispielsweise eine Website aus, auf der Kunden Restaurant Kritiken veröffentlichen können.

Lucerne hat vor kurzem Dinner Now übernommen und möchte die folgenden Änderungen vornehmen:

- Integrieren Sie Ihre Websites durch Hinzufügen von Restaurant Review-Funktionen zu Dinner now.

- Ersetzen des Zahlungssystems von Dinner Now durch das System von Lucerne

- Ausweiten der Dienstleistung von Dinner Now auf die gesamte Region.

Dinner Now verwendet SCRUM- und eXtreme-Programmierung. Sie verfügen über eine sehr hohe Testabdeckung und nur wenig nicht unterstützten Code. Risiken werden minimiert, indem kleine, funktionierende Versionen eines Systems erstellt und dann schrittweise Funktionen hinzugefügt werden. Der Code wird über kurze und regelmäßige Iterationen entwickelt. Dadurch werden Änderungen auf sichere Weise eingeführt, der Code wird häufig umgestaltet, und ein "Big Design Up Front" wird vermieden.

Lucerne unterhält eine überaus umfangreichere und komplexe Auflistung von Systemen, die teilweise über 40 Jahre alt sind. Aufgrund von Komplexität und Umfang des älteren Codes werden Änderungen nur mit größter Vorsicht vorgenommen. Lucerne verfolgt einen rigoroseren Entwicklungsprozess und zieht es vor, detaillierte Lösungen zu entwerfen und den Entwurf und sowie während der Entwicklung auftretende Änderungen zu dokumentieren.

Beide Teams verwenden Modellierungsdiagramme in Visual Studio, die sie dabei unterstützen, Systeme zu entwickeln, die die Anforderungen der Benutzer erfüllen. Sie verwenden Team Foundation Server zusammen mit anderen Tools zum Planen, Organisieren und Verwalten ihrer Arbeit.

Weitere Informationen über Team Foundation Server finden Sie unter:

- [Planen und Nachverfolgen von Arbeit](#plan-and-track-work)

- [Testen, Überprüfen und Einchecken von aktualisiertem Code](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> Rollen von Architektur- und Modellierungsdiagrammen in der Softwareentwicklung

In der folgenden Tabelle werden Rollen beschrieben, die diese Tools während verschiedener Phasen des Lebenszyklus der Softwareentwicklung spielen können:

||**Modellieren von Benutzeranforderungen**|**Modellierung von Geschäftsprozessen**|**Systemarchitektur und -entwurf**|**Visualisieren und Untersuchen von Code**|**Überprüfung**|
|------|-|-|-|-|-|
|DSL-Diagramm (domänenspezifische Sprache)|Ja|Ja|Ja|||
|Abhängigkeits Diagramm, ebenenvalidierung|||Ja|Ja|Ja|
|Code Map|||Ja|Ja|Ja|
|Klassen-Designer (codebasiert)||||Ja||

Um Abhängigkeits Diagramme zu zeichnen, müssen Sie ein Modellierungsprojekt als Teil einer vorhandenen oder neuen Projekt Mappe erstellen. Diese Diagramme müssen im Modellierungsprojekt erstellt werden.
Elemente in Abhängigkeits Diagrammen befinden sich im Modellierungsprojekt, Sie werden jedoch nicht im allgemeinen Modell gespeichert. Code Maps und .NET-Klassendiagramme, die aus Code erstellt werden, sind außerhalb des Modellierungsprojekts vorhanden.

Thema

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

- [Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Beide Teams verwenden auch die Abhängigkeits Validierung, um sicherzustellen, dass der Code in der Entwicklung mit dem Entwurf konsistent bleibt. Thema

- [Sicherstellen der Konsistenz von Code und Entwurf](#ValidatingCode)

- [Beschreiben der logischen Architektur: Abhängigkeits Diagramme](#DescribeLayers)

- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Einige Versionen von Visual Studio unterstützen die Abhängigkeits Validierung und schreibgeschützte Versionen von Code Maps für Visualisierung und Modellierung. Welche Editionen von Visual Studio diese Funktion unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Verstehen und kommunizieren von Informationen zum System

Es gibt keine vorgeschriebene Reihenfolge zum Verwenden der Visual Studio-Modellierungsdiagramme. Daher können Sie sie ganz Ihren Anforderungen oder dem Ansatz entsprechend verwenden. Normalerweise rufen Teams ihre Modelle im Verlauf des Projekts wiederholt und häufig auf. Jedes Diagramm bietet bestimmte Vorteile, um verschiedene Aspekte des Systems in der Entwicklung zu verstehen, zu beschreiben und zu kommunizieren.

Dinner now und Lucerne kommunizieren untereinander und mit Projekt Beteiligten, indem Sie Diagramme als ihre gemeinsame Sprache verwenden. Beispielsweise verwendet Dinner Now Diagramme, um folgende Aufgaben auszuführen:

- Visualisieren von vorhandenem Code

- Kommunizieren mit Lucerne über neue oder aktualisierte User Storys

- Identifizieren von Änderungen, die für die Unterstützung neuer oder aktualisierter User Storys erforderlich sind

Lucerne verwendet Diagramme, um folgende Aufgaben auszuführen:

- Aneignung von Kenntnissen über den Geschäftsprozess von Dinner Now

- Verstehen des Systementwurfs

- Kommunizieren mit Dinner Now über neue oder aktualisierte Benutzeranforderungen

- Dokumentieren von Aktualisierungen am System

Die Diagramme sind in Team Foundation Server integriert, sodass die Teams ihre Arbeit leichter planen, verwalten und verfolgen können. Beispielsweise verwenden sie Modelle, um Testfälle und Entwicklungsaufgaben zu identifizieren und ihre Arbeit einzuschätzen. Lucerne verknüpft Team Foundation Server-Arbeitselemente mit Modellelementen, sodass sie den Fortschritt überwachen sowie sicherstellen können, dass das System die Anforderungen der Benutzer erfüllt. Beispielsweise werden Anwendungsfälle mit Testfallarbeitselementen verknüpft, um sehen zu können, dass Anwendungsfälle erfüllt werden, wenn alle Tests erfolgreich verlaufen.

Bevor Teams Ihre Änderungen einchecken, überprüfen Sie den Code anhand der Tests und des Entwurfs durch das Ausführen von Builds, die die Abhängigkeits Validierung und automatisierte Tests einschließen. Dadurch wird sichergestellt, dass der aktualisierte Code dem Entwurf nicht widerspricht und Funktionen, die bereits funktionieren, nicht beeinträchtigt werden.

### <a name="identify-changes-to-the-existing-system"></a>Identifizieren von Änderungen am vorhandenen System

Dinner Now muss die Kosten für die Erfüllung der neuen Anforderung schätzen. Diese hängen teilweise davon ab, wie sehr sich diese Änderung auf andere Teile des Systems auswirkt. Zur Verdeutlichung erstellt einer der Dinner Now-Entwickler die folgenden Code Maps und Diagramme aus vorhandenem Code:

|**Code Map oder Diagramm**|**Zeigt Folgendes an**|
|-|-|
|*Code Map*<br /><br /> Thema<br /><br /> - Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)<br />- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)<br />- [Anpassen von Code Maps durch Bearbeiten der dgml-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Abhängigkeiten und andere Beziehungen im Code.<br /><br /> Dinner Now könnte z. B. damit beginnen, Assembly-Code Maps zu überprüfen, um eine Übersicht der Assemblys und ihrer Abhängigkeiten zu erhalten. Sie können in den Code Maps einen Drilldown durchführen, um die Namespaces und Klassen in diesen Assemblys zu untersuchen.<br /><br /> Dinner Now kann auch Code Maps erstellen, um bestimmte Bereiche und andere Arten von Beziehungen im Code zu untersuchen. Sie verwenden den Projektmappen-Explorer, um relevante Bereiche und Beziehungen zu finden und auszuwählen.|
|*Codebasiertes Klassendiagramm*<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Vorhandene Klassen in Code|

 Beispiel: Die Entwicklerin erstellt eine Code Map. Sie passt den Umfang an, um sich auf die Bereiche zu konzentrieren, die von dem neuen Szenario betroffen sind. Diese Bereiche werden ausgewählt und auf der Code Map hervorgehoben:

 ![Abhängigkeitsdiagramm für Namespaces](../modeling/media/namespace_reviewsystem.png)

 **Namespace-Code Map**

 Die Entwicklerin erweitert die ausgewählten Namespaces, um die zugehörigen Klassen, Methoden und Beziehungen anzuzeigen:

 ![Erweitertes Abhängigkeitsdiagramm für Namespaces](../modeling/media/dep_reviewsystem.png)

 **Erweiterte Code Map für Namespaces mit sichtbaren gruppenübergreifenden Links**

 Die Entwicklerin untersucht den Code, um nach den betroffenen Klassen und Methoden zu suchen. Um die Auswirkungen der einzelnen Änderungen sofort anzuzeigen, generieren Sie Code Maps nach jeder Änderung neu. Siehe [visualisieren von Code](../modeling/visualize-code.md).

 Um Änderungen an anderen Teilen des Systems zu beschreiben, wie z. B. Komponenten oder Interaktionen, kann das Team diese Elemente bei Bedarf auf Whiteboards zeichnen. Sie können auch die folgenden Diagramme in Visual Studio zeichnen, sodass die Details von beiden Teams erfasst, verwaltet und verstanden werden können:

|**Diagramme**|**Beschreibt**|
|-|-|
|*Codebasiertes Klassendiagramm*<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Vorhandene Klassen in Code|

### <a name="ValidatingCode"></a>Code konsistent mit dem Entwurf
 Dinner Now muss sicherstellen, dass der aktualisierte Code konsistent mit dem Entwurf bleibt. Sie erstellen Abhängigkeits Diagramme, die die Funktionsebenen im System beschreiben, die zulässigen Abhängigkeiten zwischen Ihnen angeben und diesen Ebenen Lösungs Artefakte zuordnen.

|**Diagramm**|**Beschreibt**|
|-|-|
|*Abhängigkeits Diagramm*<br /><br /> Thema<br /><br /> - [Erstellen von Abhängigkeits Diagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />[Abhängigkeits Diagramme - : Referenz](../modeling/layer-diagrams-reference.md)<br />- [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />- [Überprüfen von Code mit Abhängigkeits Diagrammen](../modeling/validate-code-with-layer-diagrams.md)|Die logische Architektur des Codes<br /><br /> Ein Abhängigkeits Diagramm organisiert die Elemente in einer Visual Studio-Projekt Mappe und ordnet sie abstrakten Gruppen zu, die als *Ebenen*bezeichnet werden. Diese Ebenen identifizieren die Rollen, Aufgaben oder Funktionen, die diese Artefakte im System spielen.<br /><br /> Abhängigkeits Diagramme sind hilfreich, um den beabsichtigten Entwurf des Systems zu beschreiben und den weiter entwickelten Code anhand dieses Entwurfs zu validieren.<br /><br /> Um Ebenen zu erstellen, ziehen Sie Elemente aus dem Projektmappen-Explorer, Code Maps, der Klassenansicht und dem Objektkatalog. Verwenden Sie die Toolbox, oder klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, um neue Ebenen zu zeichnen.<br /><br /> Um vorhandene Abhängigkeiten anzuzeigen, klicken Sie mit der rechten Maustaste auf die Abhängigkeits Diagramm Oberfläche, und klicken Sie dann auf **Abhängigkeiten generieren**. Um beabsichtigte Abhängigkeiten anzugeben, zeichnen Sie neue Abhängigkeiten.|

Das folgende Abhängigkeits Diagramm beschreibt z. b. Abhängigkeiten zwischen Ebenen und der Anzahl der Artefakte, die jeder Ebene zugeordnet sind:

![Abhängigkeits Diagramm des integrierten Zahlungssystems](../modeling/media/layer_integrated_dnlucerne.png)

 **Abhängigkeits Diagramm**

Um sicherzustellen, dass während der Code Entwicklung keine Konflikte mit dem Entwurf auftreten, verwenden die Teams die Abhängigkeits Validierung für Builds, die in Azure devops ausgeführt werden. Außerdem erstellen Sie eine benutzerdefinierte MSBuild-Aufgabe, um eine Abhängigkeits Überprüfung in ihren Eincheck Vorgängen zu erfordern. Mithilfe von Buildberichten werden Validierungsfehler erfasst.

Thema

- [Verwenden des visuellen Designers](/azure/devops/pipelines/get-started-designer)

- [Tfvc-Gated-Check-in](/azure/devops/pipelines/build/triggers#gated)

- [Build-und releaseaufgaben](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Allgemeine Tipps zum Erstellen und Verwenden von Modellen

- Die meisten Diagramme bestehen aus Knoten, die durch Linien verbunden sind. Für jeden Diagrammtyp stellt die Toolbox verschiedene Arten von Knoten und Linien bereit.

   Zum Öffnen der Toolbox klicken Sie im Menü **Ansicht** auf **Toolbox**.

- Um einen Knoten zu erstellen, ziehen Sie ihn von der Toolbox in das Diagramm. Bestimmte Arten von Knoten müssen auf vorhandene Knoten gezogen werden. In einem Komponentendiagramm muss einer vorhandenen Komponente z. B. ein neuer Port hinzugefügt werden.

- Um eine Linie oder Verbindung zu erstellen, klicken Sie in der Toolbox auf das entsprechende Tool, klicken Sie auf den Quellknoten und dann auf den Zielknoten. Einige Linien können nur zwischen bestimmten Arten von Knoten erstellt werden. Wenn Sie den Mauszeiger über mögliche Quellen oder Ziele bewegen, wird angezeigt, ob Sie eine Verbindung erstellen können.

### <a name="plan-and-track-work"></a>Planen und Nachverfolgen der Arbeit

Visual Studio-Modellierungsdiagramme sind in Team Foundation Server integriert, sodass Sie Arbeit leichter planen, verwalten und nachverfolgen können. Beide Teams verwenden Modelle, um Testfälle und Entwicklungsaufgaben zu identifizieren und ihre Arbeit einzuschätzen. Lucerne erstellt und verknüpft Team Foundation Server-Arbeitselemente mit Modellelementen, wie z. B. Anwendungsfälle oder Komponenten. Auf diese Weise kann der Status überwacht werden, und die Arbeit kann bis zu den Benutzeranforderungen zurückverfolgt werden. Somit wird sichergestellt, dass die Änderungen stets den Anforderungen entsprechen.

Im Verlauf ihrer Arbeit aktualisieren die Teams die Arbeitselemente, um die Zeit zu berücksichtigen, die sie mit ihren Aufgaben verbracht haben. Außerdem wird eine Überwachung und Berichterstellung des Status der Arbeit mithilfe der folgenden Team Foundation Server-Funktionen durchgeführt:

- Tägliche *Verbrauchs Berichte* , die anzeigen, ob Sie die geplante Arbeit in der erwarteten Zeit vervollständigen werden. Es werden andere ähnliche Berichte in Team Foundation Server generiert, um den Status von Fehlern zu verfolgen.

- Ein *Iterationsarbeitsblatt* , das Microsoft Excel verwendet, mit dem das Team die Arbeitsauslastung überwachen und zwischen den Mitgliedern ausgleichen kann. Dieses Arbeitsblatt ist mit Team Foundation Server verknüpft und bietet eine Diskussionsbasis bei den regelmäßigen Statusbesprechungen.

- Ein *Entwicklungsdashboard* , das Office Project verwendet, um das Team mit wichtigen Projektinformationen auf dem neuesten Stand zu halten.

Thema

- [Informationen zu Agile-Tools und der Agile-Projektverwaltung](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Diagramme, Dashboards und Widgets (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts)

- [Erstellen von Backlog und Aufgaben mit Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="TestValidateCheckInCode"></a>Testen, überprüfen und Einchecken von Code

Wenn die Teams jede Aufgabe vervollständigen, überprüfen Sie Ihren Code in die Quell Code Verwaltung und erhalten Erinnerungen von Team Foundation Server, wenn Sie vergessen. Bevor Team Foundation Server Ihre Eincheck Vorgänge akzeptiert, führen die Teams Komponententests und Abhängigkeits Validierung aus, um den Code anhand der Testfälle und des Entwurfs zu überprüfen. Sie verwenden Team Foundation Server, um Builds, Automatisierte Komponententests und Abhängigkeits Validierung regelmäßig auszuführen. Dadurch wird sichergestellt, dass der Code die folgenden Kriterien erfüllt:

- Er funktioniert.

- Bereits funktionierender Code wird dadurch nicht beeinträchtigt.

- Er steht nicht in Konflikt mit dem Entwurf.

Dinner Now verfügt über eine große Auflistung automatisierter Tests, die Lucerne wiederverwenden kann, da fast alle weiterhin gültig sind. Lucerne kann außerdem auf diesen Tests aufbauen und neue hinzufügen, um neue Funktionen abzudecken. Beide verwenden auch Visual Studio, um manuelle Tests auszuführen.

Um sicherzustellen, dass der Code dem Entwurf entspricht, konfigurieren die Teams Ihre Builds in Azure devops, um die Überprüfung der Abhängigkeit einzubeziehen. Wenn Konflikte auftreten, wird ein Bericht mit den Details generiert.

Thema

- [Testen der Anwendung](/azure/devops/test/overview?view=vsts)

- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)

- [Verwenden der Versionskontrolle](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualisieren des Systems mithilfe von Visualisierung und Modellierung

Lucerne und Dinner Now müssen ihre Zahlungssysteme integrieren. Die folgenden Abschnitte zeigen die Modellierungsdiagramme in Visual Studio, die beim Ausführen dieser Aufgabe helfen:

- [Visualisieren von vorhandenem Code: Code Maps](#VisualizeCode)

- [Definieren eines Glossars der Typen: Klassendiagramme](#DefineClasses)

- [Beschreiben der logischen Architektur: Abhängigkeits Diagramme](#DescribeLayers)

Thema

- [Visualisieren von Code](../modeling/visualize-code.md)

- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

- [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)

### <a name="VisualizeCode"></a> Visualisieren von vorhandenem Code: Code Maps

Code Maps zeigen die aktuelle Organisation und die Beziehungen im Code. Elemente werden auf der Code Map durch *Knoten* und Beziehungen durch *Links*dargestellt. Mit Code Maps können Sie die folgenden Arten von Aufgaben ausführen:

- Untersuchen von unbekanntem Code

- Verstehen, wo und wie sich eine vorgeschlagene Änderung auf vorhandenen Code auswirken könnte

- Hier finden Sie Bereiche mit Komplexität, natürlichen Abhängigkeiten oder Mustern oder anderen Bereichen, die von der Verbesserung profitieren können.

Dinner Now muss z. B. die Kosten für die Aktualisierung der PaymentProcessing-Komponente schätzen. Diese hängen teilweise davon ab, wie sehr sich diese Änderung auf andere Teile des Systems auswirkt. Zur Verdeutlichung erstellt einer der Dinner Now-Entwickler Code Maps aus dem Code und richtet den Fokus des Projektumfangs auf die Bereiche aus, die durch die Änderung betroffen sein könnten.

Die folgende Code Map zeigt die Abhängigkeiten zwischen der PaymentProcessing-Klasse und anderen Teilen des Dinner Now-Systems, die markiert dargestellt werden:

![Abhängigkeitsdiagramm für das Zahlungssystem von Dinner Now](../modeling/media/dep_dnpayment.png)

**Code Map für das Zahlungssystem von Dinner Now**

Der Entwickler untersucht die Code Map, indem er die PaymentProcessing-Klasse erweitert und die zugehörigen Member auswählt, um die potenziell betroffenen Bereiche anzuzeigen:

![Methoden in der PaymentProcessing-Klasse und ihre Abhängigkeiten](../modeling/media/depgraph_expandeddn.png)

**Methoden in der PaymentProcessing-Klasse und ihre Abhängigkeiten**

Für das Zahlungssystem von Lucerne wird die folgende Code Map generiert, um die zugehörigen Klassen, Methoden und Abhängigkeiten zu untersuchen. Das Team erkennt, dass das Lucerne-System auch Arbeit erfordern könnte, damit es mit anderen Teilen von Dinner Now interagieren kann:

![Abhängigkeitsdiagramm für das Zahlungssystem von Lucerne](../modeling/media/depgraph_lucernepay.png)

**Code Map für das Zahlungssystem von Lucerne**

Beide Teams arbeiten zusammen, um die Änderungen zu ermitteln, die zum Integrieren der beiden Systeme erforderlich sind. Es wird entschieden, einen Teil des Codes umzugestalten, damit er einfacher zu aktualisieren ist. Die PaymentApprover-Klasse wird in den DinnerNow.Business-Namespace verschoben und erfordert einige neue Methoden. Die Dinner Now-Klassen, die Transaktionen behandeln, erhalten einen eigenen Namespace. Die Teams erstellen und verwenden Arbeitselemente, um ihre Arbeit zu planen, zu organisieren und nachzuverfolgen. Wo sinnvoll, werden Arbeitselemente mit Modellelementen verknüpft.

Nach der Neuorganisation des Codes generieren die Teams eine neue Code Map, um die aktualisierte Struktur und die Beziehungen anzuzeigen:

![Abhängigkeitsdiagramm mit neu organisiertem Code](../modeling/media/depgraph_integrated.png)

**Code Map mit neu organisiertem Code**

Diese Code Map zeigt, dass sich die PaymentApprover-Klasse jetzt im DinnerNow.Business-Namespace befindet und über ein paar neue Methoden verfügt. Die Dinner Now-Transaktionsklassen verfügen jetzt über einen eigenen PaymentSystem-Namespace, mit dem der Code später leichter behandelt werden kann.

#### <a name="creating-a-code-map"></a>Erstellen einer Code Map

- Folgen Sie den folgenden Schritten zum Generieren einer Code Map, um eine schnelle Übersicht über Quellcode zu erhalten:

     Klicken Sie im Menü **Architektur** auf **Code Map für Projektmappe generieren**.

     Erstellen Sie für eine schnelle Übersicht über kompilierten Code eine leere Code Map, und ziehen Sie dann Assemblydateien oder Binärdateien auf die Oberfläche der Code Map.

- Um bestimmte Code- oder Projektmappenelemente zu untersuchen, wählen Sie im Projektmappen-Explorer die Elemente und Beziehungen aus, die Sie visualisieren möchten. Sie können dann entweder eine neue Code Map generieren oder einer vorhandenen Code Map ausgewählte Elemente hinzufügen. Siehe [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Um die Code Map einfacher zu untersuchen, können Sie das Layout den auszuführenden Aufgaben entsprechend neu anordnen.

     Wählen Sie beispielsweise ein Strukturlayout aus, um die Ebenen im Code zu visualisieren. Siehe [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Zusammenfassung: Vorteile von Code Maps
 Mit Code Maps können Sie Folgendes durchführen:

- Verdeutlichen der Organisation und Beziehungen in vorhandenem Code

- Identifizieren der Bereiche, die von einer vorgeschlagenen Änderung betroffen sein könnten

- Auffinden von Bereichen mit Komplexität, Mustern oder Ebenen sowie andere Bereichen, die Sie optimieren könnten, um den Code leichter verwalten, ändern und wiederverwenden zu können

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibt**|
|-|-|
|Abhängigkeits Diagramm|Die logische Architektur des Systems Verwenden Sie die Abhängigkeits Validierung, um sicherzustellen, dass der Code mit dem Entwurf konsistent bleibt.<br /><br /> Erstellen Sie eine Code Map, und gruppieren Sie zugehörige Elemente, um vorhandene Abhängigkeiten oder beabsichtigte Abhängigkeiten zu identifizieren. Informationen zum Erstellen eines Abhängigkeits Diagramms finden Sie unter:<br /><br /> - [Erstellen von Abhängigkeits Diagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)|
|Klassendiagramm (codebasiert)|Vorhandene Klassen in Code für ein bestimmtes Projekt<br /><br /> Verwenden Sie den Klassen-Designer, um eine vorhandene Klasse in Code zu visualisieren und zu ändern.<br /><br /> Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="DefineClasses"></a> Definieren eines Glossars der Typen: Klassendiagramme
 Klassendiagramme definieren die am System beteiligten Entitäten, Begriffe oder Konzepte sowie ihre Beziehungen untereinander. Beispielsweise können Sie diese Diagramme während der Entwicklung verwenden, um die Attribute und Vorgänge für jede Klasse unabhängig von Implementierungssprache oder Format zu beschreiben.

 Um die am Anwendungsfall "Process Payment" (Zahlung verarbeiten) beteiligten Entitäten zu erläutern und zu besprechen, zeichnet Lucerne das folgende Klassendiagramm:

 ![Process Payment-Entitäten in einem Klassendiagramm](../modeling/media/uml_payentities.png)

 **Process Payment-Entitäten in einem Klassendiagramm**

 Dieses Diagramm zeigt, dass ein Kunde über viele Bestellungen und verschiedene Methoden zum Bezahlen der Bestellungen verfügen kann. "BankAccount" und "CreditCard" erben beide von "Payment".

 Während der Entwicklung verwendet Lucerne das folgende Klassendiagramm, um die Details der einzelnen Klassen zu beschreiben und zu besprechen:

 ![Process Payment-Entitätsdetails in einem Klassendiagramm](../modeling/media/uml_payment.png)

 **Process Payment-Details im Klassendiagramm**

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

- [Gewusst wie: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Zusammenfassung: Vorteile von Klassendiagrammen
 Mit Klassendiagrammen können Sie Folgendes definieren:

- Ein allgemeines Glossar von Begriffen, die zum Erläutern der Benutzeranforderungen und der am System beteiligten Entitäten verwendet werden. Siehe [Modell Benutzeranforderungen](../modeling/model-user-requirements.md).

- Typen, die von Teilen des Systems verwendet werden, wie z. B. Komponenten, unabhängig von ihrer Implementierung. Weitere Informationen finden [Sie unter Modellieren der Architektur Ihrer APP](../modeling/model-your-app-s-architecture.md).

- Beziehungen, wie z. B. Abhängigkeiten zwischen Typen. Sie können z. B. anzeigen, dass ein Typ mehreren Instanzen eines anderen Typs zugeordnet sein kann.

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-|-|
|Abhängigkeits Diagramm|Definieren Sie die logische Architektur des Systems in Bezug auf Klassen.<br /><br /> Verwenden Sie die Abhängigkeits Validierung, um sicherzustellen, dass der Code mit dem Entwurf konsistent bleibt.<br /><br /> Thema<br /><br /> - [Erstellen von Abhängigkeits Diagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />[Abhängigkeits Diagramme - : Referenz](../modeling/layer-diagrams-reference.md)<br />- [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br />- [Überprüfen von Code mit Abhängigkeits Diagrammen](../modeling/validate-code-with-layer-diagrams.md)|
|Code Map|Visualisieren Sie die Organisation und Beziehungen in vorhandenem Code.<br /><br /> Um Klassen, ihre Beziehungen und ihre Methoden zu identifizieren, erstellen Sie eine Code Map, in der diese Elemente angezeigt werden.<br /><br /> Thema<br /><br /> - Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a>Beschreiben der logischen Architektur: Abhängigkeits Diagramme
 Abhängigkeits Diagramme beschreiben die logische Architektur eines Systems, indem die Artefakte in der Projekt Mappe in abstrakten Gruppen oder *Ebenen*organisiert werden. Artefakte können viele Dinge sein, z. B. Namespaces, Projekte, Klassen, Methoden usw. Ebenen stellen die Rollen oder Aufgaben dar, die die Artefakte im System ausführen. Sie können auch eine Ebenenvalidierung in die Build- und Eincheckvorgänge einschließen, um sicherzustellen, dass der Code konsistent mit dem Entwurf bleibt.

 Um den Code mit dem Entwurf konsistent zu halten, verwenden Dinner now und Lucerne das folgende Abhängigkeits Diagramm, um den Code bei der Entwicklung zu validieren:

 ![Abhängigkeits Diagramm des integrierten Zahlungssystems](../modeling/media/layer_integrated_dnlucerne.png)

 **Abhängigkeits Diagramm für Dinner now, das in Lucerne integriert ist**

 Die Ebenen in diesem Diagramm sind mit den entsprechenden Lösungsartefakten von Dinner Now und Lucerne verknüpft. Die Business-Ebene ist z. B. mit dem DinnerNow.Business-Namespace und seinen Membern verknüpft, die nun die PaymentApprover-Klasse einschließen. Die Resource Access-Ebene ist mit dem DinnerNow.Data-Namespace verknüpft. Die Pfeile (bzw. *Abhängigkeiten*) geben an, dass die Funktionen in der Resource Access-Ebene nur von der Business-Ebene verwendet werden können. Beim Aktualisieren des Codes durch die Teams wird regelmäßig eine Ebenenvalidierung ausgeführt, um Konflikte bei ihrer Entstehung sofort erkennen und beheben zu können.

 Die Teams arbeiten zusammen, um die beiden Systeme schrittweise zu integrieren und zu testen. Zuerst wird sichergestellt, dass "PaymentApprover" und der Rest von Dinner Now erfolgreich miteinander funktionieren, bevor "PaymentProcessing" behandelt wird.

 Die folgende Code Map zeigt die neuen Aufrufe zwischen Dinner Now und "PaymentApprover":

 ![Aktualisiertes Abhängigkeitsdiagramm mit integriertem System](../modeling/media/depgraph_intsystem.png)

 **Code Map mit aktualisierten Methodenaufrufen**

 Nachdem bestätigt wurde, dass das System wie erwartet funktioniert, wird der PaymentProcessing-Code von Dinner Now auskommentiert. Die Ebenenvalidierungsberichte sind einwandfrei, und die resultierende Code Map zeigt, dass keine PaymentProcessing-Abhängigkeiten mehr vorhanden sind:

 ![Abhängigkeitsdiagramm ohne PaymentProcessing](../modeling/media/depgraph_nomore.png)

 **Code Map ohne "PaymentProcessing"**

#### <a name="drawing-a-dependency-diagram"></a>Zeichnen eines Abhängigkeits Diagramms

Ein Abhängigkeits Diagramm verfügt über die folgenden Hauptfunktionen:

- *Ebenen* beschreiben logische Gruppen von Artefakten.

- Ein *Link* ist eine Zuordnung zwischen einer Ebene und einem Artefakt.

     Um Ebenen aus Artefakten zu erstellen, ziehen Sie Elemente aus dem Projektmappen-Explorer, aus Code Maps, der Klassenansicht oder dem Objektkatalog. Um neue Ebenen zu zeichnen und sie dann mit Artefakten zu verknüpfen, verwenden Sie die Toolbox, oder klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, um die Ebenen zu erstellen, und ziehen Sie dann Elemente in diese Ebenen.

     Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein. Beachten Sie folgendes, wenn Sie die Anzahl der Artefakte in einer Ebene interpretieren:

  - Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

       Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

  - Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

    Um die mit einer Ebene verknüpften Artefakte anzuzeigen, klicken Sie mit der rechten Maustaste auf die Abhängigkeit, und klicken Sie dann auf **Links anzeigen** , um den **Ebenen-Explorer**zu öffnen.

- Eine *Abhängigkeit* gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt. Eine *bidirektionale Abhängigkeit* gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.

     Wenn Sie vorhandene Abhängigkeiten im Abhängigkeits Diagramm anzeigen möchten, klicken Sie mit der rechten Maustaste auf die Diagramm Oberfläche, und klicken Sie dann auf **Abhängigkeiten generieren**. Um beabsichtigte Abhängigkeiten zu beschreiben, zeichnen Sie neue.

Thema

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)

- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Zusammenfassung: Stärken von Abhängigkeits Diagrammen

Abhängigkeits Diagramme helfen Ihnen dabei:

- Beschreiben der logischen Architektur eines Systems entsprechend den Funktionen der zugehörigen Artefakte

- Sicherstellen, dass dieser Code in der Entwicklung dem vorgegebenen Entwurf entspricht

#### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen

|**Diagramm**|**Beschreibung**|
|-|-|
|Code Map|Visualisieren Sie die Organisation und Beziehungen in vorhandenem Code.<br /><br /> Um Ebenen zu erstellen, generieren Sie eine Code Map, und gruppieren Sie dann die Elemente auf der Code Map als potenzielle Ebenen. Ziehen Sie die Gruppen aus der Zuordnung in das Abhängigkeits Diagramm.<br /><br /> Thema<br /><br /> - Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)<br />- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|-|-|
|**Foren**|- [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Siehe auch

- [Visualisieren von Code](../modeling/visualize-code.md)
- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
- [Verwenden von Modellen in der Agile-Entwicklung](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
