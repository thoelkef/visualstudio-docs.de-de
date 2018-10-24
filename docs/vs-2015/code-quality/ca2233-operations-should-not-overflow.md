---
title: 'CA2233: Vorgänge sollten nicht überlaufen. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836657"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Vorgänge sollten nicht überlaufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode führt eine arithmetische Operation aus und überprüft nicht im voraus die Operanden um einen Überlauf zu vermeiden.

## <a name="rule-description"></a>Regelbeschreibung
 Arithmetische Operationen sollte nicht ausgeführt werden, ohne zuerst zu überprüfen die Operanden aus, um sicherzustellen, dass das Ergebnis der Operation nicht außerhalb des Bereichs möglicher Werte für die beteiligten Datentypen ist. Je nach den Ausführungskontext und der beteiligten Datentypen, arithmetischer Überlauf kann dazu führen, entweder eine <xref:System.OverflowException?displayProperty=fullName> oder die höchstwertigen Bits des Ergebnisses wird verworfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Operanden vor dem Ausführen des Vorgangs.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die möglichen Werte der Operanden niemals die arithmetische Operation zu einem Überlauf führen.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

### <a name="description"></a>Beschreibung
 Eine Methode im folgenden Beispiel werden eine ganze Zahl, die gegen diese Regel verstößt bearbeitet. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] erfordert die **entfernen** Integer Überlauf-Option für diese Option, um ausgelöst werden deaktiviert werden.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Kommentare
 Wenn die Methode in diesem Beispiel übergeben wird <xref:System.Int32.MinValue?displayProperty=fullName>, würde ein Unterlauf für der Vorgang. Dies bewirkt, dass die höchstwertigen Bits des Ergebnisses verworfen werden. Der folgende Code zeigt, wie in diesem Fall.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

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

## <a name="fix-with-input-parameter-validation"></a>Beheben Sie mit der Validierung von Eingabeparametern

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, durch den Wert der Eingabe zu überprüfen.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Beheben Sie mit einer aktivierten Block

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem Sie den Vorgang in einen aktivierten Block einschließen. Wenn der Vorgang einen Überlauf, verursacht eine <xref:System.OverflowException?displayProperty=fullName> ausgelöst.

 Beachten Sie, dass geprüfte Blöcke nicht unterstützt werden [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aktivierte arithmetischen Über-/Unterlauf aktivieren
 Wenn Sie aktiviert arithmetischen Über-/Unterlauf in C# -Code aktivieren, entspricht es umbruchvorgang jede ganze Zahl in einem aktivierten Block.

 **So schalten Sie die aktivierten arithmetischen Über-/Unterlauf in c#**

1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**.

2.  Wählen Sie die Registerkarte **Build** aus, und klicken Sie auf **Erweitert**.

3.  Wählen Sie **arithmetischen Über-/Unterlauf überprüfen** , und klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
 <xref:System.OverflowException?displayProperty=fullName> [C#-Operatoren](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked und Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



