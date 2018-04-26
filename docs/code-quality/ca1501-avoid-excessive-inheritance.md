---
title: 'CA1501: Übermäßige Vererbung vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62270ac1917dea24586247ade5f8f5e802f84707
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Übermäßige Vererbung vermeiden
|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief.

## <a name="rule-description"></a>Regelbeschreibung
 Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. Diese Regel schränkt die Analyse auf Hierarchien im selben Modul.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem Basistyp, der weniger tief in der Vererbungshierarchie ist, oder entfernen Sie einige intermediate Basistypen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel. Allerdings kann der Code schwieriger zu verwalten sein. Beachten Sie, dass abhängig von der Sichtbarkeit von Basistypen, Auflösen von Verstöße gegen diese Regel wichtige Änderungen erstellen kann. Entfernen von öffentlichen Basistypen ist z. B. eine unterbrechende Änderung.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]