---
title: 'UML-Klassendiagramme: Referenz | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 239b5427c4e19b15e44d683def0e2d6c82dccdfe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516188"
---
# <a name="uml-class-diagrams-reference"></a>UML-Klassendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [UML-Klassendiagramme: Referenz](https://docs.microsoft.com/visualstudio/modeling/uml-class-diagrams-reference).  
  
Ein UML-Klassendiagramm beschreibt das Objekt und die Informationsstrukturen, die sowohl intern als auch bei der Kommunikation mit Benutzern von der Anwendung verwendet werden. Die Informationen werden ohne Verweis auf eine bestimmte Implementierung beschrieben. Die Klassen und Beziehungen können auf viele verschiedene Arten implementiert werden, z. B. Datenbanktabellen, XML-Knoten oder Zusammenstellungen von Softwareobjekten.  
  
> [!NOTE]
>  In diesem Thema geht es um UML-Klassendiagramme. Es gibt eine weitere Art von Klassendiagramm, das .NET-Klassendiagramm, das verwendet wird, um Programmcode visuell darzustellen. Weitere Informationen finden Sie unter [entwerfen und Anzeigen von Klassen und Typen](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
 Erstellen Sie ein UML-Klassendiagramm auf die **Architektur** Menü wählen **neues UML- oder Ebenendiagramm**. Weitere Informationen zum Zeichnen von UML-Klassendiagrammen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md). Weitere Informationen zum Erstellen und Zeichnen von Modellierungsdiagrammen finden Sie unter [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-class-diagrams"></a>Lesen von Klassendiagrammen  
 Die Tabelle in diesem Abschnitt beschreibt die Elemente, die Sie in einem UML-Klassendiagramm sehen können. Informationen zu den Eigenschaften dieser Elemente finden Sie unter den folgenden Themen:  
  
-   [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
-   [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
 ![Drei Klassen mit Beziehungen und Eigenschaften](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
|**Form "**|**Element**|**Beschreibung**|  
|---------------|-----------------|---------------------|  
|1|**Klasse**|Eine Definition von Objekten, die gemeinsame strukturelle Merkmale oder Verhaltensmerkmale aufweisen. Weitere Informationen finden Sie unter [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|1|Klassifizierer|Der allgemeine Name für eine Klasse, Schnittstelle oder Enumeration. Komponenten, Anwendungsfälle und Akteure sind ebenfalls Klassifizierer.|  
|2|Steuerelement erweitern/reduzieren|Wenn Sie die Details einer Klassifizierung nicht sehen können, klicken Sie auf die Erweiterung oben links im Klassifizierer. Möglicherweise müssen Sie auch  für jedes Segment auf das [+] klicken.|  
|3|**Attribut**|Ein Wert mit einem Typ, der jeder Instanz eines Klassifizierers zugeordnet ist.<br /><br /> Um ein Attribut hinzuzufügen, klicken Sie auf die **Attribute** aus, und drücken Sie dann die **EINGABETASTE**. Geben Sie die Signatur des Attributs ein. Weitere Informationen finden Sie unter [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md).|  
|4|**Vorgang**|Eine Methode oder Funktion, die von Instanzen eines Klassifizierers ausgeführt werden kann. Um einen Vorgang hinzuzufügen, klicken Sie auf die **Vorgänge** aus, und drücken Sie dann die **EINGABETASTE**. Geben Sie die Signatur des Vorgangs ein. Weitere Informationen finden Sie unter [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md).|  
|5|**Zuordnung**|Eine Beziehung zwischen den Membern von zwei Klassifizierern. Weitere Informationen finden Sie unter [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md).|  
|5a|**Aggregation**|Eine Zuordnung, die eine gemeinsame Besitzbeziehung darstellt. Die **Aggregation** der Rolle "Besitzer"-Eigenschaftensatz auf **Shared**.|  
|5 b|**Komposition**|Eine Zuordnung, die eine ganzteilige Besitzbeziehung darstellt. Die **Aggregation** der Rolle "Besitzer"-Eigenschaftensatz auf **zusammengesetzten**.|  
|6|**Zuordnungsname**|Der Name einer Zuordnung. Der Name kann leer gelassen werden.|  
|7|**Rollenname**|Der Name einer Rolle, d. h. ein Ende einer Zuordnung. Kann verwendet werden, um auf das zugeordnete Objekt zu verweisen. In der vorherigen Abbildung steht `O` für jede `O.ChosenMenu`-Bestellung für die zugeordnete Speisekarte.<br /><br /> Jede Rolle verfügt über eigene Eigenschaften, die unter den Eigenschaften der Zuordnung aufgeführt sind.|  
|8|**Multiplizität**|Gibt an, wie viele der Objekte an diesem Ende mit jedem Objekt am anderen Ende verknüpft werden können. Im Beispiel muss jede Bestellung mit genau einer Speisekarte verknüpft sein.<br /><br /> **\*** bedeutet, dass es keine obere Grenze für die Anzahl der Links, die vorgenommen werden können.|  
|9|**Generalisierung**|Die *bestimmte* Klassifizierer erbt einen Teil seiner Definition von der *allgemeine* Klassifizierer. Der allgemeine Klassifizierer befindet sich am Pfeilende des Connectors. Attribute, Zuordnungen und Vorgänge werden vom spezifischen Klassifizierer geerbt.<br /><br /> Verwenden der **Vererbung** Tool, um eine Generalisierung zwischen zwei Klassifizierern zu erstellen.|  
  
 ![Paket mit der Schnittstelle und Enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|Form|Element|Beschreibung|  
|-----------|-------------|-----------------|  
|10|**Interface**|Eine Definition eines Teils des extern sichtbaren Verhaltens eines Objekts. Weitere Informationen finden Sie unter [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|11|**Enumeration**|Ein Klassifizierer, der aus einem Satz von Literalwerten besteht.|  
|12|**Pakete**|Eine Gruppe von Klassifizierern, Zuordnungen, Lebenslinien, Komponenten und Paketen. Ein logisches Klassendiagramm zeigt, dass die Memberklassifizierer und -pakete im Paket enthalten sind.<br /><br /> Namen sind in Paketen beschränkt, damit **Class1** in **Package1** unterscheidet sich von **Class1** außerhalb des Pakets. Der Name des Pakets wird als Teil der **qualifizierten Namen** -Eigenschaften seines Inhalts.<br /><br /> Sie können festlegen, die **Linked Package** Eigenschaft des UML-Diagramms zu einem Paket zu verweisen. Alle Elemente, die Sie in diesem Diagramm erstellen, werden dann Teil des Pakets. Sie werden angezeigt, unter dem Paket im **UML-Modell-Explorer**.|  
|13|**Importieren**|Eine Beziehung zwischen Paketen, die angibt, dass ein Paket alle Definitionen eines anderen Pakets enthält.|  
|14|**Abhängigkeit**|Die Definition oder Implementierung des abhängigen Klassifizierers kann sich möglicherweise ändern, wenn der Klassifizierer am Pfeilspitzenende geändert wird.|  
  
 ![Realisierung mit Connector und Lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|Form|**Element**|Beschreibung|  
|-----------|-----------------|-----------------|  
|15|**Realisierung**|Die Klasse implementiert die Vorgänge und Attribute, die von der Schnittstelle definiert werden.<br /><br /> Verwenden der **Vererbung** Tool, um eine Realisierung zwischen einer Klasse und eine Schnittstelle zu erstellen.|  
|16|**Realisierung**|Eine alternative Darstellung der gleichen Beziehung. Die Bezeichnung auf dem Lollipopsymbol identifiziert die Schnittstelle.<br /><br /> Um diese Präsentation zu erstellen, wählen Sie eine vorhandene Realisierungsbeziehung aus. In der Nähe der Zuordnung wird ein Aktionstag angezeigt. Klicken Sie auf das Aktionstag und dann auf **als Lollipop anzeigen**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)   
 [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Eigenschaften von Operationen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)



