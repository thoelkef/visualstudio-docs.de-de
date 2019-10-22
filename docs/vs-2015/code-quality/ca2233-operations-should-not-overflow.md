---
title: 'CA2233: Vorgänge sollten nicht überlaufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 70a0bab8cfb3bf14a763f759e0e44a754ad878d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662780"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Vorgänge sollten nicht überlaufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode führt eine arithmetische Operation aus und überprüft die Operanden nicht im voraus, um einen Überlauf zu verhindern.

## <a name="rule-description"></a>Regelbeschreibung
 Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst die Operanden zu überprüfen, um sicherzustellen, dass sich das Ergebnis des Vorgangs nicht außerhalb des Bereichs der möglichen Werte für die betroffenen Datentypen befindet. Abhängig vom Ausführungs Kontext und den beteiligten Datentypen kann der arithmetische Überlauf dazu führen, dass entweder eine <xref:System.OverflowException?displayProperty=fullName> oder die signifikantesten Bits des Ergebnisses verworfen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Operanden, bevor Sie den Vorgang ausführen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die möglichen Werte der Operanden niemals einen Überlauf der arithmetischen Operation bewirken.

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

### <a name="description"></a>Beschreibung
 Eine Methode im folgenden Beispiel bearbeitet eine Ganzzahl, die gegen diese Regel verstößt. für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] muss die Option ganzzahlige Überlauf **Entfernen** deaktiviert sein, damit diese ausgelöst wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Kommentare
 Wenn die Methode in diesem Beispiel <xref:System.Int32.MinValue?displayProperty=fullName> weitergeleitet wird, würde der Vorgang zu einem Unterlauf. Dies bewirkt, dass das signifikanteste Bit des Ergebnisses verworfen wird. Der folgende Code zeigt, wie dies geschieht.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 Auftraten

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Output

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Behebung mit der Überprüfung von Eingabe Parametern

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der Wert der Eingabe überprüft wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Korrektur mit einem aktivierten Block

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem der-Vorgang in einen aktivierten-Block umwickelt wird. Wenn der Vorgang einen Überlauf verursacht, wird eine <xref:System.OverflowException?displayProperty=fullName> ausgelöst.

 Beachten Sie, dass aktivierte Blöcke in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nicht unterstützt werden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aktivierten arithmetischen Überlauf/Unterlauf aktivieren
 Wenn Sie den aktivierten arithmetischen Überlauf/Unterlauf C#in aktivieren, entspricht dies dem umwickeln aller ganzzahligen Vorgänge in einem aktivierten Block.

 **So aktivieren Sie den überprüften arithmetischen Überlauf/Unterlauf inC#**

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

2. Wählen Sie die Registerkarte **Build** aus, und klicken Sie auf **Erweitert**.

3. Wählen Sie **auf arithmetischen Überlauf/Unterlauf prüfen aus** , und klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
 aktivierte und nicht über [prüfte](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e) [ C# <xref:System.OverflowException?displayProperty=fullName>](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)
