---
title: Analysieren und Modellieren der Architektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b7d7f9f478e85229eaa72ab04d12b6b542cbab5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781035"
---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellen Sie sicher, dass Ihre App Benutzeranforderungen erfüllt, indem Sie die Visual Studio-Architektur und -Modellierungstools zum Entwerfen und Modellieren Ihrer App verwenden. Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen.  
  
 Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen. Sie können Anforderungen, Aufgaben, Testfälle, Fehler oder andere Arbeitsschritte nachverfolgen, die den Modellen zugeordnet sind, indem Sie Modellelemente mit Team Foundation Server-Arbeitselementen und dem Entwicklungsplan verknüpfen. Finden Sie unter [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Informationen dazu, welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="to"></a>Beschreibung  
  
|||  
|-|-|  
|**Visualisieren von Code**:<br /><br /> -Finden Sie unter Organisation und Beziehungen des Codes, indem Sie codezuordnungen erstellen. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />-Finden Sie der Struktur der Klasse und Member für ein bestimmtes Projekt Klassendiagramme aus Code erstellen.<br />-Finden Sie Konflikte zwischen Ihrem Code und dem Entwurf, indem Sie Ebenendiagramme zum Überprüfen von Code erstellen.<br /><br /> **Hinweis**: In dieser Version von Visual Studio wird der Begriff *Code Map* anstelle von *Abhängigkeitsdiagramm*verwendet. Der Begriff *Diagramm* allein bezieht sich in der Regel auf ein gerichtetes Diagramm oder ein DGML-Diagramm (oder -Dokument). Code Maps sind ein spezialisierter Typ von DGML-Diagrammen.|-   [Visualisieren von Code](../modeling/visualize-code.md)<br />-   [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Verstehen der codeabhängigkeiten durch Visualisierung (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Visualisieren der Auswirkungen einer Änderung (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Beschreiben und Kommunizieren von Benutzeranforderungen**:<br /><br /> -Klären Sie User Stories, Geschäftsregeln und andere Anforderungen und sicherzustellen Sie ihre Konsistenz durch Zeichnen von UML-Diagramme Anwendungsfall, Aktivität und Klassendiagramme.|-   [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)<br />-   [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md)<br />-   [Video: Verbessern der Architektur durch Modellierung (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Definieren der Architektur**:<br /><br /> -Modell der allgemeinen Struktur des Softwaresystems und der Entwurfsmuster durch Zeichnen von UML-Komponente, Klasse und Sequenzdiagramme.<br />– Definieren und Erzwingen von Einschränkungen für Abhängigkeiten zwischen den Komponenten des Codes, indem Sie Ebenendiagramme erstellen.|-   [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)<br />-   [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Verbessern der Architektur durch Modellierung (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Verwenden von Ebenendiagrammen zum Entwerfen und Überprüfen der Architektur (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Überprüfen des Systems anhand der Anforderungen und des beabsichtigten Entwurfs:**<br /><br /> – Definieren Sie Akzeptanztests oder Systemtests auf Grundlage der Anforderungsmodelle. Dies schafft eine enge Beziehung zwischen den Tests und den Anforderungen der Benutzer und erleichtert das Aktualisieren des Systems bei geänderten Anforderungen.<br />-Überprüfen Sie codeabhängigkeiten mit Ebenendiagrammen, die die beabsichtigte Architektur beschreiben und zu verhindern, dass Änderungen, die mit dem Entwurf in Konflikt stehen.|-   [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)<br />-   [Video: Verwenden von Ebenendiagrammen zum Entwerfen und Überprüfen der Architektur (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br /> -Fügen Sie Code Maps, Modellierungsprojekte, UML-Diagramme, und Ebenendiagramme unter Team Foundation-Versionskontrolle, um diese freigeben zu können.|Arbeiten mehrere Benutzer mit diesen Elementen unter Team Foundation-Versionskontrolle, verwenden Sie diese Richtlinien, um Probleme mit der Versionskontrolle zu vermeiden:<br /><br /> -   [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Generieren oder Konfigurieren von Teilen der Anwendung aus UML- oder domänenspezifischen Sprachen**:<br /><br /> -Stellen Sie Ihren Entwurf mehr anpassbar an geänderte Anforderungen und leichter für eine Produktgruppe.|-   [Generieren und Konfigurieren von Apps aus Modellen](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Anpassen von Modellen und Diagrammen**:<br /><br /> – Passen Sie Modelle, wie Sie Ihr Projekt verwendet diese durch definieren zusätzliche Eigenschaften für UML-Elemente, validierungseinschränkungen, um sicherzustellen, dass die Modelle Ihrer Geschäftsregeln und zusätzliche Menübefehle und Toolboxelemente entsprechen.<br />– Erstellen Sie eigene domänenspezifische Sprachen.|-   [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br /> – Verwenden Sie Textblöcke und Steuerelementlogik in Vorlagen, um textbasierte Dateien zu generieren.|-   [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Typen von Modellen und deren Anwendungsmöglichkeiten  
  
|**Modelltyp und typische Anwendungsmöglichkeiten**|  
|-------------------------------------|  
|**Codezuordnungen**<br /><br /> Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Überprüfen Sie Programmcode, damit Sie die Struktur und die zugehörigen Abhängigkeiten besser verstehen können, wird das Aktualisieren und schätzen Sie die Kosten der vorgeschlagenen Änderungen.<br /><br /> Thema<br /><br /> -   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Ebenendiagramm**<br /><br /> Anhand von Ebenendiagrammen können Sie die Struktur einer Anwendung als einen Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Sie können die Validierung ausführen, um Konflikte zwischen Abhängigkeiten im Code und den in einem Ebenendiagramm beschriebenen Abhängigkeiten zu ermitteln.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Stabilisieren der Struktur der Anwendung anhand zahlreicher Änderungen während der gesamten Lebensdauer.<br />: Ermitteln Sie unbeabsichtigte abhängigkeitskonflikte, vor dem Einchecken von Änderungen am Code.<br /><br /> Thema<br /><br /> -   [Erstellen von Ebenendiagrammen aus Ihrem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML-Modell**<br /><br /> Ein UML-Modell beinhaltet mehrere Ansichten, einschließlich Klasse, Komponente, Anwendungsfall sowie Aktivitäts- und Sequenzdiagramme. Sie können UML speziell für Ihre Anwendungsdomäne anpassen. Sie können z. B. Tags, zusätzliche Informationen und Einschränkungen an die Modellelemente anfügen. Außerdem können Sie Tools definieren, mit denen die Modelle bearbeitet werden können. Finden Sie unter [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md).<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Anforderungen und der Entwurf zu beschreiben. UML lässt sich bei der Entwicklung von Anwendungen schnell anwenden. Finden Sie unter [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md).<br />-Generieren oder Konfigurieren von Tests oder Teilen einer Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation anzupassen und die Generierungsvorlagen oder konfigurierbare Anwendung zu entwickeln. Finden Sie unter [generieren und Konfigurieren von Apps aus Modellen](../modeling/generate-and-configure-your-app-from-models.md).<br />– Für allgemeine Beschreibungen und codegenerierung oder-Konfiguration in kleineren Projekten.|  
|**Domänenspezifische Sprache (DSL)**<br /><br /> Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist sie normalerweise eine grafische Darstellung.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Generieren Sie oder konfigurieren Sie die Teile der Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.<br />– Bei großen Projekten oder bei Produktlinien, die, in denen die Investition in die Entwicklung DSL und die zugehörigen Tools durch ihre Verwendung in mehr als ein Projekt zurückgegeben wird.<br /><br /> Thema<br /><br /> -   [Modeling SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Wo kann ich weitere Informationen abrufen?  
  
|||  
|-|-|  
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps und Anwendungslebenszyklus-Verwaltung](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



