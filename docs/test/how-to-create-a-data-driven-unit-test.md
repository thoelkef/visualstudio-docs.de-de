---
title: "Gewusst wie: Erstellen eines datengesteuerten Komponententests | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "Komponententests, Ausführen"
  - "Komponententests, datengesteuert"
  - "Datengesteuerte Komponententests"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# Gewusst wie: Erstellen eines datengesteuerten Komponententests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden des Microsoft\-Komponententest\-Frameworks für verwalteten Code, können Sie eine Komponententestmethode installieren, um die Werte abzurufen, die in die Testmethode aus einer Datenquelle verwendet werden.  Die Methode wird nacheinander für jede Zeile in der Datenquelle ausgeführt, die es erleichtert, eine Vielzahl der Eingabe zu testen macht, indem Sie eine einzelne Methode beschrieben.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Die zu testende Methode](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Erstellen einer Datenquelle](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Hinzufügen eines TestContext-Objekts der Testklasse](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Schreiben der Testmethode](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Angeben des DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Verwenden TestContext.DataRow, um auf die Daten zuzugreifen](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Den Test und Anzeigen von Ergebnissen führen](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Das Erstellen eines datengesteuerten Komponententest umfasst die folgenden Schritte:  
  
1.  Erstellen einer Datenquelle, die die Werte enthält, die Sie in der Testmethode verwenden.  Die Datenquelle kann jeder Typ handeln, der auf dem Computer registriert ist, der den Test ausführt.  
  
2.  Fügen Sie einen privaten <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> Feld und eine öffentliche `TestContext`\-Eigenschaft der Testklasse hinzugefügt.  
  
3.  Erstellen Sie eine Komponententestmethode und fügen Sie ein <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>\-Attribut hinzu.  
  
4.  Verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Indexereigenschaft, um die Werte abzurufen, die Sie in einem Test verwenden.  
  
##  <a name="BKMK_The_method_under_test"></a> Die zu testende Methode  
 Als wir zum Beispiel an, dass wir erstellt haben:  
  
1.  Eine Projektmappe namens `MyBank`, die Transaktionen für andere Typen von Konten akzeptiert und verarbeitet.  
  
2.  Ein Projekt in `MyBank` namens `BankDb`, das die Transaktionen für Konten verwaltet.  
  
3.  Eine Klasse mit dem Namen `Maths` im `DbBank` \- Projekt, das die mathematischen Aufgaben ausführt, um sicherzustellen, dass jede der Transaktion Bank günstig ist.  
  
4.  Ein Komponententestprojekt namens `BankDbTests`, um das Verhalten der `BankDb` Komponente zu testen.  
  
5.  Eine vorhandene Klasse für Datenbankkomponententests namens `MathsTests`, um das Verhalten der `Maths`\-Klasse zu überprüfen.  
  
 Wir testen eine Methode in `Maths`, die zwei ganze Zahlen mit einer Schleife hinzugefügt:  
  
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
 Um die `AddIntegers`\-Methode zu testen, erstellen Sie eine Datenquelle mit einem Wertebereich für die Parameter und die Summe an denen Sie erwarten zurückgegeben werden.  In diesem Beispiel erstellen wir einen SQL Compact Datenbank mit dem Namen `MathsData` und eine Tabelle, die mit dem Namen `AddIntegersData` erstellt, die die folgenden Spaltennamen und die Werte enthält  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Hinzufügen eines TestContext\-Objekts der Testklasse  
 Das Komponententestframework erstellt ein `TestContext`\-Objekt, um die Datenquelleninformationen für einen datengesteuerten Test zu speichern.  Das Framework legt dann dieses Objekt als Wert der Eigenschaft `TestContext` fest, dass wir erstellen.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 In Ihrer Testmethode greifen Sie auf die Daten durch `DataRow` Indexereigenschaft `TestContext` zu.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Schreiben der Testmethode  
 Die Testmethode für `AddIntegers` ist recht einfach.  Für jede Zeile in der Datenquelle, rufen Sie `AddIntegers` mit den Spaltenwertn **FirstNumber** und **SecondNumber** als Parameter auf, und überprüfen Sie den Rückgabewert für Spaltenwert **Sum**:  
  
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
  
 Beachten Sie, dass die `Assert`\-Methode eine Meldung enthält, die die `x` und `y`\-Werte einer fehlgeschlagenen Iteration anzeigt.  Standardmäßig werden die überwachte Werte, `expected` und `actual`, bereit detailliert eines fehlgeschlagenen Tests enthalten.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Angeben des DataSourceAttribute  
 Das `DataSource`\-Attribut gibt die Verbindungszeichenfolge für die Datenquelle und den Namen der Tabelle, die Sie in der Testmethode verwenden.  Die genauen Informationen in der Verbindungszeichenfolge unterscheiden sich je nach verwendetem Datenquellentyp.  In diesem Beispiel haben wir eine SqlServerCe\-Datenbank.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Das DataSource\-Attribut hat drei Konstruktoren.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Ein Konstruktor mit einem Parameter verwendet Verbindungsinformationen, die in der Datei app.config für die Lösung gespeichert wird.  *dataSourceSettingsName* ist der Name des XML\-Elements in der Konfigurationsdatei, die die Verbindungsinformationen angibt.  
  
 Verwenden einer APP.CONFIG\-Datei ermöglicht es Ihnen, den Speicherort der Datenquelle zu ändern, ohne Änderungen am Komponententest selbst vorzunehmen.  Informationen darüber, wie die Datei app.config, finden Sie unter [Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md) erstellt und verwendet  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Der Konstruktor `DataSource` mit zwei Parametern gibt die Verbindungszeichenfolge für die Datenquelle und den Namen der Tabelle, die die Daten für Testmethode enthält.  
  
 Die Verbindungszeichenfolgen hängen vom Typ der Datenquelle ab, aber es sollte ein Anbieterelement enthalten, das dem invarianten Namen des Datenanbieters angibt.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Verwenden TestContext.DataRow, um auf die Daten zuzugreifen  
 Um auf die Daten in `AddIntegersData` zuzugreifen den gewünschten Thread, verwenden Sie den `TestContext.DataRow` Indexer.  `DataRow` ist ein <xref:System.Data.DataRow>\-Objekt, deshalb nennen wir Spaltenwerte von Index oder dem Spaltennamen ab.  Da die Werte als Objekte zurückgegeben werden, müssen wir sie in den entsprechenden Typ konvertieren:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Den Test und Anzeigen von Ergebnissen führen  
 Wenn Sie aufgehört haben, eine Testmethode zu schreiben, erstellen Sie das Testprojekt auf.  Die Testmethode wird im Test\-Explorer\-Fenster in der Gruppe **Nicht ausgeführte Tests**.  Wie Sie ausgeführt werden, Sie schreiben und überprüfen Sie die Tests, Test\-Explorer\-Anzeigen die Ergebnisse in Gruppen von **Tests mit Fehlern**, **Bestandene Tests** und **Nicht ausgeführte Tests**.  Sie können **Alle ausführen** auswählen, um alle Tests ausführen, oder wählen **Ausführen...**, um eine Teilmenge Tests auszuwählen, die ausgeführt werden.  
  
 Die Testergebnisleiste oben des Explorers wird als die Testläufe animiert.  Am Ende des Testlaufs, ist die Leiste Grün, wenn alle Tests erfolgreich bestanden wurden, Rot oder wenn einer der Tests fehlgeschlagen sind.  Eine Zusammenfassung des Testlaufs wird im Detailbereich unten im Test\-Explorer\-Fenster.  Wählen Sie einen Test aus, um die Details dieses Tests im unteren Bereich anzuzeigen.  
  
 Wenn Sie die `AddIntegers_FromDataSourceTest`\-Methode in unserem Beispiel ausgeführt haben, die Ergebnisleiste rot und die Testmethode wird auf den datengesteuerten Test **Tests mit Fehlern** Ein fehlschlägt wenn eine der durchgelaufenen Methoden aus der Datenquelle fehlschlägt verschoben.  Wenn Sie einen fehlerhaften datengesteuerten Test im Test\-Explorer\-Fenster auswählen, werden im Detailbereich die Ergebnisse jeder Iteration an, die vom Datenzeilenindex identifiziert wird.  In unserem Beispiel wird dies, dass der `AddIntegers` \- Algorithmus nicht negative Werte ordnungsgemäß behandelt.  
  
 Wenn die zu testende Methode und die Testwiederholung behoben wird, die Ergebnisleiste Grün und die Testmethode wird auf die Gruppe **Bestandene Tests** verschoben.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [How to: Create and Run a Unit Test](http://msdn.microsoft.com/de-de/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Komponententest für Code](../test/unit-test-your-code.md)   
 [Ausführen von Komponententests mit dem Test\-Explorer](../test/run-unit-tests-with-test-explorer.md)   
 [Schreiben von Komponententests für .NET Framework mit dem Microsoft\-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)