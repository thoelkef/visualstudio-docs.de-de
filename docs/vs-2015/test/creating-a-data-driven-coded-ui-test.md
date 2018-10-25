---
title: Erstellen eines Coded UI-Testprojekts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: gewarren
manager: douge
ms.openlocfilehash: d3674d6ccbda89a2a3ee1de551587ba034ba51c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932623"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Erstellen eines datengesteuerten Tests der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um unterschiedliche Bedingungen zu testen, können Sie die Tests mit anderen Parameterwerten mehrfach ausführen. Datengesteuerte Tests für die codierte UI stellen dafür eine bequeme Möglichkeit dar. Sie definieren Parameterwerte in einer Datenquelle. Jede Zeile in der Datenquelle ist eine Iteration des Tests der codierten UI. Das Gesamtergebnis des Tests basiert auf dem Ergebnis für alle Iterationen. Wenn beispielsweise eine Testiteration fehlschlägt, ist das Gesamttestergebnis ein Fehler.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## <a name="create-a-data-driven-coded-ui-test"></a>Erstellen eines datengesteuerten Tests für die codierte UI  
 Dieses Beispiel erstellt einen Test für die codierte UI, der auf der Anwendung Windows-Rechner ausgeführt wird. Er addiert zwei Zahlen und verwendet eine Assertion, um zu überprüfen, ob die Summe richtig ist. Als Nächstes werden die Assertion und die Parameterwerte für die beiden Zahlen codiert, um datengesteuert zu sein und in einer Datei mit durch Trennzeichen getrennte Werte (CSV) gespeichert zu werden.  
  
#### <a name="step-1---create-a-coded-ui-test"></a>Schritt 1: Erstellen Sie einen Test für die codierte UI  
  
1.  Erstellen eines Projekts.  
  
     ![Erstellen eines Coded UI-Testprojekts](../test/media/cuit-datadriven.png "CUIT_dataDriven_")  
  
2.  Wählen Sie das Aufzeichnen der Aktionen aus.  
  
     ![Auswählen der Aufzeichnung der Aktionen](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")  
  
3.  Öffnen Sie die Rechner-Anwendung und starten Sie die Testaufzeichnung.  
  
     ![Aufzeichnen der Aktionen](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")  
  
4.  Fügen Sie 1 plus 2 hinzu, halten Sie die Aufzeichnung an und generieren Sie die Testmethode. Später werden wir die Werte dieser Benutzereingaben mit Werten aus einer Datendatei ersetzen.  
  
     ![Generieren der Testmethode](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")  
  
     Schließen Sie den Test-Generator. Die Methode wird dem Test hinzugefügt:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
  
    }  
    ```  
  
5.  Verwenden Sie die `AddNumbers()`-Methode, um sicherzustellen, dass der Test ausgeführt wird. Platzieren Sie den Cursor in der oben gezeigten Testmethode, öffnen Sie das Kontextmenü und wählen Sie **Tests ausführen** aus. (Tastenkombination: STRG + R, T).  
  
     Das Testergebnis, das anzeigt, ob der Test erfolgreich war oder fehlgeschlagen ist, wird im Fenster des Test-Explorers angezeigt. Zum Öffnen des Fensters des Test-Explorers wählen Sie aus dem Menü **TEST** die Option **Windows****Test-Explorer** aus.  
  
6.  Da eine Datenquelle auch zur Assertion von Parameterwerten verwendet werden kann, die vom Test zur Überprüfung erwarteter Werte verwendet wird, fügen wir eine Assertion hinzu, um zu überprüfen, dass die Summe der beiden Zahlen korrekt ist. Platzieren Sie den Cursor in der oben gezeigten Testmethode, öffnen Sie das Kontextmenü, wählen Sie **Code für den Coded UI-Test generieren** und anschließend **Coded UI-Test-Generator verwenden** aus.  
  
     Ordnen Sie das Text-Steuerelement im Rechner zu, der die Summe anzeigt.  
  
     ![Zuordnen des Benutzeroberflächen-Textsteuerelements](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")  
  
7.  Fügen Sie eine Assertion hinzu, die überprüft, ob der Wert der Summe korrekt ist. Wählen Sie die Eigenschaft **DisplayText**, die den Wert **3** hat, und wählen Sie anschließend **Assertion hinzufügen** aus. Verwenden Sie den Vergleichsoperator **AreEqual**, und stellen Sie sicher, dass der Vergleichswert **3** ist.  
  
     ![Konfigurieren der Assertion](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")  
  
8.  Nach dem Konfigurieren der Assertion generieren Sie erneut Code aus dem Generator. Dies erstellt eine neue Methode für die Validierung.  
  
     ![Erstellen der Assertionsmethode](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")  
  
     Da die Methode `ValidateSum` die Ergebnisse der Methode `AddNumbers` überprüft, verschieben Sie es an das Ende des Codeblocks.  
  
    ```csharp  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
9. Stellen Sie sicher, dass der Test mithilfe der Methode `ValidateSum()` ausgeführt wird. Platzieren Sie den Cursor in der oben gezeigten Testmethode, öffnen Sie das Kontextmenü und wählen Sie **Tests ausführen** aus. (Tastenkombination: STRG + R, T).  
  
     An diesem Punkt werden alle Parameterwerte in ihren Methoden als Konstanten definiert. Als Nächstes erstellen wir ein Dataset, um unseren Test datengesteuert zu machen.  
  
#### <a name="step-2---create-a-data-set"></a>Schritt 2: Erstellen eines Datensatzes  
  
1.  Fügen Sie dem DataDrivenSample-Projekt eine Textdatei mit dem Namen `data.csv` hinzu.  
  
     ![Hinzufügen einer CSV-Datei zum Projekt](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")  
  
2.  Füllen Sie die .csv-Datei mit den folgenden Daten aus:  
  
    |Num1|Num2|Summe|  
    |----------|----------|---------|  
    |3|4|7|  
    |5|6|11|  
    |6|8|14|  
  
     Nach dem Hinzufügen der Daten sollte die Datei wie folgt aussehen:  
  
     ![Füllen der CSV-Datei mit Daten](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")  
  
3.  Es ist wichtig,dass die .csv-Datei mit der richtigen Codierung gespeichert wird. Wählen Sie im Menü **DATEI** die Option **Erweiterte Speicheroptionen** und als Kodierung **Unicode (UTF-8 ohne Signatur) - Codepage 65001** aus.  
  
4.  Die .csv-Datei muss in das Ausgabeverzeichnis kopiert werden oder der Test kann nicht ausgeführt werden. Verwenden Sie das Fenster "Eigenschaften", um ihn zu kopieren.  
  
     ![Bereitstellen der CSV-Datei](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")  
  
     Da wir jetzt das Dataset erstellt haben, binden wir die Daten für den Test.  
  
#### <a name="step-3--add-data-source-binding"></a>Schritt 3: Hinzufügen der Datenquellenbindung  
  
1.  Um die Datenquelle zu binden, fügen Sie ein Attribut `DataSource` innerhalb des vorhandenen Attributs `[TestMethod]` hinzu, das sich direkt über der Testmethode befindet.  
  
    ```  
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
  
    ```  
  
     Die Datenquelle steht Ihnen jetzt für die Verwendung in dieser Testmethode zur Verfügung.  
  
    > [!TIP]
    >  Informationen dazu finden Sie unter [Datenquellen-Attribut-Beispiele](#CreateDataDrivenCUIT_QA_DataSourceAttributes) im Fragen-und-Antworten-Bereich für Beispiele, die andere Datenquellentypen wie XML, SQL Express und Excel verwenden.  
  
2.  Führen Sie den Test aus.  
  
     Beachten Sie, dass der Test über drei Iterationen ausgeführt wird. Der Grund ist, dass die gebundene Datenquelle drei Zeilen mit Daten enthält. Sie werden aber auch feststellen, dass der Test immer noch die konstanten Parameterwerte verwendet und jedes Mal 1 + 2 mit einer Summe von 3 hinzufügen wird.  
  
     Als Nächstes konfigurieren wird den Test, um die Werte in der Datenquelldatei zu verwenden.  
  
#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>Schritt 4: Verwenden der Daten im Test der codierten UI  
  
1.  Fügen Sie `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` am Anfang der Datei CodedUITest.cs ein:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text.RegularExpressions;  
    using System.Windows.Input;  
    using System.Windows.Forms;  
    using System.Drawing;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    ```  
  
2.  Fügen Sie `TestContext.DataRow[]` in der Methode `CodedUITestMethod1()` ein, damit die Werte aus der Datenquelle angewendet werden. Die Datenquellenwerten überschreiben die Konstanten, die den UIMap-Steuerelemente mit den Steuerelementen `SearchProperties` zugewiesen sind:  
  
    ```  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
     Verwenden Sie den Editor für den Test der codierten UI, um herauszufinden, zu welchen Sucheigenschaften die Daten codieren werden sollen.  
  
    -   Öffnen Sie die UIMap.uitest-Datei.  
  
         ![Öffnen des Coded UI-Test-Editors](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")  
  
    -   Wählen Sie die UI-Aktion aus und beobachten Sie die entsprechende Zuordnung des UI-Steuerelements. Beachten Sie die Zuordnung des Codes, wie z. B. `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.  
  
         ![Verwenden des Coded UI-Test-Editors zur Unterstützung mit Code](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")  
  
    -   Öffnen Sie im Eigenschaftenfenster die Auswahl **Sucheigenschaften**. Der Wert der Sucheigenschaften **Name** ist der Wert, der im Code unter Verwendung der Datenquelle manipuliert wird. Angenommen, den `SearchProperties` werden die Werte in der ersten Spalte jeder Datenzeile zugewiesen: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();` Bei den drei Iterationen dieses Tests ändert sich der Wert **Name** für die Sucheigenschaft auf 3, dann auf 5 und zuletzt auf 6.  
  
         ![Verwenden der Sucheigenschaften zur Unterstützung der Programmierung](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")  
  
3.  Speichern Sie die Projektmappe.  
  
#### <a name="step-5--run-the-data-driven-test"></a>Schritt 5: Ausführen des datengesteuerten Tests  
  
1. Überprüfen Sie durch erneutes Ausführen des Tests, dass der Test jetzt datengesteuerte ist.  
  
    Der Testlauf über die drei Iterationen sollte unter Verwendung der Werte in der CSV-Datei angezeigt werden. Die Validierung sollte auch funktionieren und der Test sollte im Test-Explorer als erfolgreich angezeigt werden.  
  
   **Empfehlungen**  
  
   Weitere Informationen finden Sie unter [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 2: Unit Testing: Testing the Inside (Tests für Continuous Delivery mit Visual Studio 2012 – Kapitel 2: Komponententests: Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188) und [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 5: Automating System Tests (Tests für Continuous Delivery mit Visual Studio 2012 – Kapitel 5: Automatisierte Systemtests)](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="q--a"></a>Fragen und Antworten  
  
###  <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>Was bedeuten die Attribute für Datenquellen für andere Datenquellentypen wie SQL Express oder XML?  
 Sie können die Beispiel-Datenquellenzeichenfolgen in der folgenden Tabelle verwenden, indem Sie diese in Ihren Code kopieren und die erforderlichen Anpassungen vornehmen.  
  
 **Arten von Datenquellen und Attribute**  
  
-   CSV  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`  
  
-   Excel  
  
     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`  
  
-   Testfall in Team Foundation Server  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`  
  
-   XML  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`  
  
-   SQL Express  
  
     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`  
  
### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>F: Kann ich datengesteuerte Tests für meine Windows Phone-App verwenden?  
 **A:** Ja. Datengesteuerte Tests der programmierten UI für Windows Phone werden mithilfe des Attributs DataRow für eine Testmethode definiert. Im folgenden Beispiel verwenden x und y die Werte 1 und 2 für die erste und -1 und -2 für die zweite Iteration des Tests.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>F: Warum kann ich den Code in der Datei "UIMap.Designer" nicht ändern?  
 **A**: Alle Codeänderungen, die Sie an der Datei „UIMapDesigner.cs“ vornehmen, werden jedes Mal überschrieben, wenn Sie Code mit dem UIMap – Coded UI-Test-Generator generieren. In diesem Beispiel und in den meisten Fällen können die Änderungen am Code, die benötigt werden, um einen Test mit Verwendung einer Datenquelle freizugeben, zu einer Quelldatei für den Test verwendet werden (das ist CodedUITest1.cs).  
  
 Wenn Sie eine aufgezeichnete Methode ändern müssen, müssen Sie sie in die UIMap.cs-Datei kopieren und umbenennen. Die Datei "UIMap.cs" kann verwendet werden, um Methoden und Eigenschaften in der Datei "UIMapDesigner.cs" zu überschreiben. Sie müssen den Verweis auf die ursprüngliche Methode in der Datei "Coded UITest.cs" entfernen und ihn durch den umbenannten Methodennamen ersetzen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Empfohlene Vorgehensweisen für Tests der codierten UI](../test/best-practices-for-coded-ui-tests.md)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



