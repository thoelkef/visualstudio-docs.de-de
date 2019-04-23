---
title: Verwalten von Ausnahmen mit dem Debugger | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a8bc2e1f4c78e32db6fa5e09ec50bdd182f4fa6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040963"
---
# <a name="managing-exceptions-with-the-debugger"></a>Verwalten von Ausnahmen mit dem Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Ausnahme ist ein Hinweis auf einen Fehlerstatus, der auftritt, während ein Programm ausgeführt wird. Sie können und sollten Handler zur Verfügung stellen, die auf die wichtigsten Ausnahmen reagieren. Wichtig ist aber auch, den Debugger so einzurichten, dass Unterbrechungen für die Ausnahmen veranlasst werden, die Sie sehen möchten.  
  
 Wenn eine Ausnahme ausgelöst wird, schreibt der Debugger eine Ausnahmemeldung an das Fenster „Ausgabe“. In den folgenden Fällen kann er die Ausführung unterbrechen:  
  
- Wenn eine Ausnahme ausgelöst und nicht behandelt wird.  
  
- Wenn der Debugger so eingestellt ist, dass die Ausführung sofort beim Auftreten einer Ausnahme unterbrochen wird, bevor ein Handler aufgerufen wird.  
  
- Wenn Sie [Just My Code](../debugger/just-my-code.md)festgelegt haben und der Debugger so eingestellt ist, dass eine Unterbrechung bei jeder Ausnahme veranlasst wird, die nicht im Benutzercode behandelt wird.  
  
> [!NOTE]
>  ASP.NET verfügt über einen Ausnahmehandler der obersten Ebene, der Fehlerseiten in einem Browser anzeigt. Die Ausführung wird nicht unterbrochen, es sei denn, **Nur eigenen Code** ist aktiviert. Ein Beispiel finden Sie weiter unten unter [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) .  
  
> [!NOTE]
>  In Visual Basic-Anwendungen werden alle Fehler vom Debugger als Ausnahmen behandelt. Dies ist auch dann der Fall, wenn Sie Fehlerhandler des Typs On Error verwenden.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Verwalten von Ausnahmen mit dem Fenster „Ausnahmeeinstellungen“  
 Sie können das Fenster **Ausnahmeeinstellungen** verwenden, um anzugeben, welche Ausnahmen oder Sätze von Ausnahmen eine Unterbrechung des Debuggers auslösen sollen, und um anzugeben, an welchem Punkt die Unterbrechung vorgenommen werden soll. Sie können Ausnahmen hinzufügen oder löschen oder Ausnahmen für die Unterbrechung angeben. Öffnen Sie dieses Fenster, wenn eine Projektmappe geöffnet ist, indem Sie auf **Debuggen / Fenster / Ausnahmeeinstellungen**klicken.  
  
 Nach spezifischen Ausnahmen können Sie mithilfe des Fensters **Suche** in der Symbolleiste **Ausnahmeeinstellungen** suchen. Sie können die Suchergebnisse auch nach bestimmten Namespaces filtern (z. B. **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Festlegen, dass der Debugger die Ausführung bei ausgelöster Ausnahme unterbricht  
 Der Debugger kann die Ausführung beim Auftreten einer Ausnahme sofort unterbrechen. Dadurch haben Sie die Möglichkeit, die Ausnahme zu untersuchen, bevor ein Handler aufgerufen wird.  
  
 Erweitern Sie im Fenster **Ausnahmeeinstellungen** den Knoten für eine Kategorie von Ausnahmen (z. B. **Common Language Runtime-Ausnahmen**, d. h. .NET-Ausnahmen), und aktivieren Sie das Kontrollkästchen für eine bestimmte Ausnahme innerhalb dieser Kategorie (z. B. **System.AccessViolationException**). Sie können auch eine ganze Kategorie von Ausnahmen auswählen.  
  
 ![AccessViolationException aktiviert](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Wenn Sie eine bestimmte Ausnahme überprüfen, wird die Ausführung sofort bei ausgelöster Ausnahme unterbrochen, unabhängig davon, ob diese behandelt wird oder nicht. An dieser Stelle wird die Ausnahme als „erste Chance“ bezeichnet. Im Folgenden einige Szenarios:  
  
1. In der folgenden C#-Konsolenanwendung löst die Main-Methode eine **AccessViolationException** in einem `try/catch` -Blocks aus:  
  
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
  
    Wenn Sie **AccessViolationException** in den **Ausnahmeeinstellungen**aktiviert haben, wird die Ausführung an der `throw` -Zeile unterbrochen, wenn Sie diesen Code im Debugger ausführen. Danach können Sie die Ausführung fortsetzen. In der Konsole sollten beide Zeilen angezeigt werden:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    Die `here` -Zeile wird jedoch nicht angezeigt.  
  
2. Eine C#-Konsolenanwendung verweist auf eine Klassenbibliothek mit einer Klasse mit zwei Methoden: einer Methode, die eine Ausnahme auslöst und diese verarbeitet, und einer zweiten Methode, die die gleiche Ausnahme auslöst, sie aber nicht behandelt:  
  
   ```vb  
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
  
    Wenn Sie **AccessViolationException** in den **Ausnahmeeinstellungen**aktiviert haben, wird die Ausführung an der `throw` -Zeile sowohl in **ThrowHandledException()** als auch in **ThrowUnhandledException()** klicken.  
  
   Wenn Sie die Ausnahmeeinstellungen auf die Standardwerte zurücksetzen möchten, klicken Sie in der Symbolleiste auf die Schaltfläche **Wiederherstellen** :  
  
   ![Wiederherstellen der Standardwerte in den Ausnahmeeinstellungen](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a> Einstellen des Debuggers zum Fortfahren bei Ausnahmen vom Benutzercode unbehandelt  
 Wenn Sie .NET- oder JavaScript-Code mit [Just My Code](../debugger/just-my-code.md)debuggen, können Sie den Debugger so einstellen, dass er bei Ausnahmen, die an anderer Stelle als im Benutzercode behandelt werden, die Ausführung nicht unterbricht.  
  
1. Öffnen Sie im Fenster **Ausnahmeeinstellungen** das Kontextmenü, indem Sie mit der rechten Maustaste auf „Fenster“ klicken und dann **Spalten anzeigen**auswählen. (Wenn Sie **Nur eigenen Code**deaktiviert haben, wird dieser Befehl nicht angezeigt.)  
  
2. Daraufhin sollte eine zweite Spalte mit dem Namen **Zusätzliche Aktionen**angezeigt werden. Diese Spalte zeigt für bestimmte Ausnahmen die Einstellung **Fortsetzen, wenn nicht vom Benutzercode behandelt** , was bedeutet, dass der Debugger die Ausführung nicht unterbricht, wenn diese Ausnahme nicht vom Benutzercode, sondern von externem Code behandelt wird.  
  
3. Sie können diese Einstellung für eine bestimmte Ausnahme ändern: Wählen Sie die Ausnahme aus, klicken Sie mit der rechten Maustaste und aktivieren/deaktivieren Sie **Fortsetzen, wenn nicht vom Benutzercode behandelt**. Sie können die Einstellung auch für eine ganze Kategorie von Ausnahmen ändern, z. B. für alle Common Language Runtime-Ausnahmen.  
  
   Beispielsweise behandeln ASP.NET-Webanwendungen Ausnahmen dadurch, dass sie diese in einen HTTP 500-Statuscode konvertieren ([Exception Handling in ASP.NET API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), wodurch es möglicherweise unmöglich wird, die Quelle der Ausnahme zu bestimmen. Im folgenden Beispiel wird durch den Benutzercode `String.Format()` aufgerufen, wodurch eine <xref:System.FormatException>ausgelöst wird. Die Ausführung wird folgendermaßen unterbrochen:  
  
   ![Benutzer Seitenumbrüche&#45;Unhanlded Ausnahme](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Hinzufügen und Löschen von Ausnahmen  
 Sie können Ausnahmen hinzufügen und löschen. Sie können jeden Typ von Ausnahme aus einer beliebigen Kategorie löschen, indem Sie die Ausnahme auswählen und in der Symbolleiste **Ausnahmeeinstellungen** auf die Schaltfläche **Löschen** (das Minuszeichen) klicken, oder indem Sie die mit der rechten Maustaste auf die Ausnahme klicken und im Kontextmenü **Löschen** auswählen. Das Löschen einer Ausnahme hat dieselbe Wirkung wie das Deaktivieren, d. h., der Debugger wird nicht unterbrochen, wenn die Ausnahme ausgelöst wird.  
  
 Zum Hinzufügen einer Ausnahme: Wählen Sie im Fenster **Ausnahmeeinstellungen** eine der Ausnahmekategorien (z. B. **Common Language Runtime**), und klicken Sie auf die Schaltfläche **Hinzufügen** . Geben Sie den Namen der Ausnahme ein (z. B. **System.UriTemplateMatchException**). Die Ausnahme wird zur Liste hinzugefügt (in alphabetischer Reihenfolge) und wird automatisch geprüft.  
  
 Wenn Sie eine Ausnahme zu den Ausnahmen für den GPU-Speicherzugriff, den JavaScript-Laufzeitausnahmen oder den Win32-Ausnahmekategorien hinzufügen möchten, müssen Sie den Fehlercode und die Beschreibung einfügen.  
  
> [!TIP]
>  Überprüfen Sie die Rechtschreibung! Das Fenster **Ausnahmeeinstellungen** prüft nicht, ob eine hinzugefügte Ausnahme vorhanden ist. Bei Eingabe von **Sytem.UriTemplateMatchException**erhalten Sie daher einen Eintrag für diese Ausnahme und nicht für **System.UriTemplateMatchException**.  
  
 Ausnahmeeinstellungen werden in der SUO-Datei der Projektmappe beibehalten, sie gelten also für eine bestimmte Projektmappe. Sie können spezifische Ausnahmeeinstellungen nicht für andere Projektmappen wiederverwenden. Zu diesem Zeitpunkt werden nur hinzugefügte Ausnahmen beibehalten, gelöschte Ausnahmen nicht. Anders ausgedrückt ist die hinzugefügte Ausnahme weiterhin vorhanden, wenn Sie die Projektmappe schließen und wieder öffnen. Wenn Sie eine Ausnahme dagegen löschen und die Projektmappe anschließend schließen und wieder öffnen, wird die Ausnahme nicht mehr angezeigt.  
  
 Das Fenster **Ausnahmeeinstellungen** unterstützt generische Ausnahmetypen in C#, aber nicht in Visual Basic. Um bei Ausnahmen wie `MyNamespace.GenericException<T>`eine Unterbrechung vorzunehmen, müssen Sie die Ausnahme als **MyNamespace.GenericException`1**hinzufügen. Wenn Sie eine Ausnahme wie die Folgende erstellt haben:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 können Sie die Ausnahme folgendermaßen zu den **Ausnahmeeinstellungen** hinzufügen:  
  
 ![generische Ausnahme hinzufügen](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Siehe auch  
 [Fortfahren mit der Ausführung nach einer Ausnahme](../debugger/continuing-execution-after-an-exception.md)   
 [Vorgehensweise: Untersuchen von Systemcode nach einer Ausnahme](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Vorgehensweise: Verwenden von nativen Laufzeitüberprüfungen](../debugger/how-to-use-native-run-time-checks.md)   
 [Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Ausnahmen-Assistent](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)
