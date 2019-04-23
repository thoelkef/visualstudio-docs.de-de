---
title: Eigenschaften von Typen in UML-Klassendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17d18a485e57b896aaf3f40b0cfdab63e10dce2c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062229"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Eigenschaften von Typen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Klassendiagramm eine *Typ* ist eine Klasse, eine Schnittstelle oder eine Enumeration.  
  
> [!NOTE]
>  In diesem Thema werden die Eigenschaften von Typen in UML-Klassendiagrammen behandelt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)  
  
- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Eigenschaften  
 Dies sind die Eigenschaften einer Klasse, Schnittstelle oder Enumeration.  
  
 Um die Eigenschaften eines Typs anzuzeigen, Maustaste den Typ im Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden in der **Eigenschaften** Fenster.  
  
|**Property**|**Default**|Angezeigt in|Beschreibung|  
|------------------|-----------------|----------------|-----------------|  
|**Name**|Ein Standardname|Alle Elemente|Bezeichnet das Element.|  
|**Qualifizierter Name**|Enthaltendes Paket:: Typname|Alle Elemente|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|  
|**Farbe**|Standardwert für die Art des Typs|Alle Elemente|Die Farbe dieser Form. Im Gegensatz zu den anderen Eigenschaften ist dies keine Eigenschaft des zugrundeliegenden Modellelements. Verschiedene Ansichten desselben Typs können unterschiedliche Farben haben.|  
|**Ist abstrakt**|False|Klasse|Bei „true“ kann die Klasse kann nicht instanziiert werden und ist für die Verwendung als Basisklasse bestimmt.|  
|**Wird die Blattebene**|False|Klasse, Schnittstelle|Bei „true“ soll der Typ nicht über abgeleitete Typen verfügen.|  
|**Ist aktiv**|False|Klasse|Bei „true“ wird jede Instanz dieses Typs einem Kontrollthread zugeordnet.|  
|**Sichtbarkeit**|Public|Klasse, Schnittstelle, Enumeration|-Public – global sichtbar.<br />-Privat – dieser Typ innerhalb des Pakets sichtbar ist, die dieser besitzt.<br />-Paket – sichtbar innerhalb des Pakets.|  
|**Typen von Arbeitselementen**|0 zugeordnet|Alle Elemente|Die Anzahl von Arbeitsaufgaben, die diesem Element zugeordnet sind. Um Arbeitsaufgaben zu verknüpfen, finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).|  
|**Beschreibung**|(leer)|Alle Elemente|Sie können hier allgemeine Hinweise zum Element angeben.|  
|**Vorlagenbindung**|(keine)|Klasse, Schnittstelle, Enumeration|Wenn nicht leer, wird dieser Typ definiert, indem Parameterwerte an diese Vorlagenklasse gebunden werden. Erweitern Sie die Eigenschaft, um die Bindungen der Vorlagenparameter anzuzeigen.|  
|**Vorlagenparameter**|(keine)|Klasse, Schnittstelle, Enumeration|Wenn nicht leer, ist dies eine Vorlagenklasse, deren Parameter hier aufgeführt sind. Um Parameter hinzuzufügen oder die Eigenschaften einzelner Parameter anzuzeigen, klicken Sie auf **[...]** .|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Eigenschaften von Operationen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)
