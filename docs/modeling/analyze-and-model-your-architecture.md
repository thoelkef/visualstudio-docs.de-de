---
title: Analysieren und zu modellieren die Architektur | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Analysieren und Modellieren der Architektur
Stellen Sie sicher, dass Ihre app architektonische Anforderungen erfüllt, mithilfe von Visual Studio-Architektur und-Modellierungstools zum Entwerfen und modellieren Ihrer app. 

* Wenn Sie Visual Studio zum Visualisieren von Codestruktur, -verhalten und -beziehungen verwenden, können Sie vorhandenen Programmcode besser verstehen. 

* Informieren Sie Ihr Team benötigt architekturabhängigkeiten bereitzustellen.  
  
* Im Rahmen des Entwicklungsprozesses können Sie Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen.

Finden Sie unter [Szenario: Ändern des Entwurfs mithilfe von Visualisierung und Modellierung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>Aktion  
  
|||  
|-|-|  
|**Visualisieren von Code**:<br /><br /> -Finden Sie unter Organisation und Beziehungen des Codes von Code Maps erstellen. Sie können Abhängigkeiten zwischen Assemblys, Namespaces, Klassen, Methoden usw. visualisieren.<br />-Finden Sie die Klassenstruktur und Elemente für ein bestimmtes Projekt Klassendiagramme aus Code erstellen.<br />-Suchen von Konflikten zwischen Code und dem Entwurf erstellen Sie Abhängigkeitsdiagramme, um Code zu überprüfen.|-   [Visualisieren von code](../modeling/visualize-code.md)<br />-   [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Verstehen von Code mit Visual Studio 2015 Code Maps Entwurf](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Definieren der Architektur**:<br /><br /> -Definieren und Erzwingen von Einschränkungen für die Abhängigkeiten zwischen den Komponenten des Codes, indem Sie Abhängigkeitsdiagramme erstellen.|-   [Video: Überprüfen Sie Architektur Abhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Überprüfen Sie das System mit den Anforderungen und des beabsichtigten Entwurfs:**<br /><br /> -Überprüfen Sie codeabhängigkeiten mit Abhängigkeitsdiagramme, die die beabsichtigte Architektur beschreiben und zu verhindern, dass Änderungen, die einen Konflikt mit dem Entwurf verursachen könnten.|-   [Video: Überprüfen Sie Architektur Abhängigkeiten mit Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Freigeben von Modellen und Code Maps mithilfe der Team Foundation-Versionskontrolle**:<br /><br /> -Fügen Sie die Code Maps, Projekte und Deoendency Diagrammen unter Team Foundation-Versionskontrolle, damit Sie freigegeben werden können.|Arbeiten mehrere Benutzer mit diesen Elementen unter Team Foundation-Versionskontrolle, verwenden Sie diese Richtlinien, um Probleme mit der Versionskontrolle zu vermeiden:<br /><br /> -   [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Anpassen von Modellen und Diagrammen**:<br /><br /> -Erstellen Sie eigene domänenspezifische Sprachen.|-   [Modeling SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generieren Sie Text mithilfe von T4-Vorlagen**:<br /><br /> -Verwenden Sie Textblöcken und Steuerelementlogik in Vorlagen, um textbasierte Dateien zu generieren.<br /> -T4 Vorlage Builds mit MSBuild in Visual Studio enthalten|-   [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md)|

Welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Typen von Modellen und deren Anwendungsmöglichkeiten  
  
|**Modelltyp und typische Anwendungsmöglichkeiten**|  
|-------------------------------------|  
|**Codezuordnungen**<br /><br /> Mit Code Maps können Sie die Organisation und die Beziehungen im Code anzeigen.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Überprüfen Sie Programmcode, sodass Sie seine Struktur und seine Abhängigkeiten besser verstehen können, aktualisieren Sie diese, und schätzen die Kosten für vorgeschlagene Änderungen zu.<br /><br /> Thema<br /><br /> -   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzer](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Abhängigkeitsdiagramm**<br /><br /> Abhängigkeit von Ebenendiagrammen können Sie die Struktur einer Anwendung als Satz von Ebenen oder Blöcken mit expliziten Abhängigkeiten definieren. Sie können die Überprüfung aus, um Konflikte zwischen Abhängigkeiten im Code und in einem Abhängigkeitsdiagramm beschriebenen Abhängigkeiten ermitteln ausführen.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Stabilisieren der Struktur der Anwendung anhand zahlreicher Änderungen während der gesamten Lebensdauer.<br />– Ermitteln Sie unbeabsichtigte abhängigkeitskonflikte, bevor Sie Änderungen am Code einchecken.<br /><br /> Thema<br /><br /> -   [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)<br />-   [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)|  
|**Domänenspezifische Sprache (DSL)**<br /><br /> Eine DSL ist eine Notation, die für einen bestimmten Zweck entworfen wird. In Visual Studio ist sie normalerweise eine grafische Darstellung.<br /><br /> Typische Anwendungsmöglichkeiten:<br /><br /> -Generieren oder Konfigurieren von Teilen der Anwendung. Es ist ein wenig Aufwand erforderlich, um die Notation und die Tools zu entwickeln. Dadurch können Sie jedoch meist eine bessere Anpassung an die Domäne als bei einer UML-Anpassung erreichen.<br />-Bei großen Projekten oder bei Produktlinien, in denen die Investitionen in die Entwicklung DSL und deren Tools durch ihre Verwendung in mehr als ein Projekt zurückgegeben.<br /><br /> Thema<br /><br /> -   [Modeling SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Wo kann ich weitere Informationen abrufen?  
  
[Visual Studio-Visualisierungs & Modeling Tools-Forum](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps und Application Lifecycle Management](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

