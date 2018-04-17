---
title: Domäne Pfadsyntax | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3bac81f79b2639a7b1b4f93055855981d4c30786
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
 [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)