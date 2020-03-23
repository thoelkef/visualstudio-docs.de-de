---
title: Verwalten von Ausnahmen mit dem Debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301122"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Verwalten von Ausnahmen mit dem Debugger in Visual Studio

Eine Ausnahme ist ein Hinweis auf einen Fehlerstatus, der auftritt, während ein Programm ausgeführt wird. Sie können dem Debugger mitteilen, welche Ausnahmen oder Gruppen von Ausnahmen unterbrochen werden sollen und an welchem Punkt der Debugger unterbrochen werden soll (d. h. im Debugger anhalten). Wenn der Debugger unterbrochen wird, wird angezeigt, wo die Ausnahme ausgelöst wurde. Sie können auch Ausnahmen hinzufügen oder löschen. Wenn eine Lösung in Visual Studio geöffnet ist, verwenden Sie **Debug > Windows > Ausnahmeeinstellungen,** um das Fenster **Ausnahmeeinstellungen** zu öffnen.

Stellen Sie Handler bereit, die auf die wichtigsten Ausnahmen reagieren. Wenn Sie wissen müssen, wie Sie Handler für Ausnahmen hinzufügen, finden Sie weitere Informationen unter [Beheben von Fehlern durch Schreiben von besserem C-Code](../debugger/write-better-code-with-visual-studio.md). Erfahren Sie außerdem, wie Sie den Debugger so konfigurieren, dass die Ausführung für einige Ausnahmen immer unterbricht wird.

Wenn eine Ausnahme auftritt, schreibt der Debugger eine Ausnahmenachricht in das **Ausgabefenster.** In den folgenden Fällen kann die Ausführung unterbrechen:

- Es wird eine Ausnahme ausgelöst, die nicht behandelt wird.
- Der Debugger ist so konfiguriert, dass die Ausführung aufgehoben wird, bevor ein Handler aufgerufen wird.
- Sie haben [Nur meinen Code](../debugger/just-my-code.md)festgelegt, und der Debugger ist so konfiguriert, dass er für jede Ausnahme aufbricht, die im Benutzercode nicht behandelt wird.

> [!NOTE]
> ASP.NET verfügt über einen Ausnahmehandler der obersten Ebene, der Fehlerseiten in einem Browser anzeigt. Die Ausführung wird nur dann aufgehoben, wenn **Nur mein Code** aktiviert ist. Ein Beispiel finden Sie unter [Sagen Sie dem Debugger, dass er für benutzerunbehandelte Ausnahmen fortfahren soll.](#BKMK_UserUnhandled)

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In Visual Basic-Anwendungen werden alle Fehler vom Debugger als Ausnahmen behandelt. Dies ist auch dann der Fall, wenn Sie Fehlerhandler des Typs On Error verwenden.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Weisen Sie den Debugger an, zu unterbrechen, wenn eine Ausnahme ausgelöst wird.

Der Debugger kann die Ausführung an dem Punkt unterbrechen, an dem eine Ausnahme ausgelöst wird, sodass Sie die Ausnahme untersuchen können, bevor ein Handler aufgerufen wird.

Erweitern Sie im Fenster **Ausnahmeeinstellungen** (**Debug> Windows > Ausnahmeeinstellungen**) den Knoten für eine Kategorie von Ausnahmen, z. B. **Common Language Runtime Exceptions**. Aktivieren Sie dann das Kontrollkästchen für eine bestimmte Ausnahme innerhalb dieser Kategorie, z. B. **System.AccessViolationException**. Sie können auch eine ganze Kategorie von Ausnahmen auswählen.

![AccessViolationException aktiviert](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Sie können bestimmte Ausnahmen finden, indem Sie das **Suchfenster** in der Symbolleiste **Ausnahmeeinstellungen** verwenden, oder die Suche verwenden, um nach bestimmten Namespaces zu filtern (z. B. **System.IO**).

Wenn Sie im Fenster **Ausnahmeeinstellungen** eine Ausnahme auswählen, wird die Debuggerausführung an der Stelle, an der die Ausnahme ausgelöst wird, unabhängig davon, ob sie behandelt wird, gebrochen. Jetzt wird die Ausnahme als Ausnahme der ersten Chance bezeichnet. Im Folgenden einige Szenarios:

- In der folgenden Anwendung der "C-Konsole" löst `try/catch` die Main-Methode eine **AccessViolationException** innerhalb eines Blocks aus.

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

  Wenn **AccessViolationException** in **Ausnahmeeinstellungen**aktiviert ist, wird `throw` die Ausführung in der Zeile unterbrechen, wenn Sie diesen Code im Debugger ausführen. Danach können Sie die Ausführung fortsetzen. In der Konsole sollten beide Zeilen angezeigt werden:

  ```cmd
  caught exception
  goodbye
  ```

  aber es zeigt nicht `here` die Linie.

- Eine C-Konsolenanwendung verweist auf eine Klassenbibliothek mit einer Klasse mit zwei Methoden. Eine Methode löst eine Ausnahme aus und behandelt sie, während eine zweite Methode dieselbe Ausnahme auslöst, sie jedoch nicht behandelt.

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

  Wenn **AccessViolationException** in **Ausnahmeeinstellungen**aktiviert ist, wird `throw` die Ausführung sowohl in **ThrowHandledException() als** auch in **ThrowUnhandledException()** in der Zeile ausgeführt, wenn Sie diesen Code im Debugger ausführen.

Um die Ausnahmeeinstellungen auf die Standardeinstellungen zurückherzustellen, wählen Sie **die Schaltfläche Liste wiederherstellen auf die Schaltfläche "Standardeinstellungen"** aus:

![Wiederherstellen der Standardwerte in den Ausnahmeeinstellungen](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Weisen Sie den Debugger an, bei benutzerunbehandelten Ausnahmen fortzufahren.

Wenn Sie .NET- oder JavaScript-Code mit [Just My Code](../debugger/just-my-code.md)debuggen, können Sie den Debugger anweisen, Ausnahmen zu verhindern, die nicht im Benutzercode behandelt, aber an anderer Stelle behandelt werden.

1. Öffnen Sie im Fenster **Ausnahmeeinstellungen** das Kontextmenü, indem Sie mit der rechten Maustaste auf eine Spaltenbeschriftung klicken, und wählen Sie dann **Spalten > zusätzliche Aktionen anzeigen**aus. (Wenn Sie Nur **meinen Code**deaktiviert haben, wird dieser Befehl nicht angezeigt.) Eine dritte Spalte mit dem Namen **Zusätzliche Aktionen** wird angezeigt.

   ![Zusätzliche Aktionsspalte](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Bei einer Ausnahme, die **"Weiter"** anzeigt, wenn sie im Benutzercode in dieser Spalte nicht behandelt wird, wird der Debugger fortgesetzt, wenn diese Ausnahme nicht im Benutzercode, sondern extern behandelt wird.

2. Um diese Einstellung für eine bestimmte Ausnahme zu ändern, wählen Sie die Ausnahme aus, klicken Sie mit der rechten Maustaste, um das Kontextmenü anzuzeigen, und wählen Sie **Weiter, wenn sie nicht behandelt werden, im Benutzercode**aus. Sie können die Einstellung auch für eine ganze Kategorie von Ausnahmen ändern, z. B. die gesamte Common Language Runtime-Ausnahme).

   ![**Weiter, wenn in der Einstellung Benutzercode** nicht behandelt wird](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Beispielsweise verarbeiten ASP.NET Webanwendungen Ausnahmen, indem sie sie in einen HTTP 500-Statuscode konvertieren ([Ausnahmebehandlung in ASP.NET Web-API](/aspnet/web-api/overview/error-handling/exception-handling)), was Ihnen möglicherweise nicht hilft, die Quelle der Ausnahme zu bestimmen. Im folgenden Beispiel wird durch den Benutzercode `String.Format()` aufgerufen, wodurch eine <xref:System.FormatException>ausgelöst wird. Die Ausführung wird folgendermaßen unterbrochen:

![Unterbrechungen für Benutzer&#45;nicht behandelte Ausnahme](../debugger/media/exceptionunhandledbyuser.png "AusnahmeUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Hinzufügen und Löschen von Ausnahmen

Sie können Ausnahmen hinzufügen und löschen. Um einen Ausnahmetyp aus einer Kategorie zu löschen, wählen Sie die Ausnahme aus, und wählen Sie **die ausgewählte Ausnahme aus der Listenschaltfläche** (das Minuszeichen) auf der Symbolleiste **Ausnahmeeinstellungen** löschen aus. Sie können auch mit der rechten Maustaste auf die Ausnahme klicken und im Kontextmenü **löschen** auswählen. Das Löschen einer Ausnahme hat den gleichen Effekt wie das Deaktivieren der Ausnahme, d. h., der Debugger wird nicht beim Auslösen des Debuggers gebrochen.

So fügen Sie eine Ausnahme hinzu:

1. Wählen Sie im Fenster **Ausnahmeeinstellungen** eine der Ausnahmekategorien aus (z. B. **Common Language Runtime**).

2. Wählen Sie die **Schaltfläche "Ausnahme zu der ausgewählten Kategorie** hinzufügen" (das Pluszeichen).

   ![**Hinzufügen einer Ausnahme zur ausgewählten Kategorie**-Schaltfläche](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddanExceptionToTheSelectedCategoryButton")

3. Geben Sie den Namen der Ausnahme ein (z. **B. System.UriTemplateMatchException**).

   ![Geben Sie den Ausnahmenamen ein.](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Die Ausnahme wird der Liste hinzugefügt (in alphabetischer Reihenfolge) und automatisch überprüft.

Um eine Ausnahme zu den Kategorien GPU Memory Access Exceptions, JavaScript Runtime Exceptions oder Win32 Exceptions hinzuzufügen, fügen Sie den Fehlercode und die Beschreibung ein.

> [!TIP]
> Überprüfen Sie die Rechtschreibung! Das Fenster **Ausnahmeeinstellungen** prüft nicht, ob eine hinzugefügte Ausnahme vorhanden ist. Bei Eingabe von **Sytem.UriTemplateMatchException** erhalten Sie daher einen Eintrag für diese Ausnahme und nicht für **System.UriTemplateMatchException**.

Ausnahmeeinstellungen werden in der SUO-Datei der Projektmappe beibehalten, sie gelten also für eine bestimmte Projektmappe. Sie können spezifische Ausnahmeeinstellungen nicht für andere Projektmappen wiederverwenden. Jetzt werden nur noch hinzugefügte Ausnahmen beibehalten. gelöschte Ausnahmen sind nicht. Sie können eine Ausnahme hinzufügen, die Lösung schließen und erneut öffnen, und die Ausnahme ist weiterhin vorhanden. Wenn Sie eine Ausnahme dagegen löschen und die Projektmappe anschließend schließen und wieder öffnen, wird die Ausnahme nicht mehr angezeigt.

Das Fenster **Ausnahmeeinstellungen** unterstützt generische Ausnahmetypen in C#, aber nicht in Visual Basic. Um bei Ausnahmen wie `MyNamespace.GenericException<T>`eine Unterbrechung vorzunehmen, müssen Sie die Ausnahme als **MyNamespace.GenericException`1**hinzufügen. Das heißt, wenn Sie eine Ausnahme wie diesen Code erstellt haben:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Sie können die Ausnahme mit dem vorherigen Verfahren zu **Denausnahmeeinstellungen** hinzufügen:

![Generische Ausnahme wird hinzugefügt](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Hinzufügen von Bedingungen zu einer Ausnahme

Verwenden Sie das Fenster **Ausnahmeeinstellungen,** um Bedingungen für Ausnahmen festzulegen. Zu den derzeit unterstützten Bedingungen gehören die Modulnamen, die für die Ausnahme eingeschlossen oder ausgeschlossen werden sollen. Indem Sie Modulnamen als Bedingungen festlegen, können Sie festlegen, dass die Ausnahme nur für bestimmte Codemodule aufgebrochen wird. Sie können auch festlegen, dass auf bestimmten Modulen keine Verstöße auftreten.

> [!NOTE]
> Das Hinzufügen von Bedingungen zu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]einer Ausnahme wird ab in unterstützt.

So fügen Sie bedingte Ausnahmen hinzu:

1. Wählen Sie im Fenster Ausnahmeeinstellungen die Schaltfläche **Bedingungen bearbeiten** aus, oder klicken Sie mit der rechten Maustaste auf die Ausnahme, und wählen Sie **Bedingungen bearbeiten**aus.

   ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Um der Ausnahme zusätzliche erforderliche Bedingungen hinzuzufügen, wählen Sie Bedingung für jede neue Bedingung **hinzufügen** aus. Zusätzliche Konditionszeilen werden angezeigt.

   ![Zusätzliche Bedingungen für eine Ausnahme](../debugger/media/extraconditionsforanexception.png "ExtraconditionsForAnException")

3. Geben Sie für jede **Bedingungszeile** den Namen des Moduls ein, und ändern Sie die Vergleichsoperatorliste in Equals oder **Not Equals**. Sie können Platzhalter**\\**( ) im Namen angeben, um mehr als ein Modul anzugeben.

4. Wenn Sie eine Bedingung löschen müssen, wählen Sie das **X** am Ende der Konditionszeile aus.

## <a name="see-also"></a>Weitere Informationen

- [Fortfahren mit der Ausführung nach einer Ausnahme](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Gewusst wie: Überprüfen des Systemcodes nach einer Ausnahme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Use run-time checks without the C run-time library (Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek)](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md)
