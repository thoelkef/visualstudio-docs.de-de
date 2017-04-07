---
title: 'Vorgehensweise: Erstellen eines datengesteuerten Komponententests | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 2eaf4aa44fdc1bec56bb513af54ea7db72dcf3db
ms.lasthandoff: 04/04/2017

---
# <a name="how-to-create-a-data-driven-unit-test"></a>Gewusst wie: Erstellen eines datengesteuerten Komponententests
Sie können mithilfe des Microsoft Komponententestframework für verwaltenden Code eine Komponententestmethode erstellen, um Werte zu abzurufen, die in einer Testmethode von einer Datenquelle verwendet wird. Die Methode wird nacheinander für jede Zeile in der Datenquelle ausgeführt, die mithilfe einer einzelnen Methode das Testen von einer Vielzahl von Eingaben vereinfacht.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Die zu testende Methode](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Erstellen einer Datenquelle](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Hinzufügen eines TestContext zu einer Testklasse](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Schreiben der Testmethode](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Angeben des DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Verwenden von TestContext.DataRow, um auf die Daten zuzugreifen](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Ausführen des Tests und Anzeigen der Ergebnisse](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Das Erstellen eines datengesteuerten Komponententests umfasst die folgenden Schritte:  
  
1.  Erstellen Sie eine Datenquelle, die die Werte enthält, die Sie in der Testmethode verwenden. Die Datenquelle kann jeder Typ sein, der auf dem Computer registriert ist, auf dem der Test ausgeführt wird.  
  
2.  Fügen Sie eine privates Feld „<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>“ sowie eine öffentliche Eigenschaft `TestContext` zu der Testklasse hinzu.  
  
3.  Erstellen Sie eine Komponententestmethode, und fügen Sie zu dieser Methode ein Attribut „<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>“ hinzu.  
  
4.  Verwenden Sie die Indexereigenschaft „<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A>“, um die Werte zu abzurufen, die Sie in einem Test verwenden.  
  
##  <a name="BKMK_The_method_under_test"></a> Die zu testende Methode  
 Nehmen wir zum Beispiel an, dass wir folgendes erstellt haben:  
  
1.  Eine Lösung mit dem Namen `MyBank`, die Transaktionen für verschiedene Kontenarten akzeptiert und verarbeitet.  
  
2.  Ein Projekt mit dem Namen `BankDb` in `MyBank`, das die Transaktionen für Konten verwaltet.  
  
3.  Eine Klasse mit dem Namen `Maths` im Projekt `DbBank`, die die mathematische Funktionen ausführt, um sicherzustellen, dass jede Transaktion für die Bank vorteilhaft ist.  
  
4.  Ein Komponententestprojekt mit dem Namen `BankDbTests`, um das Verhalten der Komponente `BankDb` zu testen.  
  
5.  Eine Komponentententestklasse mit dem Namen `MathsTests`, um das Verhalten von Klasse `Maths` zu testen.  
  
 Eine Methode in `Maths`, die zwei ganze Zahlen mithilfe einer Schleife hinzufügt, wird getestet:  
  
```  
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
  
##  <a name="BKMK_Creating_a_data_source"></a> Erstellen einer Datenquelle  
 Zu Testen der Methode `AddIntegers` wird eine Datenquelle erstellt, die einen Wertebereich für die Parameter und der Summe angibt, der zurückgegeben werden soll. In diesem Beispiel wird eine Datenbank „Sql.Compact“ mit dem Namen `MathsData` und eine Tabelle mit dem Namen `AddIntegersData` erstellt, die die folgenden Spaltennamen und -werte enthält  
  
|FirstNumber|SecondNumber|Summe|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class">Hinzufügen eines TestContext zu einer Testklasse</a>  
 Das Komponententestframework erstellt ein Objekt `TestContext`, um die Informationen der Datenquelle für einen datengesteuerten Test zu speichern. Das Framework legt anschließend dieses Objekt als Wert für die Eigenschaft `TestContext` fest, die wir erstellen.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 In Ihrer Testmethode greifen Sie auf die Daten durch die Indexereigenschaft `DataRow` des `TestContext` zu.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Schreiben der Testmethode  
 Die Testmethode für `AddIntegers` ist recht einfach. Für jede Zeile in der Datenquelle,wird `AddIntegers` mit den Spaltenwerten von **FirstNumber** und **SecondNumber** als Parameter abgerufen, und es wird der Rückgabewert mit dem Spaltenwert **Summe** verglichen:  
  
```  
  
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
  
 Beachten Sie, dass die Methode `Assert` eine Mitteilung enthält, die die Werter einer fehlerhaften Iteration `x` und `y` anzeigt. Die bestätigen Werte `expected` und `actual` sind bereits standardmäßig in den Details eines fehlgeschlagenen Tests enthalten.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Angeben des DataSourceAttribute  
 Das Attribut `DataSource` gibt die Verbindungszeichenfolge für die Datenquelle den Tabellennamen an, die Sie in der Testmethode verwenden. Die genaue Information in der Verbindungszeichenfolge ist unterschiedlich, je nachdem welche Datenquelle Sie verwenden. In diesem Beispiel wurde eine Datenbank „SqlServerCe“ verwendet.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Das DataSource-Attribut hat drei Konstruktoren.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Ein Konstruktor mit einem Parameter verwendet die Verbindungsinformationen, die in der app.config-Datei für die Lösung gespeichert ist. *dataSourceSettingsName* ist der Name des XML-Elements in der Config-Datei, das die Verbindungsinformationen angibt.  
  
 Eine app.config-Datei hilft Ihnen dabei, den Speicherort der Datenquelle zu ändern, ohne den Komponententest selbst zu ändern. Weitere Informationen zum Erstellen und Verwenden einer app.config-Datei finden Sie unter [Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Der Konstruktor `DataSource` mit zwei Parametern gibt die Verbindungszeichenfolge für die Datenquelle und den Tabellennamen an, die die Daten für die Testmethode enthält.  
  
 Die Verbindungszeichenfolgen hängen vom Typ der Datenquelle ab, er sollte jedoch ein Anbieterelement enthalten, das den unveränderlichen Namen des Datenanbieters angibt.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Verwenden von TestContext.DataRow, um auf die Daten zuzugreifen  
 Verwenden Sie den Indexer `AddIntegersData`, um auf die Daten in der Tabelle `TestContext.DataRow` zuzugreifen. `DataRow` ist ein Objekt „<xref:System.Data.DataRow>“. Dadurch werden Spaltenwerte anhand des Index oder der Spaltennamen abgerufen. Da die Werte als Objekte zurückgegeben werden, müssen sie in den entsprechenden Typ konvertiert werden:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Ausführen des Tests und Anzeigen der Ergebnisse  
 Wenn Sie mit dem Schreiben der Testmethode fertig sind, erstellen Sie das Testprojekt. Die Testmethode wird im Fenster „Test-Explorer“ in der Gruppe **Nicht ausgeführte Tests** angezeigt. Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests** sowie **Nicht ausgeführte Tests** angezeigt. Sie können zum Ausführen aller Tests **Alle ausführen** auswählen. Sie können auch **Ausführen von** auswählen, um eine Teilmenge der Tests auszuführen.  
  
 Während Ihr Test ausgeführt wird, wird die Testergebnisleiste im oberen Bereich des Explorers animiert. Am Ende des Testlaufs wird die Leiste grün, wenn alle Tests erfolgreich waren, oder rot, wenn einer der Tests fehlgeschlagen ist. Im Detailbereich unten im Fenster des Test-Explorers wird eine Zusammenfassung des Testlaufs angezeigt. Wählen Sie einen Test aus, um die Details dieses Tests im unteren Bereich anzuzeigen.  
  
 Wenn Sie die Methode `AddIntegers_FromDataSourceTest` in diesem Beispiel ausgeführt haben, wird die Ergebnisleiste rot und die Testmethode wird in **Fehlgeschlagene Tests** verschoben. Ein datengesteuerter Test scheitert, wenn jede der durchgelaufenen Methoden von der Datenquelle fehlschlägt. Wenn Sie einen fehlgeschlagenen datengesteuerten Test im Fenster des Test-Explorers auswählen, zeigt der Detailbereich das Ergebnis von jedem Durchlauf an, der vom Datenzeilenindex identifiziert wird. Es scheint, dass in diesem Beispiel der Algorithmus `AddIntegers` negative Werte nicht richtig behandelt.  
  
 Wenn die zu testende Methode korrigiert und den Test erneut ausgeführt wird, wird die Ergebnisleiste grün, und die Testmethode wird in die Gruppe **Bestandene Tests** verschoben.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Vorgehensweise: Erstellen eines Komponententestprojekts](http://msdn.microsoft.com/en-us/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Komponententest Ihres Code](../test/unit-test-your-code.md)   
 [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)   
 [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

