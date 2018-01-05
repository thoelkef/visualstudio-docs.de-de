---
title: "CA2233: Vorgänge sollten nicht überlaufen. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5d048476997517a835337b568930367f97c2c92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Vorgänge sollten nicht überlaufen
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Methode führt eine arithmetische Operation aus und überprüft die Operanden im Vorfeld nicht um einen Überlauf zu vermeiden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst zu überprüfen die Operanden aus, um sicherzustellen, dass das Ergebnis des Vorgangs nicht außerhalb des Bereichs möglicher Werte für die beteiligten Datentypen liegt. Je nach den Ausführungskontext und die beteiligten Datentypen arithmetischer Überlauf kann dazu führen, entweder eine <xref:System.OverflowException?displayProperty=fullName> oder die höchstwertigen Bits des Ergebnisses verworfen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Operanden vor dem Ausführen des Vorgangs.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die möglichen Werte der Operanden niemals die arithmetische Operation zu einem Überlauf führen.  
  
## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes  
  
### <a name="description"></a>Beschreibung  
 Eine Methode im folgenden Beispiel verändert, eine ganze Zahl, die mit dieser Regel verletzt wird. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]erfordert die **entfernen** Integer Überlauf-Option für diese Option, um auslösen deaktiviert werden soll.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>Kommentare  
 Wenn die Methode in diesem Beispiel übergeben wird <xref:System.Int32.MinValue?displayProperty=fullName>, würde ein Unterlauf für der Vorgang. Dies bewirkt, dass das höchstwertige Bit des Ergebnisses verworfen werden. Der folgende Code zeigt, wie in diesem Fall.  
  
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
  
### <a name="output"></a>Ausgabe  
  
```  
2147483647  
```  
  
## <a name="fix-with-input-parameter-validation"></a>Beheben von mit Eingabeparameter-Überprüfung  
  
### <a name="description"></a>Beschreibung  
 Im folgende Beispiel wird der vorherige Verstoß durch Überprüfen des Werts der Eingabe korrigiert.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>Beheben von mit einem Checked-Block  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, durch den Vorgang in einem überprüften Namespaceblock einschließen. Wenn die Operation einen Überlauf verursacht eine <xref:System.OverflowException?displayProperty=fullName> ausgelöst.  
  
 Beachten Sie, dass geprüfte Blöcke nicht unterstützt werden [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aktivieren Sie dieses Kontrollkästchen aktiviert arithmetischen Über-/Unterlauf  
 Wenn Sie aktivierten arithmetischen Überlauf/Unterlauf in c# aktivieren, entspricht dies dem umbruchvorgang jede ganze Zahl in einem geprüften Block.  
  
 **So aktivieren Sie aktivierten arithmetischen Überlauf/Unterlauf in c#**  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**.  
  
2.  Wählen Sie die Registerkarte **Build** aus, und klicken Sie auf **Erweitert**.  
  
3.  Wählen Sie **arithmetischen Über-/Unterlauf prüfen** , und klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C#-Operatoren](/dotnet/csharp/language-reference/operators/index)   
 [AKtiviert und nicht aktiviert](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)