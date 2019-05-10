---
title: Erstellen von Modellen für Ihre app | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: feb0c1a5f486654844c592b6b946dedc9e2e02c0
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "59001179"
---
# <a name="create-models-for-your-app"></a>Erstellen von Modellen für Ihre App
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Modellierungsdiagrammen können Sie Ideen zum Code und den Benutzeranforderungen, die das Softwaresystem unterstützen muss, verstehen, verdeutlichen und kommunizieren. Beispielsweise können Sie zum Beschreiben und Kommunizieren von Benutzeranforderungen UML-Anwendungsfalldiagramme (Unified Modeling Language) sowie Aktivitäts-, Klassen- und Sequenzdiagramme verwenden. Um die Funktionalität Ihres Systems zu beschreiben und zu kommunizieren, können Sie UML-Komponenten-, Klassen-, Aktivitäts- und Sequenzdiagramme verwenden.  
  
 Finden Sie unter [Channel 9-Video: Verbessern der Architektur durch Modellierung](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 In dieser Version können Sie die folgenden UML-Diagramme erstellen:  
  
|**Diagramm**|**Zeigt Folgendes an**|  
|-----------------|---------------|  
|[UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)|Arbeitsfluss zwischen Aktionen und Teilnehmern in einem Geschäftsprozess|  
|[UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)|Komponenten eines Systems, ihre Schnittstellen, Ports und Beziehungen|  
|[UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)|Typen, die zum Speichern und Austauschen von Daten im System und deren Beziehungen verwendet werden|  
|[UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)|Sequenzen von Interaktionen zwischen Objekten, Komponenten, Systemen oder Akteuren|  
|[UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)|Benutzerziele und Aufgaben, die ein System unterstützt|  
  
 Welche Versionen von Visual Studio die einzelnen Diagrammtypen unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Um die Architektur eines Systems oder von vorhandenem Code visuell darzustellen, erstellen Sie die folgenden Diagramme:  
  
|**Diagramm**|**Zeigt Folgendes an**|  
|-----------------|---------------|  
|[Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)|Die allgemeine Architektur des Systems|  
|Codezuordnungen<br /><br /> [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)|Abhängigkeiten und andere Beziehungen in vorhandenem Code|  
|Von Code generierte Klassendiagramme<br /><br /> [Arbeiten mit Klassendiagrammen (Klassen-Designer)](../ide/working-with-class-diagrams-class-designer.md)|Typen und ihre Beziehungen in .NET-Code|  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|**Topic**|**Aufgabe**|  
|---------------|--------------|  
|[Erstellen von UML-Modellierungsprojekten und -Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Erstellen von Modellen** und Hinzufügen von Diagrammen.|  
|[Bearbeiten von UML-Modellen und -Diagrammen](../modeling/edit-uml-models-and-diagrams.md)|**Zeichnen von Diagrammen** zur Bearbeitung des Modells.|  
|[Definieren von Paketen und Namespaces](../modeling/define-packages-and-namespaces.md)|**Erstellen von Paketen** zum Unterteilen eines Modells in Einheiten, die verschiedene Teammitglieder arbeiten können.|  
|[Generieren von Code aus UML-Klassendiagrammen](../modeling/generate-code-from-uml-class-diagrams.md)|**Generieren Sie C#-Code aus Klassendiagrammen** auf Ihre Implementierung zu starten.|  
|[Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Anpassen von Modellelementen** mithilfe von Stereotypen, um die standardmäßigen UML-Modellelemente für bestimmte Zwecke zu erweitern.|  
|[Verknüpfen von Modellelementen und Arbeitselementen](../modeling/link-model-elements-and-work-items.md)|**Erstellen Sie Verknüpfungen zwischen Modellelementen und Arbeitsaufgaben** zum Nachverfolgen von Aufgaben, Testfälle, Fehler, Anforderungen, Probleme oder andere Arten von Arbeitsschritten, die bestimmte Teile des Modells zugeordnet sind.|  
|[Exportieren von Diagrammen als Bild](../modeling/export-diagrams-as-images.md)|**Speichern Sie Ihre Modelle und Diagramme** , damit Sie sie für andere Benutzer freigeben können, auch für diejenigen, die nicht zu verwenden [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
|**Topic**|**Aufgabe**|  
|---------------|--------------|  
|[Visualisieren von Code](../modeling/visualize-code.md)|Erstellen Sie Code Maps und Ebenendiagramme zum besseren Verständnis von unbekanntem Code.|  
|[Modellieren von Benutzeranforderungen](../modeling/model-user-requirements.md)|Verwenden Sie Modelle, um die Anforderungen der Benutzer zu verdeutlichen und zu kommunizieren.|  
|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|Verwenden Sie Modelle, um die Gesamtstruktur und das Verhalten des Systems zu beschreiben und um sicherzustellen, dass es die Anforderungen der Benutzer erfüllt.|  
|[Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)|Stellen Sie sicher, dass Ihre Software mit den Anforderungen Ihrer Benutzer und der Gesamtarchitektur des Systems konsistent bleibt.|  
|[Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)<br /><br /> [Verwenden von Modellen in Agile-Entwicklung](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Verwenden Sie Modelle, um das Systems während seiner Entwicklung zu verstehen und zu ändern.|  
|[Strukturieren der Modellierungslösung](../modeling/structure-your-modeling-solution.md)|Organisieren Sie Modelle in einem großen oder mittleren Projekt.|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
|**Kategorie**|**Links**|  
|------------------|---------------|  
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|
