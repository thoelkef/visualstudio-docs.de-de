---
title: 'CA1061: Basisklassen Methoden nicht ausblenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 24579e6aa3ba1bf70ed6f195091152b60f3232a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604012"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Basisklassenmethoden nicht ausblenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategorie|Microsoft. Design|
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

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
