---
title: "Arbeiten mit dem DSL-Definitionsdiagramm | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.diagram"
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Domänenspezifische Sprachtools, Bring Tree Here"
  - "Domänenspezifische Sprachtools, Diagramm"
  - "Domänenspezifische Sprachtools, Show As-Klasse"
  - "Domänenspezifische Sprachtools, Show Map Lines"
  - "Domänenspezifische Sprachtools, Split Tree"
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Arbeiten mit dem DSL-Definitionsdiagramm
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Diagramm einer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]\-Definition ist ein wichtiges Tool zum Festlegen der domänenspezifischen Sprache.  Sie können Ihrem Domänenmodell Elemente hinzufügen und Beziehungen im Diagramm festlegen. Darüber hinaus können Sie das Layout des Diagramms ändern, um dieses besser lesbar zu machen.  
  
## Das Layout des Diagramms  
 Das [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]\-Definitionsdiagramm verfügt über zwei Partitionen: die Partition **Klassen und Beziehungen** und die Partition **Diagrammelemente**.  Die Partition **Klassen und Beziehungen** zeigt Domänenklassen, Domänenbeziehungen und die Vererbung an. Die Partition **Diagrammelemente** zeigt Formklassen, Konnektorklassen, Klassen für Verantwortlichkeitsbereiche und das generierte Designerdiagramm an.  
  
 Domänenklassen können in der Partition **Klassen und Beziehungen** in verschiedenen Speicherorten vorhanden sein.  Eine Domänenklassendefinition zeigt eine Vererbungsstruktur an, wenn es sich um die Basisklasse für andere Domänenklassen handelt. Eine Beziehungsstruktur wird angezeigt, wenn es sich um die Quelle von einbettenden Beziehungen oder Verweisbeziehungen handelt.  Domänenklassenplatzhalter werden als die Ziele der einbettenden Beziehung oder der Verweisbeziehung angezeigt.  Platzhalterelemente werden standardmäßig im reduzierten Depot **Domäneneigenschaften** angezeigt.  Die Vererbung sowie einbettende Beziehungen oder Verweisbeziehungen werden nicht angezeigt.  
  
 Beim Hinzufügen einer Domänenklasse erscheint diese im unteren Bereich der Partition **Klassen und Beziehungen**.  Wenn Sie eine einbettende Beziehung oder eine Verweisbeziehung hinzufügen, wird diese unterhalb und rechts neben der Quelldomänenklasse gezeichnet.  
  
 Wenn Sie Domänenklassen und Beziehungen hinzufügen, kann das Suchen nach einer bestimmten Domänenklasse unter Umständen schwierig werden.  Sie können nach einer Domänenklasse suchen, indem Sie mit der rechten Maustaste in den **DSL\-Explorer** klicken und anschließend **Im Diagramm suchen** auswählen.  
  
 In den folgenden Abschnitten wird beschrieben, wie Sie die Darstellung des Diagramms ändern können, sodass dieses besser lesbar ist.  
  
## Kopieren von Elementen  
 Sie können die Elemente im DSL\-Definitionsdiagramm kopieren, ausschneiden und einfügen.  
  
## Verkleinern oder Vergrößern im Diagramm  
 Mithilfe der **DSL Designer**\-Symbolleiste können Sie im Diagramm eine Verkleinerung oder Vergrößerung vornehmen, da Sie mit dieser Symbolleiste den Zoomfaktor festlegen.  
  
## Ausblenden von Zuordnungslinien  
 Bei Zuordnungslinien handelt es sich um Linien, die zwischen einer Domänenklasse oder Domänenbeziehung und der entsprechend zugeordneten Form oder dem zugeordneten Konnektor gezeichnet werden.  Sie können die Zuordnungslinien ausblenden, wenn Sie in der **DSL Designer**\-Symbolleiste auf die Schaltfläche **Zuordnungslinien anzeigen** klicken.  Klicken Sie erneut auf die Schaltfläche, um die Linien anzuzeigen.  
  
## Ändern des Diagrammlayouts  
 Sie können das Layout der Partition **Klassen und Beziehungen** folgendermaßen ändern:  
  
### Erweitern\/Reduzieren  
 Sie können die Größe eines Depotformelements, das eine Domänenklasse oder eine Form darstellt, reduzieren, indem Sie mit der rechten Maustaste darauf klicken und anschließend **Reduzieren** auswählen.  Daraufhin wird das Depot **Domäneneigenschaften** der Form ausgeblendet.  Wenn Sie das Depot **Domäneneigenschaften** erneut anzeigen möchten, klicken Sie mit der rechten Maustaste auf die Form und anschließend auf **Erweitern**.  
  
### Nach oben\/unten verschieben  
 Sie können eine Domänenklasse oder ein Diagrammelement in der Partition nach oben oder nach unten verschieben, wenn Sie mit der rechten Maustaste auf das Element klicken und anschließend **Nach oben** oder **Nach unten** auswählen.  Wenn Sie ein Platzhalterelement verschieben, das als das Ziel einer einbettenden Beziehung oder einer Verweisbeziehung angezeigt wird, wird die Beziehung ebenfalls verschoben.  
  
### Beziehungsstruktur erweitern\/reduzieren  
 Falls eine Domänenklasse der Quellrolleninhaber bei einer einbettenden Beziehung oder einer Verweisbeziehung mit anderen Domänenklassen ist, können Sie die Beziehungen ausblenden, indem Sie mit der rechten Maustaste auf die Domänenklassendefinition klicken und anschließend **Beziehungsstruktur reduzieren** auswählen.  Damit die Beziehungen wieder angezeigt werden, klicken Sie mit der rechten Maustaste auf das Definitionselement, und wählen Sie anschließend **Beziehungsstruktur erweitern** aus.  
  
### Vererbungsstruktur erweitern\/reduzieren  
 Wenn es sich bei einer Domänenklasse um die Basisklasse anderer Domänenklassen handelt, können Sie die Vererbungsstruktur ausblenden, indem Sie mit der rechten Maustaste auf die Domänenklassendefinition klicken und anschließend **Vererbungsstruktur reduzieren** auswählen.  Damit die Vererbungsstruktur wieder angezeigt wird, klicken Sie mit der rechten Maustaste auf das Definitionselement, und wählen Sie anschließend **Vererbungsstruktur erweitern** aus.  
  
### Struktur verschieben  
 Sie können das Diagramm konsolidieren, wenn Sie mit der rechten Maustaste auf eine Platzhalter\-Domänenklasse klicken und anschließend **Struktur verschieben** auswählen.  Die Platzhalter\-Domänenklasse wird zu einem Definitionselement und zeigt die Vererbungs\- und Beziehungsstrukturen an.  Das frühere Definitionselement wird zu einem Platzhalterelement, wenn es sich dabei um das Ziel einer Beziehung oder um das untergeordnete Element einer Vererbungsbeziehung handelt. Ansonsten wird es nicht länger angezeigt.  
  
### Struktur teilen  
 Sie können Vererbungs\- oder Beziehungsstrukturen aufteilen, indem Sie mit der rechten Maustaste auf die Domänenklassendefinition klicken, die diese Strukturen anzeigt. Klicken Sie anschließend auf **Struktur teilen**.  Das Definitionselement wird zu einem Platzhalterelement, und die Definitionsdomänenklasse wird nun zusammen mit den entsprechenden Vererbungs\- und Beziehungsstrukturen unten in der Partition angezeigt.  
  
### Als Klasse anzeigen  
 Wenn eine Domänenbeziehung über abgeleitete Beziehungen verfügt oder eine einbettende Beziehung oder eine Verweisbeziehung bei anderen Domänenbeziehungen vorhanden ist, können Sie die Beziehung als Klasse anzeigen, indem Sie mit der rechten Maustaste auf die Beziehung klicken und dann die Option **Als Klasse anzeigen** auswählen.  Die Beziehung wird mit dem Depot **Domäneneigenschaften** angezeigt, sodass die Vererbungs\- und Beziehungsstrukturen sichtbar sind.  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)