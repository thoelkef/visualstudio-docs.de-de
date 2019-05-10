---
title: 'CA2233: Vorgänge sollten nicht überlaufen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c07dde4c3b992db30c9fc72a0dfa01f0f13b31e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806601"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Vorgänge sollten nicht überlaufen.

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Methode führt eine arithmetische Operation aus und überprüft nicht im voraus die Operanden um einen Überlauf zu vermeiden.

## <a name="rule-description"></a>Regelbeschreibung

Führen Sie arithmetische Operationen keine erste Validierung der Operanden aus, um sicherzustellen, dass das Ergebnis der Operation nicht außerhalb des Bereichs möglicher Werte für die beteiligten Datentypen ist. Je nach den Ausführungskontext und der beteiligten Datentypen, arithmetischer Überlauf kann dazu führen, entweder eine <xref:System.OverflowException?displayProperty=fullName> oder die höchstwertigen Bits des Ergebnisses wird verworfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Operanden vor dem Ausführen des Vorgangs.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die möglichen Werte der Operanden niemals die arithmetische Operation zu einem Überlauf führen.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

Eine Methode im folgenden Beispiel werden eine ganze Zahl, die gegen diese Regel verstößt bearbeitet. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] erfordert die **entfernen** Integer Überlauf-Option für diese Option, um ausgelöst werden deaktiviert werden.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Wenn die Methode in diesem Beispiel übergeben wird <xref:System.Int32.MinValue?displayProperty=fullName>, würde ein Unterlauf für der Vorgang. Dies bewirkt, dass die höchstwertigen Bits des Ergebnisses verworfen werden. Der folgende Code zeigt, wie in diesem Fall.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Ausgabe:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Beheben Sie mit der Validierung von Eingabeparametern

Im folgenden Beispiel wird der vorherige Verstoß korrigiert, durch den Wert der Eingabe zu überprüfen.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Beheben Sie mit einer aktivierten Block

Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem Sie den Vorgang in einen aktivierten Block einschließen. Wenn der Vorgang einen Überlauf, verursacht eine <xref:System.OverflowException?displayProperty=fullName> ausgelöst.

Geprüfte Blöcke werden nicht unterstützt, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aktivierte arithmetischen Über-/Unterlauf aktivieren

Wenn Sie aktiviert arithmetischen Über-/Unterlauf in C# -Code aktivieren, entspricht es umbruchvorgang jede ganze Zahl in einem aktivierten Block.

Um überprüfte arithmetischen Über-/Unterlauf in c# zu aktivieren:

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**.

2. Wählen Sie die Registerkarte **Build** aus, und klicken Sie auf **Erweitert**.

3. Wählen Sie **arithmetischen Über-/Unterlauf überprüfen** , und klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- <xref:System.OverflowException?displayProperty=fullName>
- [C#-Operatoren](/dotnet/csharp/language-reference/operators/index)
- [AKtiviert und nicht aktiviert](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)