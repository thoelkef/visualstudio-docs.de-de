---
title: 'CA1052: Statische Halter Typen sollten statisch oder notgeerbt sein.'
ms.date: 07/25/2019
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
ms.openlocfilehash: ba54b9f87fe8c8cd8bfdc86f39e3121135241e92
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547517"
---
# <a name="ca1052-static-holder-types-should-be-static-or-notinheritable"></a>CA1052: Statische Halter Typen sollten statisch oder notgeerbt sein.

|||
|-|-|
|TypeName|Staticholdertypesanalyzer|
|CheckId|CA1052|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein nicht abstrakter Typ enthält nur statische Member (mit Ausnahme eines möglichen Standardkonstruktors) und ist nicht mit dem [statischen](/dotnet/csharp/language-reference/keywords/static) oder [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) -Modifizierer deklariert.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Rule CA1052 geht davon aus, dass ein Typ, der nur statische Member enthält, nicht für die Vererbung konzipiert ist, da der Typ keine Funktionen bereitstellt, die in einem abgeleiteten Typ überschrieben werden können. Ein Typ, der nicht vererbt werden soll, sollte mit dem `static` -Modifizierer in C# markiert werden, um die Verwendung als Basistyp zu verhindern. Außerdem sollte der Standardkonstruktor entfernt werden. In Visual Basic sollte die-Klasse in ein [Modul](/dotnet/visual-basic/language-reference/statements/module-statement)konvertiert werden.

Diese Regel wird für abstrakte Klassen oder Klassen, die über eine Basisklasse verfügen, nicht ausgelöst. Die Regel wird jedoch für Klassen ausgelöst, die eine leere Schnittstelle unterstützen.

> [!NOTE]
> In der FxCop Analyzer-Implementierung dieser Regel umfasst Sie auch die Funktionalität von [rule CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, markieren Sie den `static` Typ als, entfernen Sie den Standardkonstruktor (C#), oder konvertieren Sie ihn in ein Modul (Visual Basic).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrückt eine Warnung aus dieser Regel nur, wenn der Typ für die Vererbung entworfen wurde. Das Fehlen des `static` Modifizierers deutet darauf hin, dass der Typ als Basistyp nützlich ist.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um beispielsweise anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar zu einer Editor config-Datei in Ihrem Projekt hinzu:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Behebung mit dem statischen Modifizierer

Im folgenden Beispiel wird gezeigt, wie Sie einen Verstoß gegen diese Regel beheben, indem Sie den `static` -Typ mit C#dem-Modifizierer in markieren:

```csharp
public static class StaticMembers
{
    public static int SomeProperty { get; set; }
    public static void SomeMethod() { }
}
```