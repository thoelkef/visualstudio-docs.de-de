---
title: "CA2233: Vorg&#228;nge sollten nicht &#252;berlaufen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233: Vorg&#228;nge sollten nicht &#252;berlaufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode führt einen arithmetischen Vorgang aus und validiert die Operanden nicht im Voraus, um einen Überlauf zu verhindern.  
  
## Regelbeschreibung  
 Arithmetische Operationen sollten erst nach einer Validierung der Operanden ausgeführt werden, um sicherzustellen, dass das Ergebnis der Operation nicht außerhalb des Bereichs möglicher Werte der beteiligten Datentypen liegt.  Je nach dem Ausführungskontext und den beteiligten Datentypen kann ein arithmetischer Überlauf entweder zu einer <xref:System.OverflowException?displayProperty=fullName> führen oder bewirken, dass die höchstwertigen Bits des Ergebnisses verworfen werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, validieren Sie die Operanden vor der Ausführung des Vorgangs.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die möglichen Werte der Operanden niemals zu einem Überlauf der arithmetischen Operation führen.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Eine Methode im folgenden Beispiel manipuliert eine ganze Zahl, die gegen die Regel verstößt.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] erfordert das Deaktivieren der Ganzzahlüberlaufoption **Entfernen**, damit der Vorgang ausgelöst werden kann.  
  
### Code  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Kommentare  
 Wenn an die Methode in diesem Beispiel <xref:System.Int32.MinValue?displayProperty=fullName> übergeben wird, würde ein Unterlauf für die Operation auftreten.  Dies bewirkt, dass das höchstwertige Bit des Ergebnisses verworfen wird.  Der folgende Code zeigt, wie es dazu kommt.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Ausgabe  
  
```  
2147483647  
```  
  
## Korrektur mit Validierung von Eingabeparametern  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der Wert der Eingabe überprüft wird.  
  
### Code  
 [!code-cs[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## Korrektur mit einem Checked\-Block  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem die Operation von einem checked\-Block umschlossen wird.  Wenn die Operation einen Überlauf verursacht, wird eine <xref:System.OverflowException?displayProperty=fullName> ausgelöst.  
  
 Beachten Sie, dass checked\-Blöcke in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nicht unterstützt werden.  
  
### Code  
 [!code-cs[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## Aktivieren des mit checked ausgeführten arithmetischen Über\-\/Unterlaufs  
 Wenn Sie den mit checked ausgeführten arithmetischen Überlauf\/Unterlauf in C\# aktivieren, entspricht dies dem Umschließen jeder einzelnen Ganzzahloperation mit einem checked\-Block.  
  
 **So aktivieren Sie den mit checked ausgeführten arithmetischen Überlauf\/Unterlauf in C\#**  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**.  
  
2.  Wählen Sie die Registerkarte **Erstellen** aus, und klicken Sie dann auf **Erweitert**.  
  
3.  Wählen Sie **Auf arithmetischen Überlauf\/Unterlauf überprüfen** aus, und klicken Sie auf **OK**.  
  
## Siehe auch  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C\#\-Operatoren](/dotnet/csharp/language-reference/operators/index)   
 [Checked und Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)