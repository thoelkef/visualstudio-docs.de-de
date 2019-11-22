---
title: 'UML Class Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297216"
---
# <a name="uml-class-diagrams-reference"></a>UML-Klassendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein UML-Klassendiagramm beschreibt das Objekt und die Informationsstrukturen, die sowohl intern als auch bei der Kommunikation mit Benutzern von der Anwendung verwendet werden. Die Informationen werden ohne Verweis auf eine bestimmte Implementierung beschrieben. Die Klassen und Beziehungen können auf viele verschiedene Arten implementiert werden, z. B. Datenbanktabellen, XML-Knoten oder Zusammenstellungen von Softwareobjekten.

> [!NOTE]
> In diesem Thema geht es um UML-Klassendiagramme. Es gibt eine weitere Art von Klassendiagramm, das .NET-Klassendiagramm, das verwendet wird, um Programmcode visuell darzustellen. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

 To create a UML class diagram, on the **Architecture** menu, choose **New UML or Layer Diagram**. For more information about how to draw UML class diagrams, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md). For more information about how to create and draw modeling diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lesen von Klassendiagrammen
 Die Tabelle in diesem Abschnitt beschreibt die Elemente, die Sie in einem UML-Klassendiagramm sehen können. Informationen zu den Eigenschaften dieser Elemente finden Sie unter den folgenden Themen:

- [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Three classes showing relationships and properties](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Shape** |       **Element**        |                                                                                                                                                             **Beschreibung**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Klasse**         |                                                           Eine Definition von Objekten, die gemeinsame strukturelle Merkmale oder Verhaltensmerkmale aufweisen. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Klassifizierer        |                                                                                                             Der allgemeine Name für eine Klasse, Schnittstelle oder Enumeration. Komponenten, Anwendungsfälle und Akteure sind ebenfalls Klassifizierer.                                                                                                             |
|     2     | Steuerelement erweitern/reduzieren |                                                                                         Wenn Sie die Details einer Klassifizierung nicht sehen können, klicken Sie auf die Erweiterung oben links im Klassifizierer. Möglicherweise müssen Sie auch  für jedes Segment auf das [+] klicken.                                                                                         |
|     3     |      **Attribut**       |   Ein Wert mit einem Typ, der jeder Instanz eines Klassifizierers zugeordnet ist.<br /><br /> To add an attribute, click the **Attributes** section and then press **ENTER**. Geben Sie die Signatur des Attributs ein. For more information, see [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Vorgang**       | Eine Methode oder Funktion, die von Instanzen eines Klassifizierers ausgeführt werden kann. To add an operation, click the **Operations** section and then press **ENTER**. Geben Sie die Signatur des Vorgangs ein. For more information, see [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Association**      |                                                                  Eine Beziehung zwischen den Membern von zwei Klassifizierern. For more information, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Aggregation**      |                                                                                                    Eine Zuordnung, die eine gemeinsame Besitzbeziehung darstellt. The **Aggregation** property of the owner role is set to **Shared**.                                                                                                     |
|    5 b     |     **Composition**      |                                                                                                      Eine Zuordnung, die eine ganzteilige Besitzbeziehung darstellt. The **Aggregation** property of the owner role is set to **Composite**.                                                                                                      |
|     6     |   **Association Name**   |                                                                                                                                         Der Name einer Zuordnung. Der Name kann leer gelassen werden.                                                                                                                                          |
|     7     |      **Role Name**       |                       Der Name einer Rolle, d. h. ein Ende einer Zuordnung. Kann verwendet werden, um auf das zugeordnete Objekt zu verweisen. In der vorherigen Abbildung steht `O` für jede `O.ChosenMenu`-Bestellung für die zugeordnete Speisekarte.<br /><br /> Jede Rolle verfügt über eigene Eigenschaften, die unter den Eigenschaften der Zuordnung aufgeführt sind.                       |
|     8     |     **Multiplicity**     |                                         Gibt an, wie viele der Objekte an diesem Ende mit jedem Objekt am anderen Ende verknüpft werden können. Im Beispiel muss jede Bestellung mit genau einer Speisekarte verknüpft sein.<br /><br /> **\\** \* means that there is no upper limit to the number of links that can be made.                                         |
|     9     |    **Generalization**    |  The *specific* classifier inherits part of its definition from the *general* classifier. Der allgemeine Klassifizierer befindet sich am Pfeilende des Connectors. Attribute, Zuordnungen und Vorgänge werden vom spezifischen Klassifizierer geerbt.<br /><br /> Use the **Inheritance** tool to create a generalization between two classifiers.   |

 ![Package containing interface and enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Form|Element|Beschreibung|
|-----------|-------------|-----------------|
|10|**Interface**|Eine Definition eines Teils des extern sichtbaren Verhaltens eines Objekts. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Ein Klassifizierer, der aus einem Satz von Literalwerten besteht.|
|12|**Pakete**|Eine Gruppe von Klassifizierern, Zuordnungen, Lebenslinien, Komponenten und Paketen. Ein logisches Klassendiagramm zeigt, dass die Memberklassifizierer und -pakete im Paket enthalten sind.<br /><br /> Names are scoped within packages so that **Class1** within **Package1** is distinct from **Class1** outside that package. The name of the package appears as part of the **Qualified Name** properties of its contents.<br /><br /> You can set the **Linked Package** property of any UML diagram to refer to a package. Alle Elemente, die Sie in diesem Diagramm erstellen, werden dann Teil des Pakets. They will appear under the package in **UML Model Explorer**.|
|13|**Importieren**|Eine Beziehung zwischen Paketen, die angibt, dass ein Paket alle Definitionen eines anderen Pakets enthält.|
|14|**Dependency**|Die Definition oder Implementierung des abhängigen Klassifizierers kann sich möglicherweise ändern, wenn der Klassifizierer am Pfeilspitzenende geändert wird.|

 ![Realization shown with conector and lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Form|**Element**|Beschreibung|
|-----------|-----------------|-----------------|
|15|**Realization**|Die Klasse implementiert die Vorgänge und Attribute, die von der Schnittstelle definiert werden.<br /><br /> Use the **Inheritance** tool to create a realization between a class and an interface.|
|16|**Realization**|Eine alternative Darstellung der gleichen Beziehung. Die Bezeichnung auf dem Lollipopsymbol identifiziert die Schnittstelle.<br /><br /> Um diese Präsentation zu erstellen, wählen Sie eine vorhandene Realisierungsbeziehung aus. In der Nähe der Zuordnung wird ein Aktionstag angezeigt. Click the action tag, and then click **Show as Lollipop**.|

## <a name="see-also"></a>Siehe auch
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md) [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md) [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md)
