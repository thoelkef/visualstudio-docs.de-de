---
title: 'Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7dde910c5622a67ad002a085ace746ebc68e8857
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439231"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie eine in der Datei „app.config“ definierte Datenquelle für Unittests verwendet wird. Sie erfahren, wie die Datei „app.config“ zum Definieren einer Datenquelle erstellt wird, die von der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>-Klasse verwendet werden kann. Die folgenden Aufgaben werden in dieser exemplarischen Vorgehensweise vorgestellt:  
  
- Erstellen der Datei „app.config“  
  
- Definieren eines benutzerdefinierten Konfigurationsabschnitts  
  
- Definieren von Verbindungszeichenfolgen  
  
- Definieren der Datenquellen  
  
- Zugreifen auf die Datenquellen über die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>-Klasse  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um die exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:  
  
- Visual Studio Enterprise  
  
- Microsoft Access oder Microsoft Excel, um Daten für mindestens eine der Testmethoden bereitzustellen  
  
- Eine Visual Studio 2012-Projektmappe, die ein Testprojekt enthält.  
  
## <a name="create-the-appconfig-file"></a>Erstellen der Datei „App.config“  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>So fügen Sie dem Projekt die Datei „app.config“ hinzu  
  
1. Wenn für das Testprojekt bereits eine Datei „app.config“ vorhanden ist, fahren Sie mit [Definieren eines benutzerdefinierten Konfigurationabschnitts](#DefineCustomConfigurationSection) fort.  
  
2. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf das Testprojekt, wählen Sie **Hinzuzufügen**, und klicken Sie dann auf **Neues Element**.  
  
     Das Fenster **Neues Element hinzufügen** wird geöffnet.  
  
3. Wählen Sie die Vorlage **Anwendungskonfigurationsdatei** aus, und klicken Sie dann auf **Hinzufügen**.  
  
## <a name="DefineCustomConfigurationSection"></a> Definieren eines benutzerdefinierten Konfigurationsabschnitts  
 Sehen Sie sich die Datei „app.config“ an. Sie enthält mindestens die XML-Deklaration und ein Stammelement.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>So fügen Sie der Datei „app.config“ den benutzerdefinierten Konfigurationsabschnitt hinzu  
  
1. Das Stammelement von app.config sollte das `configuration`-Element sein. Erstellen Sie ein `configSections`-Element innerhalb des `configuration`-Elements. `configSections` sollte das erste Element in der Datei „app.config“ sein.  
  
2. Erstellen Sie innerhalb des `configSections`-Elements ein `section`-Element.  
  
3. Fügen Sie dem `section`-Element ein Attribut mit dem Namen `name` hinzu, und weisen Sie ihm den Wert `microsoft.visualstudio.testtools` zu. Fügen Sie ein weiteres Attribut mit dem Namen `type` hinzu, und weisen Sie diesem den Wert `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a` zu.  
  
   Das `section`-Element sollte wie folgt aussehen:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
> Der Assemblyname muss mit dem verwendeten Microsoft Visual Studio .NET-Frameworkbuild übereinstimmen. Legen Sie die Version auf 9.0.0.0 fest, wenn Sie Visual Studio .NET Framework 3.5 verwenden. Wenn Sie Visual Studio .NET Framework 2.0 verwenden, legen Sie die Version auf 8.0.0.0 fest.  
  
## <a name="define-connection-strings"></a>Definieren von Verbindungszeichenfolgen  
 Die Verbindungszeichenfolgen definieren anbieterspezifische Informationen für den Zugriff auf Datenquellen. In Konfigurationsdateien definierte Verbindungszeichenfolgen enthalten wiederverwendbare Datenanbieterinformationen für eine Anwendung. In diesem Abschnitt erstellen Sie zwei Verbindungszeichenfolgen, die von den im Abschnitt „Benutzerdefinierte Konfiguration“ definierten Datenquellen verwendet werden.  
  
#### <a name="to-define-connection-strings"></a>So definieren Sie Verbindungszeichenfolgen  
  
1. Erstellen Sie hinter dem `configSections`-Element ein `connectionStrings`-Element.  
  
2. Erstellen Sie innerhalb des `connectionStrings`-Elements zwei `add`-Elemente.  
  
3. Erstellen Sie im ersten `add`-Element die folgenden Attribute und Werte für eine Verbindung mit einer Microsoft Access-Datenbank:  
  
|Attribut|Werte|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 Erstellen Sie im zweiten `add`-Element die folgenden Attribute und Werte für eine Verbindung mit einem Microsoft Excel-Arbeitsblatt:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 Das `connectionStrings`-Element sollte wie folgt aussehen:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Definieren von Datenquellen  
 Der Abschnitt „Datenquellen“ enthält vier Attribute, die von der Test-Engine zum Abrufen von Daten aus einer Datenquelle verwendet werden.  
  
- `name` definiert die von <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> verwendete Identität, um die zu verwendende Datenquelle anzugeben.  
  
- `connectionString` bezeichnet die im vorhergehenden Abschnitt „Definieren von Verbindungszeichenfolgen“ erstellte Verbindungszeichenfolge.  
  
- `dataTableName` definiert die Tabelle oder das Blatt mit den im Test zu verwendenden Daten.  
  
- `dataAccessMethod` definiert die Technik für den Zugriff auf Datenwerte in der Datenquelle.  
  
  In diesem Abschnitt definieren Sie zwei Datenquellen für die Verwendung in einem Komponententest.  
  
#### <a name="to-define-data-sources"></a>So definieren Sie Datenquellen  
  
1. Erstellen Sie hinter dem `connectionStrings`-Element ein `microsoft.visualstudio.testtools`-Element. Dieser Abschnitt wurde im Abschnitt „Definieren eines benutzerdefinierten Konfigurationabschnitts“ erstellt.  
  
2. Erstellen Sie innerhalb des `microsoft.visualstudio.testtools`-Elements ein `dataSources`-Element.  
  
3. Erstellen Sie innerhalb des `dataSources`-Elements zwei `add`-Elemente.  
  
4. Erstellen Sie im ersten `add`-Element die folgenden Attribute und Werte für eine Microsoft Access-Datenquelle:  
  
|Attribut|Werte|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Erstellen Sie im zweiten `add`-Element die folgenden Attribute und Werte für eine Microsoft Excel-Datenquelle:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Das `microsoft.visualstudio.testtools`-Element sollte wie folgt aussehen:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Die endgültige Datei „app.config“ sollte in etwa wie folgt aussehen:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Erstellen eines Komponententests mit in der Datei „app.config“ definierten Datenquellen  
 Nachdem die Datei „app.config“ definiert ist, erstellen Sie einen Komponententest, für den Daten aus den in der Datei „app.config“ definierten Datenquellen verwendet werden. In diesem Abschnitt wird Folgendes beschrieben:  
  
- Erstellen der in der Datei „app.config“ angegebenen Datenquellen  
  
- Verwenden der Datenquellen in zwei Testmethoden, bei denen die Werte der beiden Datenquellen verglichen werden  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>So erstellen Sie eine Microsoft Access-Datenquelle  
  
1. Erstellen Sie eine Microsoft Access-Datenbank mit dem Namen `testdatasource.accdb`.  
  
2. Erstellen Sie in `testdatasource.accdb` eine Tabelle mit dem Namen `MyDataTable`.  
  
3. Erstellen Sie in `MyDataTable` zwei Felder mit dem Namen `Arg1` und `Arg2` mit dem Datentyp `Number`.  
  
4. Fügen Sie `MyDataTable` fünf Entitäten mit den folgenden Werten für `Arg1` und `Arg2` hinzu: (10,50), (3,2), (6,0), (0,8) und (12312,1000).  
  
5. Speichern und schließen Sie die Datenbank.  
  
6. Ändern Sie die Verbindungszeichenfolge, um auf den Speicherort der Datenbank zu verweisen. Ändern Sie den Wert von `Data Source`, um den Speicherort der Datenbank anzugeben.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>So erstellen Sie eine Microsoft Excel-Datenquelle  
  
1. Erstellen Sie ein Microsoft Excel-Arbeitsblatt mit dem Namen `data.xlsx`.  
  
2. Erstellen Sie ein Arbeitsblatt mit dem Namen `Sheet1`, falls dieses in `data.xlsx` noch nicht vorhanden ist.  
  
3. Erstellen Sie die zwei Spaltenüberschriften `Val1` und `Val2` in `Sheet1`.  
  
4. Fügen Sie `Sheet1` fünf Entitäten mit den folgenden Werten für `Val1` und `Val2` hinzu: (1,1), (2,2), (3,3), (4,4) und (5,0).  
  
5. Speichern und schließen Sie das Arbeitsblatt.  
  
6. Ändern Sie die Verbindungszeichenfolge, um auf den Speicherort des Arbeitsblattes zu verweisen. Ändern Sie den Wert von `dbq`, um den Speicherort des Arbeitsblattes anzugeben.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>So erstellen Sie einen Komponententest mit in der Datei „app.config“ definierten Datenquellen  
  
1. Fügen Sie dem Testprojekt einen Komponententest hinzu.  
  
     Weitere Informationen finden Sie unter [Erstellen und Ausführen von Komponententests für vorhandenen Code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2. Ersetzen Sie den automatisch generierten Inhalt des Komponententests durch folgenden Code:  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3. Sehen Sie sich die DataSource-Attribute an. Beachten Sie die Einstellungsnamen aus der Datei „app.config“.  
  
4. Erstellen Sie die Projektmappe, und führen Sie die Tests „MyTestMethod“ und „MyTestMethod2“ aus.  
  
> [!IMPORTANT]
> Stellen Sie Elemente wie Datenquellen bereit, damit sie für den Test im Bereitstellungsverzeichnis zugänglich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Komponententest Ihres Code](../test/unit-test-your-code.md)   
 [Erstellen und Ausführen von Komponententests für vorhandenen Code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Testen der Anwendung](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [How To: Erstellen eines datengesteuerten Komponententests](../test/how-to-create-a-data-driven-unit-test.md)
