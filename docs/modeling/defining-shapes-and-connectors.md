---
title: Definieren von Formen und Konnektoren
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a24e447e5ec0b65635f7184bd0ae19b305edfdf8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994623"
---
# <a name="define-shapes-and-connectors"></a>Definieren von Formen und Konnektoren

Es gibt mehrere grundlegende Formtypen, die Sie zum Anzeigen von Informationen in einem Diagramm in einer domänenspezifischen Sprache (DSL) verwenden können.

## <a name="shapeTypes"></a> Grundlegende Typen von Formen und Konnektoren

Eine DSL-Diagramm wird eine Auflistung von *Formen* angezeigt, die durch Linien oder *Connectors*. Normalerweise gilt Folgendes (wenn auch nicht immer):

- Bei Formen handelt es sich um die sichtbare Darstellung der Modellelemente.

- Konnektoren stellen Verweisbeziehungen dar.

- Die Modellstamminstanz wird durch das Diagramm repräsentiert.

- Einbettende Beziehungen zwischen Modellelementen werden mithilfe der Kapselung angezeigt. Beispielsweise werden Elemente, die Komponentenports darstellen, in die Komponente eingebettet.

Diese Muster werden nicht erzwungen, sie werden allerdings stärker unterstützt. Beachten Sie beim Entwerfen einer DSL, dass das Design der einbettenden Beziehungen davon beeinflusst wird, wie das Modell auf dem Bildschirm dargestellt werden soll. Im Gegensatz dazu sollten die Verweisbeziehungen die Konzepte Ihrer Geschäftssparte wiedergeben.

Die folgenden Formtypen stehen zur Verfügung:

|Formtyp|Beschreibung|
|-|-|
|Geometrie-Form|Allgemeine rechteckige oder elliptische Form. Sie können Decorator-Elemente für Texte und Symbole an bestimmten Positionen relativ zu den Begrenzungen der Form anzeigen. Sie können die Formen innerhalb der Geometrie-Formen auch schachteln.|
|Depot-Form|Ein Rechteck, das einen Header und Depots enthält, wie beispielsweise eine UML-Klasse. Dabei kann jedes Depot eine Liste mit Textzeilen enthalten.<br /><br /> Die Zeilen stellen normalerweise die Elemente dar, die unter dem Element eingebettet sind, das durch die Form repräsentiert wird. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für Klassendiagramme.|
|Bild-Form|Eine Form, die ein Bild darstellt.|
|Anschluss-Form|Ein kleines Rechteck, das so konstruiert ist, dass dieses an die Kontur einer anderen Form angefügt werden kann. Dieser Formtyp kommt normalerweise bei Komponentenmodellen zum Einsatz.<br /><br /> Das durch einen Anschluss dargestellte Modellelement ist in der Regel unter dem Element eingebettet, das durch die übergeordnete Form repräsentiert wird. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für Komponenten.<br /><br /> Standardmäßig kann eine Anschluss-Form entlang den Seiten des entsprechenden übergeordneten Elements gleiten. Sie können eine Begrenzungsregel definieren, sodass die Form auf eine bestimmte Position beschränkt wird.<br /><br /> Wenn eine Anschluss-Form als sehr klein und transparent erstellt wird, können Sie diese Form verwenden, um einen festen Verbindungspunkt auf der Oberfläche der entsprechenden übergeordneten Form bereitzustellen.|
|Swimlanes|Mithilfe von Verantwortlichkeitsbereichen wird ein Diagramm in horizontale oder vertikale Segmente partitioniert. Der Verantwortlichkeitsbereich bleibt stets unterhalb der anderen Formen im Diagramm.<br /><br /> Normalerweise sind die Modellelemente des Verantwortlichkeitsbereichs dem Modellstamm übergeordnet, und die anderen Elemente sind diesen übergeordnet. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für den Aufgabenverlauf.|
|Connectors|Die zwischen den Formen gezeichneten Linien stellen normalerweise Verweisbeziehungen dar. Sie können Optionen festlegen, sodass ein Konnektor gerade oder geradlinig ist und verschiedene Pfeilspitzentypen zur Verfügung stehen.|

## <a name="shape-inheritance"></a>Form-Vererbung

Eine Form kann von einer anderen Form erben. Die Formen müssen allerdings vom selben Typ sein. Beispielsweise kann nur eine Geometrie-Form von einer Geometrie-Form erben. Geerbte Formen verfügen über die Depots und Decorator-Elemente ihrer entsprechenden Basis-Form. Konnektoren können von Konnektoren erben.