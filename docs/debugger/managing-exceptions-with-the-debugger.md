---
title: Verwalten von Ausnahmen mit dem Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 10/09/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97c4694ec66c9769f9433c08e74e4d0a14a952c2
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561524"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Verwalten von Ausnahmen mit der Debugger in Visual Studio

Eine Ausnahme ist ein Hinweis auf einen Fehlerstatus, der auftritt, während ein Programm ausgeführt wird. Sie können dem Debugger anweisen, welche Ausnahmen oder Sätze von Ausnahmen auf unterbrochen, und an diesem Punkt des Debuggers zum unterbrechen soll. Wenn der Debugger unterbrochen wird, wird es Sie, wo die Ausnahme ausgelöst wurde. Sie können auch hinzufügen oder Löschen von Ausnahmen. Mit einer Lösung in Visual Studio geöffnet ist, verwenden Sie **Debuggen > Windows > Ausnahmeeinstellungen** zum Öffnen der **Ausnahmeeinstellungen** Fenster.

Geben Sie Handler, die auf die wichtigsten Ausnahmen reagieren. Außerdem erfahren Sie, wie konfigurieren Sie den Debugger, um die Ausführung für einige Ausnahmen immer dann unterbrochen.

Wenn eine Ausnahme ausgelöst wird, schreibt der Debugger eine Ausnahmemeldung an das Fenster **Ausgabe**. Es kann die Ausführung unterbrechen, in den folgenden Fällen:

- Eine Ausnahme wird ausgelöst, die verarbeitet wird.
- Der Debugger ist konfiguriert, um die Ausführung zu unterbrechen, bevor ein Handler aufgerufen wird.
- Sie haben festgelegt [nur mein Code](../debugger/just-my-code.md), und der Debugger bei jeder Ausnahme unterbrochen wird, die im Benutzercode behandelt ist nicht konfiguriert ist.

> [!NOTE]
> ASP.NET verfügt über einen Ausnahmehandler der obersten Ebene, der Fehlerseiten in einem Browser anzeigt. Es nicht die Ausführung unterbrochen, es sei denn, **nur mein Code** aktiviert ist. Ein Beispiel finden Sie unter [entsprechende Konfiguration des Debuggers zum Fortfahren bei Ausnahmen vom Benutzercode unbehandelt](#BKMK_UserUnhandled) unten.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In Visual Basic-Anwendungen werden alle Fehler vom Debugger als Ausnahmen behandelt. Dies ist auch dann der Fall, wenn Sie Fehlerhandler des Typs On Error verwenden.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Teilen Sie den Debugger zu unterbrechen, wenn eine Ausnahme ausgelöst wird

Der Debugger kann die Ausführung an dem Punkt, in dem eine Ausnahme ausgelöst wird, unterbrechen, sodass Sie möglicherweise die Ausnahme zu untersuchen, bevor ein Handler aufgerufen wird.

In der **Ausnahmeeinstellungen** Fenster (**Debuggen > Windows > Ausnahmeeinstellungen**), erweitern Sie den Knoten für eine Kategorie von Ausnahmen, z. B. **Common Language Runtime-Ausnahmen**. Wählen Sie dann das Kontrollkästchen für eine bestimmte Ausnahme innerhalb dieser Kategorie, z. B. **System.AccessViolationException**. Sie können auch eine ganze Kategorie von Ausnahmen auswählen.

![AccessViolationException aktiviert](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Bestimmte Ausnahmen finden Sie unter Verwendung der **Suche** Fenster in der **Ausnahmeeinstellungen** Symbolleiste, oder verwenden Sie suchen, um nach bestimmten Namespaces Filtern (z. B. **System.IO**).

Wenn Sie auswählen, dass eine Ausnahme in der **Ausnahmeeinstellungen** Fenster Debugger die Ausführung wird unterbrochen, wo die Ausnahme ausgelöst wird, unabhängig davon, ob es behandelt wird,. Die Ausnahme wird jetzt eine erste zufällige Ausnahme aufgerufen. Im Folgenden einige Szenarios:

- In der folgenden C#-Konsolenanwendung löst die Main-Methode eine **AccessViolationException** in einem `try/catch`-Block aus.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Wenn man **AccessViolationException** eingecheckt **Ausnahmeeinstellungen**, Ausführung wird die Ausführung an die `throw` Zeile, wenn Sie diesen Code im Debugger ausführen. Danach können Sie die Ausführung fortsetzen. In der Konsole sollten beide Zeilen angezeigt werden:

  ```cmd
  caught exception
  goodbye
  ```

  Es zeigt jedoch nicht die `here` Zeile.

- Ein C# -Konsolenanwendung verweist auf eine Klassenbibliothek mit einer Klasse, die über zwei Methoden verfügt. Die Methode löst eine Ausnahme aus, und verarbeitet, während eine zweite Methode, die gleiche Ausnahme auslöst, jedoch nicht behandelt.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Dies ist die Hauptmethode der Konsolenanwendung:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Wenn man **AccessViolationException** eingecheckt **Ausnahmeeinstellungen**, Ausführung wird die Ausführung an die `throw` Zeile in beiden **ThrowHandledException()** und **ThrowUnhandledException()** Wenn Sie diesen Code im Debugger ausführen.

Um die ausnahmeeinstellungen auf die Standardwerte zurücksetzen möchten, wählen Sie die **Liste auf die Standardeinstellungen wiederherstellen** Schaltfläche:

![Wiederherstellen der Standardwerte in den Ausnahmeeinstellungen](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Entsprechende Konfiguration des Debuggers zum Fortfahren bei Ausnahmen vom Benutzercode unbehandelt

Wenn Sie .NET oder JavaScript-Code mit Debuggen [nur mein Code](../debugger/just-my-code.md), können Sie feststellen, den Debugger, Abbruch bei Ausnahmen zu verhindern, die sind nicht im Benutzercode behandelt, aber an anderer Stelle behandelt werden.

1. In der **Ausnahmeeinstellungen** Fenster öffnen Sie das Kontextmenü, indem Sie mit der rechten Maustaste einer spaltenbezeichnung, und wählen Sie dann **Spalten einblenden > zusätzliche Aktionen**. (Wenn Sie deaktiviert haben **nur mein Code**, mit diesem Befehl wird nicht angezeigt.) Eine dritte Spalte mit dem Namen **zusätzliche Aktionen** angezeigt wird.

   ![Zusätzliche Aktionsspalte](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Für eine Ausnahme, die zeigt, **fortgesetzt, wenn in Benutzercode nicht behandelt** in dieser Spalte, fährt der Debugger, wenn diese Ausnahme wird nicht im Benutzercode behandelt, sondern extern behandelt wird.

2. Um diese Einstellung für eine bestimmte Ausnahme ändern möchten, wählen Sie die Ausnahme, mit der rechten Maustaste das Kontextmenü anzuzeigen, und wählen **fortfahren bei nicht behandelten im Benutzercode**. Sie können auch die Einstellung für eine ganze Kategorie von Ausnahmen, z. B. die gesamte Common Language Runtime-Ausnahmen ändern).

   ![** Fortgesetzt, wenn im Code ** benutzereinstellung nicht behandelte](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Beispielsweise behandeln ASP.NET-Webanwendungen Ausnahmen durch Konvertierung in einen HTTP 500-Statuscode ([Behandlung von Ausnahmen in ASP.NET Web-API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), die möglicherweise keinen Hinweise auf die Quelle der Ausnahme zu bestimmen. Im folgenden Beispiel wird durch den Benutzercode `String.Format()` aufgerufen, wodurch eine <xref:System.FormatException>ausgelöst wird. Die Ausführung wird folgendermaßen unterbrochen:

![Benutzer Seitenumbrüche&#45;nicht behandelte Ausnahme](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Hinzufügen und Löschen von Ausnahmen

Sie können Ausnahmen hinzufügen und löschen. Um einen Ausnahmetyp aus einer Kategorie zu löschen, wählen Sie die Ausnahme, und wählen Sie die **löscht die ausgewählte Ausnahme aus der Liste** Schaltfläche (das Minuszeichen) auf die **Ausnahmeeinstellungen** Symbolleiste. Oder Sie können mit der rechten Maustaste in der Ausnahme, und wählen Sie **löschen** aus dem Kontextmenü. Das Löschen einer Ausnahme hat dieselbe Wirkung wie die Ausnahme, die deaktiviert ist, handelt es sich, dass der Debugger wird nicht unterbrochen, wenn er geworfen wird.

Zum Hinzufügen einer Ausnahme:

1. In der **Ausnahmeeinstellungen** Fenster, wählen Sie eine der Ausnahmekategorien (z. B. **Common Language Runtime**).

2. Wählen Sie die **eine Ausnahme hinzufügen, um die ausgewählte Kategorie** Schaltfläche (Pluszeichen).

   ![** Eine Ausnahme hinzufügen, auf die Schaltfläche ausgewählten Kategorie **](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Geben Sie den Namen der Ausnahme (z. B. **System.UriTemplateMatchException**).

   ![Geben Sie den Ausnahmenamen](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Die Ausnahme ist die Liste (in alphabetischer Reihenfolge) hinzugefügt und automatisch aktiviert.

Um eine Ausnahme, die GPU Arbeitsspeicher Ausnahmen JavaScript-Laufzeitausnahmen oder Win32-Ausnahmekategorien hinzufügen möchten, enthalten Sie den Fehlercode und die Beschreibung.

> [!TIP]
> Überprüfen Sie die Rechtschreibung! Das Fenster **Ausnahmeeinstellungen** prüft nicht, ob eine hinzugefügte Ausnahme vorhanden ist. Bei Eingabe von **Sytem.UriTemplateMatchException** erhalten Sie daher einen Eintrag für diese Ausnahme und nicht für **System.UriTemplateMatchException**.

Ausnahmeeinstellungen werden in der SUO-Datei der Projektmappe beibehalten, sie gelten also für eine bestimmte Projektmappe. Sie können spezifische Ausnahmeeinstellungen nicht für andere Projektmappen wiederverwenden. Jetzt werden nur hinzugefügte Ausnahmen beibehalten; Gelöschte Ausnahmen nicht. Sie fügen eine Ausnahme aus, schließen und öffnen Sie die Projektmappe können, und die Ausnahme wird immer noch vorhanden sein. Wenn Sie eine Ausnahme dagegen löschen und die Projektmappe anschließend schließen und wieder öffnen, wird die Ausnahme nicht mehr angezeigt.

Das Fenster **Ausnahmeeinstellungen** unterstützt generische Ausnahmetypen in C#, aber nicht in Visual Basic. Um bei Ausnahmen wie `MyNamespace.GenericException<T>`eine Unterbrechung vorzunehmen, müssen Sie die Ausnahme als **MyNamespace.GenericException`1**hinzufügen. D.h., wenn Sie eine Ausnahme wie im folgenden Code erstellt haben:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Sie können die Ausnahme hinzufügen **Ausnahmeeinstellungen** mithilfe der vorherigen Prozedur:

![generische Ausnahme hinzufügen](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Hinzufügen von Bedingungen zu einer Ausnahme

Verwenden der **Ausnahmeeinstellungen** Fenster Bedingungen auf Ausnahmen festzulegen. Derzeit unterstützte Bedingungen umfassen die Namen der Module zum ein- oder ausschließen, für die Ausnahme. Wenn Sie Modulnamen als Bedingungen festlegen, können Sie auswählen, für die Ausnahme nur für bestimmte Codemodule unterbrochen. Sie können auch auswählen, um wichtige auf bestimmte Module zu vermeiden.

> [!NOTE]
> Hinzufügen von Bedingungen zu einer Ausnahme ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

So fügen Sie bedingte Ausnahmen hinzu:

1. Wählen Sie die **Bedingungen bearbeiten** Schaltfläche im Fenster "Ausnahmeeinstellungen", oder mit der rechten Maustaste in der Ausnahme aus, und wählen Sie **Bedingungen bearbeiten**.

   ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Wählen Sie zum Hinzufügen zusätzlicher erforderlichen Bedingungen auf die Ausnahme **Bedingung hinzufügen** für jede neue Bedingung. Zusätzliche Bedingung Linien angezeigt werden.

   ![Zusätzliche Bedingungen für eine Ausnahme](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Geben Sie für jede Zeile Bedingung den Namen des Moduls, und ändern Sie die Liste der Vergleich-Operator, **gleich** oder **Not Equals**. Sie können Platzhalter angeben (**\\***) im Namen mehr als einem Modul angeben.

4. Wenn Sie eine Bedingung zu löschen möchten, wählen Sie die **X** am Ende der Zeile für die Bedingung.

## <a name="see-also"></a>Siehe auch

[Fortfahren mit der Ausführung nach einer Ausnahme](../debugger/continuing-execution-after-an-exception.md)<br/>
[Vorgehensweise: Untersuchen von Systemcode nach einer Ausnahme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Vorgehensweise: Use native run-time checks (Vorgehensweise: Verwenden von nativen Laufzeitüberprüfungen)](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Use run-time checks without the C run-time library (Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek)](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
