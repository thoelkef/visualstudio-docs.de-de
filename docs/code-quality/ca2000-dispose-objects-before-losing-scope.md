---
title: 'CA2000: Objekte verwerfen, bevor Bereich verloren geht.'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804976"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Objekte verwerfen, bevor Bereich verloren geht.

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein lokales Objekt ein <xref:System.IDisposable> Typ erstellt wird, aber das Objekt ist nicht freigegeben werden, bevor alle Verweise auf das Objekt außerhalb des gültigen Bereichs liegen.

## <a name="rule-description"></a>Regelbeschreibung

Wenn ein verwerfbares Objekt nicht explizit verworfen wird, bevor alle Verweise darauf außerhalb des gültigen Bereichs liegen, wird das Objekt zu einer unbestimmten Zeit verworfen, wenn der Garbage Collector den Finalizer des Objekts ausführt. Da möglicherweise ein Ausnahmeereignis auftritt, durch das die Ausführung des Finalizers des Objekts verhindert wird, muss das Objekt stattdessen explizit verworfen werden.

### <a name="special-cases"></a>Sonderfälle

Regel CA2000 wird für lokale Objekte der folgenden Typen nicht ausgelöst, selbst wenn das Objekt nicht verworfen wird:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Gibt ein Objekt von einem dieser Typen an einen Konstruktor zu übergeben, und klicken Sie dann auf ein Feld Zuweisen einer *dispose Übertragung des Abonnementbesitzes* in den neu erstellten Typ. Der neu erstellte Typ ist, also jetzt verantwortlich für das Verwerfen des Objekts. Wenn Ihr Code ein Objekt von einem dieser Typen an einen Konstruktor erfolgreich ist, sind keine Verletzung der Regel, dass CA2000 tritt auf, auch wenn das Objekt nicht, bevor alle Verweise darauf verworfen wird außerhalb des gültigen Bereichs.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen Sie <xref:System.IDisposable.Dispose%2A> für das Objekt auf, bevor sich alle Verweise darauf außerhalb des gültigen Bereichs befinden.

Sie können die [ `using` Anweisung](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) in Visual Basic) zum Umschließen von Objekten, die implementieren <xref:System.IDisposable>. Objekte, die auf diese Weise umschlossen werden automatisch freigegeben werden, am Ende der `using` Block. Jedoch die folgenden Situationen nicht oder kann nicht verarbeitet werden, mit einem `using` Anweisung:

- Um ein verwerfbares Objekt zurückzugeben, muss das Objekt erstellt, eine `try/finally` -Block außerhalb einer `using` Block.

- Nicht Mitglieder verwerfbares Objekt im Konstruktor Initialisieren einer `using` Anweisung.

- Bei Konstruktoren, die von nur einem Ausnahmehandler geschützt sind geschachtelt sind, der [Teil der Übernahme einer `using` Anweisung](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), ein Fehler in der äußeren Konstruktor kann dazu führen, das nie vom geschachtelten Konstruktor erstellte Objekt geschlossen wird. Im folgenden Beispiel einen Fehler in der <xref:System.IO.StreamReader> Konstruktor kann dazu führen, die <xref:System.IO.FileStream> Objekt nie geschlossen wird. CA2000 kennzeichnet einen Verstoß gegen die Regel in diesem Fall aus.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Dynamische Objekte sollten ein Schattenobjekt verwenden, um die Implementieren des Dispose-Musters von <xref:System.IDisposable> Objekte.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel, es sei denn:

- Sie haben eine Methode aufgerufen wird, auf das Objekt, das Aufrufe `Dispose`, z. B. <xref:System.IO.Stream.Close%2A>
- Die Methode, die der Rückgabe der Warnung wird ausgelöst, eine <xref:System.IDisposable> Objekt, das das Objekt umschließt.
- Zuweisen von Methode Dispose Besitz keinen; d. h. dafür verantwortlich, die das Objekt verwerfen übertragen wird, zu einem anderen Objekt oder einen Wrapper, die in der Methode erstellt und an den Aufrufer zurückgegeben

## <a name="related-rules"></a>Verwandte Regeln

- [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: Objekte nicht mehrmals verwerfen](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Beispiel

Wenn Sie eine Methode, die ein verwerfbares Objekt zurückgibt implementieren, verwenden Sie einen Try/finally-Block ohne einen Catch-Block, um sicherzustellen, dass das Objekt verworfen wird. Mit einem try/finally-Block lassen Sie Ausnahmen zu, die am Fehlerpunkt ausgelöst werden sollen, und stellen sicher, dass das Objekt verworfen wird.

In der OpenPort1-Methode kann der Aufruf zum Öffnen des SerialPorts des ISerializable-Objekts oder der Aufruf von SomeMethod fehlschlagen. Eine CA2000-Warnung wird für diese Implementierung ausgelöst.

In der OpenPort2-Methode werden zwei SerialPort-Objekte deklariert und auf NULL festgelegt:

- `tempPort` zum Testen, ob die Methodenoperationen erfolgreich ausgeführt werden.

- `port` für den Rückgabewert der Methode.

`tempPort` wird erstellt und in einem `try`-Block geöffnet. Alle anderen erforderlichen Arbeiten werden im gleichen `try`-Block ausgeführt. Am Ende des `try`-Blocks wird dem `port`-Objekt, das zurückgegeben wird, der geöffnete Port zugewiesen und das `tempPort`-Objekt wird auf `null` festgelegt.

Der `finally`-Block überprüft den Wert von `tempPort`. Wenn nicht NULL, ist eine Operation in der Methode fehlgeschlagen und `tempPort` wird geschlossen, um sicherzustellen, dass alle Ressourcen freigegeben werden. Das zurückgegebene Port-Objekt enthält das geöffnete SerialPort-Objekt, wenn die Operationen der Methode erfolgreich waren, oder es ist NULL, wenn eine Operation fehlschlug.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If

   End Try

   Return port

End Function
```

## <a name="example"></a>Beispiel

Standardmäßig verfügt Visual Basic-Compiler alle arithmetische Operatoren, die auf Überläufe zu überprüfen. Daher kann jede arithmetische Visual Basic-Operation eine <xref:System.OverflowException> auslösen. Dies kann zu unerwarteten Regelverletzungen führen, z. B. CA2000. Die folgende CreateReader1-Funktion erzeugt z. B. eine CA2000-Verletzung, da der Visual Basic-Compiler einen Befehl zur Überlaufprüfung für die Hinzufügung ausgibt, die eine Ausnahme auslösen könnte, durch die der StreamReader nicht verworfen werden würde.

Um dieses zu korrigieren, können Sie das Ausgeben von Überlaufprüfungen durch den Visual Basic-Compiler im Projekt deaktivieren, oder Sie können den Code entsprechend der folgenden CreateReader2-Funktion ändern.

Um das Ausgeben von überlaufprüfungen zu deaktivieren, mit der rechten Maustaste des Projektnamen im Projektmappen-Explorer, und klicken Sie dann auf **Eigenschaften**. Klicken Sie auf **Kompilieren**, klicken Sie auf **Advanced Compile Options**, und überprüfen Sie dann **Überprüfungen auf Ganzzahlüberlauf entfernen**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)