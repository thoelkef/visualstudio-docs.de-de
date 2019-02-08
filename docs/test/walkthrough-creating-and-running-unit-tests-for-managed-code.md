---
title: Erstellen und Ausführen von Komponententests für verwalteten Code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 12b232bf32be6802ccd82ecad647f2becc95addc
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484198"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code

Dieser Artikel führt Sie durch das Erstellen, Ausführen und Anpassen verschiedener Komponententests mithilfe des Microsoft-Komponententestframeworks für verwalteten Code und Visual Studio-**Test-Explorer**. Sie beginnen mit einem C#-Projekt in der Entwicklungsphase und erstellen Tests zur Codeüberprüfung. Anschließend führen Sie die Tests aus und überprüfen die Ergebnisse. Dann können Sie Änderungen am Projektcode vornehmen und die Tests erneut ausführen.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise wird das Microsoft-Komponententest-Framework für verwalteten Code verwendet. Der **Test-Explorer** kann außerdem Tests von Komponententestframeworks von Drittanbietern ausführen, die über Adapter für den **Test-Explorer** verfügen. Weitere Informationen finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).

Informationen zum Ausführen von Tests über die Befehlszeile finden Sie unter [Exemplarische Vorgehensweise: Befehlszeilenoptionen für VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Das Projekt "Bank". Weitere Informationen finden Sie unter [Beispielprojekt zum Erstellen von Komponententests](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Erstellen eines zu testenden Projekts

1. Öffnen Sie Visual Studio.

2. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Klicken Sie unter **Installierte Vorlagen**auf **Visual C#**.

4. Klicken Sie in der Liste der Anwendungstypen auf **Klassenbibliothek**.

5. Geben Sie **Bank** im Feld **Name** ein, und klicken Sie dann auf **OK**.

   Das neue Bank-Projekt wird erstellt und im **Projektmappen-Explorer** angezeigt, wobei der Code-Editor mit der Datei *Class1.cs* geöffnet wird.

   > [!NOTE]
   > Wenn die Datei *Class1.cs* nicht im Code-Editor geöffnet wird, doppelklicken Sie im **Projektmappen-Explorer** auf die Datei *Class1.cs*, um diese zu öffnen.

6. Kopieren Sie den Quellcode aus dem [Beispielprojekt zum Erstellen von Komponententests](../test/sample-project-for-creating-unit-tests.md), und ersetzen Sie den ursprünglichen Inhalt der Datei *Class1.cs* durch diesen kopierten Code.

7. Speichern Sie die Datei als *BankAccount.cs*.

8. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

Sie haben nun ein Projekt mit dem Namen Bank erstellt. Dieses Projekt enthält zu testenden Quellcode und Tools, mit denen der Quellcode getestet werden kann. Der Namespace für Bank (BankAccountNS) enthält die öffentliche BankAccount-Klasse, deren Methoden Sie im Folgenden testen sollen.

Die Tests in diesem Artikel beziehen sich auf die Debit-Methode. Die Debit-Methode wird aufgerufen, wenn von einem Konto Geld abgehoben wird. Die Methodendefinition lautet wie folgt:

```csharp
// Method to be tested.
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

## <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen

1. Klicken Sie im Menü **Datei** auf **Hinzufügen** > **Neues Projekt**.

   > [!TIP]
   > Es gibt mehrere andere Möglichkeiten zum Hinzufügen eines zusätzlichen Projekts zu einer vorhandenen Projektmappe. Sie können im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe klicken und anschließend **Hinzufügen** > **Neues Projekt** auswählen. Alternativ können Sie auf **Datei** > **Neu** > **Projekt** klicken und dann die Option **Zur Projektmappe hinzufügen** im Dialogfeld **Neues Projekt** auswählen:
   >
   > ![Option „Zur Projektmappe hinzufügen“ im Dialogfeld „Neues Projekt“](media/add-to-solution.png)

2. Erweitern Sie im Dialogfeld **Neues Projekt** erst die Option **Installiert** und dann die Option **Visual C#**, und klicken Sie anschließend auf **Test**.

3. Wählen Sie in der Liste der Vorlagen **Komponententestprojekt**aus.

4. Geben Sie im Feld **Name** `BankTests` ein, und klicken Sie dann auf die Schaltfläche **OK**.

   Das Projekt **BankTests** wird der Projektmappe **Bank** hinzugefügt.

5. Fügen Sie im Projekt **BankTests** einen Verweis auf die Projektmappe **Bank** ein.

   Klicken Sie im **Projektmappen-Explorer** im Projekt **BankTests** erst auf **Verweise** und dann im Kontextmenü auf **Verweis hinzufügen**.

6. Erweitern Sie im Dialogfeld **Verweis-Manager** den Eintrag **Projektmappe**, und überprüfen Sie das Element **Bank**.

## <a name="create-the-test-class"></a>Die Testklasse erstellen

Erstellen Sie eine Testklasse, um die `BankAccount`-Klasse zu überprüfen. Sie können die Datei *UnitTest1.cs* verwenden, die von der Projektvorlage generiert wurde; Datei und Klasse sollten jedoch einen aussagekräftigeren Namen erhalten. Sie können das in einem Schritt erledigen, indem Sie die Datei im **Projektmappen-Explorer** umbenennen.

### <a name="rename-a-class-file"></a>Umbenennen einer Klassendatei

Klicken Sie im **Projektmappen-Explorer** im BankTests-Projekt auf die Datei *UnitTest1.cs*. Klicken Sie im Kontextmenü auf die Option **Umbenennen**, und benennen Sie dann die Datei in *BankAccountTests.cs* um. Wenn Sie gefragt werden, ob Sie alle im Projekt enthaltenen Verweise in das Codeelement `UnitTest1` umbenennen möchten, klicken Sie auf **Ja**.

Dadurch wird der Name der Klasse in `BankAccountTests`geändert. Die Datei *BankAccountTests.cs* enthält nun den folgenden Code:

```csharp
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>Hinzufügen einer Using-Anweisung zum zu testenden Projekt

Auch der Klasse kann eine `using`-Anweisung hinzugefügt werden, damit Sie ohne vollqualifizierte Namen das zu testende Projekt aufrufen können. Fügen Sie am Anfang der Klassendatei Folgendes hinzu:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Testklassenanforderungen

Die Mindestanforderungen für eine Testklasse lauten wie folgt:

- Im Microsoft-Komponententest-Framework für verwalteten Code ist das `[TestClass]` -Attribut für jede Klasse erforderlich, die in Test-Explorer auszuführende Komponententestmethoden enthält.

- Jede Testmethode, die von Test-Explorer ausgeführt werden soll, muss über das `[TestMethod]`-Attribut verfügen.

Ein Komponententestprojekt kann auch über andere Klassen ohne das `[TestClass]` -Attribut verfügen, und Testklassen können andere Methoden ohne das `[TestMethod]` -Attribut aufweisen. Sie können diese anderen Klassen und Methoden in den Testmethoden verwenden.

## <a name="create-the-first-test-method"></a>Die erste Testmethode erstellen

In dieser Vorgehensweise schreiben Sie Komponententestmethoden, um das Verhalten der `Debit`-Methode der `BankAccount`-Klasse zu überprüfen. Die `Debit`-Methode wurde weiter oben in diesem Artikel bereits erläutert.

Es müssen mindestens drei Verhalten überprüft werden:

- Die Methode löst eine <xref:System.ArgumentOutOfRangeException> aus, wenn der Abbuchungsbetrag größer ist als das Guthaben.

- Außerdem löst sie eine <xref:System.ArgumentOutOfRangeException> aus, wenn der Abbuchungsbetrag kleiner als 0 (null) ist.

- Wenn der Abbuchungsbetrag gültig ist, zieht die Methode diesen vom Kontoguthaben ab.

> [!TIP]
> Sie können die Standardmethode `TestMethod1` löschen, da Sie sie für diese exemplarische Vorgehensweise nicht benötigen.

### <a name="to-create-a-test-method"></a>So erstellen Sie eine Testmethode

Im ersten Test überprüfen Sie, ob durch einen gültigen Betrag (kleiner als das Kontoguthaben und größer als null) der richtige Betrag vom Konto abgebucht wird. Fügen Sie dieser `BankAccountTests` -Klasse die folgende Methode hinzu.

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Die Methode ist ganz einfach: Sie richtet ein neues `BankAccount`-Objekt mit einem Startguthaben ein und bucht dann einen gültigen Betrag ab. Sie verwendet die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>-Methode, um zu überprüfen, ob das Guthaben zum Schluss den Erwartungen entspricht.

### <a name="test-method-requirements"></a>Testmethodenanforderungen

Eine Testmethode muss die folgenden Anforderungen erfüllen:

- Sie ist mit dem `[TestMethod]`-Attribut ausgestattet.

- Er gibt `void` zurück.

- Die darf keine Parameter aufweisen.

## <a name="build-and-run-the-test"></a>Den Test erstellen und ausführen

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**.

   Wenn keine Fehler auftreten, wird der **Test-Explorer** geöffnet, und in der Gruppe **Nicht ausgeführte Tests** wird **Debit_WithValidAmount_UpdatesBalance** aufgelistet.

   > [!TIP]
   > Wenn der **Test-Explorer** nach einem erfolgreichen Build nicht angezeigt wird, klicken Sie im Menü erst auf **Testen** und anschließend auf **Windows** > **Test-Explorer**.

2. Wählen Sie **Alle ausführen** aus, um den Test auszuführen. Während der Test ausgeführt wird, gibt die Statusleiste am oberen Fensterrand den aktuellen Status an. Am Ende des Testlaufs wird die Leiste grün, wenn alle Tests erfolgreich sind, oder rot, sofern bei einem der Tests ein Fehler auftritt.

3. In diesem Fall schlägt der Test fehl. Die Testmethode wird in die Gruppe **Tests mit Fehlern** verschoben. Wählen Sie die Methode im **Test-Explorer** aus, um die Details unten im Fenster anzuzeigen.

## <a name="fix-your-code-and-rerun-your-tests"></a>Den Code korrigieren und die Tests erneut ausführen

### <a name="analyze-the-test-results"></a>Analysieren der Testergebnisse

Das Testergebnis enthält eine Meldung mit der Fehlerbeschreibung. Für die `AreEqual`-Methode wird in der Meldung angezeigt, was erwartet wurde (Parameter **Expected\<*value*>**) und was tatsächlich gefunden wurde (Parameter **Actual\<*value*>**). Es wurde davon ausgegangen, dass sich das Guthaben verringern würde. Stattdessen hat es sich aber um den Betrag der Abhebung erhöht.

Beim Komponententest wurde ein Fehler festgestellt: Der Abbuchungsbetrag wird dem Kontoguthaben *hinzugerechnet*, anstatt davon *abgezogen* zu werden.

### <a name="correct-the-bug"></a>Korrigieren des Fehlers

Um den Fehler zu beheben, ersetzen Sie die Zeile:

```csharp
m_balance += amount;
```

Durch:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Erneutes Ausführen des Tests

Wählen Sie im **Test-Explorer** **Alle ausführen** aus, um den Test erneut auszuführen. Die Statusleiste wird grün, wenn der Test erfolgreich ausgeführt wurde, und der Test wird in die Gruppe **Bestandene Tests** verschoben.

## <a name="use-unit-tests-to-improve-your-code"></a>Den Code mit Komponententests verbessern

In diesem Abschnitt wird beschrieben, wie ein iterativer Prozess bestehend aus Analyse, Komponententestentwicklung und Umgestaltung helfen kann, die Robustheit und Effektivität des Produktionscodes zu verbessern.

### <a name="analyze-the-issues"></a>Analysieren der Probleme

Sie haben eine Testmethode erstellt, um zu bestätigen, dass zum jeweiligen Zeitpunkt in der `Debit`-Methode ein gültiger Betrag abgezogen wird. Überprüfen Sie jetzt, ob die Methode eine <xref:System.ArgumentOutOfRangeException> auslöst, wenn der Abbuchungsbetrag

- entweder höher als das Guthaben ist
- oder unter 0 liegt.

### <a name="create-the-test-methods"></a>Erstellen der Testmethoden

Erstellen Sie eine Testmethode, um die Richtigkeit zu bestätigen, wenn der Abbuchungsbetrag unter 0 liegt:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Verwenden Sie das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>-Attribut, um zu bestätigen, dass die richtige Ausnahme ausgelöst wurde. Das Attribut führt zu einem Fehlschlag des Tests, es sei denn, eine <xref:System.ArgumentOutOfRangeException> wird ausgelöst. Wenn Sie die zu testende Methode kurzzeitig ändern, um eine generischere <xref:System.ApplicationException> auszulösen, wenn der Abbuchungsbetrag unter 0 liegt, wird der Test richtig ausgeführt und schlägt fehl.

Gehen Sie folgendermaßen vor, um das Verhalten zu testen, wenn der abzubuchende Betrag höher ist als das Guthaben:

1. Erstellen Sie eine neue Testmethode mit dem Namen `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Kopieren Sie den Methodentext aus `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` in die neue Methode.

3. Legen Sie `debitAmount` auf eine Zahl größer als das Guthaben fest.

### <a name="run-the-tests"></a>Tests ausführen

Wenn die beiden Testmethoden ausgeführt werden, deutet dies darauf hin, dass der Test einwandfrei funktioniert.

### <a name="continue-the-analysis"></a>Fortführen der Analyse

Die letzten beiden Testmethoden stellen jedoch auch ein Problem dar. Sie können nicht sicher sagen, welche Bedingung der Methode, die getestet wird, die Ausnahme auslöst, wenn beide Methoden ausgeführt werden. Wenn man zwischen den beiden Bedingungen (einem negativen Abbuchungsbetrag und einem Betrag, der größer als das Guthaben ist) unterscheiden könnte, würde das die Tests zuverlässiger machen.

Sehen Sie sich die zu testende Methode noch einmal an: Beide Bedingungsanweisungen verwenden einen `ArgumentOutOfRangeException`-Konstruktor, der den Namen des Arguments als Parameter übernimmt:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Sie können einen Konstruktor verwenden, der weitaus ausführlichere Informationen übermittelt: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> umfasst den Namen des Arguments, den Argumentwert und eine benutzerdefinierte Meldung. Sie können die zu testende Methode so umgestalten, dass sie diesen Konstruktor verwendet. Besser noch, Sie können öffentlich verfügbare Typmitglieder verwenden, um die Fehler anzugeben.

### <a name="refactor-the-code-under-test"></a>Umgestalten des zu testenden Codes

Definieren Sie zunächst zwei Konstanten für die Fehlermeldungen im Klassengültigkeitsbereich. Fügen Sie diese in die zu testende Klasse (BankAccount) ein:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ändern Sie dann die beiden Bedingungsanweisungen in der `Debit`-Methode:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Umgestalten der Testmethoden

Entfernen Sie das Testmethodenattribut `ExpectedException`, erfassen Sie stattdessen die ausgelöste Ausnahme, und überprüfen Sie die zugewiesene Meldung. Mithilfe der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>-Methode können Sie zwei Zeichenfolgen miteinander vergleichen.

`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wird wie folgt formuliert:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Erneut testen, umschreiben und neu analysieren

Angenommen, es besteht ein Fehler in der Methode, die getestet wird, und die `Debit`-Methode löst keine <xref:System.ArgumentOutOfRangeException> aus. Dann muss keine korrekte Meldung mit der Ausnahme ausgegeben werden. Derzeit ist die Testmethode nicht für diesen Fall ausgelegt. Wenn der `debitAmount`-Wert gültig ist (d.h. kleiner als das Guthaben, jedoch größer als null), wird keine Ausnahme erfasst, sodass die Assertion nie reagiert. Die Testmethode ist trotzdem erfolgreich. Dies ist nicht gut, da bei der Testmethode ein Fehler auftreten soll, wenn keine Ausnahme ausgelöst wird.

Dabei handelt es sich um einen Fehler der Testmethode. Um das Problem zu beheben, fügen Sie eine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>-Assertion am Ende der Testmethode hinzu, um den Fall abzudecken, in dem keine Ausnahme ausgelöst wird.

Ein erneuter Test zeigt jedoch, dass der Test jetzt *fehlschlägt*, wenn die richtige Ausnahme erfasst wird. Der `catch`-Block fängt die Ausnahme zwar ab, aber die Methode wird weiterhin ausgeführt und schlägt bei der neuen <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>-Assertion fehl. Um dieses Problem zu beheben, fügen Sie nach `return` eine `StringAssert`-Anweisung zum Block `catch` hinzu. Wenn Sie den Test erneut ausführen, bestätigen Sie, dass Sie dieses Problem behoben haben. Die fertige Version von `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` sieht wie folgt aus:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Aufgrund der Verbesserungen des Testcodes wurden stabilere und informationsreichere Testmethoden erstellt. Aber noch wichtiger: es wurde auch der Code verbessert, der getestet werden soll.
