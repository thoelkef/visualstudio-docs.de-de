---
title: 'CA1061: Basisklassenmethoden nicht ausblenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd0927a9b8bcd0f4be7c020a25a32d6c9675ca05
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900537"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Basisklassenmethoden nicht ausblenden
|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein abgeleiteter Typ deklariert eine Methode mit dem gleichen Namen und die gleiche Anzahl von Parametern als eines seiner Basismethoden; mindestens einer der Parameter ist ein Basistyp des entsprechenden Parameters in der Basismethode. und alle übrigen Parameter über die Typen, die mit den entsprechenden Parametern in der Basismethode identisch sind.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ verdeckt, wenn die Parametersignatur der abgeleiteten Methode nur hinsichtlich der Typen unterscheidet, die schwächer abgeleitet als die entsprechenden Typen in der Parametersignatur der Basismethode sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder benennen Sie die Methode, oder ändern Sie die Parametersignatur, sodass die Methode die Basismethode nicht ausgeblendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzt.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]