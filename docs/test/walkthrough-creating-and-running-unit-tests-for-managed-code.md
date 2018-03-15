---
title: "Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 6320f9730be9c47da11a43b57b64c86e46a42bf4
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code
Diese exemplarische Vorgehensweise führt Sie durch das Erstellen, Ausführen und Anpassen verschiedener Komponententests mithilfe des Microsoft-Komponententest-Frameworks für verwalteten Code und mithilfe von Visual Studio-Test-Explorer. Sie beginnen mit einem C#-Projekt in der Entwicklungsphase und erstellen Tests zur Codeüberprüfung. Anschließend führen Sie die Tests aus und überprüfen die Ergebnisse. Dann können Sie Änderungen am Projektcode vornehmen und die Tests erneut ausführen.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Die exemplarische Vorgehensweise vorbereiten](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Ein Komponententestprojekt erstellen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Die Testklasse erstellen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
-   [Testklassenanforderungen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
 [Die erste Testmethode erstellen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
-   [Testmethodenanforderungen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
 [Den Test erstellen und ausführen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
 [Den Code korrigieren und die Tests erneut ausführen](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
 [Den Code mit Komponententests verbessern](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  In dieser exemplarischen Vorgehensweise wird das Microsoft-Komponententest-Framework für verwalteten Code verwendet. Test-Explorer kann außerdem Tests von Drittanbieter-Komponententest-Frameworks ausführen, die über Adapter für Test-Explorer verfügen. Weitere Informationen finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).  
  
> [!NOTE]
>  Informationen zum Ausführen von Tests über die Befehlszeile finden Sie unter [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen-Testprogramms](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Das Projekt "Bank". Weitere Informationen finden Sie unter [Beispielprojekt zum Erstellen von Komponententests](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> Vorbereiten der exemplarischen Vorgehensweise  
  
1.  Öffnen Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu** , und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Klicken Sie unter **Installierte Vorlagen**auf **Visual C#**.  
  
4.  Klicken Sie in der Liste der Anwendungstypen auf **Klassenbibliothek**.  
  
5.  Geben Sie im Feld **Name** die Bezeichnung `Bank` , und klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    >  Wenn der Name "Bank" bereits verwendet wird, wählen Sie einen anderen Namen für das Projekt aus.  
  
     Das neue Bank-Projekt wird erstellt und im Projektmappen-Explorer angezeigt, wobei der Code-Editor mit der Datei Class1.cs geöffnet wird.  
  
    > [!NOTE]
    >  Wenn die Datei Class1.cs nicht im Code-Editor geöffnet wird, doppelklicken Sie im Projektmappen-Explorer auf die Datei Class1.cs, um diese zu öffnen.  
  
6.  Kopieren Sie den Quellcode aus dem [Beispielprojekt zum Erstellen von Komponententests](../test/sample-project-for-creating-unit-tests.md).  
  
7.  Ersetzen Sie den ursprünglichen Inhalt von Class1.cs durch den Code aus dem [Beispielprojekt zum Erstellen von Komponententests](../test/sample-project-for-creating-unit-tests.md).  
  
8.  Speichern Sie die Datei als BankAccount.cs.  
  
9. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
 Sie haben nun ein Projekt mit dem Namen Bank erstellt. Dieses Projekt enthält zu testenden Quellcode und Tools, mit denen der Quellcode getestet werden kann. Der Namespace für Bank ( **BankAccountNS**) enthält die öffentliche **BankAccount**-Klasse, deren Methoden Sie im Folgenden testen werden.  
  
 Bei diesem Schnellstart konzentrieren wir uns auf die `Debit` -Methode. Diese Methode wird aufgerufen, wenn von einem Konto Geld abgebucht wird und folgender Code enthalten ist:  
  
```csharp  
// method under test  
public void Debit(double amount)  
{  
    if(amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    m_balance += amount;  
}  
  
```  
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Ein Komponententestprojekt erstellen  
 **Voraussetzung**: Führen Sie die im Verfahren " [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)" angegebenen Schritte aus.  
  
#### <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Komponententestprojekt  
  
1.  Wählen Sie im Menü **Datei** die Option **Hinzufügen**aus, und klicken Sie auf **Neues Projekt...**.  
  
2.  Erweitern Sie im Dialogfeld "Neues Projekt" die Option **Installiert**und dann die Option **Visual C#**, und wählen Sie dann **Test**aus.  
  
3.  Wählen Sie in der Liste der Vorlagen **Komponententestprojekt**aus.  
  
4.  Geben Sie in das Feld **Name** "BankTests" ein, und klicken Sie dann auf **OK**.  
  
     Das Projekt **BankTests** wird der Projektmappe **Bank** hinzugefügt.  
  
5.  Fügen Sie im Projekt **BankTests** einen Verweis auf die Projektmappe **Bank** ein.  
  
     Wählen Sie im Projektmappen-Explorer im Projekt **BankTests** die Option **Verweise** aus, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen** .  
  
6.  Erweitern Sie im Dialogfeld "Verweis-Manager" den Eintrag **Projektmappe** , und überprüfen Sie das Element **Bank** .  
  
##  <a name="BKMK_Create_the_test_class"></a> Die Testklasse erstellen  
 Zum Überprüfen der `BankAccount` -Klasse wird eine Testklasse benötigt. Sie können UnitTest1.cs verwenden, die von der Projektvorlage generiert wurde, doch Datei und Klasse sollten einen aussagekräftigeren Namen erhalten. Sie können das in einem Schritt erledigen, indem Sie die Datei im Projektmappen-Explorer umbenennen.  
  
 **Umbenennen einer Klassendatei**  
  
 Wählen Sie im Projektmappen-Explorer im BankTests-Projekt die Datei UnitTest1.cs aus. Wählen Sie im Kontextmenü die Option **Umbenennen**aus, und benennen Sie dann die Datei in BankAccountTests.cs um. Wenn Sie gefragt werden, ob Sie alle im Projekt enthaltenen Verweise in das Codeelement UnitTest1 umbenennen möchten, wählen Sie **Ja** aus. Dadurch wird der Name der Klasse in `BankAccountTest`geändert.  
  
 Die Datei BankAccountTests.cs enthält nun den folgenden Code:  
  
```csharp  
// unit test code  
using System;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
namespace BankTests  
{  
    [TestClass]  
    public class BankAccountTests  
    {  
        [TestMethod]  
        public void TestMethod1()  
        {  
        }  
    }  
}  
```  
  
 **Hinzufügen einer Using-Anweisung zum zu testenden Projekt**  
  
 Auch der Klasse kann eine Using-Anweisung hinzugefügt werden, um ohne vollqualifizierte Namen das zu testende Projekt aufrufen zu können. Fügen Sie am Anfang der Klassendatei Folgendes hinzu:  
  
```csharp  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Testklassenanforderungen  
 Die Mindestanforderungen für eine Testklasse sind die folgenden:  
  
-   Im Microsoft-Komponententest-Framework für verwalteten Code ist das `[TestClass]` -Attribut für jede Klasse erforderlich, die in Test-Explorer auszuführende Komponententestmethoden enthält.  
  
-   Jede Testmethode, die von Test-Explorer ausgeführt werden soll, muss über das `[TestMethod]`-Attribut verfügen.  
  
 Ein Komponententestprojekt kann auch über andere Klassen ohne das `[TestClass]` -Attribut verfügen, und Testklassen können andere Methoden ohne das `[TestMethod]` -Attribut aufweisen. Sie können diese anderen Klassen und Methoden in den Testmethoden verwenden.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> Die erste Testmethode erstellen  
 In dieser Vorgehensweise schreiben Sie Komponententestmethoden, um das Verhalten der `Debit` -Methode der `BankAccount` -Klasse zu überprüfen. Die Methode ist weiter oben aufgeführt.  
  
 Anhand der Analyse der zu testenden Methode bestimmen Sie, dass mindestens drei Verhaltensweisen überprüft werden müssen:  
  
1.  Die Methode löst eine <xref:System.ArgumentOutOfRangeException> aus, wenn der Abbuchungsbetrag größer ist als das Guthaben.  
  
2.  Außerdem löst sie eine `ArgumentOutOfRangeException` aus, wenn der Abbuchungsbetrag kleiner als null ist.  
  
3.  Wenn die Überprüfungen unter 1. und 2. zufriedenstellend sind, zieht die Methode den Betrag vom Kontoguthaben ab.  
  
 Im ersten Test überprüfen Sie, ob durch einen gültigen Betrag (kleiner als das Kontoguthaben und größer als null) der richtige Betrag vom Konto abgebucht wird.  
  
#### <a name="to-create-a-test-method"></a>So erstellen Sie eine Testmethode  
  
1.  Fügen Sie der Datei BankAccountTests.cs eine `BankAccountNS;` -Using-Anweisung hinzu.  
  
2.  Fügen Sie dieser `BankAccountTests` -Klasse die folgende Methode hinzu.  
  
    ```csharp  
    // unit test code  
    [TestMethod]  
    public void Debit_WithValidAmount_UpdatesBalance()  
    {  
        // arrange  
        double beginningBalance = 11.99;  
        double debitAmount = 4.55;  
        double expected = 7.44;  
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
        // act  
        account.Debit(debitAmount);  
  
        // assert  
        double actual = account.Balance;  
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
    }  
    ```  
  
 Die Methode ist recht einfach. Sie richten ein neues `BankAccount` -Objekt mit einem Startguthaben ein und buchen dann einen gültigen Betrag ab. Sie verwenden die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> -Methode des Microsoft-Komponententest-Frameworks für verwalteten Code, um sicherzustellen, dass das Guthaben zum Schluss wie erwartet ausfällt.  
  
###  <a name="BKMK_Test_method_requirements"></a> Testmethodenanforderungen  
 Eine Testmethode muss die folgenden Anforderungen erfüllen:  
  
-   Die Methode muss mit dem `[TestMethod]` -Attribut ausgestattet sein.  
  
-   Die Methode muss `void`zurückgeben.  
  
-   Die Methode darf keine Parameter aufweisen.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Den Test erstellen und ausführen  
  
#### <a name="to-build-and-run-the-test"></a>So erstellen Sie den Test und führen ihn aus  
  
1.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**.  
  
     Wenn keine Fehler auftreten, wird das UnitTestExplorer-Fenster geöffnet, und in der Gruppe **Nicht ausgeführte Tests** wird **Debit_WithValidAmount_UpdatesBalance** aufgelistet. Wenn Test-Explorer nach einem erfolgreichen Build nicht angezeigt wird, wählen Sie im Menü **Testen** aus, wählen Sie **Fenster**aus, und wählen Sie dann  **Test-Explorer**aus.  
  
2.  Wählen Sie **Alle ausführen** aus, um den Test auszuführen. Während der Test ausgeführt wird, gibt die Statusleiste am oberen Fensterrand den aktuellen Status an. Am Ende des Testlaufs wird die Leiste grün, wenn alle Tests erfolgreich sind, oder rot, sofern bei einem der Tests ein Fehler auftritt.  
  
3.  In diesem Fall schlägt der Test fehl. Die Testmethode wird in die Gruppe **Tests mit Fehlern** aufgelistet. Wählen Sie die Methode im Test-Explorer aus, um die Details unten im Fenster anzuzeigen.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Den Code korrigieren und die Tests erneut ausführen  
 **Analysieren der Testergebnisse**  
  
 Das Testergebnis enthält eine Meldung mit der Fehlerbeschreibung. Bei der `AreEquals`-Methode wird in der Meldung angezeigt, was erwartet wurde (Parameter **Expected\<*XXX*>**) und was tatsächlich gefunden wurde (Parameter **Actual\<*YYY*>**). Erwartet wurde, dass das neue Guthaben geringer ist als das Startguthaben. Stattdessen hat es sich um den Betrag der Abbuchung vergrößert.  
  
 Eine erneute Prüfung des Debit-Codes zeigt, dass der Komponententest einen Fehler gefunden hat. Der Abbuchungsbetrag wird dem Kontoguthaben hinzugerechnet, anstatt davon abgezogen zu werden.  
  
 **Korrigieren des Fehlers**  
  
 Um den Fehler zu beheben, ersetzen Sie die Zeile  
  
```csharp  
m_balance += amount;  
```  
  
 durch  
  
```csharp  
m_balance -= amount;  
```  
  
 **Erneutes Ausführen des Tests**  
  
 Wählen Sie im Test-Explorer **Alle ausführen** aus, um den Test erneut auszuführen. Die Statusleiste wird grün, und der Test wird in die Gruppe **Bestandene Tests** verschoben.  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Den Code mit Komponententests verbessern  
 In diesem Abschnitt wird beschrieben, wie ein iterativer Prozess bestehend aus Analyse, Komponententestentwicklung und Umgestaltung helfen kann, die Robustheit und Effektivität des Produktionscodes zu verbessern.  
  
 **Analysieren der Probleme**  
  
 Nachdem Sie eine Testmethode erstellt haben, um zu bestätigen, dass ein gültiger Betrag ordnungsgemäß mit der `Debit` -Methode abgezogen wird, können Sie sich nun den verbleibenden Fällen in der ursprünglichen Analyse widmen:  
  
1.  Die Methode löst eine `ArgumentOutOfRangeException` aus, wenn der Abbuchungsbetrag größer ist als das Guthaben.  
  
2.  Außerdem löst sie eine `ArgumentOutOfRangeException` aus, wenn der Abbuchungsbetrag kleiner als null ist.  
  
 **Erstellen der Testmethoden**  
  
 Ein erster Versuch zum Erstellen einer Testmethode, um diese Probleme zu beheben, scheint vielversprechend:  
  
```csharp  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Sie verwenden das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> -Attribut, um zu bestätigen, dass die richtige Ausnahme ausgelöst wurde. Das Attribut führt zu einem Fehlschlag des Tests, es sei denn, eine `ArgumentOutOfRangeException` wird ausgelöst. Indem Sie den Test mit positiven und negativen `debitAmount` -Werten ausführen und anschließend die zu testende Methode vorübergehend so ändern, dass eine generische <xref:System.ApplicationException> ausgegeben wird, wenn der Betrag kleiner als null ist, können Sie veranschaulichen, dass der Test ordnungsgemäß funktioniert. Gehen Sie folgendermaßen vor, um das Verhalten zu testen, wenn der abzubuchende Betrag größer ist als das Guthaben:  
  
1.  Erstellen Sie eine neue Testmethode mit dem Namen `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2.  Kopieren Sie den Methodentext aus `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` in die neue Methode.  
  
3.  Legen Sie `debitAmount` auf eine Zahl größer als das Guthaben fest.  
  
 **Tests ausführen**  
  
 Indem Sie die beiden Methoden mit verschiedenen Werten für `debitAmount` ausführen, wird veranschaulicht, dass die Tests die verbleibenden Fälle angemessen behandeln. Durch Ausführung aller drei Tests bestätigen Sie, dass alle Fälle aus der ursprünglichen Analyse ordnungsgemäß abgedeckt werden.  
  
 **Fortführen der Analyse**  
  
 Die letzten beiden Testmethoden sind jedoch auch etwas beunruhigend. Sie können nicht sicher, welche Bedingung im getesteten Code ausgegeben wird, wenn einer der Tests ausgeführt wird. Daher wäre es hilfreich, die beiden Bedingungen auseinanderhalten zu können. Wenn Sie das Problem noch einmal genau durchgehen, werden Sie feststellen, dass das Vertrauen in die Tests erhöht wäre, wenn Sie wüssten, welche Bedingung missachtet wurde. Diese Information wäre sehr wahrscheinlich auch für den Produktionsmechanismus hilfreich, der die Ausnahme behandelt, wenn sie durch die zu testende Methode ausgelöst wird. Die angesprochenen Unsicherheiten könnten behoben werden, wenn beim Auslösen der Methode mehr Informationen generiert würden. Das `ExpectedException` -Attribut kann diese Informationen jedoch nicht bereitstellen.  
  
 Sehen Sie sich die zu testende Methode noch einmal an. Beide Bedingungsanweisungen verwenden einen `ArgumentOutOfRangeException` -Konstruktor, der den Namen des Arguments als Parameter übernimmt:  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 Über eine Suche in der MSDN Library finden Sie einen Konstruktor, der wesentlich ausführlichere Informationen in die Berichte schreibt. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` enthält den Namen des Arguments, den Argumentwert und eine benutzerdefinierte Meldung. Sie können die zu testende Methode so umgestalten, dass sie diesen Konstruktor verwendet. Besser noch, Sie können öffentlich verfügbare Typmitglieder verwenden, um die Fehler anzugeben.  
  
 **Umgestalten des zu testenden Codes**  
  
 Zunächst definieren Sie zwei Konstanten für die Fehlermeldungen im Klassengültigkeitsbereich:  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Dann ändern Sie die beiden Bedingungsanweisungen in der `Debit` -Methode:  
  
```csharp  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Umgestalten der Testmethoden**  
  
 Entfernen Sie zunächst aus der Testmethode das `ExpectedException` -Attribut. An dessen Stelle erfassen Sie die ausgelöste Ausnahme, und überprüfen Sie, dass sie in der richtigen Bedingungsanweisung ausgelöst wurde. Allerdings müssen Sie sich jetzt zwischen zwei Optionen entscheiden, um die restlichen Bedingungen zu überprüfen. In der `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` -Methode können Sie beispielsweise eine der folgenden Aktionen ausführen:  
  
-   Bestätigen Sie, dass die `ActualValue` -Eigenschaft der Ausnahme (der zweite Parameter des Konstruktors `ArgumentOutOfRangeException` ) größer als das Startguthaben ist. Diese Option erfordert, dass Sie die `ActualValue` -Eigenschaft der Ausnahme gegen die `beginningBalance` -Variable der Testmethode testen und dann überprüfen, dass `ActualValue` größer als null ist.  
  
-   Bestätigen Sie, dass die Meldung (der dritte Parameter des Konstruktors) die `DebitAmountExceedsBalanceMessage` umfasst, die in der `BankAccount` -Klasse definiert ist.  
  
 Die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> -Methode im Microsoft-Komponententest-Framework ermöglicht es, die zweite Option ohne die Berechnungen zu überprüfen, die bei der ersten Option erforderlich sind.  
  
 Ein zweiter Versuch des Überarbeitens von `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` kann folgendermaßen aussehen:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Erneut testen, umschreiben und neu analysieren**  
  
 Beim erneuten Testen der Testmethoden mit unterschiedlichen Werten stellen Sie Folgendes fest:  
  
1.  Wenn Sie mithilfe einer Assertion, bei der `debitAmount` größer als das Guthaben ist, den richtigen Fehler gefunden haben, wird die `Contains` -Assertion übergeben, die Ausnahme wird ignoriert, und dadurch ist die Testmethode erfolgreich. Dies ist das gewünschte Verhalten.  
  
2.  Wenn Sie einen `debitAmount` kleiner als null verwenden, schlägt die Assertion fehl, da die falsche Fehlermeldung zurückgegeben wird. Die Assertion schlägt auch fehl, wenn Sie an einem anderen Punkt im Testcodepfad der zu testenden Methode eine temporäre `ArgumentOutOfRange` -Ausnahme einführen. Auch das ist gut.  
  
3.  Wenn der `debitAmount` -Wert gültig ist (d. h. kleiner als das Guthaben, jedoch größer als null), wird keine Ausnahme erfasst, sodass die Assertion nie erfasst wird. Die Testmethode ist erfolgreich. Dies ist nicht gut, da bei der Testmethode ein Fehler auftreten soll, wenn keine Ausnahme ausgelöst wird.  
  
 Bei der dritten Erkenntnis handelt es sich um einen Fehler in der Testmethode. Um zu versuchen das Problem zu beheben, fügen Sie eine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> -Assertion am Ende der Testmethode hinzu, um den Fall abzudecken, in dem keine Ausnahme ausgelöst wird.  
  
 Ein erneuter Test zeigt jedoch, dass der Test jetzt fehlschlägt, wenn die richtige Ausnahme erfasst wird. Die Catch-Anweisung setzt die Ausnahme zurück, und die Methode wird weiter ausgeführt, bis sie an der neuen Assertion fehlschlägt. Um das neue Problem zu beheben, fügen Sie nach `return` eine `StringAssert`-Anweisung hinzu. Ein erneuter Test bestätigt, dass Sie alle Probleme gelöst haben. Die fertige Version von `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` sieht wie folgt aus:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 In diesem letzten Abschnitt hat die Verbesserung des Testcodes zu robusteren und informativeren Testmethoden geführt. Noch wichtiger ist jedoch, dass die zusätzliche Analyse auch zu besserem Code im zu testenden Projekt geführt hat.
