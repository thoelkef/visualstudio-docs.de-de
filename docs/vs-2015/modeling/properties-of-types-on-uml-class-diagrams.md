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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671321"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Eigenschaften von Typen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Klassendiagramm ist ein *Typ* eine Klasse, eine Schnittstelle oder eine Enumeration.

> [!NOTE]
> In diesem Thema werden die Eigenschaften von Typen in UML-Klassendiagrammen behandelt. Weitere Informationen finden Sie unter den folgenden Themen:

- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)

- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)

- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Eigenschaften
 Dies sind die Eigenschaften einer Klasse, Schnittstelle oder Enumeration.

 Um die Eigenschaften eines Typs anzuzeigen, klicken Sie im Diagramm oder im **UML-Modell-Explorer**mit der rechten Maustaste auf den Typ, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

|**Eigenschaft**|**Standard**|Kommt vor in|BESCHREIBUNG|
|------------------|-----------------|----------------|-----------------|
|**Name**|Ein Standardname|Alle Elemente|Bezeichnet das Element.|
|**Qualifizierter Name**|Enthaltendes Paket :: Typname|Alle Elemente|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|
|**Farbe**|Standardwert für die Art des Typs|Alle Elemente|Die Farbe dieser Form. Im Gegensatz zu den anderen Eigenschaften ist dies keine Eigenschaft des zugrundeliegenden Modellelements. Verschiedene Ansichten desselben Typs können unterschiedliche Farben haben.|
|**Ist abstrakt**|Falsch|Klasse|Bei „true“ kann die Klasse kann nicht instanziiert werden und ist für die Verwendung als Basisklasse bestimmt.|
|**Is Leaf**|Falsch|Klasse, Schnittstelle|Bei „true“ soll der Typ nicht über abgeleitete Typen verfügen.|
|**Ist aktiv**|Falsch|Klasse|Bei „true“ wird jede Instanz dieses Typs einem Kontrollthread zugeordnet.|
|**Sichtbarkeit**|Öffentlich|Klasse, Schnittstelle, Enumeration|-Public-Global sichtbar.<br />-Private: dieser Typ ist innerhalb des Pakets sichtbar, das es besitzt.<br />-Das Paket ist innerhalb des Pakets sichtbar.|
|**Arbeitselemente**|0 zugeordnet|Alle Elemente|Die Anzahl von Arbeitselemente, die diesem Element zugeordnet sind. Informationen zum Zuordnen von Arbeitsaufgaben finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Beschreibung**|(leer)|Alle Elemente|Sie können hier allgemeine Hinweise zum Element angeben.|
|**Vorlagen Bindung**|(none)|Klasse, Schnittstelle, Enumeration|Wenn nicht leer, wird dieser Typ definiert, indem Parameterwerte an diese Vorlagenklasse gebunden werden. Erweitern Sie die Eigenschaft, um die Bindungen der Vorlagenparameter anzuzeigen.|
|**Vorlagen Parameter**|(none)|Klasse, Schnittstelle, Enumeration|Wenn nicht leer, ist dies eine Vorlagenklasse, deren Parameter hier aufgeführt sind. Um Parameter hinzuzufügen oder die Eigenschaften einzelner Parameter anzuzeigen, klicken Sie auf **[...]**.|

## <a name="see-also"></a>Weitere Informationen
 [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Eigenschaften von Operationen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md) [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)
