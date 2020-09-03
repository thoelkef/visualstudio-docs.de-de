---
title: Eigenschaften von Elementen in UML-Anwendungsfall Diagrammen | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671416"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Anwendungsfalldiagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, klicken Sie mit der rechten Maustaste auf das Element im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

> [!NOTE]
> In diesem Thema werden die Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen behandelt. Weitere Informationen zum Lesen von UML-Aktivitäts Diagrammen finden Sie unter [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md). Weitere Informationen zum Zeichnen von UML-Aktivitäts Diagrammen finden Sie unter [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Eigenschaften von Elementen

|Eigenschaft|Standard|Element|BESCHREIBUNG|
|--------------|-------------|-------------|-----------------|
|**Name**|Ein Standardname|All|Bezeichnet das Element.|
|**Qualifizierter Name**|Paket :: Name|All|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|
|**Arbeitselemente**|0 zugeordnet|All|Die Anzahl von Arbeitselemente, die diesem Element zugeordnet sind. Informationen zum Zuordnen von Arbeitsaufgaben finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Beschreibung**|(none)|All|Hier können Sie allgemeine Anmerkungen zum Element eingeben.|
|**Farbe**|(Standard)|All|Die Farbe der Form. Im Gegensatz zu anderen Eigenschaften ist dies keine Eigenschaft des Elements, die die Form anzeigt.|
|**Abbildpfad**|(none)|Akteur|Der Dateipfad eines Bilds, das statt des Standardakteursymbols verwendet werden soll. Bei dem Symbol sollte es sich um eine Ressourcendatei im Visual Studio-Projekt handeln.|
|**Gegen**|(none)|Anwendungsfall|Das Subsystem oder ein anderer Typ, der den Anwendungsfall besitzt.<br /><br /> Sie können sie festlegen, indem Sie den Anwendungsfall in einem Subsystem im Diagramm platzieren.|
|**Sichtbarkeit**|Öffentlich|Anwendungsfall, Akteur, Subsystem|**Public** -Global sichtbar.<br /><br /> **Paket** -sichtbar innerhalb des Pakets.|
|**IsAbstract**|Falsch|Anwendungsfall, Akteur, Subsystem|Bei „true“ kann der Typ nicht instanziiert werden und dient als Basis für die Spezialisierung durch andere Definitionen.|
|**Wird indirekt instanziiert**|Richtig|Subsystem|Das Subsystem ist nur als Entwurfsartefakt vorhanden. Zur Laufzeit sind nur ihre Teile vorhanden.|
|**Link**|(none)|Artefakt|Die URL oder der Dateipfad des Diagramms oder Dokuments, zu dem das Artefakt einen Link bereitstellt.|

 Eine Liste der Eigenschaften von Zuordnungen finden Sie unter [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Weitere Informationen
 [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)
