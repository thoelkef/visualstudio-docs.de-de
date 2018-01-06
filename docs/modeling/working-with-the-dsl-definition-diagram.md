---
title: Arbeiten mit der DSL-Definitionsdiagramm | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e2631a81cd907c6946993461f953a0bc1ddbf2ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-the-dsl-definition-diagram"></a>Arbeiten mit dem DSL-Definitionsdiagramm
Das Diagramm eine [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Definition ist ein wichtiges Tool für die Definition einer domänenspezifischen Sprache. Sie können Ihrem Domänenmodell Elemente hinzufügen und Beziehungen im Diagramm festlegen. Darüber hinaus können Sie das Layout des Diagramms ändern, um dieses besser lesbar zu machen.  
  
## <a name="the-layout-of-the-diagram"></a>Das Layout des Diagramms  
 Die [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Definitionsdiagramm weist zwei Partitionen, die **Klassen und Beziehungen** Partition und die **Diagrammelemente** Partition. Die **Klassen und Beziehungen** Partition Domänenklassen, zwischen Domänen und Vererbung angezeigt. Die **Diagrammelemente** Partition Zeigt Formklassen, konnektorklassen Verantwortlichkeitsbereich Klassen und Designer generierten Diagramm.  
  
 Domänenklassen stehen an mehreren Speicherorten in der **Klassen und Beziehungen** Partitionen. Eine Domänenklassendefinition zeigt eine Vererbungsstruktur an, wenn es sich um die Basisklasse für andere Domänenklassen handelt. Eine Beziehungsstruktur wird angezeigt, wenn es sich um die Quelle von einbettenden Beziehungen oder Verweisbeziehungen handelt. Domänenklassenplatzhalter werden als die Ziele der einbettenden Beziehung oder der Verweisbeziehung angezeigt. Standardmäßig werden Platzhalter Elemente angezeigt, mit der **Domäneneigenschaften** Depot reduziert. Die Vererbung sowie einbettende Beziehungen oder Verweisbeziehungen werden nicht angezeigt.  
  
 Wenn Sie eine Domänenklasse hinzufügen, wird im unteren Teil der **Klassen und Beziehungen** Partition. Wenn Sie eine einbettende Beziehung oder eine Verweisbeziehung hinzufügen, wird diese unterhalb und rechts neben der Quelldomänenklasse gezeichnet.  
  
 Wenn Sie Domänenklassen und Beziehungen hinzufügen, kann das Suchen nach einer bestimmten Domänenklasse unter Umständen schwierig werden. Finden Sie eine Domänenklasse, indem Sie mit der rechten Maustaste in die **Explorer für DSL** und dann auf **suchen im Diagramm**.  
  
 In den folgenden Abschnitten wird beschrieben, wie Sie die Darstellung des Diagramms ändern können, sodass dieses besser lesbar ist.  
  
## <a name="copying-elements"></a>Kopieren von Elementen  
 Sie können die Elemente im DSL-Definitionsdiagramm kopieren, ausschneiden und einfügen.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Verkleinern oder Vergrößern im Diagramm  
 Sie können vergrößern oder Verkleinern im Diagramm mit den **DSL-Designer** Symbolleiste, um die Zoomstufe festzulegen.  
  
## <a name="hiding-map-lines"></a>Ausblenden von Zuordnungslinien  
 Bei Zuordnungslinien handelt es sich um Linien, die zwischen einer Domänenklasse oder Domänenbeziehung und der entsprechend zugeordneten Form oder dem zugeordneten Konnektor gezeichnet werden. Sie können kartenlinien ausblenden, indem Sie auf die **Kartenlinien anzeigen** auf die Schaltfläche der **DSL-Designer** Symbolleiste. Klicken Sie erneut auf die Schaltfläche, um die Linien anzuzeigen.  
  
## <a name="changing-the-diagram-layout"></a>Ändern des Diagrammlayouts  
 Sie können das Layout ändern die **Klassen und Beziehungen** wie folgt zu partitionieren.  
  
### <a name="expandcollapse"></a>Erweitern/Reduzieren  
 Sie können die Größe eines Elements der Depot-Form, die eine Domänenklasse oder eine Form vom Typ darstellt, indem sie mit der rechten Maustaste, und dann auf verringern **reduzieren**. Dies Blendet die **Domäneneigenschaften** Depot der Form. Zum Anzeigen der **Domäneneigenschaften** -Fach erneut aus, mit der rechten Maustaste der Form, und klicken Sie dann auf **erweitern**.  
  
### <a name="move-updown"></a>Nach oben/unten verschieben  
 Sie können eine Klasse oder ein Diagramm Domänenelement nach oben oder unten in der Partition verschieben, indem das Element mit der rechten Maustaste, und klicken Sie dann auf **nach oben** oder **nach unten**. Wenn Sie ein Platzhalterelement verschieben, das als das Ziel einer einbettenden Beziehung oder einer Verweisbeziehung angezeigt wird, wird die Beziehung ebenfalls verschoben.  
  
### <a name="expandcollapse-relationships-tree"></a>Beziehungsstruktur erweitern/reduzieren  
 Wenn eine Domänenklasse Quellrolle einbetten oder Verweis Beziehungen mit anderen Domänenklassen wiedergegeben wird, können Sie die Beziehungen ausblenden, indem Sie die Definition der Klasse mit der rechten Maustaste, und klicken Sie dann auf **reduzieren Beziehungen Struktur**. Um die Beziehungen anzuzeigen, mit der rechten Maustaste in der Definition-Element, und klicken Sie dann auf **Beziehungen-Struktur erweitern**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Vererbungsstruktur erweitern/reduzieren  
 Wenn eine Domänenklasse die Basisklasse anderer Klassen für die Domäne ist, können Sie die Vererbungsstruktur ausblenden, indem Sie die Definition der Klasse mit der rechten Maustaste, und klicken Sie dann auf **reduzieren Vererbungsstruktur**. Klicken Sie zum Anzeigen der Vererbungsstruktur mit der rechten Maustaste in der Definition-Element, und klicken Sie dann auf **Vererbungsstruktur erweitern**.  
  
### <a name="bring-tree-here"></a>Bring Tree Here  
 Sie können das Diagramm konsolidieren, indem Sie mit der rechten Maustaste einer Platzhalter-Domain-Klasse, und klicken Sie dann auf **Struktur hier schalten**. Die Platzhalter-Domänenklasse wird zu einem Definitionselement und zeigt die Vererbungs- und Beziehungsstrukturen an. Das frühere Definitionselement wird zu einem Platzhalterelement, wenn es sich dabei um das Ziel einer Beziehung oder um das untergeordnete Element einer Vererbungsbeziehung handelt. Ansonsten wird es nicht länger angezeigt.  
  
### <a name="split-tree"></a>Split Tree  
 Sie können out vererbungs- oder Beziehungen Strukturen unterbrechen, indem mit der rechten Maustaste der Domänendefinition für die Klasse, die sie anzeigen und dann auf **Teilung Struktur**. Das Definitionselement wird zu einem Platzhalterelement, und die Definitionsdomänenklasse wird nun zusammen mit den entsprechenden Vererbungs- und Beziehungsstrukturen unten in der Partition angezeigt.  
  
### <a name="show-as-class"></a>Show As-Klasse  
 Wenn einer domänenbeziehung Beziehungen abgeleitet wurde, oder wenn einbetten oder Verweis Beziehungen mit anderen zwischen Domänen bestehen, Sie die Beziehung als eine Klasse anzeigen können, indem die Beziehung mit der rechten Maustaste, und klicken Sie dann auf **als Klasse anzeigen** . Erscheint die Beziehung mit einer **Domäneneigenschaften** -Fach und die Strukturen Vererbung und Beziehungen angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)