---
title: 'CA1052: Statische Haltertypen sollten versiegelt sein.'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 46a8c9a4e22c7a54a4b2b68f95bb2b81f3a0888e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870385"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statische Haltertypen sollten versiegelt sein.

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein nicht abstrakter Typ enthält nur statische Member und ist nicht deklariert, mit der [versiegelten](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) Modifizierer.

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Regel CA1052 wird davon ausgegangen, dass ein Typ, der nur statische Member enthält, nicht geerbt werden, konzipiert ist, da der Typ keine Funktionalität bereit, die in einem abgeleiteten Typ überschrieben werden können. Ein Typ, der nicht geerbt werden soll, sollte mit markiert werden die `sealed` oder `NotInheritable` Modifizierer, um die Verwendung als einen Basistyp zu verhindern. Mit dieser Regel wird nicht für abstrakte Klassen ausgelöst werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, markieren Sie den Typ als `sealed` oder `NotInheritable`. Wenn Sie .NET Framework 2.0 abzielen, oder höher ein besserer Ansatz ist, markieren Sie den Typ als `static` oder `Shared`. Auf diese Weise müssen Sie deklarieren, einen privaten Konstruktor verhindert, dass die Klasse erstellt wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, nur dann, wenn der Typ geerbt werden sollen. Das Fehlen der `sealed` oder `NotInheritable` Modifizierers impliziert, dass der Typ als Basistyp verwendet werden kann.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1052.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Beheben Sie mit dem static-Modifizierer

Das folgende Beispiel zeigt, wie Sie einen Verstoß gegen diese Regel zu beheben, indem Sie den Typ mit dem `static` Modifizierer C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)