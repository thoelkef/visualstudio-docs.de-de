---
title: Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 12
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 6dfb5758833d9ecda1a6ac378eb3f5069cc80561
ms.lasthandoff: 04/04/2017

---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Verwenden von Shims, um zu Komponententests die Anwendung von anderen Assemblys zu trennen
**Shimtypen** sind eine von zwei Technologien, die vom Microsoft Fakes-Framework verwendet werden, um das Isolieren von getesteten Komponenten von der Umgebung zu vereinfachen. Shims leiten Aufrufe an bestimmte Methoden für Code um, den Sie im Rahmen Ihres Tests schreiben. Viele Methoden geben abhängig von den externen Bedingungen unterschiedliche Ergebnisse zurück, aber ein Shim wird vom Test kontrolliert und kann bei jedem Aufruf konsistente Ergebnisse zurückgeben. Dies erleichtert das Schreiben von Tests erheblich.  
  
 Verwenden Sie Shims, um Ihren Code von Assemblys zu isolieren, die nicht Teil der Projektmappe sind. Um Komponenten Ihrer Projektmappe voneinander zu isolieren, wirr die Verwendung von Stubs empfohlen.  
  
 Eine Übersicht und eine Schnellstartanleitung finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
 Weitere Informationen finden Sie unter [Video (1h16): Testing Un-testable Code with Fakes in Visual Studio 2012 (Testen von nicht-testbarem Code mit Fakes in Visual Studio 2012)](http://go.microsoft.com/fwlink/?LinkId=261837).  
  
## <a name="in-this-topic"></a>In diesem Thema  
 In diesem Thema lernen Sie Folgendes:  
  
 [Beispiel: Der Y2K-Fehler](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Verwendung von Shims](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Fakes-Assemblys hinzufügen](#AddFakes)  
  
-   [ShimsContext verwenden](#ShimsContext)  
  
-   [Schreiben von Tests mit Shims](#WriteTests)  
  
 [Shims für verschiedene Arten von Methoden](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Statische Methoden](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Instanzmethoden (für alle Instanzen)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Instanzmethoden (für eine Laufzeitinstanz)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Konstruktoren](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Basismember](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Statische Konstruktoren](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Finalizer](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Private Methoden](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Binden von Schnittstellen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Ändern des Standardverhaltens](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Erkennen von Umgebungszugriffen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Parallelität](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Aufrufen der ursprüngliche Methode aus der Shimmethode](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Einschränkungen](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Beispiel: Der Y2K-Fehler  
 Betrachten wir eine Methode, die am 1. Januar 2000 eine Ausnahme auslöst:  
  
```c#  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Das Testen diese Methode ist besonders problematisch, da das Programm `DateTime.Now` benötigt, eine Methode, die von der Systemuhr des Computers abhängt, also eine von der Umgebung abhängige, nicht deterministische Methode ist. Darüber hinaus ist `DateTime.Now` eine statische Eigenschaft ist, sodass hier kein Stubtyp verwendet werden kann. Dieses Problem ist ein Symptom des Isolationsproblems bei Komponententests: Für Programme, die Datenbank-APIs direkt aufrufen, mit Webdiensten kommunizieren usw., sind Komponententests schwer auszuführen, da die Logik von der Umgebung abhängig ist.  
  
 In diesem Fall sollten Shimtypen verwendet werden. Shimtypen bieten einen Mechanismus, beliebige .NET-Methoden an einen benutzerdefinierten Delegaten umzuleiten. Shimtypen werden vom Fakes-Generator mit Code generiert und verwenden Delegaten, die als Shimtypen bezeichnet werden, um die neuen Methodenimplementierungen anzugeben.  
  
 Der folgende Test zeigt, wie der Shimtyp `ShimDateTime` verwendet wird, um eine benutzerdefinierte Implementierung von DateTime.Now bereitzustellen:  
  
```c#  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Verwendung von Shims  
  
###  <a name="AddFakes"></a> Fakes-Assemblys hinzufügen  
  
1.  Erweitern Sie im Projektmappen-Explorer die **Verweise** des Komponententestprojekts.  
  
    -   Wenn Sie mit Visual Basic arbeiten, müssen Sie auf der Symbolleiste des Projektmappen-Explorers **Alle Dateien anzeigen** auswählen, um die Verweisliste zu finden.  
  
2.  Wählen Sie die Assembly aus, in der die Klassendefinitionen enthalten sind, für die Sie Shims erstellen möchten. Wenn Sie z. B. einen Shim für DateTime erstellen möchten, wählen Sie „System.dll“ aus.  
  
3.  Wählen Sie im Kontextmenü **Fakes-Assembly hinzufügen** aus.  
  
###  <a name="ShimsContext"></a> ShimsContext verwenden  
 Wenn Sie Shimtypen in einem Komponententest-Framework verwenden, müssen Sie den Testcode mit einem `ShimsContext` umschließen, um die Lebensdauer der Shims zu steuern. Ohne diese Anforderung bleiben die Shims erhalten, bis die AppDomain heruntergefahren wird. Die einfachste Methode zum Erstellen eines `ShimsContext` besteht in der Verwendung der statischen `Create()`-Methode, wie im folgenden Code dargestellt:  
  
```c#  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Es ist wichtig, jeden Shimkontext ordnungsgemäß zu löschen. Als Faustregel gilt: Rufen Sie die `ShimsContext.Create`-Methode immer innerhalb einer `using`-Anweisung auf, um sicherzustellen, dass die registrierten Shims ordnungsgemäß gelöscht werden. Sie können beispielsweise einen Shim für eine Testmethode registrieren, die die `DateTime.Now`-Methode durch einen Delegaten ersetzt, der immer den 1. Januar 2000 zurückgibt. Wenn Sie vergessen, den registrierten Shim in der Testmethode zu löschen, gibt der Rest des Testlaufs immer den 1. Januar 2000 als DateTime.Now-Wert zurück. Dies kann überraschend und verwirrend sein.  
  
###  <a name="WriteShims"></a> Einen Test mit Shims schreiben  
 Fügen Sie in Ihrem Testcode eine *Umleitung* für die Methode ein, für die Sie ein Fake erstellen möchten. Zum Beispiel:  
  
```c#  
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
  
```vb#  
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
  
```c#  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Es kann ein Shim an `MyMethod` angefügt werden, der immer 5 zurückgibt:  
  
```c#  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Instanzmethoden (für alle Instanzen)  
 Auf ähnliche Weise wie bei statischen Methoden können auch für Instanzenmethoden Shims für alle Instanzen erstellt werden. Die Eigenschaften zum Anfügen dieser Shims werden in einem geschachtelten Typ mit dem Namen AllInstances platziert, um Verwechslungen zu vermeiden. Betrachten wir als Beispiel die `MyClass`-Klasse mit der `MyMethod`-Instanzmethode:  
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Sie können einen Shim an `MyMethod` anfügen, der unabhängig von der Instanz immer 5 zurückgibt:  
  
```c#  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 Die generierte Typstruktur von ShimMyClass sieht wie der folgende Code aus:  
  
```c#  
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
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Es können zwei Shimtypen von MyMethod eingerichtet werden, sodass der erste Typ immer 5 und der zweite immer 10 zurückgibt:  
  
```c#  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 Die generierte Typstruktur von ShimMyClass sieht wie der folgende Code aus:  
  
```c#  
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
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Der Shimtyp verfügt auch über eine implizite Konvertierung in den Typ, auf den ein Shim angewendet wurde, sodass Sie den Shimtyp in der Regel einfach unverändert verwenden können:  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Konstruktoren  
 Auch auf Konstruktoren können Shims anwendet werden, um Shimtypen an zukünftige Objekte anzufügen. Jeder Konstruktor wird als statische Constructor-Methode im Shimtyp verfügbar gemacht. Betrachten wir als Beispiel die `MyClass`-Klasse mit einem Konstruktor, der eine ganze Zahl verwendet:  
  
```c#  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Der Shimtyp des Konstruktors wird so eingerichtet, dass jede zukünftige Instanz -5 zurückgibt, wenn der Value-Getter aufgerufen wird, unabhängig vom Wert im Konstruktor:  
  
```c#  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Beachten Sie, dass jeder Shimtyp zwei Konstruktoren verfügbar macht. Der Standardkonstruktor sollte verwendet werden, wenn eine neue Instanz benötigt wird, während der Konstruktor, der eine Instanz mit angewendetem Shim als Argument verwendet, nur in Konstruktorshims verwendet werden sollte:  
  
```c#  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 Die generierte Typstruktur von ShimMyClass ähnelt dem folgenden Code:  
  
```c#  
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
  
```c#  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Ein Shim von `MyBase` kann durch Erstellen eines neuen `ShimMyBase`-Shims einrichtet werden:  
  
```c#  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Beachten Sie, dass der untergeordnete Shimtyp implizit in die untergeordnete Instanz konvertiert wird, wenn er als Parameter an den Konstruktor der Shimbasisklasse übergeben wird.  
  
 Die generierte Typstruktur von ShimMyChild und ShimMyBase ähnelt dem folgenden Code:  
  
```c#  
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
 Shimtypen machen eine statische `StaticConstructor`-Methode verfügbar, um einen Shim auf den statischen Konstruktors eines Typs anzuwenden. Da statische Konstruktoren nur einmal ausgeführt werden, müssen Sie sicherstellen, dass der Shim konfiguriert ist, bevor auf ein Member des Typs zugegriffen wird.  
  
###  <a name="BKMK_Finalizers"></a> Finalizer  
 Finalizer werden in Fakes nicht unterstützt.  
  
###  <a name="BKMK_Private_methods"></a> Private Methoden  
 Der Fakes-Codegenerator erstellt Shimeigenschaften für private Methoden, die nur sichtbare Typen in der Signatur aufweisen, d. h., für die Parametertypen und Rückgabetypen sichtbar sind.  
  
###  <a name="BKMK_Binding_interfaces"></a> Binden von Schnittstellen  
 Wenn ein Shimtyp eine Schnittstelle implementiert, gibt der Code-Generator eine Methode aus, die es ermöglicht, alle Member aus dieser Schnittstelle gleichzeitig zu binden.  
  
 Betrachten wir beispielsweise die `MyClass`-Klasse, die `IEnumerable<int>` implementiert:  
  
```c#  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Auf die Implementierungen von `IEnumerable<int>` in MyClass können Shims durch Aufrufen der Bind-Methode angewendet werden:  
  
```c#  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 Die generierte Typstruktur von ShimMyClass ähnelt dem folgenden Code:  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Ändern des Standardverhaltens  
 Jeder generierte Shimtyp enthält eine Instanz der `IShimBehavior`-Schnittstelle (durch die `ShimBase<T>.InstanceBehavior`-Eigenschaft). Das Verhalten wird immer dann verwendet, wenn ein Client einen Instanzmember aufruft, auf den nicht explizit ein Shim angewendet wurde.  
  
 Wenn das Verhalten nicht explizit festgelegt wurde, wird die Instanz verwendet, die von der statischen `ShimsBehaviors.Current`-Eigenschaft zurückgegeben wird. Standardmäßig gibt diese Eigenschaft ein Verhalten zurück, das eine `NotImplementedException`-Ausnahme auslöst.  
  
 Dieses Verhalten kann jederzeit durch Festlegen der `InstanceBehavior`-Eigenschaft für jede beliebige Shiminstanz geändert werden. Beispielsweise ändert der folgende Codeausschnitt den Shim in ein Verhalten, das keine Aktion ausführt oder den Standardwert des Rückgabetyps (default(T)) zurückgibt:   
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 Das Verhalten kann auch global für alle Shiminstanzen geändert werden, für die die `InstanceBehavior`-Eigenschaft nicht explizit durch Festlegung der `ShimsBehaviors.Current`-Eigenschaft festgelegt wurde:  
  
```c#  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Erkennen von Umgebungszugriffen  
 Es ist möglich, ein Verhalten an alle Member (einschließlich statische Methoden) eines bestimmten Typs anzufügen, indem der statischen `Behavior`-Eigenschaft des entsprechenden Shimtyps das `ShimsBehaviors.NotImplemented`-Verhalten zugewiesen wird:  
  
```c#  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Parallelität  
 Shimtypen gelten für alle Threads in der AppDomain und haben keine Threadaffinität. Dies ist wichtig, wenn Sie planen, einen Test Runner zu verwenden, der Nebenläufigkeit unterstützt: Tests unter Verwendung von Shimtypen können nicht gleichzeitig ausgeführt werden. Diese Eigenschaft wird von der Fakes-Laufzeit nicht durchgesetzt.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Aufrufen der ursprüngliche Methode aus der Shimmethode  
 Angenommen, der Text soll tatsächlich in das Dateisystem geschrieben werden, nachdem der an die Methode übergebene Dateiname überprüft wurde. In diesem Fall muss die ursprüngliche Methode in der Mitte der Shimmethode aufgerufen werden.  
  
 Der erste Ansatz zur Lösung dieses Problems besteht darin, einen Aufruf der ursprünglichen Methode mithilfe eines Delegaten und `ShimsContext.ExecuteWithoutShims()` zu umschließen, wie im folgenden Code gezeigt:  
  
```c#  
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
  
```c#  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter”);  
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
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Siehe auch  
 [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Peter Provost’s blog: Visual Studio 2012 Shims (Peter Provosts Blogs: Visual Studio 2012-Shims)](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Video (1h16): Testing Un-testable Code with Fakes in Visual Studio 2012 (Testen von nicht-testbarem Code mit Fakes in Visual Studio 2012)](http://go.microsoft.com/fwlink/?LinkId=261837)

