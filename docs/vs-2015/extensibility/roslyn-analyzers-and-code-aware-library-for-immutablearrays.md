---
title: Roslyn-Analyzers und Code bewusste Bibliothek für immutablearrays | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd54c5e730f757a0e198ad7cf1d8577e686b9ea9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845878"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn-Analyzer und codeabhängige Bibliothek für ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") unterstützt Sie beim Erstellen von Code abhängigen Bibliotheken. Eine Code fähige Bibliothek bietet Funktionen, die Sie verwenden können, und Tools (Roslyn-Analyzers), um Sie bei der optimalen Verwendung der Bibliothek oder bei der Vermeidung von Fehlern zu unterstützen. In diesem Thema wird gezeigt, wie Sie einen echten Roslyn-Analyzer erstellen, um häufige Fehler bei der Verwendung des nuget-Pakets " [NIB: unveränderliche](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) Auflistungen" zu erfassen. Das Beispiel zeigt auch, wie Sie eine Code Korrektur für ein Code Problem bereitstellen, das vom Analyzer gefunden wurde. Benutzer sehen Code Korrekturen in der Benutzeroberfläche von Visual Studio Glühbirnen und können automatisch eine Korrektur für den Code anwenden.

## <a name="getting-started"></a>Erste Schritte
Um dieses Beispiel zu erstellen, benötigen Sie Folgendes:

- Visual Studio 2015 (keine Express Edition) oder eine höhere Version. Sie können die kostenlose [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) verwenden.

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Sie können auch bei der Installation von Visual Studio Visual Studio-Erweiterungstools unter Allgemeine Tools aktivieren, um das SDK gleichzeitig zu installieren. Wenn Sie Visual Studio bereits installiert haben, können Sie dieses SDK auch installieren, indem Sie in der Hauptmenü **- &#124; Datei &#124;neu Projekt...** klicken C# , im linken Navigationsbereich auswählen und dann Erweiterbarkeit auswählen. Wenn Sie die Breadcrumb-Projektvorlage "**install the Visual Studio-Erweiterungstools**" auswählen, werden Sie aufgefordert, das SDK herunterzuladen und zu installieren.

- [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Sie können dieses SDK auch installieren, indem Sie in der Hauptmenü **- &#124; Datei &#124; neu Projekt...** klicken **C#** , im linken Navigationsbereich auswählen und dann **Erweiterbarkeit**auswählen. Wenn Sie die Breadcrumb-Projektvorlage " **.NET Compiler Platform SDK herunterladen**" auswählen, werden Sie aufgefordert, das SDK herunterzuladen und zu installieren. Dieses SDK enthält die [Roslyn-Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Dieses äußerst nützliche Tool hilft Ihnen herauszufinden, welche Code Modelltypen Sie in Ihrem Analyzer suchen sollten. Die Analyse Infrastruktur Ruft den Code für bestimmte Code Modelltypen auf, sodass der Code nur bei Bedarf ausgeführt wird und sich nur auf die Analyse von relevantem Code konzentrieren kann.

## <a name="whats-the-problem"></a>Was ist das Problem?
Stellen Sie sich vor, Sie stellen eine Bibliothek mit immutablearray (z. b. <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>)-Unterstützung bereit. C#Entwickler haben viele Möglichkeiten, mit .NET-Arrays zu arbeiten. Aufgrund der Natur von immutablearrays und Optimierungstechniken, die in der-Implementierung verwendet werden C# , bewirken Entwickler Intuitionen jedoch, dass Benutzer Ihrer Bibliothek einen unterbrochenen Code schreiben, wie unten erläutert. Außerdem werden die Fehler erst zur Laufzeit angezeigt, wenn die Benutzer in Visual Studio mit .net in Visual Studio verwendet werden.

Benutzer sind mit dem Schreiben von Code wie dem folgenden vertraut.

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Die Erstellung leerer Arrays, die mit nachfolgenden Codezeilen ausgefüllt werden sollen, und die Verwendung der sammlungsinitialisierersyntax sind C# Entwicklern sehr vertraut. Das Schreiben desselben Codes für ein immutablearray stürzt jedoch zur Laufzeit ab:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

Der erste Fehler ist darauf zurückzuführen, dass die immutablearray-Implementierung eine Struktur verwendet, um den zugrunde liegenden Datenspeicher zu wrappen. Strukturen müssen Parameter lose Konstruktoren aufweisen, damit `default(T)` Ausdrücke Strukturen mit allen NULL-oder null-Elementen zurückgeben können. Wenn der Code auf `b1.Length`zugreift, gibt es einen Laufzeitfehler bei Null Dereferenzierung, da kein zugrunde liegendes Speicher Array in der immutablearray-Struktur vorhanden ist. Die richtige Methode zum Erstellen eines leeren "immutablearray" ist `ImmutableArray<int>.Empty`.

 Der Fehler bei sammlungsinitialisierern tritt auf, weil die immutablearray. Add-Methode jedes Mal, wenn Sie Sie aufruft, neue Instanzen zurückgibt. Da sich immutablearrays nie ändern, wenn Sie ein neues Element hinzufügen, erhalten Sie ein neues immutablearray-Objekt (das möglicherweise Speicher aus Leistungsgründen mit einem bereits vorhandenen immutablearray freigibt). Da `b2` auf das erste immutablearray zeigt, bevor Sie `Add()` fünfmal aufrufen, ist `b2` ein Standardmäßiges immutablearray. Der Aufruf von length für ihn stürzt auch mit einem NULL-dereferenzierungsfehler ab. Die richtige Methode zum Initialisieren eines "immutablearray" ohne manuelles Aufrufen von "Add" ist die Verwendung von `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Suchen relevanter Syntax Knoten Typen zum auslöst ihrer Analyse
Um mit der Erstellung der Analyse zu beginnen, müssen Sie zunächst herausfinden, welche Art von syntaxnode Sie suchen müssen.   Starten Sie den Syntax Visualizer über die **Menü &#124; Ansicht andere &#124; Windows Roslyn Syntax Visualizer**.

Platzieren Sie die Einfügemarke des Editors in der Zeile, die `b1`deklariert. Die Syntax Visualizer zeigt, dass Sie sich in einem `LocalDeclarationStatement` Knoten der Syntax Struktur befinden. Dieser Knoten verfügt über eine `VariableDeclaration`, die wiederum über einen `VariableDeclarator`verfügt, der wiederum über einen `EqualsValueClause`verfügt, und schließlich ist ein `ObjectCreationExpression`vorhanden. Wenn Sie in die Syntax Visualizer Struktur der Knoten klicken, wird die Syntax im Editor Fenster hervorgehoben, um den von diesem Knoten dargestellten Code anzuzeigen. Die Namen der syntaxnode-Untertypen entsprechen den in der C# Grammatik verwendeten Namen.

## <a name="creating-the-analyzer-project"></a>Erstellen des Analyzer-Projekts
Klicken Sie im Hauptmenü auf **Datei &#124; neu &#124; Projekt...** . Wählen Sie im Dialogfeld **Neues Projekt** unter **C#** Projekte in der linken Navigationsleiste die Option Erweiterbarkeit aus, und wählen Sie dann im rechten Bereich die Vorlage **Analyzer mit Code Fix** Project aus. Geben Sie einen Namen ein, und bestätigen Sie den Dialog.

Die Vorlage öffnet eine DiagnosticAnalyzer.cs-Datei. Wählen Sie die Registerkarte Editor-Puffer aus. Diese Datei enthält eine Analyzer-Klasse (aus dem Namen, den Sie dem Projekt gegeben haben), der von `DiagnosticAnalyzer` (einem Roslyn-API-Typ) abgeleitet ist. Die neue Klasse verfügt über eine `DiagnosticAnalyzerAttribute` die Deklaration Ihres Analyzers C# für die Sprache relevant ist, sodass der Compiler den Analyzer ermittelt und lädt.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Sie können einen Analyzer mithilfe von Visual Basic implementieren, C# der auf Code abzielt, und umgekehrt. Es ist wichtiger in diagnosticanalyzerattribute, auszuwählen, ob Ihr Analyzer auf eine Sprache oder beides abzielt. Komplexere Analysen, die eine ausführliche Modellierung der Sprache erfordern, können nur auf eine Sprache abzielen. Wenn Ihr Analyzer z. b. nur Typnamen oder öffentliche Elementnamen überprüft, kann es möglich sein, das Common Language Model Roslyn-Angebote über Visual Basic und C#zu verwenden. Beispielsweise warnt FxCop, dass eine Klasse <xref:System.Runtime.Serialization.ISerializable>implementiert, aber die Klasse verfügt nicht über das <xref:System.SerializableAttribute> Attribut ist sprachunabhängig und funktioniert sowohl für Visual Basic als auch C# für Code.

## <a name="initalizing-the-analyzer"></a>Analyse der Analyse
Scrollen Sie in der `DiagnosticAnalyzer`-Klasse nach unten, um die `Initialize`-Methode anzuzeigen. Der Compiler ruft diese Methode auf, wenn ein Analyzer aktiviert wird. Die-Methode nimmt ein `AnalysisContext` Objekt an, das es Ihrem Analyzer ermöglicht, Kontextinformationen zu erhalten und Rückrufe für Ereignisse für die Arten von Code zu registrieren, die Sie analysieren möchten.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Öffnen Sie in dieser Methode eine neue Zeile, und geben Sie "Context" ein. , um eine IntelliSense-Vervollständigungsliste anzuzeigen. In der Vervollständigungsliste können Sie sehen, dass es viele `Register…` Methoden gibt, um verschiedene Arten von Ereignissen zu verarbeiten. Beispielsweise ruft der erste, `RegisterCodeBlockAction`, den Code für einen-Block zurück, bei dem es sich in der Regel um Code zwischen geschweiften Klammern handelt. Beim Registrieren für einen-Block wird auch der Code für den Initialisierer eines Felds, den Wert für ein Attribut oder den Wert eines optionalen Parameters zurückgegeben.

Ein weiteres Beispiel `RegisterCompilationStartAction`ist, dass Sie den Code zu Beginn einer Kompilierung aufrufen, was nützlich ist, wenn Sie den Zustand über viele Speicherorte erfassen müssen. Sie können beispielsweise eine Datenstruktur erstellen, um alle verwendeten Symbole zu erfassen, und jedes Mal, wenn der Analyzer für eine Syntax oder ein Symbol zurückgerufen wird, können Sie Informationen zu jedem Speicherort in der Datenstruktur speichern. Wenn Sie aufgrund der Kompilierung wieder aufgerufen werden, können Sie alle Speicherorte analysieren, die Sie gespeichert haben, z. b. um zu melden, welche Symbole der Code aus den einzelnen `using`-Anweisungen verwendet.

Wenn Sie die **Syntax Visualizer**verwenden, haben Sie gelernt, dass Sie aufgerufen werden möchten, wenn der Compiler einen objectkreationexpression verarbeitet. Mit diesem Code können Sie den Rückruf einrichten:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Sie registrieren sich für einen Syntax Knoten und Filtern nur nach Syntax Knoten für die Objekt Erstellung. Gemäß der Konvention verwenden Analyzer-Autoren beim Registrieren von Aktionen einen Lambda-Ausdruck, der die Zustands lose Analyse der Analysen erleichtert. Sie können das Visual Studio-Feature **generieren aus der Verwendung** verwenden, um die `AnalyzeObjectCreation`-Methode zu erstellen. Dadurch wird auch der richtige Typ von Kontext Parametern für Sie generiert.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Festlegen von Eigenschaften für Benutzer Ihrer Analyse
Damit Ihr Analyzer in der Visual Studio-Benutzeroberfläche ordnungsgemäß angezeigt wird, suchen Sie die folgende Codezeile, und ändern Sie Sie, um Ihren Analyzer zu ermitteln:

```csharp
internal const string Category = "Naming";
```

Änderung `"Naming"` zu `"API Guidance"`.

Suchen Sie als nächstes die Datei Resources. resx in Ihrem Projekt, und öffnen Sie Sie mit dem **Projektmappen-Explorer**. Sie können eine Beschreibung für Analyzer, Titel usw. einfügen. Sie können den Wert für alle diese Werte jetzt in "`“Don’t use ImmutableArray<T> constructor”`" ändern. Sie können Zeichen folgen-Formatierungs Argumente in der Zeichenfolge ({0}, {1}usw.) einfügen, und später, wenn Sie `Diagnostic.Create()`aufzurufen, können Sie ein params-Array von Argumenten bereitstellen, das übergeben werden soll.

## <a name="analyzing-an-object-creation-expression"></a>Analysieren eines Ausdrucks zur Objekt Erstellung
Die `AnalyzeObjectCreation`-Methode nimmt einen anderen Typ von Kontext auf, der vom Code Analyzer-Framework bereitgestellt wird. Die `AnalysisContext` der Initialize-Methode ermöglicht es Ihnen, Aktions Rückrufe zu registrieren, um den Analyzer einzurichten. Der `SyntaxNodeAnalysisContext`verfügt beispielsweise über eine `CancellationToken`, die Sie weiterleiten können. Wenn ein Benutzer mit der Eingabe im Editor beginnt, bricht Roslyn die Ausführung von Analysemodulen ab, um Arbeit zu sparen und die Leistung zu verbessern. Ein weiteres Beispiel: dieser Kontext verfügt über eine Node-Eigenschaft, die den Objekt Erstellungs Syntax Knoten zurückgibt.

Sie erhalten den Knoten, den Sie annehmen können, ist der Typ, für den Sie die Syntax Knoten Aktion gefiltert haben:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Erst malig starten von Visual Studio mit Ihrem Analyzer
Starten Sie Visual Studio, indem Sie den Analyzer entwickeln und ausführen (drücken Sie **F5**). Da das Startprojekt in der **Projektmappen-Explorer** das VSIX-Projekt ist, wird durch das Ausführen Ihres Codes der Code und eine VSIX-Datei erstellt und anschließend Visual Studio mit installierter VSIX gestartet. Wenn Sie Visual Studio auf diese Weise starten, wird diese mit einer eindeutigen Registrierungs Struktur gestartet, sodass Ihre Hauptverwendung von Visual Studio bei der Erstellung von Analysemodulen nicht von den Test Instanzen beeinträchtigt wird. Wenn Sie diese Methode zum ersten Mal starten, führt Visual Studio mehrere Initialisierungen aus, ähnlich wie beim ersten Starten von Visual Studio nach der Installation.

 Erstellen Sie ein Konsolen Projekt, und geben Sie dann den arraycode in die Hauptmethode ihrer Konsolen Anwendungen ein:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Die Codezeilen mit `ImmutableArray` haben Wellenlinien, da Sie das unveränderliche nuget-Paket erhalten und dem Code eine `using`-Anweisung hinzufügen müssen. Klicken Sie im **Projektmappen-Explorer** auf den Knoten mit der rechten Maustaste, und wählen Sie **nuget-Pakete verwalten...** aus. Geben Sie im nuget-Manager "immutable" in das Suchfeld ein, und wählen Sie das Element "System. Collections. immutable" (Wählen Sie "Microsoft. BCL. immutable" nicht aus) im linken Bereich aus, und klicken Sie im rechten Bereich auf die Schaltfläche "installieren". Durch die Installation des Pakets wird ein Verweis auf die Projekt Verweise hinzugefügt.

Unter `ImmutableArray`werden weiterhin rote Wellenlinien angezeigt. Platzieren Sie die Einfügemarke in diesem Bezeichner, und drücken Sie **STRG +.** (Zeitraum), um das vorgeschlagene fixmenü anzuzeigen, und wählen Sie das Hinzufügen der entsprechenden `using`-Anweisung aus.

**Speichern Sie alles, und schließen** Sie die zweite Instanz von Visual Studio, damit Sie den Vorgang fortsetzen können.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Abschließen der Analyse mithilfe von "Bearbeiten und Fortfahren"
Legen Sie in der ersten Instanz von Visual Studio am Anfang der `AnalyzeObjectCreation` Methode einen Haltepunkt fest, indem Sie **F9** mit der Einfügemarke in der ersten Zeile drücken.

Starten Sie den Analyzer erneut mit **F5**, und öffnen Sie in der zweiten Instanz von Visual Studio die Konsolenanwendung, die Sie zuletzt erstellt haben, erneut.

Sie kehren zur ersten Instanz von Visual Studio am Haltepunkt zurück, da der Roslyn-Compiler einen Objekt Erstellungs Ausdruck gesehen und in den Analyzer aufgerufen hat.

**Erstellen Sie den Knoten zum Erstellen von Objekten.** Überspringen Sie die Zeile, in der die `objectCreation` Variable durch Drücken von **F10**festgelegt wird, und prüfen Sie im **direkt Fenster** den Ausdruck `“objectCreation.ToString()”`. Sie sehen, dass der Syntax Knoten, auf den die Variable verweist, der Code `"new ImmutableArray<int>()"`ist, genau das, was Sie suchen.

**Get immutablearray\<t > Type-Objekt.** Sie müssen überprüfen, ob der erstellte Typ immutablearray ist. Zuerst erhalten Sie das Objekt, das diesen Typ darstellt. Sie überprüfen Typen mit dem Semantik Modell, um sicherzustellen, dass Sie genau den richtigen Typ haben, und Sie vergleichen die Zeichenfolge nicht von ToString (). Geben Sie die folgende Codezeile am Ende der-Funktion ein:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Sie bestimmen generische Typen in Metadaten mit Backquotes (') und der Anzahl generischer Parameter. Daher wird "... Immutablearray\<t > "im Metadatennamen.

Das Semantik Modell bietet viele nützliche Dinge, mit denen Sie Fragen zu Symbolen, Datenfluss, Variablen Lebensdauer usw. stellen können. Roslyn trennt Syntax Knoten aus dem Semantik Modell für verschiedene technische Gründe (Leistung, Modellierung von fehlerhaftem Code usw.). Das Kompilierungs Modell soll in verweisen enthaltene Informationen für einen exakten Vergleich suchen.

Sie können den gelben Ausführungs Zeiger auf der linken Seite des Editor Fensters ziehen. Ziehen Sie Sie in die Zeile, in der die `objectCreation` Variable festgelegt wird, und überspringen Sie die neue Codezeile mithilfe von **F10**. Wenn Sie mit dem Mauszeiger auf die Variable `immutableArrayOfType`zeigen, sehen Sie, dass der genaue Typ im Semantik Modell gefunden wurde.

**Gibt den Typ des Objekterstellungs-Ausdrucks ab.** "Type" wird auf verschiedene Weise in diesem Artikel verwendet. Dies bedeutet jedoch, dass Sie ein Modell von foo erhalten müssen, wenn Sie einen "New foo"-Ausdruck haben. Sie müssen den Typ des Ausdrucks zur Objekt Erstellung ermitteln, um festzustellen, ob es sich um den Typ "immutablearray\<t > Typ handelt. Verwenden Sie das Semantik Modell erneut, um Symbol Informationen für das Typsymbol (immutablearray) im Objekt Erstellungs Ausdruck zu erhalten. Geben Sie die folgende Codezeile am Ende der-Funktion ein:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Da Ihr Analyzer unvollständigen oder falschen Code in Editor Puffern verarbeiten muss (z. b. Wenn eine `using`-Anweisung fehlt), sollten Sie überprüfen, ob `symbolInfo` `null`wird. Sie müssen einen benannten Typ (inamedtypesymbol) aus dem Symbol Informationsobjekt erhalten, um die Analyse abzuschließen.

**Vergleichen Sie die Typen.** Da es sich um einen offenen generischen Typ von T handelt, den wir suchen, und der Typ im Code ein konkreter generischer Typ ist, Fragen Sie die Symbol Informationen nach dem Typ ab (ein offener generischer Typ) und vergleichen das Ergebnis mit `immutableArrayOfTType`. Geben Sie am Ende der Methode Folgendes ein:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Melden Sie die Diagnose.** Das Melden der Diagnose ist ziemlich einfach. Sie verwenden die für Sie erstellte Regel in der Projektvorlage, die vor der Initialize-Methode definiert ist. Da es sich bei dieser Situation im Code um einen Fehler handelt, können Sie die Zeile, in der die Regel initialisiert wurde, ändern, um `DiagnosticSeverity.Warning` (grüne Wellenlinie) durch `DiagnosticSeverity.Error` (rote Wellenlinie) zu ersetzen. Der Rest der Regel Initialisiert aus den Ressourcen, die Sie am Anfang der exemplarischen Vorgehensweise bearbeitet haben. Außerdem müssen Sie den Speicherort für die Wellenlinie melden, bei der es sich um den Speicherort der Typspezifikation für die Objekt Erstellungs-Express Sion handelt. Geben Sie den folgenden Code in den `if`-Block ein:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Die Funktion sollte wie folgt aussehen (möglicherweise anders formatiert):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Entfernen Sie den Breakpoint, damit Sie sehen können, dass Ihr Analyzer funktioniert (und Sie nicht mehr zur ersten Instanz von Visual Studio zurückkehren). Ziehen Sie den Ausführungs Zeiger an den Anfang der Methode, und drücken Sie **F5** , um die Ausführung fortzusetzen. Wenn Sie zurück zur zweiten Instanz von Visual Studio wechseln, wird der Code von dem Compiler erneut untersucht, und es wird ein Rückruf an den Analyzer durchführt. Sie können unter `ImmutableType<int>`eine Wellenlinie sehen.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Hinzufügen eines "Code Fixes" für das Code Problem
Bevor Sie beginnen, schließen Sie die zweite Instanz von Visual Studio, und beenden Sie das Debuggen in der ersten Instanz von Visual Studio (in der Sie den Analyzer entwickeln).

**Fügen Sie eine neue Klasse hinzu.** Verwenden Sie das Kontextmenü (rechts Zeiger Schaltfläche) auf dem Projekt Knoten im Projektmappen-Explorer, und wählen Sie ein neues Element hinzufügen aus. Fügen Sie eine Klasse mit dem Namen `BuildCodeFixProvider`hinzu. Diese Klasse muss von `CodeFixProvider`abgeleitet werden, und Sie müssen **STRG + verwenden.** (Zeitraum) zum Aufrufen der Code Korrektur, mit der die richtige `using`-Anweisung hinzugefügt wird. Diese Klasse muss ebenfalls mit `ExportCodeFixProvider`-Attribut versehen werden, und Sie müssen eine `using`-Anweisung hinzufügen, um die `LanguageNames`-Enumeration aufzulösen. Sie sollten über eine Klassendatei mit folgendem Code verfügen:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub out abgeleitete Member.** Platzieren Sie nun die Einfügemarke des Editors in den Bezeichner `CodeFixProvider` und drücken Sie **STRG +.** (Zeitraum), um die Implementierung für diese abstrakte Basisklasse auszulagern. Dadurch werden eine-Eigenschaft und eine-Methode für Sie generiert.

**Implementieren Sie die-Eigenschaft.** Geben Sie den `get` Text der `FixableDiagnosticIds` Eigenschaft mit folgendem Code ein:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn vereint Diagnose und Korrekturen, indem diese Bezeichner abgeglichen werden, die nur Zeichen folgen sind. Die Projektvorlage hat eine Diagnose-ID generiert, und Sie können Sie ändern. Der Code in der-Eigenschaft gibt lediglich die ID der Analyzer-Klasse zurück.

**Die registercodefixasync-Methode nimmt einen Kontext an.** Der Kontext ist wichtig, da eine Code Korrektur auf mehrere Diagnosen angewendet werden kann, oder es gibt mehr als ein Problem in einer Codezeile. Wenn Sie "Context" eingeben. im Text der-Methode werden in der IntelliSense-Vervollständigungsliste einige nützliche Member angezeigt. Es gibt einen CancellationToken-Member, den Sie überprüfen können, um festzustellen, ob das Problem behoben werden soll. Es gibt ein dokumentmember, das viele nützliche Member enthält und Ihnen ermöglicht, die Projekt-und projektmappenmodellobjekte zu erhalten. Es gibt einen spannen Member, bei dem es sich um den Anfang und das Ende des Code Speicher Orts handelt, der beim Melden der Diagnose angegeben wurde.

**Legen Sie die Methode als asynchron an.** Als erstes müssen Sie die generierte Methoden Deklaration so korrigieren, dass Sie eine `async` Methode ist. Die Code Korrektur für das Ausführen eines Stubs der Implementierung einer abstrakten Klasse enthält nicht das `async`-Schlüsselwort, obwohl die Methode eine `Task`zurückgibt.

**Der Stamm der Syntax Struktur wird angezeigt.** Um den Code zu ändern, müssen Sie eine neue Syntax Struktur mit den Änderungen entwickeln, die durch den Code behoben werden. Sie benötigen die `Document` aus dem Kontext, um `GetSyntaxRootAsync`aufzurufen. Dabei handelt es sich um eine asynchrone Methode, da es unbekannte Aufgaben gibt, die Syntax Struktur zu erhalten, u. u. die Datei vom Datenträger zu erhalten, Sie zu verarbeiten und das Roslyn-Code Modell dafür zu entwickeln. Die Visual Studio-Benutzeroberfläche sollte während dieser Zeit reaktionsfähig sein, was die Verwendung `async` ermöglicht. Ersetzen Sie die Codezeile in der-Methode durch Folgendes:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Suchen Sie den Knoten mit dem Problem.** Sie übergeben die Spanne des Kontexts, aber der Knoten, den Sie finden, ist möglicherweise nicht der Code, den Sie ändern müssen. Die gemeldete Diagnose stellte nur die Spanne für den Typbezeichner bereit (wobei die Wellenlinie zu gehörte), aber Sie müssen den gesamten Objekt Erstellungs Ausdruck ersetzen, einschließlich der `new` keywoard am Anfang und die Klammern am Ende. Fügen Sie der-Methode den folgenden Code hinzu (und verwenden Sie **STRG +.** So fügen Sie eine `using`-Anweisung für `ObjectCreationExpressionSyntax`hinzu):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Registrieren Sie Ihre Code Korrektur für die Glühbirnen-Benutzeroberfläche.** Wenn Sie Ihre Code Korrektur registrieren, wird Roslyn automatisch an die Benutzeroberfläche von Visual Studio Glühbirnen angeschlossen. Endbenutzern wird angezeigt, dass Sie **STRG +** verwenden können. (Zeitraum), wenn Ihr Analyzer einen ungültigen `ImmutableArray<T>` Konstruktor verwendet. Da Ihr Code Korrektur-Anbieter nur ausgeführt wird, wenn ein Problem vorliegt, können Sie davon ausgehen, dass Sie über den Objekt Erstellungs Ausdruck verfügen, nach dem Sie suchen. Über den Kontext Parameter können Sie die neue Code Korrektur registrieren, indem Sie am Ende `RegisterCodeFixAsync` Methode den folgenden Code hinzufügen:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Sie müssen die Einfügemarke des Editors in den Bezeichner (`CodeAction`) platzieren und dann **STRG + verwenden.** (Zeitraum), um die entsprechende `using`-Anweisung für diesen Typ hinzuzufügen.

Platzieren Sie dann die Einfügemarke des Editors in den `ChangeToImmutableArrayEmpty` Bezeichner, und verwenden Sie **STRG +.** erneut, um diesen Methodenstub für Sie zu generieren.

Mit diesem letzten Code Ausschnitt, den Sie hinzugefügt haben, wird die Code Korrektur registriert, indem ein `CodeAction` und die Diagnose-ID für die Art des gefundenen Problems übergeben werden. In diesem Beispiel gibt es nur eine Diagnose-ID, für die dieser Code Korrekturen bereitstellt, sodass Sie einfach das erste Element des Arrays mit den Diagnose-IDs übergeben können. Wenn Sie die `CodeAction`erstellen, übergeben Sie den Text, den die Glühbirnen-UI als Beschreibung der Code Korrektur verwenden soll. Außerdem übergeben Sie eine Funktion, die ein CancellationToken annimmt und ein neues Dokument zurückgibt. Das neue Dokument enthält eine neue Syntax Struktur, die den gepatchten Code enthält, der `ImmutableArray.Empty`aufruft. Dieser Code Ausschnitt verwendet einen Lambda-Ausdruck, sodass er sich über den objectcreation-Knoten und das Kontext Dokument schließen kann.

**Erstellen Sie die neue Syntax Struktur.** Geben Sie in der `ChangeToImmutableArrayEmpty`-Methode, deren Stub Sie zuvor generiert haben, die Codezeile ein: `ImmutableArray<int>.Empty;`. Wenn Sie das Syntax Visualizer Tool Fenster erneut anzeigen, sehen Sie, dass diese Syntax ein simplemembership accessexpression-Knoten ist. Diese Methode muss in einem neuen Dokument erstellt und zurückgegeben werden.

Die erste Änderung an `ChangeToImmutableArrayEmpty` besteht darin, `async` vor `Task<Document>` hinzuzufügen, da die Code-Generatoren nicht annehmen können, dass die Methode Async sein sollte.

Füllen Sie den Text mit dem folgenden Code aus, damit die-Methode in etwa wie folgt aussieht:

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Sie müssen die Einfügemarke des Editors in den `SyntaxGenerator` Bezeichner einfügen und **STRG + verwenden.** (Zeitraum), um die entsprechende `using`-Anweisung für diesen Typ hinzuzufügen.

In diesem Code wird `SyntaxGenerator`verwendet, bei dem es sich um einen sehr nützlichen Typ zum Erstellen von neuem Code handelt. Nachdem Sie einen Generator für das Dokument mit dem Code Problem erhalten haben, ruft `ChangeToImmutableArrayEmpty` `MemberAccessExpression`auf und übergibt den Typ, der den Member enthält, auf den wir zugreifen möchten, und übergibt den Namen des Members als Zeichenfolge.

Als nächstes Ruft die Methode den Stamm des Dokuments ab, und da dies beliebige Arbeit im allgemeinen Fall einschließen kann, erwartet der Code diesen-Befehl und übergibt das Abbruch Token. Roslyn-Code Modelle sind unveränderlich, wie z. b. das Arbeiten mit einer .net-Zeichenfolge. Wenn Sie die Zeichenfolge aktualisieren, erhalten Sie ein neues Zeichen folgen Objekt in der Rückgabe. Wenn Sie `ReplaceNode`aufgerufen haben, erhalten Sie einen neuen Stamm Knoten. Der größte Teil der Syntax Struktur ist freigegeben (da er unveränderlich ist), aber der `objectCreation` Knoten wird durch den `memberAccess` Knoten sowie alle übergeordneten Knoten bis zum Syntax Struktur Stamm ersetzt.

## <a name="trying-your-code-fix"></a>Testen der Code Korrektur
Sie können jetzt **F5** drücken, um den Analyzer in einer zweiten Instanz von Visual Studio auszuführen. Öffnen Sie das Konsolen Projekt, das Sie zuvor verwendet haben. Nun sollte die Glühbirne angezeigt werden, auf der sich der neue Objekt Erstellungs Ausdruck für `ImmutableArray<int>`befindet. Wenn Sie **STRG + drücken.** (Zeitraum), dann wird der Code Fehler behoben, und Sie sehen eine automatisch generierte Code Differenz Vorschau auf der Glühbirnen-Benutzeroberfläche. Roslyn erstellt diese für Sie.

Pro-Tipp: Wenn Sie die zweite Instanz von Visual Studio starten und die Glühbirne nicht mit ihrer Code Korrektur angezeigt wird, müssen Sie möglicherweise den Visual Studio-Komponenten Cache löschen. Wenn Sie den Cache löschen, erzwingt Visual Studio die erneute Untersuchung der Komponenten, daher sollte Visual Studio dann ihre neueste Komponente abrufen. Fahren Sie zuerst die zweite Instanz von Visual Studio herunter. Navigieren Sie dann in Windows-Explorer zu Ihrem Benutzerverzeichnis (c:\Benutzer\\< UserID\>), und suchen Sie nach appdata\local\microsoft\visualstudio\14.0roslyn\\. Löschen Sie in diesem Verzeichnis das Unterverzeichnis componentmodelcache. Die Version "14" ändert sich mit Visual Studio in Version.

## <a name="talk-video-and-finish-code-project"></a>Talk-Video und Code Projekt abschließen
Sie sehen, dass dieses Beispiel in [diesem Gespräch](https://channel9.msdn.com/events/Build/2015/3-725)entwickelt und erläutert wurde. Der Talk demonstriert den funktionierenden Analyzer und führt Sie durch die Schritte.

Den gesamten Code finden Sie [hier](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Die Unterordner donotuseimmutablearraycollectioninitializer und donotuseimmutablearrayctor verfügen jeweils über C# eine Datei zum Auffinden von C# Problemen und eine Datei, die die Code Korrekturen implementiert, die in der Benutzeroberfläche von Visual Studio Glühbirnen angezeigt werden. Beachten Sie, dass der fertige Code eine etwas mehr Abstraktion hat, um zu vermeiden, dass die immutablearray-\<t > Type-Objekts immer wiederholt abgerufen wird. Er verwendet in der Liste gespeicherte registrierte Aktionen, um das Typobjekt in einem Kontext zu speichern, der immer verfügbar ist, wenn die untergeordneten Aktionen (Objekt Erstellung analysieren und Auflistungs Initialisierungen analysieren) ausgeführt werden.

## <a name="see-also"></a>Siehe auch
[\\\Build 2015 Talk](https://channel9.msdn.com/events/Build/2015/3-725)
[vollständigen Code auf GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[mehrere Beispiele auf GitHub, die in drei Arten von Analyse](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) Modulen 
[anderen Dokumente auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
FxCop-Regeln, die [mit Roslyn-Analysen auf GitHub implementiert](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop) wurden, gruppiert sind.
