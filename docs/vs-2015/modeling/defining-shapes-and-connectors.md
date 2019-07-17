---
title: Definieren von Formen und Konnektoren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 761e0e77a0fe9f6f32f08045d81f6eab815801dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181898"
---
# <a name="defining-shapes-and-connectors"></a>Definieren von Formen und Konnektoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt mehrere grundlegende Formtypen, die Sie zum Anzeigen von Informationen in einem Diagramm in einer domänenspezifischen Sprache (DSL) verwenden können.  
  
## <a name="shapeTypes"></a> Grundlegende Typen von Formen und Konnektoren  
 Eine DSL-Diagramm wird eine Auflistung von *Formen* angezeigt, die durch Linien oder *Connectors*.  Normalerweise gilt Folgendes (wenn auch nicht immer):  
  
- Bei Formen handelt es sich um die sichtbare Darstellung der Modellelemente.  
  
- Konnektoren stellen Verweisbeziehungen dar.  
  
- Die Modellstamminstanz wird durch das Diagramm repräsentiert.  
  
- Einbettende Beziehungen zwischen Modellelementen werden mithilfe der Kapselung angezeigt. Beispielsweise werden Elemente, die Komponentenports darstellen, in die Komponente eingebettet.  
  
  Diese Muster werden nicht erzwungen, sie werden allerdings stärker unterstützt. Beachten Sie beim Entwerfen einer DSL, dass das Design der einbettenden Beziehungen davon beeinflusst wird, wie das Modell auf dem Bildschirm dargestellt werden soll. Im Gegensatz dazu sollten die Verweisbeziehungen die Konzepte Ihrer Geschäftssparte wiedergeben.  
  
  Die folgenden Formtypen stehen zur Verfügung:  
  
|Formtyp|Beschreibung|  
|----------------|-----------------|  
|Geometrie-Form|Allgemeine rechteckige oder elliptische Form. Sie können Decorator-Elemente für Texte und Symbole an bestimmten Positionen relativ zu den Begrenzungen der Form anzeigen.<br /><br /> Um die Formen innerhalb der Geometrie-Formen geschachtelt werden, finden Sie unter [Schachteln von Formen](../modeling/nesting-shapes.md).|  
|Depot-Form|Ein Rechteck, das einen Header und Depots enthält, wie beispielsweise eine UML-Klasse. Dabei kann jedes Depot eine Liste mit Textzeilen enthalten.<br /><br /> Die Zeilen stellen normalerweise die Elemente dar, die unter dem Element eingebettet sind, das durch die Form repräsentiert wird. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für Klassendiagramme.|  
|Bild-Form|Eine Form, die ein Bild darstellt.|  
|Anschluss-Form|Ein kleines Rechteck, das so konstruiert ist, dass dieses an die Kontur einer anderen Form angefügt werden kann. Dieser Formtyp kommt normalerweise bei Komponentenmodellen zum Einsatz.<br /><br /> Das durch einen Anschluss dargestellte Modellelement ist in der Regel unter dem Element eingebettet, das durch die übergeordnete Form repräsentiert wird. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für Komponenten.<br /><br /> Standardmäßig kann eine Anschluss-Form entlang den Seiten des entsprechenden übergeordneten Elements gleiten. Sie können eine Begrenzungsregel definieren, sodass die Form auf eine bestimmte Position beschränkt wird.<br /><br /> Wenn eine Anschluss-Form als sehr klein und transparent erstellt wird, können Sie diese Form verwenden, um einen festen Verbindungspunkt auf der Oberfläche der entsprechenden übergeordneten Form bereitzustellen.|  
|Swimlanes|Mithilfe von Verantwortlichkeitsbereichen wird ein Diagramm in horizontale oder vertikale Segmente partitioniert. Der Verantwortlichkeitsbereich bleibt stets unterhalb der anderen Formen im Diagramm.<br /><br /> Normalerweise sind die Modellelemente des Verantwortlichkeitsbereichs dem Modellstamm übergeordnet, und die anderen Elemente sind diesen übergeordnet. Erstellen Sie zum Beispiel eine DSL mithilfe der Lösungsvorlage für den Aufgabenverlauf.|  
|Connectors|Die zwischen den Formen gezeichneten Linien stellen normalerweise Verweisbeziehungen dar. Sie können Optionen festlegen, sodass ein Konnektor gerade oder geradlinig ist und verschiedene Pfeilspitzentypen zur Verfügung stehen.|  
  
## <a name="shapeInheritance"></a> Form-Vererbung  
 Eine Form kann von einer anderen Form erben. Die Formen müssen allerdings vom selben Typ sein. Beispielsweise kann nur eine Geometrie-Form von einer Geometrie-Form erben. Geerbte Formen verfügen über die Depots und Decorator-Elemente ihrer entsprechenden Basis-Form. Konnektoren können von Konnektoren erben.
