---
title: Eigenschaften von Elementen in UML-Komponentendiagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c77c9e6be69604176c470fa8de9e33a74c05532
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291420"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Eigenschaften von Elementen in UML-Komponentendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Komponentendiagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, die Maustaste des Elements im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden in der **Eigenschaften** Fenster.  
  
> [!NOTE]
>  In diesem Thema werden die Eigenschaften von Elementen in UML-Komponentendiagrammen behandelt. Weitere Informationen zum Lesen von UML-Komponentendiagrammen finden Sie unter [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md). Weitere Informationen über das Zeichnen von UML-Komponentendiagrammen finden Sie unter [UML-Komponentendiagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Eigenschaften von Elementen  
  
|Eigenschaft|Standard|Element|Beschreibung|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Ein Standardname|Alle|Bezeichnet das Element.|  
|**Qualifizierter Name**|Namespace :: Name|Alle|Bezeichnet das Element eindeutig.<br /><br /> Dem Namen einer Komponente oder eines Typs wird der qualifizierte Name des Pakets vorangestellt, in dem die Komponente bzw. der Typ enthalten ist.<br /><br /> Dem Namen eines Teils oder Ports wird der qualifizierte Name der Komponente vorangestellt, die Besitzer des Teils bzw. Ports ist.|  
|**Typen von Arbeitselementen**|0 zugeordnet|Alle|Die Anzahl von Arbeitsaufgaben, die diesem Element zugeordnet sind. Um Arbeitsaufgaben zu verknüpfen, finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).|  
|**Beschreibung**|(keine)|Alle|Hier können Sie allgemeine Anmerkungen zum Element eingeben.|  
|**Farbe**|(Standardeinstellung für den Typ)|Komponente, Teil, Delegierung, Teilassembly|Die Farbe der Form. Im Gegensatz zu anderen Eigenschaften ist dies die Farbe der Form und nicht des Modellelements, das von der Form angezeigt wird.|  
|**Is Indirectly Instantiated**|True|Komponente|Die Komponente ist nur als Entwurfsartefakt vorhanden. Zur Laufzeit sind nur ihre Teile vorhanden.|  
|**Ist abstrakt**|False|Komponente|Die Komponentendefinition kann nur als Verallgemeinerung verwendet werden, von der spezifischere Komponenten abgeleitet werden können.|  
|**Sichtbarkeit**|Public|Komponente, Teil, Port|**Öffentliche** – global sichtbar.<br /><br /> **Paket** – sichtbar innerhalb des Pakets.<br /><br /> **Private** – sichtbar innerhalb der besitzenden Komponente.<br /><br /> **Geschützte** – sichtbar für Komponenten, die vom Besitzer abgeleitet sind.|  
|**Type**|Typ bei der Erstellung|Segment<br /><br /> Port|Der Typ eines Teils ist eine Komponente oder Klasse.<br /><br /> Der Typ eines Ports ist eine Schnittstelle.|  
|**Multiplizität**|1|Segment<br /><br /> Port|Gibt an, wie viele Instanzen des angegebenen Typs einen Teil der übergeordneten Komponente bilden.<br /><br /> `1` – genau eine Instanz.<br /><br /> `0..1` – eine oder keine Instanz.<br /><br /> `*` – eine Auflistung einer beliebigen Anzahl von Instanzen.<br /><br /> `n..m` – eine Auflistung von n bis m Instanzen.|  
|**Trifft**|False|Port|Wenn „true“, werden Meldungen an diesen Port von Aktivitäten oder Vorgängen behandelt, die als Teil der Komponente statt als Teile des Teils beschrieben werden.|  
|**Ist-Dienst**|False|Port|Wenn „true“, ist dieser Port Teil der veröffentlichten Schnittstelle dieser Komponente.|  
|**LinkedPackage**|Modell|Diagramm|Der Standardnamespace für diesem Diagramm hinzugefügte Elemente.|  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)



