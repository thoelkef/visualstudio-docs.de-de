---
title: Isolieren von getestetem Code mithilfe von Microsoft Fakes | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a03c2e83-a41f-4854-bcf2-fcaa277a819d
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c272906aa402c124b98e6b9f5556d8c825ee963
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660480"
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Isolieren von getestetem Code mithilfe von Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Microsoft Fakes isolieren Sie den zu testenden Code, indem Sie andere Teile der Anwendung durch *Stupf* oder *Shims*ersetzen. Dabei handelt es sich um kurze Codes, die von den Tests kontrolliert werden. Wenn Sie den Code für die Tests isolieren, wissen Sie beim Fehlschlagen des Tests, dass die Ursache im isolierten Code und nicht an anderer Stelle liegt. Mit Stubs und Shims können Sie den Code auch dann testen, wenn andere Teile der Anwendung noch nicht funktionieren.

 Es gibt zwei Arten von Fakes:

- Ein [Stub](#stubs) tauscht eine Klasse gegen einen kleinen Ersatz aus, der die gleiche Schnittstelle implementiert.  Um Stubs verwenden zu können, müssen Sie die Anwendung so entwerfen, dass jede Komponente nur von Schnittstellen abhängt und nicht von anderen Komponenten. (Mit "Komponente" ist eine Klasse oder eine Gruppe von Klassen gemeint, die zusammen entworfen und aktualisiert werden und in der Regel in einer Assembly enthalten sind.)

- Ein [Shim](#shims) ändert den kompilierten Code der Anwendung zur Laufzeit, damit anstelle des angegebenen Methodenaufrufs der vom Test bereitgestellte Shimcode ausgeführt wird. Mit Shims können Aufrufe von Assemblys ersetzt werden, die nicht geändert werden können, wie etwa .NET-Assemblys.

  ![Fakes ersetzen andere Komponenten](../test/media/fakes-2.png "Fakes-2")

  **Anforderungen**

- Visual Studio Enterprise

## <a name="choosing-between-stub-and-shim-types"></a>Auswählen zwischen Stub- und Shim-Typen
 In der Regel lässt sich ein Visual Studio-Projekt als Komponente betrachten, da die Klassen gleichzeitig entwickelt und aktualisiert werden. Sie können Stubs und Shims für Aufrufe verwenden, die das Projekt an andere Projekte in der Projektmappe oder an andere Assemblys, auf die das Projekt verweist, richtet.

 Als allgemeine Richtlinie verwenden Sie Stubs für Aufrufe in der Visual Studio-Projektmappe und Shims für Aufrufe von anderen Assemblys, auf die verwiesen wird. Dies liegt daran, dass es in der eigenen Projektmappe ratsam ist, die Komponenten zu entkoppeln, indem Schnittstellen so definiert werden, dass Stubs erforderlich sind. Externe Assemblys wie "System.dll" hingegen werden in der Regel nicht mit separaten Schnittstellendefinitionen bereitgestellt, sodass Sie stattdessen Shims verwenden müssen.

 Weitere Überlegungen:

 **Leistung** Shims werden langsamer ausgeführt, da der Code zur Laufzeit neu geschrieben wird. Die Leistung von Stubs wird nicht auf diese Weise beeinträchtigt. Sie sind so schnell, wie es bei virtuellen Methoden möglich ist.

 **Statische Methoden, versiegelte Typen:** Sie können Stubs nur verwenden, um Schnittstellen zu implementieren. Daher können Stubtypen für folgende Methoden nicht verwendet werden: statische Methoden, nicht virtuelle Methoden, versiegelte virtuelle Methoden, Methoden in versiegelten Typen usw.

 **Interne Typen** Stubs und Shims können mit internen Typen verwendet werden, die verfügbar gemacht werden, indem das Assemblyattribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> verwendet wird.

 **Private Methoden** Shims können Aufrufe von privaten Methoden ersetzen, wenn alle Typen auf der Methodensignatur sichtbar sind. Stubs können nur sichtbare Methoden ersetzen.

 **Schnittstellen und abstrakte Methoden:** Stubs stellen Implementierungen von Schnittstellen und abstrakten Methoden bereit, die in den Tests verwendet werden können. Shims können Schnittstellen und abstrakte Methoden nicht instrumentieren, da sie über keine Methodentexte verfügen.

 Im Allgemeinen empfiehlt es sich, Stubtypen zu verwenden, um eine Isolierung von den Abhängigkeiten in der Codebase zu erzielen. Sie erreichen dies, indem Sie die Komponenten hinter den Schnittstellen ausblenden. Shimtypen können verwendet werden, um eine Isolierung von Drittanbieterkomponenten zu erzielen, die keine testfähige API bereitstellen.

## <a name="getting-started-with-stubs"></a><a name="stubs"></a> Erste Schritte mit Stubs
 Eine ausführlichere Beschreibung finden Sie unter [Verwenden von Stubs, um für Komponententests Teile der Anwendung voneinander zu trennen](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Einfügen von Schnittstellen**

     Um Stubs verwenden zu können, müssen Sie den zu testenden Code so schreiben, dass Klassen in einer anderen Komponente der Anwendung nicht explizit erwähnt werden. Mit "Komponente" sind eine oder mehrere Klassen gemeint, die zusammen entworfen und aktualisiert werden und in der Regel in einem Visual Studio-Projekt enthalten sind. Variablen und Parameter sollten über Schnittstellen deklariert werden, und Instanzen anderer Komponenten sollten durch eine Factory übergeben oder erstellt werden. Wenn StockFeed eine Klasse in einer anderen Komponente der Anwendung ist, wäre dies ein negatives Beispiel:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Definieren Sie stattdessen eine Schnittstelle, die von der anderen Komponente und auch durch einen Stub für Testzwecke implementiert werden kann:

    ```csharp
    public int GetContosoPrice(IStockFeed feed)
    { return feed.GetSharePrice("COOO"); }

    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Hinzufügen von Fakes-Assemblys**

    1. Erweitern Sie im Projektmappen-Explorer die Verweisliste des Testprojekts. Wenn Sie in Visual Basic arbeiten, müssen Sie **Alle Dateien anzeigen** auswählen, um die Verweisliste anzuzeigen.

    2. Wählen Sie den Verweis auf die Assembly aus, in der die Schnittstelle (beispielsweise IStockFeed) definiert ist. Klicken Sie im Kontextmenü des Verweises auf **Fakes-Assembly hinzufügen**.

    3. Generieren Sie die Projektmappe neu.

3. Erstellen Sie in den Tests Instanzen des Stubs, und stellen Sie Code für dessen Methoden bereit:

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

     Das Besondere hierbei ist die `StubIStockFeed`-Klasse. Der Microsoft Fakes-Mechanismus generiert für jede Schnittstelle in der Assembly, auf die verwiesen wird, eine Stubklasse. Der Name der Stubklasse wird vom Namen der Schnittstelle abgeleitet, wobei " `Fakes.Stub` " als Präfix und die Parametertyp Namen angehängt werden.

     Stubs werden auch für die Getter und Setter von Eigenschaften, für Ereignisse sowie für generische Methoden generiert. Weitere Informationen finden Sie unter [Verwenden von Stubs, um für Komponententests Teile der Anwendung voneinander zu trennen](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="getting-started-with-shims"></a><a name="shims"></a> Erste Schritte mit Shims
 (Eine ausführlichere Beschreibung finden Sie unter [Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

 Angenommen, die Komponente enthält Aufrufe von `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }

```

 Da die richtige Version ungünstigerweise bei jedem Aufruf einen anderen Wert zurückgibt, möchten Sie während der Tests ein Shim für die `Now`-Eigenschaft durchführen.

 Für Shims müssen Sie den Anwendungscode nicht ändern und ihn auch nicht auf bestimmte Weise schreiben.

1. **Hinzufügen von Fakes-Assemblys**

    Öffnen Sie im Projektmappen-Explorer die Verweise des Komponententestprojekts, und wählen Sie den Verweis auf die Assembly mit der Methode aus, für die Sie ein Fake durchführen möchten. In diesem Beispiel befindet sich die `DateTime`-Klasse in **System.dll**.  Um die Verweise in einem Visual Basic-Projekt anzuzeigen, wählen Sie **Alle Dateien anzeigen** aus.

    Wählen Sie **Fakes-Assembly hinzufügen** aus.

2. **Hinzufügen eines Shims zu einem ShimsContext**

   ```csharp
   [TestClass]
   public class TestClass1
   {
           [TestMethod]
           public void TestCurrentYear()
           {
               int fixedYear = 2000;

               // Shims can be used only in a ShimsContext:
               using (ShimsContext.Create())
               {
                 // Arrange:
                   // Shim DateTime.Now to return a fixed date:
                   System.Fakes.ShimDateTime.NowGet =
                   () =>
                   { return new DateTime(fixedYear, 1, 1); };

                   // Instantiate the component under test:
                   var componentUnderTest = new MyComponent();

                 // Act:
                   int year = componentUnderTest.GetTheCurrentYear();

                 // Assert:
                   // This will always be true if the component is working:
                   Assert.AreEqual(fixedYear, year);
               }
           }
   }

   ```

   ```vb
   <TestClass()> _
   Public Class TestClass1
       <TestMethod()> _
       Public Sub TestCurrentYear()
           Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
               Dim fixedYear As Integer = 2000
               ' Arrange:
               ' Detour DateTime.Now to return a fixed date:
               System.Fakes.ShimDateTime.NowGet = _
                   Function() As DateTime
                       Return New DateTime(fixedYear, 1, 1)
                   End Function

               ' Instantiate the component under test:
               Dim componentUnderTest = New MyComponent()
               ' Act:
               Dim year As Integer = componentUnderTest.GetTheCurrentYear
               ' Assert:
               ' This will always be true if the component is working:
               Assert.AreEqual(fixedYear, year)
           End Using
       End Sub
   End Class
   ```

    Shimklassennamen werden gebildet, indem dem ursprünglichen Typnamen `Fakes.Shim` vorangestellt wird. Parameternamen werden dem Methodennamen angefügt. (Sie müssen keine Assemblyverweise zu System.Fakes hinzufügen.)

   Im vorherigen Beispiel wird ein Shim für eine statische Methode verwendet. Um einen Shim für eine Instanzmethode zu verwenden, schreiben Sie `AllInstances` zwischen den Typnamen und den Methodennamen:

```
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

 (Es gibt keine Assembly „System.IO.Fakes“, auf die verwiesen werden kann. Der Namespace wird vom Shim-Erstellungsprozess generiert. Sie können jedoch „using“ oder „import“ auf die übliche Weise verwenden.)

 Sie können Shims auch für bestimmte Instanzen, für Konstruktoren und für Eigenschaften erstellen. Weitere Informationen finden Sie unter [Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Verwenden von Stubs, um für Komponententests Teile der Anwendung voneinander zu trennen](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

 [Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

 [Codegenerierung, Kompilierung und Benennungskonventionen in Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
