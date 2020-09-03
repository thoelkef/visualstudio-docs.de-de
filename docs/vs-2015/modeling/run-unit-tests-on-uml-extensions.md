---
title: Ausführen von Komponententests für UML-Erweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f634f028dafea3260a69537893513f13cc0ebe83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74292536"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Ausführen von Komponententests auf UML-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Damit Ihr Code auch nach nachfolgenden Änderungen stabil bleibt, wird empfohlen, dass Sie Komponententests erstellen und diese im Rahmen des normalen Buildprozesses ausführen. Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md). Zum Einrichten von Tests für Visual Studio-Modellierungserweiterungen sind einige wichtige Informationen erforderlich. Zusammenfassung:

- [Einrichten eines Komponententests für VSIX-Erweiterungen](#Host)

   Ausführen von Tests mit dem VS IDE-Hostadapter Stellen Sie jeder Testmethode `[HostType("VS IDE")]`als Präfix voran. Dieser Hostadapter startet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , wenn Ihre Tests ausgeführt werden.

- [Zugreifen auf DTE und Modellspeicher](#DTE)

   In der Regel müssen Sie ein Modell und seine Diagramme öffnen und dann während der Testinitialisierung auf `IModelStore` zugreifen.

- [Öffnen von Modelldiagrammen](#Opening)

   Sie können `EnvDTE.ProjectItem` in und von `IDiagramContext`umwandeln.

- [Durchführen von Änderungen im UI-Thread](#UiThread)

   Tests, die Änderungen am Modellspeicher vornehmen, müssen im UI-Thread durchgeführt werden. Sie können dazu `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` verwenden.

- [Testen von Befehlen, Gesten und anderen MEF-Komponenten](#MEF)

   Zum Testen von MEF-Komponenten müssen Sie deren importierten Eigenschaften explizit mit Werten verbinden.

  Diese Punkte werden in den folgenden Abschnitten ausgearbeitet.

## <a name="requirements"></a>Anforderungen
 Siehe [Anforderungen](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="setting-up-a-unit-test-for-vsix-extensions"></a><a name="Host"></a> Einrichten eines Komponententests für VSIX-Erweiterungen
 Die Methoden in Ihren Modellierungserweiterungen funktionieren normalerweise mit einem Diagramm, das bereits geöffnet ist. Die Methoden verwenden MEF-Importe wie **IDiagramContext** und **ILinkedUndoContext**. Dieser Kontext muss von Ihrer Testumgebung eingerichtet werden, bevor Sie die Tests ausführen.

#### <a name="to-set-up-a-unit-test-that-executes-in-vsprvs"></a>So richten Sie einen Komponententest ein, der in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird

1. Erstellen Sie ein UML-Erweiterungsprojekt sowie das Komponententestprojekt.

    1. **Ein UML-Erweiterungsprojekt.** Normalerweise erstellen Sie dies mithilfe der Befehls-, Gesten- oder Validierungsprojektvorlagen. Informationen hierzu finden Sie beispielsweise [unter Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Ein Komponententestprojekt.** Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md).

2. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Lösung, die ein UML-Modellierungsprojekt enthält. Sie werden diese Lösung als Ausgangszustand für Ihre Tests verwenden. Sie sollte von der Lösung getrennt sein, in der Sie die UML-Erweiterung und ihre Komponententests erstellen. Weitere Informationen finden Sie unter [Erstellen von UML-Modellierungs Projekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **Im UML-Erweiterungsprojekt**bearbeiten Sie die CSPROJ-Datei als Text und stellen sicher, dass die folgenden Zeilen den Wert `true`anzeigen:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     Wählen Sie im Kontextmenü des Projektmappen-Explorers die Option **Projekt entladen** , um die CSPROJ-Datei als Text zu bearbeiten. Wählen Sie dann **Bearbeiten….csproj**aus. Nachdem Sie den Text bearbeitet haben, wählen Sie **Projekt erneut laden**aus.

4. Fügen Sie in Ihrem UML-Erweiterungsprojekt die folgende Zeile zu **Properties\AssemblyInfo.cs**hinzu. Dadurch können die Komponententests auf die Methoden zugreifen, die Sie testen möchten:

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **Fügen Sie im Komponententestprojekt**die folgenden Assemblyverweise hinzu:

    - *Ihr UML-Erweiterungsprojekt*

    - **EnvDTE.dll**

    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**

    - **Microsoft.VisualStudio.Uml.Interfaces.dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. Stellen Sie jeder Testmethode, einschließlich der Initialisierungsmethoden, das `[HostType("VS IDE")]` -Attribut als Präfix voran.

     Dadurch wird sichergestellt, dass der Test in einer experimentellen Instanz von Visual Studio ausgeführt wird.

## <a name="accessing-dte-and-modelstore"></a><a name="DTE"></a> Zugreifen auf DTE und Model Store
 Erstellen Sie eine Methode zum Öffnen eines Modellierungsprojekts in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In der Regel öffnen Sie eine Lösung während eines Testlaufs nur einmal. Damit die Methode nur einmal ausgeführt wird, stellen Sie das `[AssemblyInitialize]` -Attribut der Methode als Präfix voran. Vergessen Sie nicht, dass auch das [HostType("VS IDE")]-Attribut für jede Testmethode erforderlich ist.  Beispiel:

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 Wenn eine Instanz von <xref:EnvDTE.Project?displayProperty=fullName> ein Modellierungsprojekt darstellt, können Sie Sie in und aus [IModelingProject](/previous-versions/ee789474(v=vs.140))umwandeln.

## <a name="opening-a-model-diagram"></a><a name="Opening"></a> Öffnen eines Modell Diagramms
 Für jeden Test oder jede Testklasse möchten Sie normalerweise mit einem geöffneten Diagramm arbeiten. Das folgende Beispiel verwendet das `[ClassInitialize]` -Attribut, das diese Methode vor anderen Methoden in dieser Testklasse ausführt. Vergessen Sie wiederum nicht, dass auch das [HostType("VS IDE")]-Attribut für die einzelnen Testmethoden erforderlich ist.

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="perform-model-changes-in-the-ui-thread"></a><a name="UiThread"></a> Durchführen von Modelländerungen im UI-Thread
 Wenn Ihre Tests oder die getesteten Methoden Änderungen am Modellspeicher vornehmen, müssen Sie sie im Benutzeroberflächenthread ausführen. Wenn Sie dies ignorieren, wird möglicherweise eine `AccessViolationException`angezeigt. Schließen Sie den Code der Testmethode in einen Aufruf zum Aufrufen von Folgendem ein:

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="testing-command-gesture-and-other-mef-components"></a><a name="MEF"></a> Testen von Befehls-, Gesten-und anderen MEF-Komponenten
 MEF-Komponenten verwenden Eigenschaftsdeklarationen, die über das `[Import]` -Attribut verfügen und deren Werte von ihren Hosts festgelegt werden. Im Allgemeinen umfassen diese Eigenschaften "IDiagramContext", "SVsServiceProvider" und "ILinkedUndoContext". Wenn Sie eine Methode testen, die eine dieser Eigenschaften verwendet, müssen Sie deren Werte festlegen, bevor Sie die getestete Methode ausführen. Wenn Sie z. B. eine Befehlserweiterung erstellt haben, die dem folgenden Code ähnelt:

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 Dann können Sie die importierten Eigenschaften wie folgt festlegen:

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 Wenn Sie eine Methode testen möchten, die eine importierte Eigenschaft als Parameter übernimmt, können Sie die Eigenschaft in die Testklasse importieren und `SatisfyImportsOnce` auf die Testinstanz anwenden. Beispiel:

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 In diesem Beispiel werden die beiden Attribute der einzelnen Testmethoden praktischerweise in einer Zeile zusammengefasst.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Zugreifen aus Tests auf private Methoden und Variablen
 Gelegentlich möchten Sie möglicherweise eine Methode testen, die privat ist oder Sie möchten den Zustand eines privaten Felds überprüfen, bevor und nachdem Sie eine getestete Methode ausführen. Dies erweist sich als Schwierigkeit, da sich die Tests in einer Assembly befinden, die von den getesteten Klassen getrennt ist. Es gibt verschiedene Möglichkeiten, die Sie erwägen können, einschließlich der Folgenden:

 Testen Sie die Tests nur mit öffentlichen und internen Elementen, sodass Sie nur öffentliche (oder interne) Klassen und Member verwenden. Dies ist der optimale Ansatz. Ihre Tests funktionieren auch dann noch, wenn Sie die interne Implementierung der zu testenden Assembly umgestalten. Indem Sie dieselben Tests vor und nach den Änderungen anwenden, können Sie sicherstellen, dass sich Ihre Änderungen nicht auf das Verhalten der Assembly ausgewirkt haben.

 Dazu müssen Sie möglicherweise den Code umstrukturieren. Möglicherweise müssen Sie einige Methoden in eine andere Klasse verschieben.

 Wenn Sie diesen Ansatz ernsthaft in Betracht ziehen, werden Sie häufig den Eindruck erhalten, dass Ihr Code einfacher zu lesen, zu ändern sowie weniger fehleranfällig ist, wenn Änderungen erforderlich sind.

 Sie können der Testassembly den Zugriff auf interne Elemente gestatten, indem Sie in **Properties\AssemblyInfo.cs** im zu testenden Projekt ein Attribut hinzufügen:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Definieren einer Test Schnittstelle definieren Sie eine Schnittstelle, die sowohl die öffentlichen Member einer zu testenden Klasse als auch zusätzliche Eigenschaften und Methoden für die privaten Member enthält, die von den Tests verwendet werden sollen. Fügen Sie diese Schnittstelle zum zu testenden Projekt hinzu. Beispiel:

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Fügen Sie Methoden zur zu testenden Klasse hinzu, um die Accessormethoden explizit zu implementieren. Trennen Sie die zusätzlichen Methoden von der Hauptklasse, indem Sie sie in einer partiellen Klassendefinition in einer separaten Datei erstellen. Beispiel:

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Gestatten Sie der Testassembly die Verwendung der Testschnittstellen, indem Sie dieses Attribut zur testenden Assembly hinzufügen:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Verwenden Sie die Testschnittstelle in den Komponententestmethoden. Beispiel:

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Definieren von Accessoren mithilfe von Reflektion Dies ist die empfohlene Vorgehensweise. Ältere Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] haben ein Hilfsprogramm bereitgestellt, das automatisch eine Accessormethode für die einzelnen privaten Methoden bereitgestellt hat. Obwohl diese Vorgehensweise praktisch ist, sagt uns unsere Erfahrung, dass dies eher zu Komponententests führt, die sehr stark an die interne Struktur der zu testenden Anwendung gebunden sind. Dies führt bei sich ändernden Anforderungen oder einer veränderten Architektur wiederum zu zusätzlichem Aufwand, da die Tests zusammen mit der Implementierung geändert werden müssen. Zudem werden sämtliche fehlerhaften Annahmen für den Implementierungsentwurf auch in die Tests übernommen, sodass in den Tests keine Fehler gefunden werden.

## <a name="see-also"></a>Weitere Informationen
 [Anatomie eines Komponententests](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
