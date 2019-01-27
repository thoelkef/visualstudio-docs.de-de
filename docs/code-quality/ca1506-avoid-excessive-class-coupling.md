---
title: 'CA1506: Übermäßige Klassenkopplungen vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a359df7f9538c1b1bc3fe03f1f711a41adca009e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931244"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ oder Methode ist mit vielen anderen Knotentypen gekoppelt.

## <a name="rule-description"></a>Regelbeschreibung
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.

 Typen und Methoden, die einen hohen Grad an Klassenkopplungen können schwierig zu verwalten sein. Es hat sich bewährt, Typen und Methoden, die lose Kopplung und hohe Kohäsion aufweisen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, versuchen Sie, gestalten Sie den Typ oder eine Methode zum Verringern der Anzahl von Typen, mit denen er verknüpft ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Ausgeschlossen Sie diese Warnung, wenn der Typ oder die Methode weiterhin gewartet werden kann, trotz der großen Anzahl von Abhängigkeiten von anderen Typen betrachtet wird.

## <a name="see-also"></a>Siehe auch

- [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)
- [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/code-metrics-values.md)