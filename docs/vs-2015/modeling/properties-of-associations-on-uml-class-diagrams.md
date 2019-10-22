---
title: Eigenschaften von Zuordnungen in UML-Klassendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652091"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Eigenschaften von Zuordnungen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Klassendiagramm können Sie *Zuordnungen* zwischen einem beliebigen Paar von Typen zeichnen. Ein Typ ist eine Klasse, Schnittstelle oder Enumeration.

 Eine Zuordnung gibt an, dass das System, das Sie entwickeln, bestimmte Links zwischen den Instanzen der zugeordneten Typen speichert. Im Allgemeinen sagt dies nichts über die Implementierung der Links aus. Sie können z. B. Zeiger, Zeilen in einer Tabelle, Namen in XML, auf die verwiesen wird, usw. sein.

 Eine Zuordnung ist eine schematische Methode zur Darstellung eines Attributs oder Attributpaars. Wenn Sie z. B. eine Klasse „Restaurant“ so definiert haben, dass sie ein Attribut vom Typ „Menu“ aufweist, können Sie dieselbe Definition durch Zeichnen einer Zuordnung zwischen „Restaurant“ und „Menu“ angeben.

 Um eine Zuordnung zu zeichnen, klicken Sie in der Toolbox auf **Association** , klicken Sie auf den ersten Typ und dann auf den zweiten. Sie können den gleichen Typ zweimal auswählen, um anzuzeigen, dass Instanzen mit anderen Instanzen des gleichen Typs verknüpft werden können.

## <a name="properties"></a>Eigenschaften
 Dies sind die Eigenschaften einer Zuordnung in einem UML-Klassendiagramm.

 Klicken Sie mit der rechten Maustaste auf die Zuordnung, und klicken Sie dann auf **Eigenschaften**, um die Eigenschaften einer Zuordnung anzuzeigen. Die Eigenschaften werden im Eigenschaftenfenster angezeigt.

 Einige Eigenschaften sind auch im Diagramm sichtbar, wie in der folgenden Abbildung dargestellt.

 ![Eigenschaften von "Zuweisungen"](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Property**|Beschreibung|
|------------------|-----------------|
|**Name (1)**|Identifiziert die Zuordnung. Diese Eigenschaft wird auch in der Nähe des Mittelpunkts der Zuordnung im Diagramm angezeigt.|
|**Qualifizierter Name**|Identifiziert die Zuordnung eindeutig. Der qualifizierte Name des Pakets, das die erste Rolle der Zuordnung enthält, wird vorangestellt.|
|**Arbeitselemente**|Die Anzahl der Arbeitsaufgaben, die mit dieser Zuordnung verknüpft sind. Informationen zum Verknüpfen von Arbeits Elementen finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Farbe**|Die Farbe des Verbindungselements. Im Gegensatz zu den anderen Eigenschaften ist dies eine Eigenschaft dieser Ansicht der Zuordnung und keine Eigenschaft der zugrunde liegenden Beziehung im Modell.|
|**Erste Rolle**<br /><br /> **Zweite Rolle**|Jedes Ende der Zuordnung wird als „Rolle“ bezeichnet. Jede Rolle beschreibt die Eigenschaften des entsprechenden Attributs der Klasse am entgegengesetzten Ende der Zuordnung.<br /><br /> Im Beispieldiagramm verfügt die Zuordnung zwischen „Menu“ und „Menu Item“ über Rollen namens „Menu“ und „Contents“.<br /><br /> „Contents“ ist der Name eines Attributs in der Menu-Klasse.|

### <a name="properties-of-each-role"></a>Eigenschaften der einzelnen Rollen
 Um die Eigenschaften der einzelnen Rollen anzuzeigen, erweitern Sie die Eigenschaft **erste Rolle** oder **zweite Rolle** .

|     **Property**     |          **Default**          |                                                                                                                                                                                                                                                                                                                                        Beschreibung                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Rollen Name (2)**   | Name des Typs dieser Rolle |                                                                                                                                                                                                                                                                                                       Der Name der Rolle. Wird am Ende der Zuordnung im Diagramm angezeigt.                                                                                                                                                                                                                                                                                                        |
|   **Aggregation**    |             Keiner              |                                                                        **None** (4): stellt eine allgemeine Beziehung zwischen Instanzen der-Klasse dar.<br /><br /> **Composite** (5): das-Objekt in dieser Rolle enthält das-Objekt in der entgegengesetzten Rolle. Sie können das zusammen **gesetzte** Tool verwenden, um eine Zuordnung mit zusammengesetzter Aggregation zu erstellen.<br /><br /> **Shared** (6): das Objekt in dieser Rolle enthält Verweise auf das Objekt in der anderen Rolle. Sie können das **Aggregations** Tool verwenden, um eine Zuordnung mit frei gegebener Aggregation zu erstellen.<br /><br /> Die genaue Interpretation richtet sich nach der lokalen Konvention.                                                                         |
|    **Ist abgeleitet**    |             False             |                                                                                                                                                                                                                          Wenn „true“, wird das Objekt an diesem Ende des Links aus anderen Attributen und Zuordnungen berechnet. Beispielsweise wird MyWorkPlace aus MyEmployer.WorkPlace berechnet. Die Details sollten in die Beschreibung oder einen angefügten Kommentar eingegeben werden.                                                                                                                                                                                                                           |
| **Ist abgeleitete Union** |             False             |                                                                                                                                                                                                                                                                                                             Wenn „true“, ist die Rolle die Vereinigung einer Gruppe von Rollen in abgeleiteten Typen.                                                                                                                                                                                                                                                                                                             |
|   **Ist navigiert**   |             True              |                                                 Die Zuordnung kann in dieser Richtung gelesen werden. Bei Vorgabe einer Instanz der entgegengesetzten Rolle kann die Software, die Sie beschreiben, die zugeordnete Instanz in dieser Rolle effizient ermitteln.<br /><br /> Wenn eine Rolle navigierbar ist und die andere nicht, wird ein Pfeil (7) für die Zuordnung in der navigierbaren Richtung angezeigt.<br /><br /> Standardmäßig erstellt das Zuordnungstool eine Zuordnung, die in einer Richtung navigierbar ist. Um es in eine bidirektionale Zuordnung zu konvertieren, können Sie die Zuordnung auswählen, auf das angezeigte Aktions Tag klicken und dann auf **bidirektionale erstellen**klicken.                                                 |
|   **Ist schreibgeschützt**   |             False             |                                                                                                                                                                                                                                                                                   Wenn „true“, kann eine Instanz der Zuordnung nach ihrer Erstellung nicht geändert werden. Der Link bezieht sich immer auf dasselbe Objekt.                                                                                                                                                                                                                                                                                    |
| **Multiplizität (3)** |               1               | **1** -dieses Ende der Zuordnung ist immer mit einem Objekt verknüpft. In der Abbildung hat jedes „Menu Item“ ein „Menu“.<br /><br /> **0.. 1** : entweder dieses Ende der Zuordnung ist mit einem Objekt verknüpft, oder es ist kein Link vorhanden.<br /><br /> **\\** \*: jedes Objekt am anderen Ende der Zuordnung ist an diesem Ende mit einer Auflistung von Objekten verknüpft, und die Auflistung ist möglicherweise leer.<br /><br /> **1.. \\** \*-jedes Objekt am anderen Ende der Zuordnung ist mit mindestens einem Objekt an diesem Ende verknüpft. In der Abbildung hat jedes „Menu“ mindestens ein „Menu Item“.<br /><br /> *n* **..** *m* -jedes Objekt am anderen Ende verfügt über eine Auflistung zwischen *n* und *m* Links zu Objekten an diesem Ende. |
|    **Ist geordnet**    |             False             |                                                                                                                                                                                                                                                                                                  Wenn „true“, bildet die zurückgegebene Auflistung eine sequenzielle Liste. Für „Multiplicity“ von mehr als 1.                                                                                                                                                                                                                                                                                                   |
|    **Ist eindeutig**     |             False             |                                                                                                                                                                                                                                                                                              Wenn „true“, enthält die zurückgegebene Auflistung keine doppelten Werte. Für „Multiplicity“ von mehr als 1.                                                                                                                                                                                                                                                                                              |
|    **Sichtbarkeit**    |            Öffentlich             |                                                                                                                                                                                                                                 Public – global sichtbar<br /><br /> Private – außerhalb des besitzenden Typs nicht sichtbar<br /><br /> Protected – sichtbar für Typen, die vom Besitzer abgeleitet sind<br /><br /> Package – sichtbar für andere Typen innerhalb des gleichen Pakets                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Siehe auch
 [UML-Klassendiagramme: Verweis](../modeling/uml-class-diagrams-reference.md) [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md) [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Eigenschaften von Operationen in UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) -Klassendiagrammen [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)
