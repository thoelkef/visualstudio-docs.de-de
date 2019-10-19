---
title: Analysieren und Modellieren der Architektur
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f669b8e0b737aa945641d1e7a32c7c05bee3c711
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654346"
---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur

Stellen Sie sicher, dass Ihre APP die architektonischen Anforderungen erfüllt, indem Sie die Architektur-und Modellierungstools von Visual Studio zum Entwerfen und modellieren Ihrer APP verwenden

* Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen.

* Informieren Sie Ihr Team über die Notwendigkeit, architektonische Abhängigkeiten zu berücksichtigen.

* Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen.

Weitere Informationen finden [Sie unter Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Artikel Referenz

|||
|-|-|
|**Visualisieren von Code**:<br /><br />-Sehen Sie sich die Organisation und Beziehungen des Codes an, indem Sie Code Maps erstellen. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />-Zeigen Sie die Klassenstruktur und Member für ein bestimmtes Projekt an, indem Sie Klassendiagramme aus Code erstellen.<br />-Suchen Sie Konflikte zwischen dem Code und dessen Entwurf, indem Sie Abhängigkeits Diagramme erstellen, um Code zu validieren.|- [Visualisieren von Code](../modeling/visualize-code.md)<br />- [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- -[Video: Grundlegendes zum Entwerfen aus Code mit Visual Studio 2015-Code Maps](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- -[Video: Überprüfen der Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definieren der Architektur**:<br /><br />-Definieren und Erzwingen von Einschränkungen für Abhängigkeiten zwischen den Komponenten des Codes durch das Erstellen von Abhängigkeits Diagrammen.|- -[Video: Überprüfen der Architektur Abhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Überprüfen des Systems anhand der Anforderungen und des beabsichtigten Entwurfs:**<br /><br />-Überprüfen von Code Abhängigkeiten mit Abhängigkeits Diagrammen, die die vorgesehene Architektur beschreiben und Änderungen verhindern, die mit dem Entwurf in Konflikt stehen können.|- -[Video: Überprüfen der Architektur Abhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Anpassen von Modellen und Diagrammen**:<br /><br />-Erstellen Sie eigene domänenspezifische Sprachen.|- [Modeling SDK für Visual Studio-domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br />-Verwenden Sie Textblöcke und Steuerelement Logik in Vorlagen, um textbasierte Dateien zu generieren.<br /> -T4-Vorlagen Build mit MSBuild in Visual Studio enthalten|- [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md)|
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br />-Platzieren Sie Code Maps, Projekte und Abhängigkeits Diagramme unter Team Foundation-Versionskontrolle, damit Sie diese freigeben können.| |

Welche Editionen von Visual Studio die einzelnen Features unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

## <a name="types-of-models-and-typical-uses"></a>Modelltypen und typische Verwendungsmöglichkeiten

### <a name="code-maps"></a>Codezuordnungen

Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.

**Typische Verwendungszwecke:**

- Überprüfen Sie Programmcode, um sich mit der Struktur, den Abhängigkeiten sowie dem Aktualisieren vertraut zu machen und um die Kosten für vorgeschlagene Änderungen einschätzen zu können.

**Sieh:**

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Abhängigkeits Diagramme

Mithilfe von Abhängigkeits Diagrammen können Sie die Struktur einer Anwendung als Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Die Live Validierung zeigt Konflikte zwischen Abhängigkeiten im Code und den in einem Abhängigkeits Diagramm beschriebenen Abhängigkeiten an.

**Typische Verwendungszwecke:**

- Stabilisieren der Struktur der Anwendung anhand zahlreicher Änderungen während der gesamten Lebensdauer.
- Ermitteln Sie unbeabsichtigte Abhängigkeitskonflikte, bevor Sie Änderungen am Code einchecken.

**Sieh:**

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Domänenspezifische Sprache (DSL)

Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist es in der Regel grafisch.

**Typische Verwendungszwecke:**

- Generieren oder Konfigurieren von Teilen einer Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.
- Bei großen Projekten oder bei Produktlinien, bei denen die Investitionen in die Entwicklung DSL und deren Tools sich deshalb lohnen, weil die DSL für mehrere Projekte verwendet werden kann.

**Sieh:**

- [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Siehe auch

- [Neuerungen bei der Modellierung in Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps und Anwendungslebenszyklus-Verwaltung](/azure/devops/user-guide/devops-alm-overview)
