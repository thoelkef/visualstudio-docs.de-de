---
title: Domänenpfadsyntax
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: de364760b5d7446b050cd8931ea2e95867b88e81
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="domain-path-syntax"></a>Domänenpfadsyntax
In DSL-Definitionen wird eine XPath-artige Syntax für die Suche nach bestimmten Elementen in einem Modell verwendet.

 In der Regel ist es nicht erforderlich, direkt mit dieser Syntax zu arbeiten. Wenn sie in DSL-Details oder im Eigenschaftenfenster angezeigt wird, können Sie auf den nach unten weisenden Pfeil klicken und den Pfad-Editor verwenden. Der Pfad wird jedoch in dieser Form im Feld angezeigt, nachdem Sie den Editor verwendet haben.

 Ein Domänenpfad weist die folgende Form auf:

 *RelationshipName.PropertyName/! Rolle ""*

 ![CommentReferencesSubjects-verweisbeziehung](../modeling/media/dsl_reference.png "Dsl_reference")

 Die Syntax durchläuft die Baumstruktur des Modells. Z. B. die domänenbeziehung **CommentReferencesSubjects** in der Abbildung oben wurde eine **Themen** Rolle. Das Pfadsegment **/! Subjectt** gibt an, dass der Pfad für Elemente, die Zugriff über abgeschlossen ist die **Themen** Rolle.

 Jedes Segment beginnt mit dem Namen einer Domänenbeziehung. Wenn Durchlauf von einem Element an einer Beziehung ist, wird das Pfadsegment als *Relationship.PropertyName*. Ist der Hop über einen Link auf ein Element, das Pfadsegment angezeigt wird, als *Beziehung /! RoleName*.

 Die Syntax eines Pfads wird durch Schrägstriche unterteilt. Jedes Pfadsegment ist entweder ein Hop von einem Element zu einem Link (einer Instanz einer Beziehung) oder von einem Link zu einem Element. Pfadsegmente treten häufig paarweise auf. Ein Pfadsegment steht für einen Hop von einem Element zu einem Link, und das nächste Segment steht für einen Hop vom Link zum Element am anderen Ende. (Jeder Link kann auch die Quelle oder das Ziel der Beziehung selbst sein.)

 Der Name, den Sie für den Hop vom Element zum Link verwenden, ist der Wert von `Property Name` der Rolle. Der Name, den Sie für den Hop vom Link zum Element verwenden, ist der Zielrollenname.

## <a name="see-also"></a>Siehe auch

- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)