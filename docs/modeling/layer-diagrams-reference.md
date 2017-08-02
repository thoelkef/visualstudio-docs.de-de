---
title: "Abhängigkeitsdiagramme: Verweisen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 33
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 74829877befa9f48988d42e04a58e2a418e7d82b
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-reference"></a>Abhängigkeitsdiagramme: Referenz
In Visual Studio können Sie eine *Abhängigkeitsdiagramm* um die hochrangige, logische Architektur des Systems visuell darzustellen. Ein Abhängigkeitsdiagramm ordnet die physischen Artefakte im System in logischen, abstrakten Gruppen, genannt *Ebenen*. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Durch das Organisieren des Systems in Ebenen, die verschiedene Rollen und Funktionen beschreiben, können ein Abhängigkeitsdiagramm für Sie zu verstehen, wiederverwenden und Verwalten des Codes zu vereinfachen.  
  
 Verwenden Sie ein Abhängigkeitsdiagramm, können Sie die folgenden Aufgaben ausführen:  
  
-   Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems  
  
-   Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur  
  
-   Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems  
  
-   Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge  
  
 Dieses Thema beschreibt die Elemente, die in einem Abhängigkeitsdiagramm verwendet werden können. Ausführlichere Informationen zum Erstellen und zeichnen Abhängigkeitsdiagramme, finden Sie unter [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md). Weitere Informationen zu Ebenenmuster finden Sie auf der [Muster & Practices-Website](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Lesen Sie Abhängigkeitsdiagramme  
 ![Elemente in Abhängigkeit von Diagrammen](~/docs/modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 Die folgende Tabelle beschreibt die Elemente, die in einem Abhängigkeitsdiagramm verwendet werden können.  
  
|**Form**|**Element**|**Beschreibung**|  
|---------------|-----------------|---------------------|  
|1|**Ebene**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> Um die Elemente anzuzeigen, die mit einer Ebene verknüpft sind, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **Links anzeigen** öffnen **Ebenen-Explorer**.<br /><br /> Weitere Informationen finden Sie unter [Ebenen-Explorer](#Explorer).<br /><br /> -   **Forbidden Namespace Dependencies** -gibt an, dass dieser Ebene zugeordnete Artefakte auf den angegebenen Namespaces abhängen dürfen.<br />-   **Forbidden Namespaces** -gibt an, dass dieser Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören müssen.<br />-   **Erforderliche Namespaces** -gibt an, dass dieser Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen.|  
|2|**Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|  
|3|**Bidirektionale Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|  
|4|**Kommentar**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|  
|5|**Kommentarverknüpfung**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|  
  
##  <a name="a-nameexplorera-layer-explorer"></a><a name="Explorer"></a>Im Ebenen-Explorer  
 Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:  
  
-   Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.  
  
     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.  
  
-   Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.  
  
 Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:  
  
-   [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)  
  
-   [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>So untersuchen Sie die verknüpften Artefakte  
  
-   Öffnen Sie das Kontextmenü für eine oder mehrere Ebenen der Abhängigkeitsdiagramm, und wählen Sie dann **Links anzeigen**.  
  
     **Ebenen-Explorer** wird geöffnet und zeigt die Artefakte, die mit den ausgewählten Ebenen verknüpft sind. **Ebenen-Explorer** verfügt über eine Spalte, die einzelnen Eigenschaften der Artefaktlinks anzeigt.  
  
    > [!NOTE]
    >  Wenn Sie diese Eigenschaften nicht angezeigt wird, erweitern Sie die **Ebenen-Explorer** Fenster.  
  
    |**Spalte im Ebenen-Explorer**|**Beschreibung**|  
    |----------------------------------|---------------------|  
    |**Kategorien**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|  
    |**Ebene**|Die Ebene, die mit dem Artefakt verknüpft ist.|  
    |**Unterstützt die Validierung**|Wenn **True**, und klicken Sie dann die ebenenvalidierung überprüfen, ob das Projekt mit Abhängigkeiten zu oder von diesem Element entspricht.<br /><br /> Wenn **False**, und klicken Sie dann der Link nicht an der ebenenvalidierung beteiligt ist.<br /><br /> Weitere Informationen finden Sie unter [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).|  
    |**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)

