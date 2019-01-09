---
title: Verwenden von Shims zum Isolieren der Anwendung für Unittests
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 908a31a50b1af99f7123f292f250f9262a7da62e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947334"
---
# <a name="use-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Shims zum Isolieren der Anwendung für Komponententests in Visual Studio verwenden

**Shimtypen** sind eine von zwei Technologien, die vom Microsoft Fakes-Framework verwendet werden, um das Isolieren von getesteten Komponenten von der Umgebung zu vereinfachen. Shims leiten Aufrufe an bestimmte Methoden für Code um, den Sie im Rahmen Ihres Tests schreiben. Viele Methoden geben abhängig von den externen Bedingungen unterschiedliche Ergebnisse zurück, aber ein Shim wird vom Test kontrolliert und kann bei jedem Aufruf konsistente Ergebnisse zurückgeben. Dies erleichtert das Schreiben von Tests erheblich.

Verwenden Sie Shims, um Ihren Code von Assemblys zu isolieren, die nicht Teil der Projektmappe sind. Um Komponenten Ihrer Projektmappe voneinander zu isolieren, wirr die Verwendung von Stubs empfohlen.

Eine Übersicht und eine Schnellstartanleitung finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Anforderungen**

-   Visual Studio Enterprise
-   Ein .NET Framework-Projekt

> [!NOTE]
> .NET Standard-Projekte werden nicht unterstützt.

## <a name="example-the-y2k-bug"></a>Beispiel: Der Y2K-Fehler

Betrachten wir eine Methode, die am 1. Januar 2000 eine Ausnahme auslöst:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Das Testen dieser Methode ist problematisch, da das Programm `DateTime.Now` benötigt, eine Methode, die von der Systemuhr des Computers abhängt, also eine von der Umgebung abhängige, nicht deterministische Methode ist. Darüber hinaus ist `DateTime.Now` eine statische Eigenschaft, sodass hier kein Stub-Typ verwendet werden kann. Dieses Problem ist ein Symptom des Isolationsproblems bei Komponententests: Für Programme, die Datenbank-APIs direkt aufrufen, mit Webdiensten kommunizieren usw., sind Komponententests schwer auszuführen, da die Logik von der Umgebung abhängig ist.

In diesem Fall sollten Shimtypen verwendet werden. Shimtypen bieten einen Mechanismus zum Umleiten beliebiger .NET-Methoden an einen benutzerdefinierten Delegaten. Shimtypen werden vom Fakes-Generator mit Code generiert und verwenden Delegaten, die als Shimtypen bezeichnet werden, um die neuen Methodenimplementierungen anzugeben.

Der folgende Test zeigt, wie der Shimtyp `ShimDateTime` verwendet wird, um eine benutzerdefinierte Implementierung von DateTime.Now bereitzustellen:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

##  <a name="how-to-use-shims"></a>Verwendung von Shims

###  <a name="AddFakes"></a> Fakes-Assemblys hinzufügen

1.  Erweitern Sie im **Projektmappen-Explorer** die **Verweise** des Komponententestprojekts.

    -   Wenn Sie mit Visual Basic arbeiten, müssen Sie auf der Symbolleiste des **Projektmappen-Explorers** auf **Alle Dateien anzeigen** klicken, um den Knoten **Verweise** zu finden.

2.  Wählen Sie die Assembly aus, in der die Klassendefinitionen enthalten sind, für die Sie Shims erstellen möchten. Wenn Sie z.B. einen Shim für **DateTime** erstellen möchten, klicken Sie auf **System.dll**.

3.  Wählen Sie im Kontextmenü **Fakes-Assembly hinzufügen** aus.

###  <a name="ShimsContext"></a> ShimsContext verwenden

Wenn Sie Shimtypen in einem Komponententest-Framework verwenden, müssen Sie den Testcode mit einem `ShimsContext` umschließen, um die Lebensdauer der Shims zu steuern. Ohne diese Anforderung bleiben die Shims erhalten, bis die AppDomain heruntergefahren wird. Die einfachste Methode zum Erstellen eines `ShimsContext` besteht in der Verwendung der statischen `Create()`-Methode, wie im folgenden Code dargestellt:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Es ist wichtig, jeden Shimkontext ordnungsgemäß zu löschen. Als Faustregel gilt: Rufen Sie die `ShimsContext.Create`-Methode immer innerhalb einer `using`-Anweisung auf, um sicherzustellen, dass die registrierten Shims ordnungsgemäß gelöscht werden. Sie können beispielsweise einen Shim für eine Testmethode registrieren, die die `DateTime.Now`-Methode durch einen Delegaten ersetzt, der immer den 1. Januar 2000 zurückgibt. Wenn Sie vergessen, den registrierten Shim in der Testmethode zu löschen, gibt der Rest des Testlaufs immer den 1. Januar 2000 als DateTime.Now-Wert zurück. Dies mag Sie vielleicht überraschen und verwirren.

###  <a name="WriteShims"></a> Einen Test mit Shims schreiben

Fügen Sie in Ihrem Testcode eine *Umleitung* für die Methode ein, für die Sie ein Fake erstellen möchten. Beispiel:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
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

Shimklassennamen werden gebildet, indem dem ursprünglichen Typnamen `Fakes.Shim` vorangestellt wird.

Die Funktion von Shims besteht darin, *Umleitungen* in den Code der zu testenden Anwendung einzufügen. Bei jedem Aufruf der ursprünglichen Methode führt das Fakes-System einen Umleitung durch, sodass anstelle der tatsächlichen Methode der Shimcode aufgerufen wird.

Beachten Sie, dass Umleitungen zur Laufzeit erstellt und gelöscht werden. Sie müssen eine Umleitung immer innerhalb der Lebensdauer eines `ShimsContext` erstellen. Beim Löschen werden alle während der aktiven Phase des Kontexts erstellten Shims entfernt. Am besten funktioniert dies innerhalb einer `using`-Anweisung.

Möglicherweise wird eine Buildfehlermeldung ausgegeben, die besagt, dass der Fakes-Namespace nicht existiert. Dieser Fehler tritt manchmal auf, wenn andere Kompilierungsfehler vorliegen. Wenn Sie die anderen Fehler beheben, wird auch dieser nicht mehr angezeigt.

##  <a name="BKMK_Shim_basics"></a> Shims für verschiedene Arten von Methoden

Mit Shimtypen können Sie jede beliebige .NET-Methode durch Ihre eigenen Delegaten ersetzen, einschließlich statischer Methoden oder nicht virtueller Methoden.

###  <a name="BKMK_Static_methods"></a> Statische Methoden

Die Eigenschaften zum Anfügen von Shims an statische Methoden werden in einem Shimtyp platziert. Jede Eigenschaft verfügt über nur einen Setter, der zum Anfügen eines Delegaten an die Zielmethode verwendet werden kann. Betrachten wir als Beispiel die `MyClass`-Klasse mit einer statischen `MyMethod`-Methode:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Es kann ein Shim an `MyMethod` angefügt werden, der immer 5 zurückgibt:

```csharp
// unit test code
ShimMyClass.MyMethod = () =>5;
```

###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Instanzmethoden (für alle Instanzen)

Auf ähnliche Weise wie bei statischen Methoden können auch für Instanzenmethoden Shims für alle Instanzen erstellt werden. Die Eigenschaften zum Anfügen dieser Shims werden in einem geschachtelten Typ mit dem Namen AllInstances platziert, um Verwechslungen zu vermeiden. Betrachten wir als Beispiel die `MyClass`-Klasse mit der `MyMethod`-Instanzmethode:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Sie können einen Shim an `MyMethod` anfügen, der unabhängig von der Instanz immer 5 zurückgibt:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Die generierte Typstruktur von ShimMyClass sieht wie der folgende Code aus:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Beachten Sie, dass Fakes in diesem Fall die Laufzeitinstanz als erstes Argument des Delegaten übergibt.

###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Instanzmethoden (für eine Laufzeitinstanz)

Auf Instanzmethoden können auch von anderen Delegaten Shims angewendet werden, basierend auf dem Empfänger des Aufrufs. So kann die gleiche Instanzmethode unterschiedliche Verhaltensweisen pro Typinstanz haben. Die Eigenschaften zum Einrichten dieser Shims sind Instanzmethoden des Shimtyps selbst. Jeder instanziierte Shimtyp ist auch einer unformatierten Instanz eines Shimtyps zugeordnet.

Betrachten wir als Beispiel die `MyClass`-Klasse mit der `MyMethod`-Instanzmethode:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Es können zwei Shimtypen von MyMethod eingerichtet werden, sodass der erste Typ immer 5 und der zweite immer 10 zurückgibt:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Die generierte Typstruktur von ShimMyClass sieht wie der folgende Code aus:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

Auf die tatsächliche Shimtypinstanz kann über die Instance-Eigenschaft zugegriffen werden:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Der Shimtyp verfügt auch über eine implizite Konvertierung in den Typ, auf den ein Shim angewendet wurde, sodass Sie den Shimtyp in der Regel einfach unverändert verwenden können:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime
                         // instance
```

###  <a name="BKMK_Constructors"></a> Konstruktoren

Auch auf Konstruktoren können Shims anwendet werden, um Shimtypen an zukünftige Objekte anzufügen. Jeder Konstruktor wird als statische Constructor-Methode im Shimtyp verfügbar gemacht. Betrachten wir als Beispiel die `MyClass`-Klasse mit einem Konstruktor, der eine ganze Zahl verwendet:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Der Shimtyp des Konstruktors wird so eingerichtet, dass jede zukünftige Instanz -5 zurückgibt, wenn der Value-Getter aufgerufen wird, unabhängig vom Wert im Konstruktor:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Jeder Shimtyp macht zwei Konstruktoren verfügbar. Der Standardkonstruktor sollte verwendet werden, wenn eine neue Instanz benötigt wird, während der Konstruktor, der eine Instanz mit angewendetem Shim als Argument verwendet, nur in Konstruktorshims verwendet werden sollte:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Die generierte Typstruktur von ShimMyClass ähnelt dem folgenden Code:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

###  <a name="BKMK_Base_members"></a> Basismember

Auf die Shimeigenschaften von Basismembern kann zugegriffen werden, indem ein Shim für den Basistyp erstellt und die untergeordnete Instanz als Parameter an den Konstruktor der Shimbasisklasse übergeben wird.

Betrachten wir als Beispiel die `MyBase`-Klasse mit der `MyMethod`-Instanzmethode und dem Untertyp `MyChild`:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Ein Shim von `MyBase` kann durch Erstellen eines neuen `ShimMyBase`-Shims einrichtet werden:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Beachten Sie, dass der untergeordnete Shimtyp implizit in die untergeordnete Instanz konvertiert wird, wenn er als Parameter an den Konstruktor der Shimbasisklasse übergeben wird.

Die generierte Typstruktur von ShimMyChild und ShimMyBase ähnelt dem folgenden Code:

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

###  <a name="BKMK_Static_constructors"></a> Statische Konstruktoren

Shimtypen machen eine statische `StaticConstructor`-Methode verfügbar, um einen Shim auf den statischen Konstruktors eines Typs anzuwenden. Da statische Konstruktoren nur einmal ausgeführt werden, müssen Sie sicherstellen, dass der Shim konfiguriert ist, bevor auf einen Member des Typs zugegriffen wird.

###  <a name="BKMK_Finalizers"></a> Finalizer

Finalizer werden in Fakes nicht unterstützt.

###  <a name="BKMK_Private_methods"></a> Private Methoden

Der Fakes-Codegenerator erstellt Shimeigenschaften für private Methoden, die nur sichtbare Typen in der Signatur aufweisen, d.h. sichtbare Parameter- und Rückgabetypen.

###  <a name="BKMK_Binding_interfaces"></a> Binden von Schnittstellen

Wenn ein Shimtyp eine Schnittstelle implementiert, gibt der Code-Generator eine Methode aus, die es ermöglicht, alle Member aus dieser Schnittstelle gleichzeitig zu binden.

Betrachten wir beispielsweise die `MyClass`-Klasse, die `IEnumerable<int>` implementiert:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Auf die Implementierungen von `IEnumerable<int>` in MyClass können Shims durch Aufrufen der Bind-Methode angewendet werden:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Die generierte Typstruktur von ShimMyClass ähnelt dem folgenden Code:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

##  <a name="change-the-default-behavior"></a>Ändern des Standardverhaltens

Jeder generierte Shimtyp enthält eine Instanz der `IShimBehavior`-Schnittstelle (durch die `ShimBase<T>.InstanceBehavior`-Eigenschaft). Das Verhalten wird immer dann verwendet, wenn ein Client einen Instanzmember aufruft, auf den nicht explizit ein Shim angewendet wurde.

Wenn das Verhalten nicht explizit festgelegt wurde, wird die Instanz verwendet, die von der statischen `ShimsBehaviors.Current`-Eigenschaft zurückgegeben wird. Standardmäßig gibt diese Eigenschaft ein Verhalten zurück, das eine `NotImplementedException`-Ausnahme auslöst.

Dieses Verhalten kann jederzeit durch Festlegen der `InstanceBehavior`-Eigenschaft für jede beliebige Shiminstanz geändert werden. Beispielsweise ändert der folgende Codeausschnitt den Shim in ein Verhalten, das keine Aktion ausführt oder den Standardwert des Rückgabetyps (default(T)) zurückgibt: 

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Das Verhalten kann auch global für alle Shiminstanzen geändert werden, für die die `InstanceBehavior`-Eigenschaft nicht explizit durch Festlegung der `ShimsBehaviors.Current`-Eigenschaft festgelegt wurde:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current =
    ShimsBehaviors.DefaultValue;
```

##  <a name="detect-environment-accesses"></a>Erkennen von Umgebungszugriffen

Es ist möglich, ein Verhalten an alle Member (einschließlich statische Methoden) eines bestimmten Typs anzufügen, indem der statischen `Behavior`-Eigenschaft des entsprechenden Shimtyps das `ShimsBehaviors.NotImplemented`-Verhalten zugewiesen wird:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

##  <a name="BKMK_Concurrency"></a> Parallelität

Shim-Typen gelten für alle Threads in der AppDomain und haben keine Threadaffinität. Dies ist wichtig, wenn Sie planen, einen Test Runner zu verwenden, der Nebenläufigkeit unterstützt: Tests unter Verwendung von Shimtypen können nicht gleichzeitig ausgeführt werden. Diese Eigenschaft wird von der Fakes-Laufzeit nicht erzwungen.

##  <a name="call-the-original-method-from-the-shim-method"></a>Aufrufen der ursprüngliche Methode aus der Shimmethode

Angenommen, der Text soll tatsächlich in das Dateisystem geschrieben werden, nachdem der an die Methode übergebene Dateiname überprüft wurde. In diesem Fall muss die ursprüngliche Methode in der Mitte der Shimmethode aufgerufen werden.

Der erste Ansatz zur Lösung dieses Problems besteht darin, einen Aufruf der ursprünglichen Methode mithilfe eines Delegaten und `ShimsContext.ExecuteWithoutShims()` zu umschließen, wie im folgenden Code gezeigt:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Ein anderer Ansatz besteht darin, den Shim auf NULL festzulegen, die ursprüngliche Methode aufzurufen und den Shim wiederherzustellen.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

##  <a name="BKMK_Limitations"></a> Einschränkungen

Shims können nicht für alle Typen in der .NET-Basisklassenbibliothek **mscorlib** und **System** verwendet werden.

## <a name="see-also"></a>Siehe auch

- [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost's blog: Visual Studio 2012 shims (Blog von Peter Provost: Shims in Visual Studio 2012)](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Testing Un-testable Code with Fakes in Visual Studio 2012 (Testen von nicht-testbarem Code mithilfe von Fakes in Visual Studio 2012)](http://go.microsoft.com/fwlink/?LinkId=261837)
