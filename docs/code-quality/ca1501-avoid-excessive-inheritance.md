---
title: 'CA1501: Übermäßige Vererbung vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d77ecc255f03e38e39a9321d9c7a9e5568e94a4d
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232302"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Übermäßige Vererbung vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief.

## <a name="rule-description"></a>Regelbeschreibung

Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. Mit dieser Regel schränkt die Analyse für Hierarchien im selben Modul.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ aus einer Basisklasse, die in der Vererbungshierarchie weniger komplex ist, oder entfernen Sie einige der mittleren Basistypen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Allerdings kann der Code schwieriger zu warten sein. Beachten Sie, dass je nach Sichtbarkeit der Basistypen, Auflösen von Verstöße gegen diese Regel Änderungen erstellen kann. Entfernen die öffentliche Basistypen ist beispielsweise eine unterbrechende Änderung.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt:

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]