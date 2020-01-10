---
title: Analysieren und modellieren der Architektur | Microsoft-Dokumentation
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
ms.openlocfilehash: 1a505cd9fd40a47c58135506cf7e022409e9b77e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852059"
---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellen Sie sicher, dass Ihre App Benutzeranforderungen erfüllt, indem Sie die Visual Studio-Architektur und -Modellierungstools zum Entwerfen und Modellieren Ihrer App verwenden. Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen.

 Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen. Sie können Anforderungen, Aufgaben, Testfälle, Fehler oder andere Arbeitsschritte nachverfolgen, die den Modellen zugeordnet sind, indem Sie Modellelemente mit Team Foundation Server-Arbeitselementen und dem Entwicklungsplan verknüpfen. Weitere Informationen finden [Sie unter Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>Zu

|||
|-|-|
|**Visualisieren von Code**:<br /><br /> -Sehen Sie sich die Organisation und Beziehungen des Codes an, indem Sie Code Maps erstellen. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />-Zeigen Sie die Klassenstruktur und Member für ein bestimmtes Projekt an, indem Sie Klassendiagramme aus Code erstellen.<br />-Suchen Sie Konflikte zwischen dem Code und dessen Entwurf, indem Sie ebenendiagramme erstellen, um Code zu validieren.<br /><br /> **Hinweis**: In dieser Version von Visual Studio wird der Begriff *Code Map* anstelle von *Abhängigkeitsdiagramm*verwendet. Der Begriff *Diagramm* allein bezieht sich in der Regel auf ein gerichtetes Diagramm oder ein DGML-Diagramm (oder -Dokument). Code Maps sind ein spezialisierter Typ von DGML-Diagrammen.|-   [Visualisieren von Code](../modeling/visualize-code.md)<br />-   [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   - [Video: verstehen der Code Abhängigkeiten durch Visualisierung (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   - [Video: visualisieren der Auswirkungen einer Änderung (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**Beschreiben und Kommunizieren von Benutzeranforderungen**:<br /><br /> : Verdeutlichen Sie Benutzer Textabschnitte, Geschäftsregeln und andere Anforderungen, und stellen Sie sicher, dass ihre Konsistenz durch Zeichnen von UML-Diagrammen wie Anwendungsfall, Aktivität und Klassendiagrammen gewährleistet ist.|-   [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)<br />[Benutzer Anforderungen](../modeling/model-user-requirements.md) für -   Modell<br />-   - [Video: verbessern der Architektur durch Modellierung (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**Definieren der Architektur**:<br /><br /> -Modellieren Sie die umfangreiche Struktur des Software Systems und die Entwurfsmuster, indem Sie UML-Komponenten-, Klassen-und Sequenzdiagramme zeichnen.<br />-Definieren und Erzwingen von Einschränkungen für Abhängigkeiten zwischen den Komponenten des Codes durch das Erstellen von ebenendiagrammen.|-   [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)<br />-   [Modellieren der Architektur Ihrer APP](../modeling/model-your-app-s-architecture.md)<br />-   - [Video: verbessern der Architektur durch Modellierung (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [-Video: Verwenden von ebenendiagrammen zum Entwerfen und Überprüfen der Architektur (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Überprüfen des Systems anhand der Anforderungen und des beabsichtigten Entwurfs:**<br /><br /> -Definieren von Akzeptanz Tests oder Systemtests basierend auf den Anforderungs Modellen. Dies schafft eine enge Beziehung zwischen den Tests und den Anforderungen der Benutzer und erleichtert das Aktualisieren des Systems bei geänderten Anforderungen.<br />-Überprüfen von Code Abhängigkeiten mit ebenendiagrammen, die die vorgesehene Architektur beschreiben und Änderungen verhindern, die mit dem Entwurf in Konflikt stehen können.|-   Überprüfen des [Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)<br />-   [-Video: Verwenden von ebenendiagrammen zum Entwerfen und Überprüfen der Architektur (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br /> -Platzieren Sie Code Maps, Modellierungs Projekte, UML-Diagramme und ebenendiagramme unter Team Foundation-Versionskontrolle, damit Sie Sie freigeben können.|Arbeiten mehrere Benutzer mit diesen Elementen unter Team Foundation-Versionskontrolle, verwenden Sie diese Richtlinien, um Probleme mit der Versionskontrolle zu vermeiden:<br /><br /> -   [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generieren oder Konfigurieren von Teilen der Anwendung aus UML- oder domänenspezifischen Sprachen**:<br /><br /> : Sorgen Sie dafür, dass Ihr Design besser auf die Anforderungen von Anforderungen und auf einfache Weise in einer Produktlinie reagiert.|-   [generieren und Konfigurieren der APP aus Modellen](../modeling/generate-and-configure-your-app-from-models.md)|
|**Anpassen von Modellen und Diagrammen**:<br /><br /> -Passen Sie Modelle an die Verwendung durch das Projekt an, indem Sie zusätzliche Eigenschaften für UML-Elemente definieren, Validierungs Einschränkungen, um sicherzustellen, dass Ihre Modelle Ihren Geschäftsregeln entsprechen, sowie zusätzliche Menübefehle und Toolbox Elemente.<br />-Erstellen Sie eigene domänenspezifische Sprachen.|-   [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK für Visual Studio-domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br /> -Verwenden Sie Textblöcke und Steuerelement Logik in Vorlagen, um textbasierte Dateien zu generieren.|-   [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Typen von Modellen und deren Anwendungsmöglichkeiten

|**Modelltyp und typische Anwendungsmöglichkeiten**|
|-------------------------------------|
|**Codezuordnungen**<br /><br /> Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Überprüfen Sie den Programmcode, damit Sie die Struktur und die zugehörigen Abhängigkeiten besser verstehen können, wie Sie Sie aktualisieren und die Kosten für vorgeschlagene Änderungen schätzen können.<br /><br /> Thema<br /><br /> -   Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Ermitteln potenzieller Probleme mithilfe Code Map](../modeling/find-potential-problems-using-code-map-analyzers.md) Analyzer|
|**Ebenendiagramm**<br /><br /> Anhand von Ebenendiagrammen können Sie die Struktur einer Anwendung als einen Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Sie können die Validierung ausführen, um Konflikte zwischen Abhängigkeiten im Code und den in einem Ebenendiagramm beschriebenen Abhängigkeiten zu ermitteln.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Die Struktur der Anwendung wird durch zahlreiche Änderungen im Laufe ihrer Lebensdauer stabilisiert.<br />-Erkennen Sie unbeabsichtigte Abhängigkeits Konflikte, bevor Sie Änderungen am Code einchecken.<br /><br /> Thema<br /><br /> -   [Erstellen von ebenendiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Überprüfen von Code mit ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|
|**UML-Modell**<br /><br /> Ein UML-Modell beinhaltet mehrere Ansichten, einschließlich Klasse, Komponente, Anwendungsfall sowie Aktivitäts- und Sequenzdiagramme. Sie können UML speziell für Ihre Anwendungsdomäne anpassen. Sie können z. B. Tags, zusätzliche Informationen und Einschränkungen an die Modellelemente anfügen. Außerdem können Sie Tools definieren, mit denen die Modelle bearbeitet werden können. Weitere Informationen finden [Sie unter Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md).<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> : Beschreiben Sie die Anforderungen und den Entwurf. UML lässt sich bei der Entwicklung von Anwendungen schnell anwenden. Weitere Informationen finden [Sie unter Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md).<br />: Generieren oder konfigurieren Sie Tests oder Teile einer Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation anzupassen und die Generierungsvorlagen oder konfigurierbare Anwendung zu entwickeln. Weitere [Informationen finden Sie unter Generieren und Konfigurieren der APP aus Modellen](../modeling/generate-and-configure-your-app-from-models.md).<br />: Allgemeine Beschreibung und Codegenerierung oder-Konfiguration in kleineren Projekten.|
|**Domänenspezifische Sprache (DSL)**<br /><br /> Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist sie normalerweise eine grafische Darstellung.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Hiermit werden Teile der Anwendung generiert oder konfiguriert. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.<br />-Bei großen Projekten oder in Produktlinien, in denen die Investition in die Entwicklung der DSL und ihrer Tools durch die Verwendung in mehr als einem Projekt zurückgegeben wird.<br /><br /> Thema<br /><br /> -   [Modeling SDK für Visual Studio-domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Wo kann ich weitere Informationen abrufen?

|||
|-|-|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Siehe auch

- [Neuerungen bei der Modellierung in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps und Anwendungslebenszyklus-Verwaltung](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
