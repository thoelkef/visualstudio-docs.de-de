---
title: 'CA1061: Basisklassenmethoden nicht ausblenden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57da84c7109826ff08a60ca5f2b808facaaa5ce9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995609"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Basisklassenmethoden nicht ausblenden.

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein abgeleiteter Typ deklariert eine Methode mit dem gleichen Namen und mit der gleichen Anzahl von Parametern als eines seiner Basismethoden; mindestens einer der Parameter ist ein Basistyp des entsprechenden Parameters in der Basis-Methode. und alle übrigen Parameter müssen Typen, die mit den entsprechenden Parametern in die Basismethode identisch sind.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ ausgeblendet, wenn die Parametersignatur der abgeleiteten Methode nur von Typen unterscheidet, die schwächer abgeleitet als die entsprechenden Typen in der Parametersignatur der Basismethode sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder benennen Sie die Methode, oder ändern Sie die Parametersignatur, sodass die Methode die Basismethode nicht ausgeblendet wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]