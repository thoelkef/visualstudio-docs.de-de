---
title: 'Vorgehensweise: Erstellen eines datengesteuerten Komponententests in Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 435e4d852464a74a1dc4f418ffa9906c1e22791a
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382580"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Gewusst wie: Erstellen eines datengesteuerten Komponententests

Sie können mithilfe des Microsoft Komponententestframework für verwaltenden Code eine Komponententestmethode erstellen, um Werte zu abzurufen, die in einer Testmethode von einer Datenquelle verwendet wird. Die Methode wird nacheinander für jede Zeile in der Datenquelle ausgeführt, die mithilfe einer einzelnen Methode das Testen von einer Vielzahl von Eingaben vereinfacht.

Das Erstellen eines datengesteuerten Komponententests umfasst die folgenden Schritte:

1.  Erstellen Sie eine Datenquelle, die die Werte enthält, die Sie in der Testmethode verwenden. Die Datenquelle kann jeder Typ sein, der auf dem Computer registriert ist, auf dem der Test ausgeführt wird.

2.  Fügen Sie der Testklasse ein privates <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>-Feld sowie eine öffentliche `TestContext`-Eigenschaft hinzu.

3.  Erstellen Sie eine Komponententestmethode, und fügen Sie ihr ein <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>-Attribut an.

4.  Verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A>-Indexereigenschaft, um die Werte abzurufen, die Sie in einem Test verwenden.

##  <a name="BKMK_The_method_under_test"></a> Die zu testende Methode

Nehmen wir zum Beispiel an, dass Sie über Folgendes verfügen:

1.  Eine Lösung mit dem Namen `MyBank`, die Transaktionen für verschiedene Kontenarten akzeptiert und verarbeitet.

2.  Ein Projekt mit dem Namen `BankDb` in `MyBank`, das die Transaktionen für Konten verwaltet.

3.  Eine Klasse mit dem Namen `Maths` im Projekt `DbBank`, die die mathematische Funktionen ausführt, um sicherzustellen, dass jede Transaktion für die Bank vorteilhaft ist.

4.  Ein Komponententestprojekt mit dem Namen `BankDbTests`, um das Verhalten der Komponente `BankDb` zu testen.

5.  Eine Komponentententestklasse mit dem Namen `MathsTests`, um das Verhalten von Klasse `Maths` zu testen.

Eine Methode in `Maths`, die zwei ganze Zahlen mithilfe einer Schleife hinzufügt, wird getestet:

```csharp
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

##  <a name="create-a-data-source"></a>Erstellen einer Datenquelle
 Erstellen Sie zum Testen der Methode `AddIntegers` eine Datenquelle, die einen Wertebereich für die Parameter und die Summe angibt, die zurückgegeben werden soll. In diesem Beispiel wird eine SQL Compact-Datenbank mit dem Namen `MathsData` und eine Tabelle mit dem Namen `AddIntegersData` erstellt, die die folgenden Spaltennamen und -werte enthält:

|FirstNumber|SecondNumber|Summe|
|-----------------|------------------|---------|
|0|1|1|
|1|1|2|
|2|-3|-1|

##  <a name="add-a-testcontext-to-the-test-class"></a>Hinzufügen eines TestContext zur Testklasse
 Das Komponententestframework erstellt ein Objekt `TestContext`, um die Informationen der Datenquelle für einen datengesteuerten Test zu speichern. Im Framework wird anschließend dieses Objekt als Wert für die von Ihnen erstellte Eigenschaft `TestContext` festgelegt.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

 In Ihrer Testmethode greifen Sie auf die Daten durch die Indexereigenschaft `DataRow` des `TestContext` zu.

##  <a name="write-the-test-method"></a>Schreiben der Testmethode
 Die Testmethode für `AddIntegers` ist recht einfach. Rufen Sie für jede Zeile in der Datenquelle `AddIntegers` mit den Spaltenwerten **FirstNumber** und **SecondNumber** als Parameter auf, und vergleichen Sie den Rückgabewert mit dem Spaltenwert **Summe**:

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});
}
```

Die Methode `Assert` enthält eine Nachricht, die die Werte `x` und `y` einer fehlerhaften Iteration anzeigt. Die bestätigen Werte `expected` und `actual` sind bereits standardmäßig in den Details eines fehlgeschlagenen Tests enthalten.

###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Angeben des DataSourceAttribute
 Das Attribut `DataSource` gibt die Verbindungszeichenfolge für die Datenquelle den Tabellennamen an, die Sie in der Testmethode verwenden. Die genaue Information in der Verbindungszeichenfolge ist unterschiedlich, je nachdem welche Datenquelle Sie verwenden. In diesem Beispiel wurde eine Datenbank „SqlServerCe“ verwendet.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Das DataSource-Attribut hat drei Konstruktoren.

```csharp
[DataSource(dataSourceSettingName)]
```

 Ein Konstruktor mit einem Parameter verwendet die Verbindungsinformationen, die in der *app.config*-Datei für die Projektmappe gespeichert sind. *dataSourceSettingsName* ist der Name des XML-Elements in der Config-Datei, das die Verbindungsinformationen angibt.

 Eine *app.config*-Datei hilft Ihnen dabei, den Speicherort der Datenquelle zu ändern, ohne den Komponententest selbst zu ändern. Weitere Informationen zum Erstellen und Verwenden einer *app.config*-Datei finden Sie unter [Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

```csharp
[DataSource(connectionString, tableName)]
```

 Der Konstruktor `DataSource` mit zwei Parametern gibt die Verbindungszeichenfolge für die Datenquelle und den Tabellennamen an, die die Daten für die Testmethode enthält.

 Die Verbindungszeichenfolgen hängen vom Typ der Datenquelle ab, er sollte jedoch ein Anbieterelement enthalten, das den unveränderlichen Namen des Datenanbieters angibt.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Verwenden von TestContext.DataRow für den Zugriff auf die Daten
 Verwenden Sie den Indexer `AddIntegersData`, um auf die Daten in der Tabelle `TestContext.DataRow` zuzugreifen. `DataRow` ist ein <xref:System.Data.DataRow>-Objekt. Dadurch werden Spaltenwerte anhand des Index oder der Spaltennamen abgerufen. Da die Werte als Objekte zurückgegeben werden, konvertieren Sie sie in den entsprechenden Typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

##  <a name="run-the-test-and-view-results"></a>Ausführen des Tests und Anzeigen von Ergebnissen
 Wenn Sie mit dem Schreiben der Testmethode fertig sind, erstellen Sie das Testprojekt. Die Testmethode wird im Fenster **Test-Explorer** in der Gruppe **Nicht ausgeführte Tests** angezeigt. Beim Ausführen, Schreiben und erneuten Ausführen Ihrer Tests werden die Ergebnisse vom **Test-Explorer** in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests** und **Nicht ausgeführte Tests** angezeigt. Sie können zum Ausführen aller Tests **Alle ausführen** auswählen. Sie können auch **Ausführen** auswählen, um eine Teilmenge der Tests auszuführen.

 Während Ihr Test ausgeführt wird, wird die Testergebnisleiste im oberen Bereich des Explorers animiert. Am Ende des Testlaufs wird die Leiste grün, wenn alle Tests erfolgreich waren, oder rot, wenn einer der Tests fehlgeschlagen ist. Im Detailbereich unten im Fenster des **Test-Explorers** wird eine Zusammenfassung des Testlaufs angezeigt. Wählen Sie einen Test aus, um die Details dieses Tests im unteren Bereich anzuzeigen.

 Wenn Sie die `AddIntegers_FromDataSourceTest`-Methode in unserem Beispiel ausgeführt haben, wird die Ergebnisleiste rot, und die Testmethode wird in die Gruppe **Fehlgeschlagene Tests** verschoben. Ein datengesteuerter Test schlägt fehl, wenn eine der durchlaufenen Methoden aus der Datenquelle fehlschlägt. Wenn Sie einen fehlgeschlagenen datengesteuerten Test im Fenster des **Test-Explorers** auswählen, wird im Detailbereich das Ergebnis von jedem Durchlauf angezeigt, der vom Datenzeilenindex identifiziert wird. Es scheint, dass in diesem Beispiel der Algorithmus `AddIntegers` negative Werte nicht richtig behandelt.

 Wenn die zu testende Methode korrigiert und den Test erneut ausgeführt wird, wird die Ergebnisleiste grün, und die Testmethode wird in die Gruppe **Bestandene Tests** verschoben.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)
- [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)