---
title: 'CA2000: Objekte verwerfen, bevor Bereich verloren geht'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b492324b87bfc25741492669b7c659c43fc9765
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Objekte verwerfen, bevor Bereich verloren geht
|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Es wird ein lokales Objekt eines <xref:System.IDisposable>-Typs erstellt. Das Objekt wird jedoch erst verworfen, nachdem sich alle Verweise auf das Objekt außerhalb des gültigen Bereichs befinden.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein verwerfbares Objekt nicht explizit verworfen wird, bevor alle Verweise darauf außerhalb des gültigen Bereichs liegen, wird das Objekt zu einer unbestimmten Zeit verworfen, wenn der Garbage Collector den Finalizer des Objekts ausführt. Da möglicherweise ein Ausnahmeereignis auftritt, durch das die Ausführung des Finalizers des Objekts verhindert wird, muss das Objekt stattdessen explizit verworfen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie <xref:System.IDisposable.Dispose%2A> für das Objekt auf, bevor sich alle Verweise darauf außerhalb des gültigen Bereichs befinden.

 Beachten Sie, dass Sie die `using`-Anweisung (`Using` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) zum Umschließen von Objekten verwenden können, die `IDisposable` implementieren. Auf diese Weise umschlossene Objekte werden zum Abschluss des `using`-Blocks automatisch verworfen.

 Im Folgenden werden einige Situationen beschrieben, in denen die using-Anweisung nicht zum Schutz von IDisposable-Objekten ausreicht und bewirken kann, dass CA2000 ausgelöst wird.

-   Um ein verwerfbares Objekt zurückzugeben, ist es erforderlich, dass das Objekt in einem try/finally-Block außerhalb eines using-Blocks erstellt ist.

-   Die Member eines verwerfbaren Objekts sollten nicht im Konstruktor einer using-Anweisung initialisiert werden.

-   Das Schachteln von Konstruktoren, die nur von einem Ausnahmehandler geschützt sind. Ein auf ein Objekt angewendeter

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     Dadurch wird bewirkt, dass CA2000 ausgelöst wird, da ein Fehler in der Konstruktion des StreamReader-Objekts dazu führen kann, dass das FileStream-Objekt nie geschlossen wird.

-   Dynamische Objekte sollten ein Schattenobjekt verwenden, um das Dispose-Muster von IDisposable-Objekten zu implementieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, Sie haben eine Methode für das Objekt aufgerufen, die `Dispose` aufruft, zum Beispiel <xref:System.IO.Stream.Close%2A>, oder die Methode, durch die die Warnung ausgelöst wurde, gibt ein IDisposable-Objekt zurück, das das Objekt umschließt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Objekte nicht mehrmals verwerfen](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Beispiel
 Wenn Sie eine Methode implementieren, die ein verwerfbares Objekt zurückgibt, verwenden Sie einen try/finally-Block ohne einen catch-Block, um sicherzustellen, dass das Objekt verworfen wird. Mit einem try/finally-Block lassen Sie Ausnahmen zu, die am Fehlerpunkt ausgelöst werden sollen, und stellen sicher, dass das Objekt verworfen wird.

 In der OpenPort1-Methode kann der Aufruf zum Öffnen des SerialPorts des ISerializable-Objekts oder der Aufruf von SomeMethod fehlschlagen. Eine CA2000-Warnung wird für diese Implementierung ausgelöst.

 In der OpenPort2-Methode werden zwei SerialPort-Objekte deklariert und auf NULL festgelegt:

-   `tempPort` zum Testen, ob die Methodenoperationen erfolgreich ausgeführt werden.

-   `port` für den Rückgabewert der Methode.

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
 Standardmäßig überprüft der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Compiler auf Überläufe mit allen arithmetischen Operatoren. Daher kann jede arithmetische Visual Basic-Operation eine <xref:System.OverflowException> auslösen. Dies kann zu unerwarteten Regelverletzungen führen, z. B. CA2000. Die folgende CreateReader1-Funktion erzeugt z. B. eine CA2000-Verletzung, da der Visual Basic-Compiler einen Befehl zur Überlaufprüfung für die Hinzufügung ausgibt, die eine Ausnahme auslösen könnte, durch die der StreamReader nicht verworfen werden würde.

 Um dieses zu korrigieren, können Sie das Ausgeben von Überlaufprüfungen durch den Visual Basic-Compiler im Projekt deaktivieren, oder Sie können den Code entsprechend der folgenden CreateReader2-Funktion ändern.

 Um das Ausgeben von überlaufprüfungen zu deaktivieren, mit der rechten Maustaste im Projektmappen-Explorer des Projektnamen, und klicken Sie dann auf **Eigenschaften**. Klicken Sie auf **Kompilieren**, klicken Sie auf **Erweiterte Kompilierungsoptionen**, und überprüfen Sie dann **Überprüfungen auf Ganzzahlüberlauf entfernen**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable> [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)