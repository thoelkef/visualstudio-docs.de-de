---
title: Roslyn-Analyzer und codeabhängige Bibliothek für ImmutableArrays | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28ddaafc8ab4ddbaef1d7e42faedc2229664c6e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433330"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn-Analyzer und codeabhängige Bibliothek für ImmutableArrays

Die [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") hilft Ihnen, Code unterstützende Bibliotheken zu erstellen. Eine codeabhängige Bibliothek bietet Funktionen, die Sie verwenden können, und der Tools (Roslyn-Analysetools) können Sie die Bibliothek verwenden, auf die bestmögliche Weise oder Fehler zu vermeiden. In diesem Thema erfahren Sie, wie zum Erstellen eines Roslyn-Analyzers Praxis, um häufige Fehler abzufangen, bei Verwendung der [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet-Paket. Darüber hinaus wird veranschaulicht, wie eine Codefehlerbehebung für ein Codeproblem gefunden, die vom Analyzer bereitgestellt werden. Benutzer sehen codefehlerbehebungen in der Visual Studio-Glühbirne Benutzeroberfläche und eine Korrektur für den Code automatisch anwenden können.

## <a name="get-started"></a>Erste Schritte

Sie benötigen Folgendes zum Erstellen dieses Beispiels:

* Visual Studio 2015 (keine Express Edition) oder eine höhere Version. Sie können die kostenlose [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Sehen Sie sich auch bei der Installation von Visual Studio **Visual Studio-Erweiterbarkeitstools** unter **häufig verwendete Tools** zur gleichen Zeit das SDK zu installieren. Wenn Sie Visual Studio bereits installiert haben, können Sie dieses SDK auch installieren, indem Sie auf das Hauptmenü **Datei** > **neu** > **Projekt**, Auswahl **c#** im linken Navigationsbereich und klicken Sie dann auswählen **Erweiterbarkeit**. Bei der Auswahl der "**installieren Sie Visual Studio-Erweiterbarkeitstools**" Breadcrumb-Projektvorlage, sie werden aufgefordert, das SDK herunterladen und installieren.
* [.NET Compiler Platform ("Roslyn") SDK](https://aka.ms/roslynsdktemplates). Sie können dieses SDK auch installieren, indem Sie auf das Hauptmenü **Datei** > **neu** > **Projekt**auswählen **c#** in den linken Navigationsbereich, auswählen und dann **Erweiterbarkeit**. Bei der Auswahl "**das .NET Compiler Platform SDK herunterladen**" Breadcrumb-Projektvorlage, sie werden aufgefordert, das SDK herunterladen und installieren. Dieses SDK enthält die [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Diesem nützliches Tool können Sie herausfinden, welche Modelltypen Code sollten Sie in Ihr Analysemodul gesucht. Die Analyse-Infrastruktur-Aufrufe in Ihren Code für bestimmten Code-Modelltypen, damit Ihr Code nur ausgeführt wird, wenn erforderlich und kann sich nur auf die Analyse relevanten Codes konzentrieren.

## <a name="whats-the-problem"></a>Was ist das Problem?

Angenommen, Sie eine Bibliothek mit ImmutableArray angeben (z. B. <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) unterstützen. C#-Entwickler haben viel Erfahrung mit .NET Arrays. Allerdings dazu führen, dass aufgrund der Art der ImmutableArrays Techniken zur leistungsoptimierung und in der Implementierung verwendet werden soll, C#-Entwickler Intuitions Benutzer der Bibliothek zum Schreiben des Codes, wie nachstehend beschrieben. Darüber hinaus werden Benutzer nicht ihre Fehler bis zur Laufzeit angezeigt, die die Qualität Erfahrung ist, die sie in Visual Studio mit .NET vertraut sind.

Benutzer, die mit dem Schreiben von Code wie dem folgenden vertraut sind:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Erstellen leere Arrays aus, um sich mit den nachfolgenden Zeilen des Codes zu füllen und Verwenden von Auflistungsinitialisierer-Syntax vertraut sind C# Entwickler. Allerdings stürzt ab, schreiben den gleichen Code für eine ImmutableArray zur Laufzeit:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Der erste Fehler liegt ImmutableArray-Implementierung mit einer Struktur, um die zugrunde liegenden Datenspeicher zu umschließen. Strukturen müssen parameterlosen Konstruktoren haben, damit `default(T)` Ausdrücke können Strukturen mit allen geben 0 (null) oder null Elemente. Wenn der Code greift auf `b1.Length`, es ist ein NULL-Wert zur Laufzeit Fehler dereferenzieren, da keine zugrunde liegende Speicherarray in Struktur ImmutableArray vorhanden ist. Ist die richtige Vorgehensweise zum Erstellen einer leeren ImmutableArray `ImmutableArray<int>.Empty`.

Der Fehler mit den auflistungsinitialisieren liegt daran, dass die `ImmutableArray.Add` Methodenrückgabe neue Instanzen jedes Mal, die Sie aufrufen. Da ImmutableArrays sich nie ändern, wenn Sie ein neues Element hinzufügen, erhalten Sie ein neues ImmutableArray-Objekt (die Speicher zur Verbesserung der Leistung für eine bereits vorhandene ImmutableArray freigeben kann). Da `b2` verweist auf das erste "immutablearray" vor dem Aufruf `Add()` fünfmal `b2` ist eine Standardoption ImmutableArray. Aufrufen Länge darauf auch Abstürze mit einer Null-Fehler zu dereferenzieren. Die richtige Methode, die eine ImmutableArray zu initialisieren, ohne manuell aufrufen hinzufügen, ist die Verwendung `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Suchen Sie relevante Syntax Knotentypen Ihr Analysemodul auslösen

 Zunächst erstellen Sie den Analyzer zunächst herausfinden Sie, welche Art von "syntaxnode" gesucht werden sollen. Starten Sie die **Syntax Visualizer** aus dem Menü **Ansicht** > **Other Windows** > **Roslyn Syntax Visualizer**.

Platzieren Sie im Editor-Caretzeichen in der Zeile, die deklariert `b1`. Sehen Sie den Syntax Visualizer zeigt Sie befinden sich in einem `LocalDeclarationStatement` Knoten, der die Syntax-Struktur. Dieser Knoten verfügt über eine `VariableDeclaration`, die wiederum hat eine `VariableDeclarator`, wiederum IValidator.h ein `EqualsValueClause`, und schließlich gibt es eine `ObjectCreationExpression`. Wie Sie in der Syntax Visualizer-Struktur der Knoten klicken, werden die Syntax im Editor-Fenster hervorgehoben, damit Sie sehen, dass den Code, der von diesem Knoten dargestellt wird. Die Namen der Typen "syntaxnode" Sub übereinstimmen, die Namen, die in der C#-Grammatik verwendet wird.

## <a name="create-the-analyzer-project"></a>Erstellen des Analyzer-Projekts

Wählen Sie im Hauptmenü **Datei** > **neu** > **Projekt**. In der **neues Projekt** Dialogfeld unter **c#** wählen Sie die Projekte in der linken Navigationsleiste auf **Erweiterbarkeit**, und wählen Sie im rechten Bereich die **Analyzer mit Code Fix** Projektvorlage. Geben Sie einen Namen ein, und bestätigen Sie das Dialogfeld.

Öffnet die Vorlage eine *"diagnosticanalyzer.cs"* Datei. Wählen Sie die Registerkarte "Puffer" Editor. Diese Datei enthält eine Analyse-Klasse (gebildet aus dem Namen des Projekts gegeben haben), die abgeleitet `DiagnosticAnalyzer` (ein Roslyn-API-Typ). Die neue Klasse verfügt über eine `DiagnosticAnalyzerAttribute` deklarieren Ihr Analysemodul ist relevant für die Sprache c#, damit der Compiler ermittelt und das Analysemodul lädt.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Sie können einen Analyzer mit Visual Basic, die c#-Code abzielt implementieren und umgekehrt. Es ist noch wichtiger ist, in der DiagnosticAnalyzerAttribute auswählen, ob Ihr Analysemodul ausgerichtet, eine Sprache oder beides ist. Komplexere Analysen, die ausführliche Modellierung der Sprache erfordern, können nur eine einzelne Sprache abzielen. Wenn Ihr Analysemodul, beispielsweise nur Namen oder den Namen der öffentlichen Member überprüft, kann es möglich, common Language Model verwenden, die, das roslyn in Visual Basic und c# bietet. Z. B. FxCop wird gewarnt, dass eine Klasse implementiert <xref:System.Runtime.Serialization.ISerializable>, aber die Klasse verfügt nicht über die <xref:System.SerializableAttribute> Attribut ist unabhängig von Sprache und für Visual Basic und C#-Code funktioniert.

## <a name="initialize-the-analyzer"></a>Initialisieren des Analyzers

 Scrollen Sie etwas in die `DiagnosticAnalyzer` Klasse finden Sie unter den `Initialize` Methode. Der Compiler ruft diese Methode auf, wenn eine Analyse zu aktivieren. Die Methode akzeptiert eine `AnalysisContext` -Objekt, das können Ihr Analysemodul Kontextinformationen erhalten und Registrieren von Rückrufen für Ereignisse für die Arten von Code, analysieren möchten.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Öffnen Sie eine neue Zeile in dieser Methode, und geben "Context". eine IntelliSense-Vervollständigungsliste angezeigt. Sehen Sie in der Liste stehen viele `Register...` Methoden, um die verschiedenen Arten von Ereignissen behandeln. Z. B. dem ersten Beispiel, `RegisterCodeBlockAction`, Aufrufe zurück an Ihren Code für einen Block, in der Regel Code zwischen den geschweiften Klammern. Registrieren für einen Block ruft auch wieder zu Ihrem Code für die Initialisierung eines Felds, den Wert eines Attributs oder der Wert von einem optionalen Parameter.

Wenn Sie beispielsweise `RegisterCompilationStartAction`, Aufrufe zurück an Ihren Code am Anfang einer Kompilierung, was nützlich ist, wenn Sie über viele Orte Status sammeln möchten. Sie können erstellen eine Datenstruktur, beispielsweise zum Sammeln von alle Symbole verwendet, und jedes Mal, wenn Ihr Analysemodul für einige Syntax oder Symbole und aufgerufen wird, können Sie Informationen zu jedem Speicherort in der Datenstruktur speichern. Wenn Sie aufgrund der Kompilierung beendet wieder aufgerufen werden, können Sie die Speicherorte, die für die Sie gespeichert, z. B. haben um welche Symbole zu melden, der Code von jedem verwendet, Analysieren `using` Anweisung.

Mithilfe der **Syntax Visualizer**, haben Sie gelernt, dass aufgerufen werden, wenn der Compiler eine ObjectCreationExpression verarbeitet werden sollen. Sie verwenden Sie diesen Code, um den Rückruf einzurichten:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Sie registrieren für einen syntaxknoten und Filter für nur Objekt Erstellung syntaxknoten. Gemäß der Konvention verwenden Analyzer Autoren ein Lambda-Ausdrucks, beim Registrieren von Aktionen, die Ihnen hilft, um Analysen zustandslos zu halten. Können Sie das Visual Studio-Feature **Generate From Usage** zum Erstellen der `AnalyzeObjectCreation` Methode. Dies generiert den richtigen Typ des Kontextparameters zu.

## <a name="set-properties-for-users-of-your-analyzer"></a>Legen Sie Eigenschaften für Benutzer Ihres Analysemoduls

Damit das Analysemodul in Visual Studio-Benutzeroberfläche ordnungsgemäß angezeigt wird, suchen Sie nach, und ändern Sie die folgende Codezeile, um Ihr Analysemodul zu identifizieren:

```csharp
internal const string Category = "Naming";
```

Änderung `"Naming"` zu `"API Guidance"`.

Als Nächstes suchen und öffnen Sie die *"Resources.resx"* Datei in Ihrem Projekt mithilfe der **Projektmappen-Explorer**. Sie können eine Beschreibung für den Analyzer, Titel usw. einfügen. Ändern Sie den Wert für alle diese zum `"Don't use ImmutableArray<T> constructor"` jetzt. Können Sie Argumente in der Zeichenfolge für die zeichenfolgenformatierung einfügen ({0}, {1}usw.), und höher, wenn Sie aufrufen `Diagnostic.Create()`, Sie können angeben, ein `params` Array von Argumenten übergeben werden.

## <a name="analyze-an-object-creation-expression"></a>Analysieren einer Objekterstellungsausdruck

Die `AnalyzeObjectCreation` Methode nimmt einen anderen Typ, der durch das Code-Analyzer-Framework bereitgestellten Kontexts. Die `Initialize` Methode `AnalysisContext` können Sie zum Registrieren von Aktionsrückrufen, um das Analysemodul einzurichten. Die `SyntaxNodeAnalysisContext`, hat beispielsweise eine `CancellationToken` , die Sie rund um übergeben können. Wenn ein Benutzer im Editor eingeben startet, wird Roslyn abgebrochen, Analysen, ausgeführte Arbeit zu speichern und die Leistung verbessern. Als weiteres Beispiel ist dieser Kontext eine Knoteneigenschaft, die Erstellung Syntax Objektknoten zurückgibt.

Rufen Sie den Knoten, der Sie davon ausgehen können, der Typ ist für den Sie die syntaxknotenaktion gefiltert:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Starten Sie Visual Studio mit Ihr Analysemodul beim ersten.

Starten Sie Visual Studio durch Erstellen und Ausführen Ihrer Analyzer (drücken Sie die **F5**). Da die Startup-Projekt der **Projektmappen-Explorer** wird das VSIX-Projekt, das Ihren Code Builds ausgeführt, Ihren Code und einer VSIX-Datei, und klicken Sie dann startet Visual Studio mit dieser VSIX installiert. Beim Starten von Visual Studio auf diese Weise wird gestartet mit einer unterschiedlichen Registrierungsstruktur, damit Ihr Hauptverwendungszweck von Visual Studio nicht von Ihrer testen Instanzen betroffen sind beim Erstellen von Analysen. Beim ersten Sie auf diese Weise starten führt Visual Studio ähnlich wie Visual Studio gestartet nach der Installation von mehreren Initialisierungen.

Erstellen Sie ein Konsolenprojekt, und geben Sie dann die Array-Code in Ihre Konsole Anwendungen Main-Methode:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Die Zeilen des Codes mit `ImmutableArray` Wellenlinien haben, müssen Sie das unveränderliche NuGet-Paket abrufen und Hinzufügen einer `using` Anweisung, um Ihren Code. Drücken Sie die Zeiger nach rechts-Taste auf den Projektknoten in der **Projektmappen-Explorer** , und wählen Sie **NuGet-Pakete verwalten**. Klicken Sie im NuGet-Manager, geben Sie "Unveränderlich" in das Suchfeld, und wählen Sie das Element **System.Collections.Immutable** (Wählen Sie nicht **Microsoft.Bcl.Immutable**) im linken Bereich, und drücken Sie die  **Installieren Sie** Schaltfläche im rechten Bereich. Installieren des Pakets, fügt einen Verweis auf die Projektverweise hinzu.

Sie sehen immer noch rote Wellenlinien unter `ImmutableArray`, daher platzieren Sie den Textcursor in diesem Bezeichner und drücken Sie **STRG**+**.** (Punkt), rufen Sie das Menü "vorgeschlagene Lösung", und wählen Sie zum Hinzufügen der entsprechenden `using` Anweisung.

**Speichern und schließen** die zweite Instanz von Visual Studio jetzt, um Sie in einen fehlerfreien Zustand weiterhin einfügen.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Beenden Sie den Analyzer, die mit dem Bearbeiten und fortfahren

Legen Sie in der ersten Instanz von Visual Studio einen Haltepunkt am Anfang Ihrer `AnalyzeObjectCreation` Methode durch Drücken von **F9** mit dem Caretzeichen in der ersten Zeile.

Starten Sie Ihr Analysemodul mit **F5**, und in der zweiten Instanz von Visual Studio, öffnen Sie die Konsolenanwendung, die Sie zuletzt erstellt.

Sie zurück zur ersten Instanz von Visual Studio die Ausführung am Haltepunkt, da der Roslyn-Compiler eine Objekterstellungsausdruck gesehen und in Ihr Analysemodul aufgerufen.

**Ruft den Knoten des Objekt erstellen.** Überspringen Sie die Zeile, die festlegt der `objectCreation` Variable durch Drücken von **F10**, und klicken Sie in der **Direktfenster** wertet den Ausdruck `"objectCreation.ToString()"`. Sie sehen, dass die syntaxknoten, die die Variable verweist auf den Code `"new ImmutableArray<int>()"`, einfach was Sie suchen.

**Abrufen von ImmutableArray < T\> Typobjekt.** Sie müssen überprüfen, ob der erstellte Typ wird ImmutableArray ist. Zunächst rufen Sie das Objekt, das diesen Typ darstellt. Überprüfen Sie Sie Typen, die das semantische Modell verwenden, um sicherzustellen, dass Sie genau den richtigen Typ, und Sie nicht die Zeichenfolge aus vergleichen `ToString()`. Geben Sie die folgende Codezeile am Ende der Funktion:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Sie festlegen, generische Typen in den Metadaten mit Graviszeichen (') und die Anzahl der generischen Parameter. Dies ist deshalb nicht angezeigt werden "... ImmutableArray\<T > "in der Name der Metadaten.

Das semantische Modell weist viele nützliche Aufgaben auf, mit denen Sie Fragen zu Symbole, den Datenfluss, die Lebensdauer der Variablen usw. an. Roslyn trennt syntaxknoten aus dem Semantikmodell aus verschiedenen Gründen engineering (Leistung, Modellieren von fehlerhaften Code usw.). Das Kompilierungsmodell in Verweise korrekt Vergleich enthaltenen Informationen gesucht werden sollen.

Sie können der gelben Ausführungszeiger auf der linken Seite des Editorfensters ziehen. Ziehen Sie es in der Zeile aus, setzt der `objectCreation` Variable und Überspringen von Code mit Ihrer neuen Zeile **F10**. Wenn Sie den Mauszeiger auf die Variable zeigen `immutableArrayOfType`, sehen Sie, dass wir den exakten Typ finden Sie in das semantische Modell.

**Rufen Sie die Objekterstellungsausdruck-Typ.** "Type" wird auf verschiedene Weise in diesem Artikel verwendet, aber dies bedeutet bei "neue Foo" Ausdruck ist, benötigen Sie ein Modell von "Foo". Sie müssen den Typ des der Objekterstellungsausdruck, um festzustellen, ob es sich um das "immutablearray" ist\<T > Typ. Verwenden Sie das semantische Modell erneut, um Symbolinformationen für die Typ-Symbol ("ImmutableArray") in der Objekterstellungsausdruck abzurufen. Geben Sie die folgende Codezeile am Ende der Funktion:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Da das Analysemodul unvollständigen oder falschen Code im Editor-Puffern behandeln muss (beispielsweise besteht ein fehlendes `using` Anweisung), sollten Sie überprüfen, für die `symbolInfo` wird `null`. Müssen Sie einen benannten Typ (INamedTypeSymbol) abrufen aus dem Symbol Information-Objekt zum Abschluss der Analyse.

**Vergleichen Sie die Typen.** Da es ist ein offener generischer Typ t, den wir suchen und der Typ im Code eine konkrete generischer Typ ist, wird Sie Abfragen die Symbolinformationen für die Art aus (ein offener generischer Typ) erstellt wird und vergleichen das Ergebnis mit `immutableArrayOfTType`. Geben Sie Folgendes am Ende der Methode ein:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Die Diagnose zu melden.** Melden der Diagnose ist ziemlich einfach. Sie verwenden die Regel, die für Sie erstellt werden, in der Projektvorlage, die vor der Initialize-Methode definiert ist. Da dies im Code einen Fehler handelt, können Sie ändern Sie die Zeile, die mit dieser Regel werden ersetzen initialisiert `DiagnosticSeverity.Warning` (grüne schlängellinie) mit `DiagnosticSeverity.Error` (rote Wellenlinie). Der Rest der Regel initialisiert aus den Ressourcen, die Sie am Anfang dieser exemplarischen Vorgehensweise bearbeitet haben. Außerdem müssen Sie den Speicherort, damit der Schnörkel, zu melden, die der Speicherort der Objekterstellungsausdruck Typspezifikation ist. Geben Sie diesen Code in die `if` blockieren:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Die Funktion sollte wie folgt die (möglicherweise anders formatiert) aussehen:

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Entfernen Sie den Haltepunkt, damit Sie können finden Sie unter Ihrem Analyzer verwenden (und die Rückgabe an die erste Instanz von Visual Studio zu beenden). Ziehen Sie den Ausführungszeiger an den Anfang der Methode, und drücken Sie **F5** um die Ausführung fortzusetzen. Wenn Sie sich an die zweite Instanz von Visual Studio wechseln, wird der Compiler wird gestartet, um den Code erneut zu überprüfen, und Ihr Analysemodul aufgerufen wird. Sehen Sie eine Wellenlinie unter `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Hinzufügen von "Codefixing" für das Codeproblem

Bevor Sie beginnen, schließen Sie die zweite Instanz von Visual Studio, und beenden Sie des Debuggens in die erste Instanz von Visual Studio (wobei Sie den Analyzer entwickeln).

**Fügen Sie eine neue Klasse hinzu.** Verwenden Sie das Kontextmenü (Zeiger nach rechts-Taste), auf den Projektknoten in der **Projektmappen-Explorer** , und wählen Sie ein neues Element hinzufügen. Fügen Sie eine Klasse namens `BuildCodeFixProvider`. Diese Klasse muss für die Ableitung `CodeFixProvider`, und Sie müssen mit **STRG**+**.** (Punkt), die Codefehlerbehebung aufzurufen, die den richtigen fügt `using` Anweisung. Diese Klasse muss außerdem mit Anmerkung versehen sein `ExportCodeFixProvider` -Attribut, und Sie müssen Hinzufügen einer `using` Anweisung zum Auflösen der `LanguageNames` Enum. Sie sollten eine Klassendatei mit dem folgenden Code darin haben:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Ich den Abriss abgeleiteten Elemente.** Jetzt Zirkumflexzeichen des Editors im Bezeichner `CodeFixProvider` , und drücken Sie **STRG**+**.** (Punkt), um die Implementierung dieser abstrakten Basisklasse stub. Dadurch wird eine Eigenschaft und eine Methode für Sie generiert.

**Implementieren Sie die Eigenschaft an.** Geben Sie die `FixableDiagnosticIds` Eigenschaft `get` Text mit den folgenden Code:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn vereint die Diagnose und korrigiert, indem die übereinstimmenden diese Bezeichner, die nur Zeichenfolgen sind. Die Projektvorlage eine Diagnose-ID für Sie generiert, und Sie sind kostenlos, um ihn zu ändern. Der Code in die Eigenschaft gibt nur die ID von der Analyzer-Klasse zurück.

**Die RegisterCodeFixAsync-Methode nimmt es sich um einen Kontext an.** Der Kontext ist wichtig, da es sich bei eine Codefehlerbehebung kann für mehrere Diagnose gelten, oder es kann mehr als ein Problem in einer Zeile des Codes. Bei der Eingabe von "Context". im Text der Methode zeigt die IntelliSense-Vervollständigungsliste einige nützliche Member. Es ist ein CancellationToken-Element, das Sie überprüfen können, um festzustellen, ob etwas das Update abbrechen möchte. Es ist ein Dokument-Element, das verfügt über viele nützliche Member und können Sie in der Modellobjekte Projekt- und Projektmappendateien abrufen. Ist es ein Span-Element, das den Anfang und Ende der Code-Ort angegeben, wenn Sie die Diagnose gemeldet.

**Stellen Sie die Methode asynchron sein.** Die erste, was Sie tun müssen ist, beheben Sie die generierte Methode-Deklaration, um eine `async` Methode. Die Codefehlerbehebung für das Ausführen eines Stubs für die Implementierung einer abstrakten Klasse sind nicht enthalten. die `async` Schlüsselwort, obwohl die Methode gibt eine `Task`.

**Das Stammelement der Syntaxstruktur abrufen.** Macht Ihren Codefix, Code zu ändern, Sie eine neue Syntaxstruktur mit den Änderungen zu erzeugen müssen. Sie müssen die `Document` aus dem Kontext aufgerufen `GetSyntaxRootAsync`. Dies ist eine asynchrone Methode, da unbekannte Arbeit zum Abrufen der Syntaxstruktur, die möglicherweise auch die Datei vom Datenträger abgerufen, analysieren und erstellen die Roslyn-Codemodell dafür vorliegt. Die Benutzeroberfläche von Visual Studio muss während dieser Zeit, da hierbei die Reaktionsfähigkeit `async` ermöglicht. Ersetzen Sie die Zeile des Codes in der Methode durch Folgendes:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Suchen Sie den Knoten mit dem Problem.** Sie übergeben den Kontext für die Spanne, aber den Knoten, den Sie finden den Code möglicherweise nicht, die, den Sie ändern müssen. Die gemeldete Diagnose wird nur die Spanne für die Typ-ID (wobei die Wellenlinie gehörte) bereitgestellt, aber Sie müssen die gesamte Objekterstellungsausdruck, ersetzen einschließlich der `new` Schlüsselwort an die Anfangs- und die Klammern am Ende. Fügen Sie den folgenden Code an Ihre Methode (und **STRG**+**.** Hinzufügen einer `using` -Anweisung für `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrieren Sie Ihr Codefix für die Glühbirne Benutzeroberfläche.** Wenn Sie Ihren Codefix registrieren, schließt Roslyn automatisch an die Visual Studio-Glühbirne Benutzeroberfläche an. Endbenutzer sehen können **STRG**+**.** (Punkt), wenn Ihr Analysemodul ein ungültiger Wellenlinien `ImmutableArray<T>` Konstruktor verwenden. Da Ihr Code Fix-Anbieter nur ausgeführt wird, wenn ein Problem vorliegt, können Sie davon ausgehen, dass Sie die Objekterstellungsausdruck verfügen, die Sie suchen. Aus dem Kontextparameter, können Sie die neue Codefehlerbehebung registrieren, indem Sie den folgenden Code am Ende hinzufügen `RegisterCodeFixAsync` Methode:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Müssen Sie dem Bezeichner des Editors Einfügemarke direktes `CodeAction`, verwenden Sie dann **STRG**+**.** (Punkt), zum Hinzufügen der entsprechenden `using` Anweisung für diesen Typ.

Legen Sie die Einfügemarke des Editors, in der `ChangeToImmutableArrayEmpty` Bezeichner und Verwendung **STRG**+**.** erneut aus, um dieser Methodenstub für Sie generiert.

Dieser letzte Codeausschnitt hinzugefügten registriert die Codefehlerbehebung durch Übergeben einer `CodeAction` und die Diagnose-ID für die Art von Problem gefunden. In diesem Beispiel ist nur eine Diagnose-ID, die diesen Code bereitstellt, korrigiert, sodass Sie nur das erste Element des Arrays diagnostische IDs übergeben können. Bei der Erstellung der `CodeAction`, übergeben Sie den Text, der die Glühbirne Benutzeroberfläche als eine Beschreibung für die Codefehlerbehebung verwenden soll. Sie übergeben außerdem in einer Funktion, die von einem CancellationToken, und gibt ein neues Dokument. Das neue Dokument verfügt über eine neue Syntaxstruktur, die gepatchten Code enthält, die aufruft `ImmutableArray.Empty`. Diesem Codeausschnitt wird einen Lambda-Ausdruck, damit es über den Knoten ObjectCreation und den Kontext des Dokuments zu schließen.

**Erstellen Sie die neue Syntaxstruktur.** In der `ChangeToImmutableArrayEmpty` Methode, deren Stub, die Sie zuvor generiert Geben Sie die Zeile des Codes: `ImmutableArray<int>.Empty;`. Bei der Anzeige der **Syntax Visualizer** Toolfenster in diesem Fall sehen Sie diese Syntax ist ein SimpleMemberAccessExpression-Knoten. Das ist Was muss diese Methode erstellen und in einem neuen Dokument zurückzukehren.

Die erste Änderung am `ChangeToImmutableArrayEmpty` hinzufügen `async` vor `Task<Document>` , da der Code-Generatoren können nicht davon ausgehen sollte die Methode asynchron sein.

Geben Sie den Text durch den folgenden Code, damit Ihre Methode sieht etwa wie folgt aus:

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

Sie müssen für die Anmerkung der Redaktion Einfügemarke die `SyntaxGenerator` Bezeichner und Verwendung **STRG**+**.** (Punkt), zum Hinzufügen der entsprechenden `using` Anweisung für diesen Typ.

Dieser Code verwendet `SyntaxGenerator`, d.h. ein nützlich zum Erstellen von neuen Codes. Nachdem der erste eines Generators für das Dokument, das den Code, erleidet `ChangeToImmutableArrayEmpty` Aufrufe `MemberAccessExpression`, übergeben Sie den Typ, der das Element verfügt, wir zugreifen möchten, und übergeben Sie den Namen des Elements als Zeichenfolge.

Als Nächstes die Methode ruft den Stamm des Dokuments ab, und da dies mit beliebigen arbeiten im Allgemeinen umfassen kann, wird der Code wartet auf diesen Aufruf und übergibt das Abbruchtoken. Roslyn-Codemodelle sind unveränderlich, wie das Arbeiten mit einer Zeichenfolge für .NET. Wenn Sie die Zeichenfolge aktualisieren, erhalten Sie ein neues Zeichenfolgenobjekt im Gegenzug. Beim Aufruf `ReplaceNode`, erhalten Sie einen neuen Stammknoten. Die meisten der Syntaxstruktur freigegeben ist (weil er unveränderlich ist), aber die `objectCreation` Knoten ersetzt wird, mit der `memberAccess` Knoten sowie alle übergeordneten Knoten bis zum Stamm Syntax-Struktur.

## <a name="try-your-code-fix"></a>Versuchen Sie es Ihren Codefix

Sie können jetzt drücken **F5** das Analysemodul in eine zweite Instanz von Visual Studio ausführen. Öffnen Sie das Konsolenprojekt, die, dem Sie zuvor verwendet. Nachdem Sie, dass die Glühbirne angezeigt sehen sollten, in denen Ihre neuen Objekterstellungsausdruck ist `ImmutableArray<int>`. Wenn Sie drücken **STRG**+**.** (Punkt), sehen Sie Ihren Code zu beheben, und Sie sehen eine Vorschau des automatisch generierten Code-Unterschied in der Glühbirne Benutzeroberfläche. Roslyn, die dies für Sie erstellt haben.

**Pro-Tipps:** Wenn Sie die zweite Instanz von Visual Studio starten, und Sie nicht die Glühbirne, mit Ihren Codefix angezeigt, müssen Sie den Visual Studio-Komponente-Cache zu löschen. Zum Löschen des Zwischenspeichers erzwingt, dass Visual Studio, um die Komponenten neu zu überprüfen, damit Visual Studio und die aktuelle Komponente Adresse sollte. Fahren Sie zunächst die zweite Instanz von Visual Studio. Klicken Sie auf **Windows Explorer**, navigieren Sie zu *%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn\\*. (Die "16.0" ändert sich von Version zu Version mit Visual Studio.) Löschen Sie das Unterverzeichnis *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Sprechen Sie Video- und schließen Sie Codeprojekt

Sie finden dieses Beispiel entwickelte und erläutert weiter in [dieser Vortrag](https://channel9.msdn.com/events/Build/2015/3-725). Die Rede veranschaulicht, den Analyzer arbeiten und führt Sie durch die Erstellung.

Sie sehen alle fertig gestellten Code [hier](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Der Unterordner *DoNotUseImmutableArrayCollectionInitializer* und *DoNotUseImmutableArrayCtor* für jedes eine C#-Datei für die Suche nach Problemen und eine C#-Datei, die den Code implementiert korrigiert, die erscheinen der Visual Studio-Glühbirne Benutzeroberfläche. Beachten Sie, dass der komplette Code ist etwas mehr Abstraktion, vermeiden Sie das "immutablearray"\<T >-Objekt immer wieder eingeben. Geschachtelte registrierte Aktionen verwendet, um die Typ-Objekt in einem Kontext zu speichern, die verfügbar ist immer die Sub-Aktionen (Analysieren der objekterstellung und Analysieren Auflistung Initialisierungen) ausführen.

## <a name="see-also"></a>Siehe auch

* [\\\Build 2015 sprechen](https://channel9.msdn.com/events/Build/2015/3-725)
* [Abgeschlossene Code auf GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Beispiele auf GitHub an, gruppiert drei Arten von Analysen](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Weitere Dokumente auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [FxCop-Regeln, die mit Roslyn-Analysetools auf GitHub implementiert](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
