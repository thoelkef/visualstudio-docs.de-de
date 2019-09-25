---
title: 'CA1505: Nicht wartbaren Code vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ba027ef2e663870d0af50bc6d2154133f7980c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234542"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Nicht wartbaren Code vermeiden.

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.

## <a name="rule-description"></a>Regelbeschreibung

Der Wartbarkeitsindex wird mithilfe der folgenden Metriken berechnet: Codezeilen, Programm Volume und zyklomatische Komplexität. Das Programm Volume ist ein Maß für die Schwierigkeit, ein Typ oder eine Methode zu verstehen, die auf der Anzahl von Operatoren und Operanden im Code basiert. Die zyklomatische Komplexität ist ein Maß für die strukturelle Komplexität des Typs oder der Methode. Weitere Informationen zu Codemetriken finden Sie unter [Messen der Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/code-metrics-values.md).

Ein niedriger Wartbarkeitsindex gibt an, dass ein Typ oder eine Methode wahrscheinlich schwierig zu verwalten ist, und wäre ein guter Kandidat für die Umgestaltung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entwerfen Sie zum Beheben dieses Verstoßes den Typ oder die Methode neu, und versuchen Sie, ihn in kleinere und stärker fokussierte Typen oder Methoden aufzuteilen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie können diese Warnung unterdrücken, wenn der Typ oder die Methode nicht geteilt werden kann oder trotz ihrer großen Größe als wart Bar eingestuft wird.

## <a name="see-also"></a>Siehe auch

- [Wart barkeits Warnungen](../code-quality/maintainability-warnings.md)
- [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/code-metrics-values.md)