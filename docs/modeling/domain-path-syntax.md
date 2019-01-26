---
title: Domänenpfadsyntax
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: b8825d123c9d4cce5b72582fe213ba61ce6e7f6b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975958"
---
# <a name="domain-path-syntax"></a>Domänenpfadsyntax
In DSL-Definitionen wird eine XPath-artige Syntax für die Suche nach bestimmten Elementen in einem Modell verwendet.

 In der Regel ist es nicht erforderlich, direkt mit dieser Syntax zu arbeiten. Wenn sie in DSL-Details oder im Eigenschaftenfenster angezeigt wird, können Sie auf den nach unten weisenden Pfeil klicken und den Pfad-Editor verwenden. Der Pfad wird jedoch in dieser Form im Feld angezeigt, nachdem Sie den Editor verwendet haben.

 Ein Domänenpfad weist die folgende Form auf:

 *RelationshipName.PropertyName/!Role*

 ![CommentReferencesSubjects-Verweisbeziehung](../modeling/media/dsl_reference.png)

 Die Syntax durchläuft die Baumstruktur des Modells. Z. B. die domänenbeziehung **"commentreferencessubjects"** in der obigen Abbildung weist eine **Themen** Rolle. Das Pfadsegment **/! Subjectt** gibt an, dass der Pfad auf Elemente, die über Zugriff auf abgeschlossen ist die **Themen** Rolle.

 Jedes Segment beginnt mit dem Namen einer Domänenbeziehung. Wenn der Durchlauf von einem Element zu einer Beziehung erfolgt, wird das Pfadsegment als *Beziehung.Eigenschaftenname*. Wenn der Hop von einem Link auf ein Element ist, wird das Pfadsegment als *Beziehung /! RoleName*.

 Die Syntax eines Pfads wird durch Schrägstriche unterteilt. Jedes Pfadsegment ist entweder ein Hop von einem Element zu einem Link (einer Instanz einer Beziehung) oder von einem Link zu einem Element. Pfadsegmente treten häufig paarweise auf. Ein Pfadsegment steht für einen Hop von einem Element zu einem Link, und das nächste Segment steht für einen Hop vom Link zum Element am anderen Ende. (Jeder Link kann auch die Quelle oder das Ziel der Beziehung selbst sein.)

 Der Name, den Sie für den Hop vom Element zum Link verwenden, ist der Wert von `Property Name` der Rolle. Der Name, den Sie für den Hop vom Link zum Element verwenden, ist der Zielrollenname.

## <a name="see-also"></a>Siehe auch

- [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)