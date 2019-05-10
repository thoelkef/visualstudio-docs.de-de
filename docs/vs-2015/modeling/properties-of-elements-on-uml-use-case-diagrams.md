---
title: Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b52afab80bc22c03dc5ff980b937cad53869f5db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444418"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Anwendungsfalldiagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, die Maustaste des Elements im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden in der **Eigenschaften** Fenster.  
  
> [!NOTE]
> In diesem Thema werden die Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen behandelt. Weitere Informationen zum Lesen von UML-Aktivitätsdiagrammen finden Sie unter [UML-Anwendungsfalldiagramme: Reference (Referenz zu UML-Klassendiagrammen)](../modeling/uml-use-case-diagrams-reference.md). Weitere Informationen über das Zeichnen von UML-Aktivitätsdiagrammen finden Sie unter [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Eigenschaften von Elementen  
  
|Eigenschaft|Standard|Element|Beschreibung|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Ein Standardname|Alle|Bezeichnet das Element.|  
|**Qualifizierter Name**|Paket:: Name|Alle|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|  
|**Typen von Arbeitselementen**|0 zugeordnet|Alle|Die Anzahl von Arbeitsaufgaben, die diesem Element zugeordnet sind. Um Arbeitsaufgaben zu verknüpfen, finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).|  
|**Beschreibung**|(keine)|Alle|Hier können Sie allgemeine Anmerkungen zum Element eingeben.|  
|**Farbe**|(Standard)|Alle|Die Farbe der Form. Im Gegensatz zu anderen Eigenschaften ist dies keine Eigenschaft des Elements, die die Form anzeigt.|  
|**Pfad des containerimages**|(keine)|Akteur|Der Dateipfad eines Bilds, das statt des Standardakteursymbols verwendet werden soll. Bei dem Symbol sollte es sich um eine Ressourcendatei im Visual Studio-Projekt handeln.|  
|**Themen**|(keine)|Anwendungsfall|Das Subsystem oder ein anderer Typ, der den Anwendungsfall besitzt.<br /><br /> Sie können sie festlegen, indem Sie den Anwendungsfall in einem Subsystem im Diagramm platzieren.|  
|**Sichtbarkeit**|Public|Anwendungsfall, Akteur, Subsystem|**Öffentliche** – global sichtbar.<br /><br /> **Paket** – sichtbar innerhalb des Pakets.|  
|**IsAbstract**|False|Anwendungsfall, Akteur, Subsystem|Bei „true“ kann der Typ nicht instanziiert werden und dient als Basis für die Spezialisierung durch andere Definitionen.|  
|**Is Indirectly Instantiated**|True|Subsystem|Das Subsystem ist nur als Entwurfsartefakt vorhanden. Zur Laufzeit sind nur ihre Teile vorhanden.|  
|**Link**|(keine)|Artefakt|Die URL oder der Dateipfad des Diagramms oder Dokuments, zu dem das Artefakt einen Link bereitstellt.|  
  
 Eine Liste der Eigenschaften von Zuordnungen, finden Sie unter [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)
