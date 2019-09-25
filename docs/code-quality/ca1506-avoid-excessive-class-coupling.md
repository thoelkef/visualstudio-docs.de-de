---
title: 'CA1506: Übermäßige Klassenkopplungen vermeiden.'
ms.date: 11/04/2016
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
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234494"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ oder eine Methode ist mit vielen anderen Typen verknüpft.

## <a name="rule-description"></a>Regelbeschreibung

Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.

Typen und Methoden mit einem hohen Grad an Klassen Kopplung können schwer zu verwalten sein. Es empfiehlt sich, Typen und Methoden zu nutzen, die eine geringe Kopplung und einen hohen Zusammenhalt aufweisen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um diese Verletzung zu beheben, versuchen Sie, den Typ oder die Methode umzugestalten, um die Anzahl der Typen, mit denen Sie gekoppelt ist, zu reduzieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Schließen Sie diese Warnung aus, wenn der Typ oder die Methode trotz der großen Anzahl von Abhängigkeiten von anderen Typen als wart Bar eingestuft wird.

## <a name="see-also"></a>Siehe auch

- [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)
- [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/code-metrics-values.md)