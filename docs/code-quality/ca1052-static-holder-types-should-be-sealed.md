---
title: 'CA1052: Statische Haltertypen sollten versiegelt sein'
ms.date: 11/09/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ec090fd11c122699bafb3d72ca1eeab13ecb830
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825944"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statische Haltertypen sollten versiegelt sein

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine öffentliche oder geschützte, nicht abstrakten Typ enthält nur statische Member und ist nicht deklariert, mit der [versiegelten](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) Modifizierer.

## <a name="rule-description"></a>Regelbeschreibung

Regel CA1052 wird davon ausgegangen, dass ein Typ, der nur statische Member enthält, nicht geerbt werden, konzipiert ist, da der Typ keine Funktionalität bereit, die in einem abgeleiteten Typ überschrieben werden können. Ein Typ, der nicht geerbt werden soll, sollte mit markiert werden die `sealed` oder `NotInheritable` Modifizierer, um die Verwendung als einen Basistyp zu verhindern. Mit dieser Regel wird nicht für abstrakte Klassen ausgelöst werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, markieren Sie den Typ als `sealed` oder `NotInheritable`. Wenn Sie .NET Framework 2.0 abzielen, oder höher ein besserer Ansatz ist, markieren Sie den Typ als `static` oder `Shared`. Auf diese Weise müssen Sie deklarieren, einen privaten Konstruktor verhindert, dass die Klasse erstellt wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, nur dann, wenn der Typ geerbt werden sollen. Das Fehlen der `sealed` oder `NotInheritable` Modifizierers impliziert, dass der Typ als Basistyp verwendet werden kann.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Beheben Sie mit dem static-Modifizierer

Das folgende Beispiel zeigt, wie Sie einen Verstoß gegen diese Regel zu beheben, indem Sie den Typ mit dem `static` Modifizierer C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)