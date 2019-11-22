---
title: 'Layer Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd2b2d19e55cbaf9af63ddeafdbdf9f6d677c5bc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301620"
---
# <a name="layer-diagrams-reference"></a>Ebenendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *layer diagram* to visualize the high-level, logical architecture of your system. A layer diagram organizes the physical artifacts in your system into logical, abstract groups called *layers*. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Indem es das System in Ebenen organisiert, die eindeutige Rollen und Funktionen beschreiben, kann ein Ebenendiagramm das Verstehen, Wiederverwenden und Verwalten von Code vereinfachen.

 Verwenden Sie ein Ebenendiagramm als Unterstützung bei folgenden Aufgaben:

- Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems

- Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur

- Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems

- Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge

  In diesem Thema werden die Elemente beschrieben, die Sie in Ebenendiagrammen verwenden können. For more detailed information about how to create and draw layer diagrams, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md). For more information about layering patterns, visit the [Patterns & Practices site](https://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-layer-diagrams"></a>Lesen von Ebenendiagrammen
 ![Elements on layer diagrams](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 In der folgenden Tabelle werden die Elemente beschrieben, die in einem Ebenendiagramm verwendet werden können.

|**Shape**|**Element**|**Beschreibung**|
|---------------|-----------------|---------------------|
|1|**Layer**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> To see the artifacts that are linked to a layer, open the shortcut menu for the layer, and then choose **View Links** to open **Layer Explorer**.<br /><br /> For more information, see [Layer Explorer](#Explorer).<br /><br /> -   **Forbidden Namespace Dependencies** - Specifies that artifacts associated with this layer cannot depend on the specified namespaces.<br />-   **Forbidden Namespaces** - Specifies that artifacts associated with this layer must not belong to the specified namespaces.<br />-   **Required Namespaces** - Specifies that artifacts associated with this layer must belong to one of the specified namespaces.|
|2|**Dependency**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|3|**Bidirectional Dependency**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|4|**Kommentar**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|
|5|**Comment Link**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|

## <a name="Explorer"></a> Layer Explorer
 Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:

- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

   Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

  Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:

- [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>So untersuchen Sie die verknüpften Artefakte

- On the layer diagram, open the shortcut menu for one or more layers, and then choose **View Links**.

     **Layer Explorer** opens and shows the artifacts that are linked to the selected layers. **Layer Explorer** has a column that shows each of the properties of the artifact links.

    > [!NOTE]
    > If you cannot see all of these properties, expand the **Layer Explorer** window.

    |**Column in Layer Explorer**|**Beschreibung**|
    |----------------------------------|---------------------|
    |**Categories**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|
    |**Layer**|Die Ebene, die mit dem Artefakt verknüpft ist.|
    |**Supports Validation**|If **True**, then the layer validation process can verify that the project conforms to dependencies to or from this element.<br /><br /> If **False**, then the link does not participate in the layer validation process.<br /><br /> For more information, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md).|
    |**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|

## <a name="see-also"></a>Siehe auch
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
