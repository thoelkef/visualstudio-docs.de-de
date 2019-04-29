---
title: Arbeiten mit dem DSL-Definitionsdiagramm
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3133c3f37a7ce899575e4e6b0798ce8037b33929
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951244"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Arbeiten mit dem DSL-Definitionsdiagramm
Das Diagramm ein [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Definition ist ein wichtiges Tool für die Definition einer domänenspezifischen Sprache. Sie können Ihrem Domänenmodell Elemente hinzufügen und Beziehungen im Diagramm festlegen. Darüber hinaus können Sie das Layout des Diagramms ändern, um dieses besser lesbar zu machen.

## <a name="the-layout-of-the-diagram"></a>Das Layout des Diagramms
 Die [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] -Definitionsdiagramm verfügt über zwei Partitionen, die **Klassen und Beziehungen** Partition und die **Diagrammelemente** Partition. Die **Klassen und Beziehungen** Partition Zeigt Domänenklassen, domänenbeziehungen und Vererbung. Die **Diagrammelemente** Partition Zeigt Formklassen, konnektorklassen, Klassen für Verantwortlichkeitsbereiche und das generierte designerdiagramm.

 Domänenklassen können angezeigt werden, an mehreren Speicherorten in der **Klassen und Beziehungen** Partitionen. Eine Domänenklassendefinition zeigt eine Vererbungsstruktur an, wenn es sich um die Basisklasse für andere Domänenklassen handelt. Eine Beziehungsstruktur wird angezeigt, wenn es sich um die Quelle von einbettenden Beziehungen oder Verweisbeziehungen handelt. Domänenklassenplatzhalter werden als die Ziele der einbettenden Beziehung oder der Verweisbeziehung angezeigt. Standardmäßig werden Platzhalterelemente angezeigt, mit der **Domäneneigenschaften** reduzierten Depot. Die Vererbung sowie einbettende Beziehungen oder Verweisbeziehungen werden nicht angezeigt.

 Wenn Sie eine Domänenklasse hinzufügen, wird Sie im unteren Teil der **Klassen und Beziehungen** Partition. Wenn Sie eine einbettende Beziehung oder eine Verweisbeziehung hinzufügen, wird diese unterhalb und rechts neben der Quelldomänenklasse gezeichnet.

 Wenn Sie Domänenklassen und Beziehungen hinzufügen, kann das Suchen nach einer bestimmten Domänenklasse unter Umständen schwierig werden. Sie können eine Domänenklasse finden, indem Sie mit der rechten Maustaste in den **DSL-Explorer** , und klicken Sie dann auf **im Diagramm suchen**.

 In den folgenden Abschnitten wird beschrieben, wie Sie die Darstellung des Diagramms ändern können, sodass dieses besser lesbar ist.

## <a name="copying-elements"></a>Kopieren von Elementen
 Sie können die Elemente im DSL-Definitionsdiagramm kopieren, ausschneiden und einfügen.

## <a name="zooming-in-or-out-on-the-diagram"></a>Verkleinern oder Vergrößern im Diagramm
 Sie können das Diagramm vergrößern oder verkleinern, mit der **DSL-Designers** Symbolleiste, um den Zoomfaktor festlegen.

## <a name="hiding-map-lines"></a>Ausblenden von Zuordnungslinien
 Bei Zuordnungslinien handelt es sich um Linien, die zwischen einer Domänenklasse oder Domänenbeziehung und der entsprechend zugeordneten Form oder dem zugeordneten Konnektor gezeichnet werden. Sie können Zuordnungslinien ausblenden, indem Sie auf die **Zuordnungslinien anzeigen** Schaltfläche der **DSL-Designer** Symbolleiste. Klicken Sie erneut auf die Schaltfläche, um die Linien anzuzeigen.

## <a name="changing-the-diagram-layout"></a>Ändern des Diagrammlayouts
 Sie können das Layout des Ändern der **Klassen und Beziehungen** wie folgt zu partitionieren.

### <a name="expandcollapse"></a>Erweitern/Reduzieren
 Sie können die Größe eines depotformelements, das eine Domänenklasse oder eine Form darstellt, mit der rechten Maustaste es, und klicken Sie dann auf reduzieren **reduzieren**. Dies Blendet die **Domäneneigenschaften** Depot der Form. Zum Anzeigen der **Domäneneigenschaften** Depot erneut aus, mit der rechten Maustaste der Form, und klicken Sie dann auf **erweitern**.

### <a name="move-updown"></a>Nach oben/unten verschieben
 Sie können eine Klasse oder ein Diagramm Domänenelement nach oben oder unten in der Partition verschieben, indem mit der rechten Maustaste in des Elements, und klicken Sie dann auf **nach oben** oder **nach unten**. Wenn Sie ein Platzhalterelement verschieben, das als das Ziel einer einbettenden Beziehung oder einer Verweisbeziehung angezeigt wird, wird die Beziehung ebenfalls verschoben.

### <a name="expandcollapse-relationships-tree"></a>Beziehungsstruktur erweitern/reduzieren
 Wenn in einbetten oder Verweis Beziehungen mit anderen Domänenklassen die Quellrolle für eine Domänenklasse wiedergegeben wird, können Sie die Beziehungen ausblenden, indem Sie einen Rechtsklick auf die domänenklassendefinition, und klicken Sie dann auf **Beziehungsstruktur**. Um die Beziehungen anzuzeigen, mit der rechten Maustaste in des Definitionselement, und klicken Sie dann auf **Beziehungsstruktur**.

### <a name="expandcollapse-inheritance-tree"></a>Vererbungsstruktur erweitern/reduzieren
 Ist eine Domänenklasse der Basisklasse anderer Domänenklassen, können Sie die Vererbungsstruktur ausblenden, indem Sie einen Rechtsklick auf die domänenklassendefinition, und klicken Sie dann auf **Vererbungsstruktur reduzieren**. Um die Vererbungsstruktur wieder angezeigt, mit der rechten Maustaste in des Definitionselement, und klicken Sie dann auf **Vererbungsstruktur erweitern**.

### <a name="bring-tree-here"></a>Struktur verschieben
 Sie können mit der rechten Maustaste einer Platzhalter-Domänenklasse aus, und klicken Sie dann auf das Diagramm konsolidieren **Struktur hier**. Die Platzhalter-Domänenklasse wird zu einem Definitionselement und zeigt die Vererbungs- und Beziehungsstrukturen an. Das frühere Definitionselement wird zu einem Platzhalterelement, wenn es sich dabei um das Ziel einer Beziehung oder um das untergeordnete Element einer Vererbungsbeziehung handelt. Ansonsten wird es nicht länger angezeigt.

### <a name="split-tree"></a>Struktur teilen
 Sie können vererbungs- oder Strukturen auszubrechen, in der rechten Maustaste auf die domänenklassendefinition, die sie anzeigen, und klicken Sie dann auf **Baum teilen**. Das Definitionselement wird zu einem Platzhalterelement, und die Definitionsdomänenklasse wird nun zusammen mit den entsprechenden Vererbungs- und Beziehungsstrukturen unten in der Partition angezeigt.

### <a name="show-as-class"></a>Als Klasse anzeigen
 Wenn eine domänenbeziehung abgeleitete Beziehungen verfügt über, oder wenn dies bei anderen domänenbeziehungen Beziehungen einbetten oder verweisbeziehungen ist, Sie die Beziehung als Klasse anzeigen können, indem Sie mit der rechten Maustaste in der Beziehungs, und klicken Sie dann auf **als Klasse anzeigen** . Die Beziehung mit angezeigt wird eine **Domäneneigenschaften** Depot, und zeigt die Vererbung und Beziehungen-Strukturen.

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)