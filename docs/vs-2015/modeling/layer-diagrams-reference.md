---
title: 'Ebenendiagramme: Verweis | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c9ea6398ca02291bb9dc11693c98336cd33b14b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061988"
---
# <a name="layer-diagrams-reference"></a>Ebenendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie eine *Ebenendiagramm* um die hochrangige, logische Architektur des Systems zu visualisieren. Ein Ebenendiagramm organisiert die physischen Artefakte in Ihrem System in logischen, abstrakten Gruppen, die sog. *Ebenen*. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Indem es das System in Ebenen organisiert, die eindeutige Rollen und Funktionen beschreiben, kann ein Ebenendiagramm das Verstehen, Wiederverwenden und Verwalten von Code vereinfachen.  
  
 Verwenden Sie ein Ebenendiagramm als Unterstützung bei folgenden Aufgaben:  
  
- Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems  
  
- Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur  
  
- Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems  
  
- Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge  
  
  In diesem Thema werden die Elemente beschrieben, die Sie in Ebenendiagrammen verwenden können. Ausführlichere Informationen zum Erstellen und Zeichnen von Ebenendiagrammen finden Sie unter [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md). Weitere Informationen zu Ebenenmuster finden Sie auf die [Patterns & Practices-Website](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-layer-diagrams"></a>Lesen von Ebenendiagrammen  
 ![Elemente in Ebenendiagrammen](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")  
  
 In der folgenden Tabelle werden die Elemente beschrieben, die in einem Ebenendiagramm verwendet werden können.  
  
|**Form "**|**Element**|**Beschreibung**|  
|---------------|-----------------|---------------------|  
|1|**Layer**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> Um die Artefakte anzuzeigen, die auf eine Ebene verknüpft sind, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **Links anzeigen** öffnen **Ebenen-Explorer**.<br /><br /> Weitere Informationen finden Sie unter [Ebenen-Explorer](#Explorer).<br /><br /> -   **Namespace-Abhängigkeiten verboten** – gibt an, dass dieser Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen.<br />-   **Forbidden Namespaces** – gibt an, dass dieser Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören müssen.<br />-   **Erforderliche Namespaces** – gibt an, dass dieser Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen.|  
|2|**Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|  
|3|**Bidirektionale Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|  
|4|**Kommentar**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|  
|5|**Kommentarverknüpfung**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|  
  
## <a name="Explorer"></a> Ebenen-Explorer  
 Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:  
  
- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.  
  
   Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.  
  
- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.  
  
  Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:  
  
- [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)  
  
- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>So untersuchen Sie die verknüpften Artefakte  
  
- Im Ebenendiagramm das Kontextmenü für eine oder mehrere Ebenen öffnen, und wählen Sie dann **Links anzeigen**.  
  
     **Ebenen-Explorer** wird geöffnet und zeigt die Elemente, die mit den ausgewählten Ebenen verknüpft sind. **Ebenen-Explorer** verfügt über eine Spalte, die die Eigenschaften der Artefaktlinks anzeigt.  
  
    > [!NOTE]
    >  Wenn Sie alle diese Eigenschaften können nicht angezeigt wird, erweitern Sie die **Ebenen-Explorer** Fenster.  
  
    |**Die Spalte im Ebenen-Explorer**|**Beschreibung**|  
    |----------------------------------|---------------------|  
    |**Kategorien**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|  
    |**Layer**|Die Ebene, die mit dem Artefakt verknüpft ist.|  
    |**Unterstützt die Validierung**|Wenn **"true"**, und klicken Sie dann die ebenenvalidierung überprüfen kann, dass das Projekt mit Abhängigkeiten zu oder von diesem Element entspricht.<br /><br /> Wenn **"false"**, und klicken Sie dann der Link nicht an der ebenenvalidierung beteiligt ist.<br /><br /> Weitere Informationen finden Sie unter [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).|  
    |**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
