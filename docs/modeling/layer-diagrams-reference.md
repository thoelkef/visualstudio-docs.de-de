---
title: Diagramme Abhängigkeitsverweis
ms.date: 09/28/2018
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
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baee97f08a4e6015d6c2e1d88f83f5835431578b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957912"
---
# <a name="dependency-diagrams-reference"></a>Abhängigkeitsdiagramme: Referenz

In Visual Studio können Sie eine *Abhängigkeitsdiagramm* um die hochrangige, logische Architektur des Systems zu visualisieren. Ein Abhängigkeitsdiagramm organisiert die physischen Artefakte in Ihrem System in logischen, abstrakten Gruppen, die sog. *Ebenen*. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.

Welche Editionen von Visual Studio dieses Feature unterstützen, finden Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Abhängigkeitsdiagramme werden für .NET Core-Projekte in Visual Studio 2017 nicht unterstützt.

Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Indem Sie Ihr System in Ebenen, die verschiedene Rollen und Funktionen zu beschreiben organisieren, können ein Abhängigkeitsdiagramm für Sie einfacher zu verstehen, wiederverwenden und Verwalten von Code erleichtern.

Verwenden Sie ein Abhängigkeitsdiagramm, können Sie die folgenden Aufgaben ausführen:

-   Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems

-   Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur

-   Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems

-   Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge

Dieses Thema beschreibt die Elemente, die Sie in einem Abhängigkeitsdiagramm verwenden können. Ausführlichere Informationen zum Erstellen und zeichnen Abhängigkeitsdiagramme, finden Sie unter [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md). Weitere Informationen zu Ebenenmuster finden Sie auf die [Patterns & Practices-Website](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-dependency-diagrams"></a>Lesen von Abhängigkeitsdiagrammen

![Elemente in Abhängigkeitsdiagrammen](../modeling/media/uml_layerrefreading.png)

Die folgende Tabelle beschreibt die Elemente, die Sie in einem Abhängigkeitsdiagramm verwenden können.

|**Form "**|**Element**|**Beschreibung**|
|-|-|-|
|1|**Layer**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> Um die Artefakte anzuzeigen, die auf eine Ebene verknüpft sind, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **Links anzeigen** öffnen **Ebenen-Explorer**.<br /><br /> Weitere Informationen finden Sie unter [Ebenen-Explorer](#Explorer).<br /><br /> -   **Namespace-Abhängigkeiten verboten** – gibt an, dass dieser Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen.<br />-   **Forbidden Namespaces** – gibt an, dass dieser Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören müssen.<br />-   **Erforderliche Namespaces** – gibt an, dass dieser Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen.|
|2|**Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|
|3|**Bidirektionale Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Richtung** -gibt die Richtung der Abhängigkeit.|
|4|**Kommentar**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|
|5|**Kommentarverknüpfung**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|

## <a name="Explorer"></a> Ebenen-Explorer

Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:

-   Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

-   Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:

-   [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

-   [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Überprüfen Sie die verknüpften Artefakte

Das Abhängigkeitsdiagramm, öffnen Sie das Kontextmenü für eine oder mehrere Ebenen, und wählen Sie dann **Links anzeigen**.

**Ebenen-Explorer** wird geöffnet und zeigt die Elemente, die mit den ausgewählten Ebenen verknüpft sind. **Ebenen-Explorer** verfügt über eine Spalte, die die Eigenschaften der Artefaktlinks anzeigt.

> [!NOTE]
> Wenn Sie alle diese Eigenschaften können nicht angezeigt wird, erweitern Sie die **Ebenen-Explorer** Fenster.

|**Die Spalte im Ebenen-Explorer**|**Beschreibung**|
|-|-|
|**Kategorien**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|
|**Layer**|Die Ebene, die mit dem Artefakt verknüpft ist.|
|**Unterstützt die Validierung**|Wenn **"true"**, und klicken Sie dann die ebenenvalidierung überprüfen kann, dass das Projekt mit Abhängigkeiten zu oder von diesem Element entspricht.<br /><br /> Wenn **"false"**, und klicken Sie dann der Link nicht an der ebenenvalidierung beteiligt ist.<br /><br /> Weitere Informationen finden Sie unter [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).|
|**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|

## <a name="see-also"></a>Siehe auch

- [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
