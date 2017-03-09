---
title: "Problembehandlung bei Ausnahmen: System.NullReferenceException | Microsoft Docs"
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
  - "NullReferenceException-Klasse"
ms.assetid: 4822b0b4-8105-43fb-887a-3cc51ff02899
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.NullReferenceException
Eine <xref:System.NullReferenceException> tritt auf, wenn Sie versuchen, eine Methode oder Eigenschaft eines *Verweistyps* \([C\#](/dotnet/csharp/language-reference/keywords/reference-types), [Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)\) zu verwenden, deren Wert `null` ist. Möglicherweise haben Sie versucht, ein Objekt zu verwenden, ohne zunächst das Schlüsselwort [new](/dotnet/csharp/language-reference/keywords/new) \([New](/dotnet/visual-basic/language-reference/operators/new-operator) in Visual Basic\) zu verwenden, oder der Wert des Objekts war [null](/dotnet/csharp/language-reference/keywords/null) \([Nothing](/dotnet/visual-basic/language-reference/nothing) in Visual Basic\).  
  
##  <a name="BKMK_Contents"></a> Abschnitte in diesem Artikel  
 [In diesem Artikel verwendete Klassen](#BKMK_Classes_used_in_the_examples)  
  
 [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 [Ermitteln der Ursache einer NullReferenceException bei der Entwicklung](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 [Vermeiden von NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 [Behandlung von NullReferenceExceptions im Releaseversionscode](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
##  <a name="BKMK_Classes_used_in_the_examples"></a> In diesem Artikel verwendete Klassen  
 Die meisten Beispiele in diesem Artikel verwenden eine oder beide der folgenden Klassen:  
  
```c#  
public class Automobile { public EngineInfo Engine {get; set;} } public class EngineInfo { public EngineInfo() { } public EngineInfo(string powerSrc, double engineSize) { Power = powerSrc; Size = engineSize; } public double Size { get; set; } public string Power = null; }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo End Class Public Class EngineInfo Public Sub New() End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = Nothing End Class  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
##  <a name="BKMK_Common_causes_of_NullReferenceExceptions"></a> Häufige Ursachen für NullReferenceExceptions  
 Jede Verweistyp\-Variable kann null sein. Lokale Variablen, Eigenschaften von Klassen, Methodenparameter und Methodenrückgabewerte können Nullverweise enthalten. Beim Aufrufen von Methoden oder Eigenschaften dieser Variablen mit Nullwert wird eine NullReferenceException geworfen. Sonderfälle:  
  
 [Eine lokale Variable oder ein Member-Feld ist deklariert, jedoch nicht initialisiert](#BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized)  
  
 [Eine Eigenschaft oder ein Feld ist null](#BKMK_A_property_or_field_is_null)  
  
 [Ein Methodenparameter ist null](#BKMK_A_method_parameter_is_null)  
  
 [Der Rückgabewert einer Methode ist null](#BKMK_The_return_value_of_a_method_is_null)  
  
 [Ein Objekt in einer Sammlung oder einem Array ist null](#BKMK_An_object_in_a_collection_or_array_is_null)  
  
 [Ein Objekt wird aufgrund einer Bedingung nicht erstellt](#BKMK_An_object_is_not_created_because_of_a_condition)  
  
 [Ein nach Verweis an eine Methode übergebenes Objekt ist null](#BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null)  
  
###  <a name="BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized"></a> Eine lokale Variable oder ein Member\-Feld ist deklariert, jedoch nicht initialisiert  
 Dieser einfache Fehler tritt am Häufigsten in Visual Basic\-Code auf. Mit der Ausnahme einer Variablendeklaration, die als Ausgabeparameter verwendet wird, erlaubt der C\#\-Compiler keine Verwendung einer lokalen Verweisvariable, wenn diese nicht initialisiert wurde. Der VB\-Compiler generiert eine Warnung.  
  
-   Im folgenden C\#\-Code generiert die hervorgehobene Zeile diesen Compilerfehler:  
  
 **Verwendung der nicht zugewiesenen lokalen Variablen 'Modul'**  
  
-   Im Visual Basic Code generiert die hervorgehobene Zeile die Compilerwarnung BC42104:  
  
 **Die Variable wird verwendet, bevor ihr ein Wert zugewiesen wird. Zur Laufzeit kann eine null\-Verweisausnahme auftreten.**     Und die Zeile wirft bei der Ausführung eine NullReferenceException.  
  
```c#  
public void NullReferencFromUninitializedLocalVariable() { EngineInfo engine; Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferencFromUninitializedLocalVariable() Dim engine As EngineInfo Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_A_property_or_field_is_null"></a> Eine Eigenschaft oder ein Feld ist null  
 Die Felder und Eigenschaften einer Klasse werden bei der Erstellung der Klasse automatisch mit deren [Standardwert](../Topic/Data%20Member%20Default%20Values.md) initialisiert. Der Standardwert eines Verweistyps ist `null` \(`Nothing` in Visual Basic\). Beim Aufrufen von Membermethoden auf ein Feld oder eine Eigenschaft einer übergeordneten Klasse wird eine NullReferenceException geworfen, wenn das Feld bzw. die Eigenschaft null ist.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile eine NullReferenceException, da die `Engine`\-Eigenschaft von `car` automatisch auf null initialisiert wird.  
  
```c#  
public void NullReferenceFromProperty() { var car = new Automobile(); Console.WriteLine(car.Engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferenceFromProperty() Dim car = New Automobile() Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_A_method_parameter_is_null"></a> Ein Methodenparameter ist null  
 Ein Methodenparameter, der ein Verweistyp ist, kann `null` \(`Nothing` in Visual Basic\) sein. Beim Aufrufen von Membermethoden oder Eigenschaften auf einen Parameterwert wird eine NullReferenceException geworfen, wenn dieser Wert null ist.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile eine NullReferenceException, da `BadEngineInfoPassedToMethod``NullReferenceFromMethodParameter` mit einem Parameter aufruft, der null ist.  
  
```c  
public void BadEngineInfoPassedToMethod() { EngineInfo eng = null; NullReferenceFromMethodParameter(eng); } public void NullReferenceFromMethodParameter(EngineInfo engine) { Console.WriteLine(engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadParameterPassedToMethod() As EngineInfo Dim eng As EngineInfo = Nothing NullReferenceFromMethodParameter(eng) End Sub Public Sub NullReferenceFromMethodParameter(engine As EngineInfo) Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_The_return_value_of_a_method_is_null"></a> Der Rückgabewert einer Methode ist null  
 Eine Methode, die einen Verweistyp zurückgibt, kann `null` \(`Nothing` in Visual Basic\) zurückgeben. Beim Aufrufen von Methoden oder Eigenschaften des zurückgegebenen Verweistyps wird eine NullReferenceException geworfen, wenn der Verweis null ist.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile eine NullReferenceException, da der Aufruf von `BadGetEngineInfo` einen Nullverweis in der `NullReferenceFromMethodParameter`\-Methode zurückgibt.  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void NullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Function BadGetEngineInfo() As EngineInfo Dim engine As EngineInfo = Nothing Return engine End Function Public Sub NullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() Console.WriteLine(engine.ToString()) End Sub  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_in_a_collection_or_array_is_null"></a> Ein Objekt in einer Sammlung oder einem Array ist null  
 Eine Liste oder ein Array von Verweistypen kann ein Element enthalten, das null ist. Beim Aufrufen von Methoden oder Eigenschaften auf ein Listenelement wird eine NullReferenceException geworfen, wenn dieses Element null ist.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile in `NullReferenceFromListItem()` eine NullReferenceException, da der Aufruf an `BadGetCarList` ein Element zurückgibt, das null ist.  
  
```c#  
public Automobile[] BadGetCarList() { var autos = new Automobile[10]; for (int i = 0; i autos.Length; i++) { if (i != 6) { autos[i] = new Automobile(); } } return autos; } public void NullReferenceFromListItem() { var cars = BadGetCarList(); foreach (Automobile car in cars) { Console.WriteLine(car.ToString()); } }  
```  
  
```vb  
Public Function BadGetCarList() As Automobile() Dim autos = New Automobile(10) {} For i As Integer = 0 To 9 If i <> 6 Then autos(i) = New Automobile() End If Next Return autos End Function Public Sub NullReferenceFromListItem() Dim cars = BadGetCarList() For Each car As Automobile In cars Console.WriteLine(car.ToString()) Next End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_is_not_created_because_of_a_condition"></a> Ein Objekt wird aufgrund einer Bedingung nicht erstellt  
 Wenn ein Verweistyp in einem bedingten Block initialisiert wird, kann es passieren, dass das Objekt nicht erstellt wird, wenn die Bedingung nicht erfüllt ist.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile in `NullReferenceFromConditionalCreation` eine NullReferenceException, da die `engine`\-Variable nur initialisiert wird, wenn die `DetermineTheCondition()`\-Methode den Wert `true` zurückgibt.  
  
```c#  
public bool DetermineTheCondition() { return false; } public void NullReferenceFromConditionalCreation() { EngineInfo engine = null; var condition = DetermineTheCondition(); if (condition) { engine = new EngineInfo(); engine.Power = "Diesel"; engine.Size = 2.4; } Console.WriteLine(engine.Size); }  
```  
  
```vb  
Public Function DetermineTheCondition() As Boolean Return False End Function Public Sub NullReferenceFromConditionalCreation() Dim engine As EngineInfo = Nothing Dim condition = DetermineTheCondition() If condition Then engine = New EngineInfo() engine.Power = "Diesel" engine.Size = 2.4 End If Console.WriteLine(engine.Size) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
### Die Eigenschaft eines an eine Methode übergebenen Objekts ist null  
 Wenn Sie ein Objekt nach Wert als Parameter an eine Methode übergeben \(ohne die Schlüsselwörter `ref` bzw. `out` in C\# oder das Schlüsselwort `ByRef` in Visual Basic\), kann die Methode den Speicherort des Parameters \(auf den der Parameter zeigt\) nicht ändern. Sie kann jedoch die Eigenschaften des Objekts ändern.  
  
 In diesem Beispiel erstellt die`NullPropertyReferenceFromPassToMethod`\-Methode ein `Automobile` \-Objekt und initialisiert die `Engine`\-Eigenschaft. Anschließend wird `BadSwapCarEngine` aufgerufen und das neue Objekt als Parameter übergeben.`BadSwapCarEngine` setzt die Engine\-Eigenschaft auf null. Dadurch wirft die hervorgehobene Zeile in `NullPropertyReferenceFromPassToMethod` eine NullReferenceException.  
  
```c#  
public void BadSwapCarEngine(Automobile car) { car.Engine = null; } public void (Automobile car) { car.Engine = new EngineInfo("GAS", 1.5); BadSwapCarEngine(car); Console.WriteLine(car.Engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadSwapCarEngine(car As Automobile) car.Engine = Nothing End Sub Public Sub NullPropertyReferenceFromPassToMethod() Dim car As New Automobile() car.Engine = New EngineInfo("GAS", 1.5) BadSwapCarEngine(car) Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null"></a> Ein nach Verweis an eine Methode übergebenes Objekt ist null  
 Wenn Sie ein Objekt nach Verweis als Parameter an eine Methode übergeben \(mit dem Schlüsselwort `ref` bzw. `out` in C\# oder das Schlüsselwort `ByRef` in Visual Basic\), können Sie den Speicherort ändern, auf den der Parameter zeigt.  
  
 Wenn Sie einen Verweistyp nach Verweis an eine Methode übergeben, kann die Methode den Verweistyp zu `null` \(`Nothing` in Visual Basic\) ändern.  
  
 In diesem Beispiel wirft die hervorgehobene Zeile in `NullReferenceFromPassToMethodByRef` eine NullReferenceException, da der Aufruf an die `BadEngineSwapByRef`\-Methode die `stockEngine`\-Variable auf null setzt.  
  
```c#  
public void BadEngineSwapByRef(ref EngineInfo engine) { engine = null; } public void NullReferenceFromPassToMethodByRef() { var stockEngine = new EngineInfo(); stockEngine.Power = "Gas"; stockEngine.Size = 7.0; BadSwapEngineByRef(ref stockEngine); Console.WriteLine(stockEngine.ToString()); }  
```  
  
```vb  
Public Sub BadSwapEngineByRef(ByRef engine As EngineInfo) engine = Nothing End Sub Public Sub NullReferenceFromPassToMethodByRef() Dim formatStr = "The stock engine has been replaced by a {0} liter {} engine" Dim stockEngine = New EngineInfo() stockEngine.Power = "Gas" stockEngine.Size = 7.0 BadSwapEngineByRef(stockEngine) Console.WriteLine(stockEngine.ToString()) End Sub  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Häufige Ursachen für NullReferenceExceptions](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_of_a_null_reference_exception_during_development"></a> Ermitteln der Ursache einer NullReferenceException bei der Entwicklung  
 [Verwenden Sie Datentipps, das Lokalfenster und die Überwachungsfenster, um die Variablenwerte anzuzeigen](#BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values)  
  
 [Durchlaufen Sie die Aufrufliste, um herauszufinden, an welcher Stelle eine Verweisvariable nicht initialisiert oder auf null gesetzt wird](#BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_)  
  
 [Erstellen bedingter Haltepunkte, um das Debuggen zu unterbrechen, wenn ein Objekt null (Nothing in Visual Basic) ist](#BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_)  
  
###  <a name="BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values"></a> Verwenden Sie Datentipps, das Lokalfenster und die Überwachungsfenster, um die Variablenwerte anzuzeigen  
  
-   Zeigen Sie mit der Maus auf die Variablennamen, um deren Werte in einem [Datentipp](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) anzuzeigen. Wenn die Variable auf ein Objekt oder eine Sammlung verweist, können Sie den Datentyp erweitern, um dessen Eigenschaften oder Elemente zu prüfen.  
  
-   Öffnen Sie das Fenster **Lokal**, um alle im aktuellen Kontext aktiven Variablen anzuzeigen.  
  
-   Mit dem [Überwachungsfenster](../debugger/watch-and-quickwatch-windows.md) können Sie die Änderungen von Variablenwerten überwachen, während Sie den Code durchlaufen.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Ermitteln der Ursache einer NullReferenceException bei der Entwicklung](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_"></a> Durchlaufen Sie die Aufrufliste, um herauszufinden, an welcher Stelle eine Verweisvariable nicht initialisiert oder auf null gesetzt wird  
 Das [Aufruflistenfenster](../debugger/how-to-use-the-call-stack-window.md) in Visual Studio enthält eine Liste mit den Namen der Methoden, die nicht abgeschlossen wurden, wenn der Debugger bei einer Ausnahme oder einem Haltepunkt anhält. Sie können einen Namen im Fenster **Anrufliste** und **Zu Rahmen wechseln** auswählen, um den Ausführungskontext zur entsprechenden Methode zu wechseln und deren Variablen zu untersuchen.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Ermitteln der Ursache einer NullReferenceException bei der Entwicklung](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_"></a> Erstellen bedingter Haltepunkte, um das Debuggen zu unterbrechen, wenn ein Objekt null \(Nothing in Visual Basic\) ist  
 Sie können einen [bedingten Haltepunkt](http://msdn.microsoft.com/library/5557y8b4.aspx#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) festlegen, um die Ausführung zu unterbrechen, wenn eine Variable null ist. Bedingte Haltepunkte sind hilfreich, wenn der Nullverweis nur selten auftritt, z. B. wenn ein Element in einer Sammlung nur gelegentlich null ist. Bedingte Haltepunkte haben außerdem den Vorteil, dass Sie mit deren Hilfe ein Problem debuggen können, bevor Sie sich für eine bestimmte Behandlungsroutine entscheiden.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Ermitteln der Ursache einer NullReferenceException bei der Entwicklung](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
##  <a name="BKMK_Avoid_NullReferenceExceptions"></a> Vermeiden von NullReferenceExceptions  
 [Bestätigen von Invarianten mit Debug.Assert](#BKMK_Use_Debug_Assert_to_confirm_an_invariant)  
  
 [Vollständiges Initialisieren von Verweistypen](#BKMK_Fully_initialize_reference_types)  
  
###  <a name="BKMK_Use_Debug_Assert_to_confirm_an_invariant"></a> Bestätigen von Invarianten mit Debug.Assert  
 Eine *Invariante* ist eine Bedingung, bei der Sie sicher sind, dass diese wahr ist. Eine [Debug.Assert \(System.Diagnostics](http://msdn.microsoft.com/library/system.diagnostics.debug.assert.aspx)\-Anweisung wird nur in Debug\-Builds Ihrer Anwendungen aufgerufen und nicht im Versionscode. Wenn die invariante Bedingung nicht wahr ist, hält der Debugger bei der Assert\-Anweisung an und zeigt ein Dialogfeld an.`Debug.Assert` ermöglicht eine Prüfung, dass sich eine Bedingung bei der Entwicklung der Anwendung nicht geändert hat. Eine Assertion dokumentiert auch für andere, die Ihren Code lesen, dass die Bedingung immer erfüllt sein muss.  
  
 Die `MakeEngineFaster`\-Methode nimmt z. B. an, dass der `engine`\-Parameter niemals null ist, da deren einzige aufrufende Methode \(`TheOnlyCallerOfMakeEngineFaster`\) die `EngineInfo`bekannterweise komplett initialisiert. Die Assertion in `MakeEngineFaster` dokumentiert diese Annahme und prüft zugleich, ob diese erfüllt ist.  
  
 Wenn jemand eine neue aufrufende Methode hinzufügt \(`BadNewCallerOfMakeEngineFaster`\), die den Parameter nicht initialisiert, wird die Annahme ausgelöst.  
  
```c#  
private void TheOnlyCallerOfMakeEngineFaster() { var engine = new EngineInfo(); engine.Power = "GAS"; engine.Size = 1.5; MakeEngineFaster(engine); } private void MakeEngineFaster(EngineInfo engine) { System.Diagnostics.Debug.Assert(engine != null, "Assert: engine != null"); engine.Size *= 2; Console.WriteLine("The engine is twice as fast"); } private void BadNewCallerOfMakeEngineFaster() { EngineInfo engine = null; MakeEngineFaster(engine); }  
```  
  
```vb  
Public Sub TheOnlyCallerOfMakeEngineFaster() Dim engine As New EngineInfo engine.Power = "GAS" engine.Size = 1.5 MakeEngineFaster(engine) End Sub Private Sub MakeEngineFaster(engine As EngineInfo) System.Diagnostics.Debug.Assert(engine IsNot Nothing, "Assert: engine IsNot Nothing") engine.Size = engine.Size * 2 Console.WriteLine("The engine is twice as fast") End Sub Public Sub BadNewCallerOfMakeEngineFaster() Dim engine As EngineInfo = Nothing MakeEngineFaster(engine) End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Vermeiden von NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_Fully_initialize_reference_types"></a> Vollständiges Initialisieren von Verweistypen  
 Sie sollten Verweistypen so nahe wie möglich an deren Erstellung vollständig initialisieren, um viele NullReferenceExceptions zu vermeiden.  
  
 **Vollständige Initialisierung in Ihren eigenen Klassen**  
  
 Wenn Sie die Klasse kontrollieren, die eine NullReferenceException wirft, sollten Sie das Objekt im Typkonstruktor vollständig initialisieren. Hier ist z. B. eine überarbeitete Version der Beispielklassen mit garantierter vollständiger Initialisierung:  
  
```c#  
public class Automobile { public EngineInfo Engine { get; set; } public Automobile(){this.Engine = new EngineInfo();} public Automobile(string powerSrc, double engineSize) { this.Engine = new EngineInfo(powerSrc, engineSize); } } public class EngineInfo { public double Size {get; set;} public string Power {get; set;} public EngineInfo(){// the base enginethis.Power = "GAS";this.Size = 1.5;} public EngineInfo(string powerSrc, double engineSize) { this.Power = powerSrc; this.Size = engineSize; } }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo     Public Sub New()Me.Engine = New EngineInfo()End SubPublic Sub New(powerSrc As String, engineSize As Double)Me.Engine = New EngineInfo(powerSrc, engineSize)End Sub End Class Public Class BaseEngineInfo Public Sub New()' the base engineMe.Power = "GAS"Me.Size = 1.5End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = String.Empty End Class  
```  
  
> [!NOTE]
>  **Verzögerte Initialisierung für große oder selten verwendete Eigenschaften**  
>   
>  Um die Speicherverwendung Ihrer Klassen zu senken und deren Leistung zu verbessern, können Sie Eigenschaften mit Verweistypen verzögert initialisieren. Siehe [Lazy Initialization](../Topic/Lazy%20Initialization.md).  
  
##  <a name="BKMK_Handle_NullReferenceExceptions_in_release_code"></a> Behandlung von NullReferenceExceptions im Releaseversionscode  
 [Prüfen auf null (Nothing in Visual Basic) vor dem Verwenden von Verweistypen](#BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type)  
  
 [Verwenden von try – catch – finally (Try – Catch – Finally in Visual Basic) zur Behandlung von Ausnahmen](#BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception)  
  
 Es ist immer besser, NullReferenceExceptions zu vermeiden, anstatt diese nach dem Auftreten zu behandeln. Die Behandlung von Ausnahmen kann die Wartbarkeit und Lesbarkeit Ihres Codes erschweren und gelegentlich sogar zu neuen Problemen führen. NullReferenceExceptions sind oftmals nicht behebbare Fehler. In diesen Fällen macht es oft Sinn, wenn die Ausnahme die Anwendung beenden kann.  
  
 Oft ist es jedoch auch möglich, den Fehler auf sinnvolle Art zu behandeln.  
  
-   Ihre Anwendung kann Objekte ignorieren, die null sind. Wenn Ihre Anwendung Einträge in einer Datenbank abruft und verarbeitet, können Sie z. B. ungültige Einträge ignorieren, die zu Nullobjekten führen. Möglicherweise reicht es aus, die ungültigen Daten in einer Protokolldatei oder der Anwendungs\-GUI aufzuzeichnen.  
  
-   Sie können nach einer Ausnahme fortfahren. Aufrufe an einen Webdienst, der einen Verweistyp zurückgibt, können z. B. null zurückgeben, wenn die Verbindung unterbrochen wird oder eine Zeitüberschreitung auftritt. Sie können versuchen, die Verbindung erneut herzustellen oder den Aufruf zu wiederholen.  
  
-   Sie können Ihre Anwendung zurück in einen gültigen Status versetzen. Wenn Sie z. B. eine Aufgabe mit mehreren Schritten ausführen, die Informationen in einem Datenspeicher ablegen muss, bevor eine Methode aufgerufen wird, die eine NullReferenceException zurückgibt. Wenn das nicht initialisierte Objekt den Datensatz ungültig machen würde, können Sie z. B. die vorherigen Daten entfernen, bevor Sie die Anwendung schließen.  
  
-   Sie möchten die Ausnahme melden. Wenn der Fehler z. B. von einem Benutzer Ihrer Anwendung verursacht wurde, möchten Sie möglicherweise eine Nachricht generieren, um den Benutzer bei der Angabe der korrekten Informationen zu unterstützen. Außerdem können Sie Informationen über den Fehler protokollieren, um bei der Korrektur des Problems zu helfen. Einige Frameworks, wie ASP.NET, verfügen über einen hohen Ausnahmehandler, der alle Fehler aufzeichnet, damit die Anwendung nie abstürzt. In diesem Fall kann die Protokollierung der Ausnahme möglicherweise die einzige Möglichkeit sein, damit Sie wissen, dass sie auftritt.  
  
 Hier sehen Sie zwei Möglichkeiten für die Behandlung von NullReferenceExceptions im Releaseversionscode.  
  
###  <a name="BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type"></a> Prüfen auf null \(Nothing in Visual Basic\) vor dem Verwenden von Verweistypen  
 Sie können ein Objekt vor der Verwendung explizit auf null testen, um die Leistungseinbuße von try\-catch\-finally\-Blöcken zu vermeiden. Sie müssen jedoch trotzdem entscheiden und implementieren, was im Fall eines nicht initialisierten Objekts geschehen soll.  
  
 In diesem Beispiel die `CheckForNullReferenceFromMethodReturnValue` prüft den Rückgabewert der `BadGetEngineInfo` Methode. Wenn das Objekt nicht null ist, wird es verwendet; andernfalls meldet die Methode einen Fehler.  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void CheckForNullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); if(engine != null) { // modify the info engine.Power = "DIESEL"; engine.Size = 2.4; } else { // report the error Console.WriteLine("BadGetEngine returned null") } }  
  
```  
  
```vb  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } Public Sub CheckForNullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() If (engine IsNot Nothing) Then ' modify the info engine.Power = "DIESEL" engine.Size = 2.4 Else ' report the error Console.WriteLine("BadGetEngineInfo returned Nothing") End If End Sub  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Behandlung von NullReferenceExceptions im Releaseversionscode](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
###  <a name="BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception"></a> Verwenden von try – catch – finally \(Try – Catch – Finally in Visual Basic\) zur Behandlung von Ausnahmen  
 Die integrierten Konstrukte für die Ausnahmebehandlung \([try, catch, finally](/dotnet/csharp/language-reference/keywords/exception-handling-statements) in C\#, [Try, Catch, Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) in Visual Basic\) bieten weitere Optionen für den Umgang mit NullReferenceExceptions neben der Prüfung, ob ein Objekt nicht null ist.  
  
 In diesem Beispiel verwendet `CatchNullReferenceFromMethodCall` zwei Assertions, um die Annahme zu bestätigen, dass der Parameter ein komplettes Automobil inklusive Motor enthält. Im `try`\-Block wirft die hervorgehobene Zeile eine NullReferenceException, da der Aufruf an `RarelyBadEngineSwap`die `Engine`\-Eigenschaft des Autos zerstören kann. Der `catch`\-Block fängt die Ausnahme ab, schreibt deren Informationen in eine Datei und meldet den Fehler an den Benutzer. Im `finally`\-Block stellt die Methode sicher, dass der Status des Autos nicht schlechter ist als beim Methodeneintritt.  
  
```c#  
public void RarelyBadSwapCarEngine(Automobile car) { if ((new Random()).Next() == 42) { car.Engine = null; } else { car.Engine = new EngineInfo("DIESEL", 2.4); } } public void CatchNullReferenceFromMethodCall(Automobile car) { System.Diagnostics.Debug.Assert(car != null, "Assert: car != null"); System.Diagnostics.Debug.Assert(car.Engine != null, "Assert: car.Engine != null"); // save current engine properties in case they're needed var enginePowerBefore = car.Engine.Power; var engineSizeBefore = car.Engine.Size; try { RarelyBadSwapCarEngine(car); var msg = "Swap succeeded. New engine power source: {0} size {1}"; Console.WriteLine(msg, car.Engine.Power, car.Engine.Size); } catch(NullReferenceException nullRefEx) { // write exception info to log file LogException(nullRefEx); // notify the user Console.WriteLine("Engine swap failed. Please call your customer rep."); } finally { if(car.Engine == null) { car.Engine = new EngineInfo(enginePowerBefore, engineSizeBefore); } } }  
  
```  
  
```vb  
Public Sub RarelyBadSwapCarEngine(car As Automobile) If (New Random()).Next = 42 Then car.Engine = Nothing Else car.Engine = New EngineInfo("DIESEL", 2.4) End If End Sub Public Sub CatchNullReferenceFromMethodCall(car As Automobile) System.Diagnostics.Debug.Assert(car IsNot Nothing) System.Diagnostics.Debug.Assert(car.Engine IsNot Nothing) ' save current engine properties in case they're needed Dim powerBefore = car.Engine.Power Dim sizeBefore = car.Engine.Size Try RarelyBadSwapCarEngine(car) Dim msg = "Swap succeeded. New engine power source: {0} size {1}" Console.WriteLine(msg, car.Engine.Power, car.Engine.Size) Catch nullRefEx As NullReferenceException ' write exception info to log file LogException(nullRefEx) ' notify user Console.WriteLine("Engine swap failed. Please call your customer rep.") Finally If car.Engine Is Nothing Then car.Engine = New EngineInfo(powerBefore, sizeBefore) End Try End Sub  
  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Behandlung von NullReferenceExceptions im Releaseversionscode](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)  
  
## Verwandte Artikel  
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
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Abschnitte in diesem Artikel](#BKMK_Contents)