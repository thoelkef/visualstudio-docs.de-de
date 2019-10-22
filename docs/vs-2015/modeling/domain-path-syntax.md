---
title: Syntax des Domänen Pfads | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669738"
---
# <a name="domain-path-syntax"></a>Domänenpfadsyntax
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In DSL-Definitionen wird eine XPath-artige Syntax für die Suche nach bestimmten Elementen in einem Modell verwendet.

 In der Regel ist es nicht erforderlich, direkt mit dieser Syntax zu arbeiten. Wenn sie in DSL-Details oder im Eigenschaftenfenster angezeigt wird, können Sie auf den nach unten weisenden Pfeil klicken und den Pfad-Editor verwenden. Der Pfad wird jedoch in dieser Form im Feld angezeigt, nachdem Sie den Editor verwendet haben.

 Ein Domänenpfad weist die folgende Form auf:

 *RelationshipName. PropertyName/! Spielen*

 ![Commentreferencessubjects-Verweis Beziehung](../modeling/media/dsl-reference.png "dsl_reference")

 Die Syntax durchläuft die Baumstruktur des Modells. Die Domänen Beziehung **commentreferencessubjects** in der obigen Abbildung hat z. b **. eine** betreffrolle. Das Pfad Segment **/! Subjett** gibt an, dass der Pfad für Elemente abgeschlossen ist, auf die über die **Themen** Rolle zugegriffen wird.

 Jedes Segment beginnt mit dem Namen einer Domänenbeziehung. Wenn der Durchlauf von einem Element zu einer Beziehung erfolgt, wird das Pfad Segment als *Relationship. PropertyName*angezeigt. Wenn der Hop von einem Link zu einem Element erfolgt, wird das Pfad Segment als *Beziehung/! RoleName*.

 Die Syntax eines Pfads wird durch Schrägstriche unterteilt. Jedes Pfadsegment ist entweder ein Hop von einem Element zu einem Link (einer Instanz einer Beziehung) oder von einem Link zu einem Element. Pfadsegmente treten häufig paarweise auf. Ein Pfadsegment steht für einen Hop von einem Element zu einem Link, und das nächste Segment steht für einen Hop vom Link zum Element am anderen Ende. (Jeder Link kann auch die Quelle oder das Ziel der Beziehung selbst sein.)

 Der Name, den Sie für den Hop vom Element zum Link verwenden, ist der Wert von `Property Name` der Rolle. Der Name, den Sie für den Hop vom Link zum Element verwenden, ist der Zielrollenname.

## <a name="see-also"></a>Siehe auch
 [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)
