---
title: "Problembehandlung bei Ausnahmen: System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException-Klasse"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.InvalidOperationException
Ein <xref:System.InvalidOperationException?displayProperty=fullName> wird ausgelöst, wenn eine Methode eines Objekts aufgerufen wird, wenn der Zustand des Objekts den Methodenaufruf nicht unterstützen kann. Die Ausnahme wird auch ausgelöst, wenn eine Methode versucht, die Benutzeroberfläche von einem Thread, der sich nicht im Hauptfenster oder UI\-Thread befindet, zu bearbeiten.  
  
> [!IMPORTANT]
>  Da <xref:System.InvalidOperationException>s in einer Vielzahl von Bedingungen ausgelöst werden kann, ist es wichtig, die <xref:System.Exception.Message%2A> gelesen und verstanden haben, die im Ausnahmen\-Assistent angezeigt werden.  
  
##  <a name="BKMK_In_this_article"></a> In diesem Artikel  
 [Eine auf einem UI-Thread-externen ausgeführte Methode aktualisiert die Benutzeroberfläche](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [Eine Anweisung in einer Foreach (For Each in Visual Basic)-Block ändert die Sammlung, die sie durchläuft](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [Ein Typ Nullable &lt; T &gt;, der null ist, wird in T umgewandelt.](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [Eine System.Linq.Enumerable-Methode wird für eine leere Auflistung aufgerufen.](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [Verwandte Artikel](#BKMK_Related_articles)  
  
 Die Codebeispiele in diesem Artikel zeigen Ihnen, wie einige häufige <xref:System.InvalidOperationException> Ausnahmen in Ihrer Anwendung auftreten können. Wie Sie Probleme behandeln, hängt von der besonderen Situation ab. Wenn die Ausnahme die Funktionalität Ihrer Anwendung schwerwiegend beeinträchtigt, möchten Sie möglicherweise ein [try … catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \([Try .. Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) in Visual Basic\)\-Konstrukt verwenden, um die Ausnahme zu erfassen und den Status der Anwendung vor dem Beenden zu bereinigen. Aber andere <xref:System.InvalidOperationException> können erwartet und vermieden werden. Die überarbeitete Methodenbeispiele zeigen Sie einigen dieser Techniken angezeigt.  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> Eine auf einem UI\-Thread\-externen ausgeführte Methode aktualisiert die Benutzeroberfläche  
 [Verursacht eine InvalidOperationException mit einem UI-Update von einem nicht-UI-Thread](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [Vermeiden von InvalidOperationExceptions in nicht-UI-Threads](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 Die meisten .NET GUI \(grafische Benutzeroberfläche\) Anwendungs\-Frameworks, wie z. B. Windows Forms und Windows Presentation Foundation \(WPF\) ermöglichen Ihnen den Zugriff auf GUI\-Objekte nur aus dem Thread, der die Benutzeroberfläche \(den**Main\-** oder **UI**\-Thread\). Ein <xref:System.InvalidOperationException> wird ausgelöst, wenn Sie versuchen, auf ein Element der Benutzeroberfläche von einem anderen Thread zuzugreifen, der nicht der UI\-Thread ist.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> Verursacht eine InvalidOperationException mit einem UI\-Update von einem nicht\-UI\-Thread  
  
> [!NOTE]
>  Die folgenden Beispiele verwenden die [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md), um Threads zu erstellen, die nicht zur Benutzeroberfläche gehören. Die Beispiele sind jedoch für alle [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md) von .NET relevant.  
  
 In diesen Beispielen ruft der `ThreadsExampleBtn_Click` Ereignishandler die `DoSomeWork`\-Methode zweimal auf. Der erste Aufruf der Methode \(`DoSomeWork(20);` wird synchron ausgeführt und erfolgreich abgeschlossen. Der zweite Aufruf \(`Task.Run( () => { DoSomeWork(1000);});`\) wird jedoch in einem Thread im [Threadpool](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx) der App ausgeführt. Da dieser Aufruf versucht, die Benutzeroberfläche von einem nicht\-UI\-Thread zu aktualisieren, wird durch die Anweisung ein<xref:System.InvalidOperationException> ausgelöst  
  
 **WPF und Store\-Anwendungen**  
  
> [!NOTE]
>  In Store Phone\-Anwendungen wird ein <xref:System.Exception> anstatt der spezifischeren <xref:System.InvalidOperationException> ausgelöst.  
  
 **Ausnahmemeldungen:**  
  
|||  
|-|-|  
|WPF\-Anwendungen|Zusätzliche Informationen: Der aufrufende Thread kann nicht auf dieses Objekt zugreifen, da ein anderer Thread es besitzt.|  
|Store\-Apps|Weitere Informationen: Die Anwendung rief eine Schnittstelle auf, die für einen anderen Thread der Anwendung aufgerufen wurde. \(Ausnahme von HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Windows Forms\-Anwendungen**  
  
 **Ausnahmemeldung:**  
  
-   Weitere Informationen: threadübergreifender Vorgang ungültig: Steuerelement "TextBox1" von einem anderen Thread als dem erstellten Thread aufgerufen.  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine auf einem UI-Thread-externen ausgeführte Methode aktualisiert die Benutzeroberfläche](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> Vermeiden von InvalidOperationExceptions in nicht\-UI\-Threads  
 Windows\-Benutzeroberflächen\-Frameworks implementieren ein *Dispatcher*\-Muster, das eine Methode umfasst, mit der überprüft werden kann, ob ein Aufruf an ein Mitglied eines Benutzeroberflächenelements auf dem UI\-Thread ausgeführt wird, und andere Methoden, um den Anruf an den UI\-Thread zu planen.  
  
 **WPF\-Anwendungen**  
  
 In WPF\-Anwendungen verwenden Sie eine der <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName>\-Methoden, um einen Delegaten auf dem UI\-Thread auszuführen. Verwenden Sie bei Bedarf die <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName>\-Methode, um festzulegen, ob eine Methode in einem nicht\-UI\-Thread ausgeführt wird oder nicht.  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Windows Forms\-Anwendungen**  
  
 In Windows Forms\-Anwendungen verwenden die <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>\-Methode, um einen Delegaten auszuführen, der den UI\-Thread aktualisiert. Verwenden Sie bei Bedarf die <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>\-Methode, um festzulegen, ob eine Methode in einem nicht\-UI\-Thread ausgeführt wird oder nicht.  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **Store\-Apps**  
  
 In Windows Forms\-Anwendungen verwenden Sie die <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName>\-Methode, um einen Delegaten auszuführen, der den UI\-Thread aktualisiert. Verwenden Sie bei Bedarf die <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A>\-Methode, um festzulegen, ob eine Methode in einem nicht\-UI\-Thread ausgeführt wird oder nicht.  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine auf einem UI-Thread-externen ausgeführte Methode aktualisiert die Benutzeroberfläche](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> Eine Anweisung in einer Foreach \(For Each in Visual Basic\)\-Block ändert die Sammlung, die sie durchläuft  
 [Verursacht eine InvalidOperationException mit foreach](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [Vermeidet InvalidOperationExceptions in Schleifen](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 Eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)\-Anweisung \([For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) in Visual Basic\) wiederholt eine Gruppe von eingebetteten Anweisungen für jedes Element in einem Array oder einer Auflistung, die die <xref:System.Collections.IEnumerable?displayProperty=fullName> oder <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>\-Schnittstelle implementiert. Die `foreach`\-Anweisung wird zum Durchlaufen der Auflistung zum Lesen und Ändern der Elemente, aber nicht zum Hinzufügen oder Entfernen von Elementen aus der Auflistung verwendet. Ein <xref:System.InvalidOperationException> wird ausgelöst, wenn Sie Elemente aus der Auflistung in einer Foreach\-Anweisung hinzufügen oder daraus entfernen.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> Verursacht eine InvalidOperationException mit foreach  
 In diesem Beispiel wird eine <xref:System.InvalidOperationException> ausgelöst, wenn die `numList.Add(5);`\-Anweisung versucht, die Liste im Foreach\-Block zu ändern.  
  
 **Ausnahmemeldung:**  
  
-   Zusätzliche Informationen: Die Auflistung wurde geändert; der Enumerationsvorgang kann nicht ausgeführt werden.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine Anweisung in einer Foreach (For Each in Visual Basic)-Block ändert die Sammlung, die sie durchläuft](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> Vermeidet InvalidOperationExceptions in Schleifen  
  
> [!IMPORTANT]
>  Das Hinzufügen oder Entfernen von Elementen zu einer Liste während Sie die Sammlung durchlaufen können unbeabsichtigte und schwer vorhersagbare Nebenwirkungen haben. Wenn möglich, sollten Sie den Vorgang außerhalb der Iteration verschieben.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Falls Ihre Situation erfordet, dass Sie Elemente zu einer Liste hinzufügen oder daraus entfernen, während Sie eine Liste durchlaufen, verwenden Sie eine Schleife [für](/dotnet/csharp/language-reference/keywords/for) \([für](/dotnet/visual-basic/language-reference/statements/for-next-statement) in Visual Basic\):  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine Anweisung in einer Foreach (For Each in Visual Basic)-Block ändert die Sammlung, die sie durchläuft](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> Ein Typ Nullable \< T \>, der null ist, wird in T umgewandelt.  
 [Verursachen einer InvalidOperationException mit einer ungültigen Umwandlung](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [Vermeiden von InvalidOperationException aus eine ungültigen Umwandlung](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 Wenn Sie eine Struktur<xref:System.Nullable%601> auslösen, die in dem zugrunde liegenden Typ `null` \(`Nothing` in Visual Basic\) ist, wird eine <xref:System.InvalidOperationException>\-Ausnahme ausgelöst.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> Verursachen einer InvalidOperationException mit einer ungültigen Umwandlung  
 Bei dieser Methode wird eine <xref:System.InvalidOperationException> ausgelöst, wenn die Select\-Methode ein null\-Element des DbQueryResults in int umgewandelt  
  
 **Ausnahmemeldung:**  
  
-   Weitere Informationen: Auf null festlegbares Objekt muss einen Wert haben.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Ein Typ Nullable &lt; T &gt;, der null ist, wird in T umgewandelt.](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> Vermeiden von InvalidOperationException aus eine ungültigen Umwandlung  
 Um <xref:System.InvalidOperationException> zu vermeiden:  
  
-   Verwenden Sie die <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName>\-Eigenschaft, um nur die Elemente auszuwählen, die nicht null sind.  
  
-   Verwenden Sie eine der überladenen <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> Methoden, um einen Standardwert für ein null\-Element anzugeben.  
  
 **Nullable \< T \>.HasValue Beispiel**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Nullable \< T \>.GetValueOrDefault Beispiel**  
  
 In diesem Beispiel verwenden wir <xref:System.Nullable%601.GetValueOrDefault%28%600%29> zur Angabe eines Standardwertes, der außerhalb der von `dbQueryResults` zurückgegebenen erwarteten Werten liegt.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Ein Typ Nullable &lt; T &gt;, der null ist, wird in T umgewandelt.](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> Eine System.Linq.Enumerable\-Methode wird für eine leere Auflistung aufgerufen.  
 Die <xref:System.Linq.Enumerable> Methoden<xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Single%2A> und <xref:System.Linq.Enumerable.SingleOrDefault%2A> führen Operationen für eine Sequenz durch und geben ein Einzelergebnis zurück.  
  
 Einige Überladungen dieser Methoden lösen eine <xref:System.InvalidOperationException> Ausnahme aus, wenn die Sequenz leer ist \(andere Überladungen geben`null` \(`Nothing` in Visual Basic\) zurück.<xref:System.Linq.Enumerable.SingleOrDefault%2A>löst außerdem <xref:System.InvalidOperationException> aus, wenn die Sequenz mehr als ein Element enthält.  
  
> [!TIP]
>  Die meisten der <xref:System.Linq.Enumerable> in diesem Abschnitt diskutierten Methoden sind überladen. Achten Sie darauf, dass Sie das Verhalten der Überladung verstehen, die Sie auswählen.  
  
 **Ausnahmemeldungen:**  
  
 [Summe, Durchschnitt, Letzte, Max und Min Methoden](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [First und FirstOrDefault-Methoden](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Single- und SingleOrDefault-Methoden](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Summe, Durchschnitt, Letzte, Max und Min Methoden  
  
-   Weitere Informationen: Sequenz enthält keine Elemente  
  
 **Verursacht eine InvalidOperationException mit Durchschnitt**  
  
 In diesem Beispiel löst die folgende Methode eine <xref:System.InvalidOperationException> aus, wenn sie die <xref:System.Linq.Enumerable.Average%2A>\-Methode aufruft, da der Ausdruck Linq eine Sequenz zurückgibt, die keine Elemente enthält, die größer sind als 4.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 Wenn Sie eine dieser Methoden verwenden, ohne eine Überprüfung auf eine leere Sequenz durchzuführen, gehen Sie implizit davon aus, dass die Sequenz nicht leer ist und eine leere Sequenz ein unerwartetes Ereignis ist. Das Abfangen oder Auslösen der Ausnahme ist geeignet, wenn Sie davon ausgehen, dass die Sequenz nicht leer ist.  
  
 **Vermeiden Sie eine InvalidOperationException, die von einer leeren Sequenz zurückgeführt wird.**  
  
 Verwenden Sie eine der <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> Methoden, um zu überprüfen, ob die Sequenz leer ist.  
  
> [!TIP]
>  Mit <xref:System.Linq.Enumerable.Any%2A> kann die Prüfleistung verbessert werden, wenn die Sequenz, die durchschnittliche Sequenz möglicherweise eine große Anzahl von Elementen enthält oder wenn die Operation, die die Sequenz generiert, teuer ist.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine System.Linq.Enumerable-Methode wird für eine leere Auflistung aufgerufen.](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> First und FirstOrDefault\-Methoden  
 <xref:System.Linq.Enumerable.First%2A> gibt das erste Element in einer Sequenz zurück oder löst eine <xref:System.InvalidOperationException> aus, wenn die Sequenz leer ist.  Sie erreichen die <xref:System.Linq.Enumerable.FirstOrDefault%2A>\-Methode anstelle von <xref:System.Linq.Enumerable.First%2A> zum Zurückgeben eines angegebenen Werts oder Standardwerts, statt die Ausnahme auszulösen.  
  
> [!NOTE]
>  Im .NET Framework verfügen Typen über ein Konzept von Standardwerten. Für jeden Referenztyp ist der Standardwert beispielsweise null, und für einen Integertyp ist er 0 \(null\). Siehe [Tabelle für Standardwerte](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Auslösen einer InvalidOperationException mit First**  
  
 Die <xref:System.Linq.Enumerable.First%2A> ist eine Methode der Leistungsoptimierung, die das erste Element in einer Sequenz zurückgeben wird, die eine angegebene Bedingung erfüllt. Wenn ein Element, das die Bedingung nicht erfüllt, nicht gefunden wird, lösen die Methoden eine <xref:System.InvalidOperationException> Ausnahme aus.  
  
 In diesem Beispiel löst die `First`\-Methode eine Ausnahme aus, da `dbQueryResults` kein Element enthält, das größer als 4 ist.  
  
 **Ausnahmemeldung:**  
  
-   Zusätzliche Informationen: Die Sequenz enthält kein übereinstimmendes Element  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **Vermeiden einer Ausnahme mit "FirstOrDefault"**  
  
 Verwenden Sie eine der <xref:System.Linq.Enumerable.FirstOrDefault%2A>\-Methoden anstelle von <xref:System.Linq.Enumerable.First%2A>, um zu prüfen, ob die `firstNum` Sequenz mindestens ein Element enthält. Wenn bei der Abfrage kein Element gefunden wird, das die Bedingung erfüllt, gibt sie einen angegebenen oder Standardwert zurück. Sie können den zurückgegebenen Wert überprüfen, um festzustellen, ob alle Elemente gefunden werden.  
  
> [!NOTE]
>  Mit kann <xref:System.Linq.Enumerable.FirstOrDefault%2A> schwieriger zu implementieren sein, wenn der Standardwert des Typs ein gültiges Element in der Sequenz ist.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine System.Linq.Enumerable-Methode wird für eine leere Auflistung aufgerufen.](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Single\- und SingleOrDefault\-Methoden  
 Die <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName>\-Methode gibt das einzige Element einer Sequenz oder das einzige Element einer Sequenz, das einen angegebenen Test besteht, zurück.  
  
 Wenn keine Elemente in der Sequenz vorhanden sind, oder wenn mehr als ein Element in der Sequenz vorhanden ist, löst die Methode eine <xref:System.InvalidOperationException> Ausnahme aus.  
  
 Sie können <xref:System.Linq.Enumerable.SingleOrDefault%2A> zum Zurückgeben eines angegebenen Werts oder Standardwerts verwenden, anstatt die Ausnahme auszulösen, wenn die Sequenz keine Elemente enthält. Allerdings löst <xref:System.Linq.Enumerable.SingleOrDefault%2A> immer noch ein <xref:System.InvalidOperationException> aus, wenn die Sequenz mehr als ein Element enthält, das das Auswahlprädikat erfüllt.  
  
> [!NOTE]
>  Im .NET Framework verfügen Typen über ein Konzept von Standardwerten. Für jeden Referenztyp ist der Standardwert beispielsweise null, und für einen Integertyp ist er 0 \(null\). Siehe [Tabelle für Standardwerte](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Auslösen von InvalidOperationExceptions mit**  
  
 In diesem Beispiel löst `singleObject` eine <xref:System.InvalidOperationException> aus, da `dbQueryResults` kein Element enthält, das größer als 4 ist.  
  
 **Ausnahmemeldung:**  
  
-   Zusätzliche Informationen: Die Sequenz enthält kein übereinstimmendes Element  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Auslösen von InvalidOperationExceptions mit Single oder SingleOrDefault**  
  
 In diesem Beispiel löst `singleObject` eine <xref:System.InvalidOperationException> aus, da `dbQueryResults` mehr als ein Element enthält, das größer ist als 2.  
  
 **Ausnahmemeldung:**  
  
-   Zusätzliche Informationen: die Sequenz enthält mehrere übereinstimmende Elemente  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Vermeiden von InvalidOperationExceptions mit Single**  
  
 <xref:System.Linq.Enumerable.Single%2A> und <xref:System.Linq.Enumerable.SingleOrDefault%2A> dienen auch als Dokumentation für Ihre Absichten.<xref:System.Linq.Enumerable.Single%2A> stark setzt voraus, dass Sie erwarten, dass nur ein Ergebnis aus dem Zustand zurückgegeben wird.<xref:System.Linq.Enumerable.SingleOrDefault%2A> deklariert, dass Sie ein oder null aber nicht mehr Ergebnisse erwarten. Wenn diese Bedingungen nicht zutreffen, ist das Auslösen und Abfangen der <xref:System.InvalidOperationException> geeignet. Wenn Sie jedoch erwarten, dass ungültige Bedingungen häufig auftreten, sollten Sie mit anderen <xref:System.Linq.Enumerable>\-Methoden, z. B. <xref:System.Linq.Enumerable.First%2A> oder <xref:System.Linq.Enumerable.Where%2A> die Ergebnisse generieren.  
  
 Während der Entwicklung können Sie mit einer der <xref:System.Diagnostics.Debug.Assert%2A>\-Methoden Ihre Annahmen überprüfen. In diesem Beispiel bewirkt der hervorgehobene Code, dass der Debugger bricht, und zeigt das Dialogfeld Assert während der Entwicklung an. Die Assertion ist im Versions\-Code entfernt, und jede <xref:System.Linq.Enumerable.Single%2A> wird ausgelöst, wenn die Ergebnisse ungültig sind.  
  
> [!NOTE]
>  Mit <xref:System.Linq.Enumerable.Take%2A> und der Konfiguration seines `count`\-Parameters auf 2 wird die zurückgegebene Sequenz auf höchstens zwei Elemente beschränkt. Diese Reihenfolge gilt auch für alle Fälle, die Sie benötigen, um \(0, 1 und mehr als 1 Elemente\) zu überprüfen, und kann die Prüfleistung verbessern, wenn die Sequenz eine große Anzahl von Elementen enthält oder wenn die Operation, die die Sequenz generiert, teuer ist.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 Wenn Sie die Ausnahme verhindern, aber immernoch die ungültigen Zustände im Versions\-Code behandeln möchten, können Sie das oben beschriebene Verfahren ändern. In diesem Beispiel reagiert die Methode auf die Anzahl von zurückgegebenen Elementen `moreThan2` in der Switch\-Anweisung.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Eine System.Linq.Enumerable-Methode wird für eine leere Auflistung aufgerufen.](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> Verwandte Artikel  
 [Entwurfsrichtlinien für Ausnahmen \(.NET Framework\-Entwurfsrichtlinien\)](http://msdn.microsoft.com/library/ms229014)  
  
 [Behandeln und Auslösen von Ausnahmen \(.NET Framework\-Anwendungsgrundlagen\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [Gewusst wie: Empfangen von Ausnahmebenachrichtigungen \(.NET Framework\-Entwicklungsleitfaden\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [Gewusst wie: Behandeln von Ausnahmen in einer PLINQ\-Abfrage \(.NET Framework\-Entwicklungsleitfaden](http://msdn.microsoft.com/library/Dd460712)  
  
 [Ausnahmen in verwalteten Threads \(.NET Framework\-Entwicklungsleitfaden\)](http://msdn.microsoft.com/library/ms228965)  
  
 [Ausnahmen und Ausnahmebehandlung \(C\#\-Programmierhandbuch\)](http://msdn.microsoft.com/library/ms173160)  
  
 [Ausnahmebehandlungsanweisungen \(C\#\-Referenz\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally\-Anweisung \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [Ausnahmebehandlung \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [Ausnahmen in C\+\+\/CLI](http://msdn.microsoft.com/library/Hh875008)  
  
 [Ausnahmebehandlung \(Task Parallel Library\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [Ausnahmebehandlung \(Debuggen\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [Exemplarische Vorgehensweise: Behandeln einer Parallelitätsausnahme \(Datenzugriff in Visual Studio\)](http://msdn.microsoft.com/library/ms171936)  
  
 [Gewusst wie: Behandeln von Fehlern und Ausnahmen in Zusammenhang mit der Datenbindung \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [Behandeln von Ausnahmen in Netzwerk\-Apps \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [In diesem Artikel](#BKMK_In_this_article)