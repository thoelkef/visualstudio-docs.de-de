---
title: 'UML-Klassendiagramme: Referenz | Microsoft-Dokumentation'
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
ms.openlocfilehash: 6d2368c19292f9e4205cec9f1b42b1553ce3188f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658437"
---
# <a name="uml-class-diagrams-reference"></a>UML-Klassendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein UML-Klassendiagramm beschreibt das Objekt und die Informationsstrukturen, die sowohl intern als auch bei der Kommunikation mit Benutzern von der Anwendung verwendet werden. Die Informationen werden ohne Verweis auf eine bestimmte Implementierung beschrieben. Die Klassen und Beziehungen können auf viele verschiedene Arten implementiert werden, z. B. Datenbanktabellen, XML-Knoten oder Zusammenstellungen von Softwareobjekten.

> [!NOTE]
> In diesem Thema geht es um UML-Klassendiagramme. Es gibt eine weitere Art von Klassendiagramm, das .NET-Klassendiagramm, das verwendet wird, um Programmcode visuell darzustellen. Weitere Informationen finden Sie unter [Entwerfen und Anzeigen von Klassen und Typen](http://go.microsoft.com/fwlink/?LinkId=142231).

 Um ein UML-Klassendiagramm zu erstellen, wählen Sie im Menü **Architektur** die Option **neues UML-oder ebenendiagramm**aus. Weitere Informationen zum Zeichnen von UML-Klassendiagrammen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md). Weitere Informationen zum Erstellen und Zeichnen von Modellierungs Diagrammen finden Sie unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lesen von Klassendiagrammen
 Die Tabelle in diesem Abschnitt beschreibt die Elemente, die Sie in einem UML-Klassendiagramm sehen können. Informationen zu den Eigenschaften dieser Elemente finden Sie unter den folgenden Themen:

- [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Drei Klassen, die Beziehungen und Eigenschaften zeigen](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Gebildet** |       **Element**        |                                                                                                                                                             **Beschreibung**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Klasse**         |                                                           Eine Definition von Objekten, die gemeinsame strukturelle Merkmale oder Verhaltensmerkmale aufweisen. Weitere Informationen finden Sie unter [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Klassifizierer        |                                                                                                             Der allgemeine Name für eine Klasse, Schnittstelle oder Enumeration. Komponenten, Anwendungsfälle und Akteure sind ebenfalls Klassifizierer.                                                                                                             |
|     2     | Steuerelement erweitern/reduzieren |                                                                                         Wenn Sie die Details einer Klassifizierung nicht sehen können, klicken Sie auf die Erweiterung oben links im Klassifizierer. Möglicherweise müssen Sie auch  für jedes Segment auf das [+] klicken.                                                                                         |
|     3     |      **Attribut**       |   Ein Wert mit einem Typ, der jeder Instanz eines Klassifizierers zugeordnet ist.<br /><br /> Um ein Attribut hinzuzufügen, klicken Sie auf den Abschnitt **Attribute** und drücken dann die **Eingabe**Taste. Geben Sie die Signatur des Attributs ein. Weitere Informationen finden Sie unter [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Vorgang**       | Eine Methode oder Funktion, die von Instanzen eines Klassifizierers ausgeführt werden kann. Klicken Sie zum Hinzufügen eines Vorgangs auf den Abschnitt **Vorgänge** , und drücken Sie dann die **Eingabe**Taste. Geben Sie die Signatur des Vorgangs ein. Weitere Informationen finden Sie unter [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Anwalt**      |                                                                  Eine Beziehung zwischen den Membern von zwei Klassifizierern. Weitere Informationen finden Sie unter [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Aggregation**      |                                                                                                    Eine Zuordnung, die eine gemeinsame Besitzbeziehung darstellt. Die **Aggregations** Eigenschaft der Rolle "Besitzer" ist auf " **Shared**" festgelegt.                                                                                                     |
|    5 b     |     **Gas**      |                                                                                                      Eine Zuordnung, die eine ganzteilige Besitzbeziehung darstellt. Die **Aggregations** Eigenschaft der Rolle "Besitzer" ist auf " **Composite**" festgelegt.                                                                                                      |
|     6     |   **Zuordnungs Name**   |                                                                                                                                         Der Name einer Zuordnung. Der Name kann leer gelassen werden.                                                                                                                                          |
|     7     |      **Rollen Name**       |                       Der Name einer Rolle, d. h. ein Ende einer Zuordnung. Kann verwendet werden, um auf das zugeordnete Objekt zu verweisen. In der vorherigen Abbildung steht `O` für jede `O.ChosenMenu`-Bestellung für die zugeordnete Speisekarte.<br /><br /> Jede Rolle verfügt über eigene Eigenschaften, die unter den Eigenschaften der Zuordnung aufgeführt sind.                       |
|     8     |     **Deu**     |                                         Gibt an, wie viele der Objekte an diesem Ende mit jedem Objekt am anderen Ende verknüpft werden können. Im Beispiel muss jede Bestellung mit genau einer Speisekarte verknüpft sein.<br /><br /> **\\** \* bedeutet, dass es keine Obergrenze für die Anzahl der Verknüpfungen gibt.                                         |
|     9     |    **Generalisierung**    |  Der *spezifische* Klassifizierer erbt seinen Teil seiner Definition von der *allgemeinen* Klassifizierung. Der allgemeine Klassifizierer befindet sich am Pfeilende des Connectors. Attribute, Zuordnungen und Vorgänge werden vom spezifischen Klassifizierer geerbt.<br /><br /> Verwenden Sie das **Vererbungs** Tool, um eine Generalisierung zwischen zwei Klassifizierern zu erstellen.   |

 ![Paket mit Schnittstelle und Enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Form|Element|Beschreibung|
|-----------|-------------|-----------------|
|10|**Interface**|Eine Definition eines Teils des extern sichtbaren Verhaltens eines Objekts. Weitere Informationen finden Sie unter [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Ein Klassifizierer, der aus einem Satz von Literalwerten besteht.|
|12|**Pakete**|Eine Gruppe von Klassifizierern, Zuordnungen, Lebenslinien, Komponenten und Paketen. Ein logisches Klassendiagramm zeigt, dass die Memberklassifizierer und -pakete im Paket enthalten sind.<br /><br /> Namen werden innerhalb von Paketen festgelegt, sodass sich **Class1** innerhalb von **package1** von **Class1** außerhalb dieses Pakets unterscheidet. Der Name des Pakets wird als Teil der Eigenschaften des **qualifizierten Namens** seines Inhalts angezeigt.<br /><br /> Sie können die Eigenschaft des **verknüpften Pakets** eines beliebigen UML-Diagramms so festlegen, dass Sie auf ein Paket verweist. Alle Elemente, die Sie in diesem Diagramm erstellen, werden dann Teil des Pakets. Sie werden unter dem Paket im **UML-Modell-Explorer**angezeigt.|
|13|**Importieren**|Eine Beziehung zwischen Paketen, die angibt, dass ein Paket alle Definitionen eines anderen Pakets enthält.|
|14|**Gkeit**|Die Definition oder Implementierung des abhängigen Klassifizierers kann sich möglicherweise ändern, wenn der Klassifizierer am Pfeilspitzenende geändert wird.|

 ![Mit dem "-und Lollipop" angezeigte Realisierung](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Form|**Element**|Beschreibung|
|-----------|-----------------|-----------------|
|15|**Alisierungs**|Die Klasse implementiert die Vorgänge und Attribute, die von der Schnittstelle definiert werden.<br /><br /> Verwenden Sie das **Vererbungs** Tool, um eine Realisierung zwischen einer Klasse und einer Schnittstelle zu erstellen.|
|16|**Alisierungs**|Eine alternative Darstellung der gleichen Beziehung. Die Bezeichnung auf dem Lollipopsymbol identifiziert die Schnittstelle.<br /><br /> Um diese Präsentation zu erstellen, wählen Sie eine vorhandene Realisierungsbeziehung aus. In der Nähe der Zuordnung wird ein Aktionstag angezeigt. Klicken Sie auf das Aktions-Tag, und klicken Sie dann auf **als Lollipop anzeigen**.|

## <a name="see-also"></a>Siehe auch
 [Bearbeiten von UML-Modellen und-Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md) [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md) [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md) Eigenschaften [von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)
