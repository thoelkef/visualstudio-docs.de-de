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
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545235"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Vorgänge sollten nicht überlaufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode führt eine arithmetische Operation aus und überprüft die Operanden nicht im voraus, um einen Überlauf zu verhindern.

## <a name="rule-description"></a>Beschreibung der Regel
 Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst die Operanden zu überprüfen, um sicherzustellen, dass sich das Ergebnis des Vorgangs nicht außerhalb des Bereichs der möglichen Werte für die betroffenen Datentypen befindet. Abhängig vom Ausführungs Kontext und den beteiligten Datentypen kann der arithmetische Überlauf dazu führen, dass entweder ein <xref:System.OverflowException?displayProperty=fullName> oder die signifikantesten Bits des Ergebnisses verworfen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Operanden, bevor Sie den Vorgang ausführen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die möglichen Werte der Operanden niemals einen Überlauf der arithmetischen Operation bewirken.

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

### <a name="description"></a>BESCHREIBUNG
 Eine Methode im folgenden Beispiel bearbeitet eine Ganzzahl, die gegen diese Regel verstößt. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] erfordert, dass die Option zum **Entfernen** ganz Zahl Überlauf deaktiviert wird, damit diese ausgelöst wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Kommentare
 Wenn die-Methode in diesem Beispiel weitergegeben wird <xref:System.Int32.MinValue?displayProperty=fullName> , würde der Vorgang zu einem Unterlauf. Dies bewirkt, dass das signifikanteste Bit des Ergebnisses verworfen wird. Der folgende Code zeigt, wie dies geschieht.

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

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der Wert der Eingabe überprüft wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Korrektur mit einem aktivierten Block

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem der-Vorgang in einen aktivierten-Block umwickelt wird. Wenn der Vorgang einen Überlauf verursacht, wird eine ausgelöst <xref:System.OverflowException?displayProperty=fullName> .

 Beachten Sie, dass aktivierte Blöcke in nicht unterstützt werden [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aktivierten arithmetischen Überlauf/Unterlauf aktivieren
 Wenn Sie den überprüften arithmetischen Überlauf/Unterlauf in c# aktivieren, entspricht dies dem Umtragen jeder ganzzahligen Operation in einem aktivierten Block.

 **So aktivieren Sie den überprüften arithmetischen Überlauf/Unterlauf in C #**

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

2. Wählen Sie die Registerkarte **Build** aus, und klicken Sie auf **Erweitert**.

3. Wählen Sie **auf arithmetischen Überlauf/Unterlauf prüfen aus** , und klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen
 <xref:System.OverflowException?displayProperty=fullName>Aktivierte [und überprüfte](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e) [c#-Operatoren](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)
