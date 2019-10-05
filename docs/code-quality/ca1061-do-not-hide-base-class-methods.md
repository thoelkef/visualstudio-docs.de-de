---
title: 'CA1061: Basisklassenmethoden nicht ausblenden.'
ms.date: 11/04/2016
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
ms.openlocfilehash: eacd20dee0758ff481b259807ba52bb78b26f5d2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235388"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Basisklassenmethoden nicht ausblenden.

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein abgeleiteter Typ deklariert eine Methode, die denselben Namen und dieselbe Anzahl von Parametern wie eine seiner Basis Methoden hat. mindestens einer der Parameter ist ein Basistyp des entsprechenden Parameters in der Basis Methode. und alle verbleibenden Parameter verfügen über Typen, die mit den entsprechenden Parametern in der Basis Methode identisch sind.

## <a name="rule-description"></a>Regelbeschreibung
Eine Methode in einem Basistyp wird durch eine identikalisch benannte Methode in einem abgeleiteten Typ ausgeblendet, wenn die Parameter Signatur der abgeleiteten Methode nur von Typen abweicht, die schwächer abgeleitet sind als die entsprechenden Typen in der Parameter Signatur der Basis Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die-Methode, oder benennen Sie Sie um, oder ändern Sie die Parameter Signatur, sodass die-Methode die Basis Methode nicht ausblenden kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]