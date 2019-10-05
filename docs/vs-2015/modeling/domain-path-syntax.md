---
title: Domänenpfadsyntax | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c115e8fff6cddbc1b08c697b72c7bda3a970ed4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203454"
---
# <a name="domain-path-syntax"></a>Domänenpfadsyntax
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In DSL-Definitionen wird eine XPath-artige Syntax für die Suche nach bestimmten Elementen in einem Modell verwendet.  
  
 In der Regel ist es nicht erforderlich, direkt mit dieser Syntax zu arbeiten. Wenn sie in DSL-Details oder im Eigenschaftenfenster angezeigt wird, können Sie auf den nach unten weisenden Pfeil klicken und den Pfad-Editor verwenden. Der Pfad wird jedoch in dieser Form im Feld angezeigt, nachdem Sie den Editor verwendet haben.  
  
 Ein Domänenpfad weist die folgende Form auf:  
  
 *RelationshipName.PropertyName/! Rolle*  
  
 ![CommentReferencesSubjects-verweisbeziehung](../modeling/media/dsl-reference.png "Dsl_reference")  
  
 Die Syntax durchläuft die Baumstruktur des Modells. Z. B. die domänenbeziehung **"commentreferencessubjects"** in der obigen Abbildung weist eine **Themen** Rolle. Das Pfadsegment **/! Subjectt** gibt an, dass der Pfad auf Elemente, die über Zugriff auf abgeschlossen ist die **Themen** Rolle.  
  
 Jedes Segment beginnt mit dem Namen einer Domänenbeziehung. Wenn der Durchlauf von einem Element zu einer Beziehung erfolgt, wird das Pfadsegment als *Beziehung.Eigenschaftenname*. Wenn der Hop von einem Link auf ein Element ist, wird das Pfadsegment als *Beziehung /! RoleName*.  
  
 Die Syntax eines Pfads wird durch Schrägstriche unterteilt. Jedes Pfadsegment ist entweder ein Hop von einem Element zu einem Link (einer Instanz einer Beziehung) oder von einem Link zu einem Element. Pfadsegmente treten häufig paarweise auf. Ein Pfadsegment steht für einen Hop von einem Element zu einem Link, und das nächste Segment steht für einen Hop vom Link zum Element am anderen Ende. (Jeder Link kann auch die Quelle oder das Ziel der Beziehung selbst sein.)  
  
 Der Name, den Sie für den Hop vom Element zum Link verwenden, ist der Wert von `Property Name` der Rolle. Der Name, den Sie für den Hop vom Link zum Element verwenden, ist der Zielrollenname.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)
