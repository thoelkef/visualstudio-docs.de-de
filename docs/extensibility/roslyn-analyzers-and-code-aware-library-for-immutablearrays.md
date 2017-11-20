---
title: "Roslyn-Analyzer und Code unterstützende Clientbibliothek für ImmutableArrays | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b33516bd013f744813b2fdb357f224bcb0d9822
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn-Analyzer und Code unterstützende Clientbibliothek für ImmutableArrays

Die [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") hilft Ihnen, Code-fähigen Bibliotheken zu erstellen.  Eine Code-fähigen Bibliothek bietet Funktionalität, die Sie verwenden können, und Tools (Roslyn-Analysen), können Sie die Bibliothek, in die beste Möglichkeit oder Fehler zu vermeiden.  Dieses Thema veranschaulicht das Erstellen eines realen Roslyn Analyzers zum Abfangen von häufigen Fehlern bei Verwendung der [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet-Paket.  Darüber hinaus wird veranschaulicht, wie eine Codekorrektur für eine vom Analyzer gefundenes Code bereitstellen.  Benutzer sehen Codekorrekturen in der Visual Studio-Glühbirne Benutzeroberfläche und eine Korrektur für den Code automatisch anwenden können.

## <a name="getting-started"></a>Erste Schritte

Erstellen in diesem Beispiel wird Folgendes benötigt:

* Visual Studio 2015 (keine Express Edition) oder eine höhere Version.  Sie können die kostenlose [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  Sehen Sie sich auch bei der Installation von Visual Studio, Visual Studio-Erweiterbarkeitstools unter häufig verwendete Tools zur gleichen Zeit das SDK zu installieren.  Wenn Sie Visual Studio bereits installiert haben, können Sie auch dieses SDK installieren, navigieren Sie zu der Sie im Hauptmenü **Datei &#124; Neue &#124; Projekt...** c# im linken Navigationsbereich, klicken Sie dann auswählen und Erweiterbarkeit.  Bei Auswahl der "**installieren Sie Visual Studio-Erweiterbarkeitstools**" Breadcrumb-Projektvorlage, sie werden aufgefordert, das SDK heruntergeladen und installiert.
* [.NET Compiler Platform ("Roslyn") SDK](http://aka.ms/roslynsdktemplates).  Sie können auch dieses SDK installieren, navigieren Sie zu der Sie im Hauptmenü **Datei &#124; Neue &#124; Projekt...** , Auswahl der Option **c#** in den linken Navigationsbereich, auswählen und dann **Erweiterbarkeit**.  Bei Auswahl "**.NET Compiler Platform SDK downloaden**" Breadcrumb-Projektvorlage, sie werden aufgefordert, das SDK heruntergeladen und installiert.  Dieses SDK enthält die [Roslyn Syntax Schnellansicht](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Diesem äußerst nützlich Tool können Sie herausfinden, welche Modelltypen Code sollten Sie in Ihrer Analyzer gesucht.  Der Analyzer ruft in Ihren Code für bestimmten Code Modelltypen, damit Ihr Code nur ausgeführt wird, wenn erforderlich und kann sich nur auf die Analyse relevante Code konzentrieren.

## <a name="whats-the-problem"></a>Was ist das Problem?

Angenommen, Sie geben eine Bibliothek mit ImmutableArray (z. B. <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) unterstützen.  C#-Entwickler über viel Erfahrung mit .NET Arrays verfügen.  Jedoch bewirken, dass aufgrund der Natur der ImmutableArrays Techniken zur leistungsoptimierung und in der Implementierung verwendet werden soll, C#-Entwickler Intuitions Benutzer Ihrer Bibliothek fehlerhaften Code schreiben, wie nachstehend beschrieben.  Darüber hinaus Benutzern nicht ihre Fehler bis zur Laufzeit angezeigt, die nicht die Qualität ist, die sie in Visual Studio mit .NET zu verwendet werden.

Benutzer, die mit dem Schreiben von Code wie den folgenden vertraut sind:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Erstellen leere Arrays, die sich mit nachfolgenden Codezeilen füllen und Verwenden von Auflistungsinitialisierersyntax sind sehr vertraut, C#-Entwickler.  Allerdings stürzt ab, dem Schreiben Code für eine ImmutableArray zur Laufzeit:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Der erste Fehler ist aufgrund von ImmutableArray-Implementierung mit einer Struktur, um die zugrunde liegenden Datenspeicher zu umschließen. Strukturen parameterlosen Konstruktoren verfügen müssen, damit `default(T)` Ausdrücke können mit allen Strukturen zurückgeben 0 (null) oder null Elemente.  Wenn der Code greift auf `b1.Length`, es ist ein NULL-Wert zur Laufzeit Fehler dereferenzieren, da keine zugrunde liegende Speicherarray in der Struktur ImmutableArray vorliegt.  Ist die korrekte Methode zum Erstellen einer leeren ImmutableArray `ImmutableArray<int>.Empty`.

Der Fehler mit Auflistungsinitialisierer liegt daran, dass der ImmutableArray.Add neue Instanzen jedes Mal Methodenrückgabe Sie sie aufrufen.  Da ImmutableArrays nie ändern, wenn Sie ein neues Element hinzufügen, erhalten Sie ein neues ImmutableArray-Objekt (die Speicher zur Verbesserung der Leistung für eine bereits vorhandene ImmutableArray freigeben kann).  Da `b2` verweist auf die erste ImmutableArray vor dem Aufruf `Add()` fünf Mal `b2` ist eine Standardoption ImmutableArray.  Fehler dereferenzieren aufrufen Länge darauf auch Abstürze (crashes), einen NULL-Wert.  Die richtige Methode, eine ImmutableArray zu initialisieren, ohne manuell Aufrufs von Add ist die Verwendung `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Suchen relevante Syntax Knotentypen zum Auslösen der Analyzer

 Um zu beginnen, erstellen den Analyzer, zunächst herausfinden Sie, welche Art von SyntaxNode gesucht werden sollen. Starten Sie die Syntax Schnellansicht aus dem Menü **View &#124; Anderen Windows &#124; Roslyn-Syntax Schnellansicht**.

Platzieren Sie den Editor bspw. in der Zeile, die deklariert `b1`.  Sehen Sie die Schnellansicht Syntax zeigt Sie befinden sich in einem `LocalDeclarationStatement` Knoten der Syntaxstruktur.  Dieser Knoten verfügt über eine `VariableDeclaration`, wiederum verfügt über eine `VariableDeclarator`, wiederum enthält ein `EqualsValueClause`, und schließlich folgt eine `ObjectCreationExpression`.  Wenn Sie in der Schnellansicht Syntax-Struktur der Knoten klicken, werden die Syntax im Editor-Fenster zum Anzeigen von des von diesem Knoten dargestellten Codes hervorgehoben.  Die Namen der SyntaxNode Sub Typen mit den Namen, die in der C#-Grammatik verwendet übereinstimmen.

## <a name="creating-the-analyzer-project"></a>Erstellen des Projekts Analyzer

Wählen Sie im Hauptmenü **Datei &#124; Neue &#124; Projekt...** .  In der **neues Projekt** Dialogfeld unter **c#** Projekte in der linken Navigationsleiste Erweiterbarkeit auswählen, und wählen Sie im rechten Bereich die **Analyzer mit Code korrigiert haben** Projekt Vorlage.  Geben Sie einen Namen ein, und bestätigen Sie das Dialogfeld ".

Die Vorlage wird eine DiagnosticAnalyzer.cs-Datei geöffnet.  Wählen Sie diese Editor Puffer Registerkarte aus.  Diese Datei weist eine Analyzer-Klasse (gebildet aus dem Namen des Projekts zugewiesen haben), die abgeleitet `DiagnosticAnalyzer` (ein Roslyn-API-Typ).  Die neue Klasse verfügt über eine `DiagnosticAnalyzerAttribute` Deklarieren der Analyzer spielt der C#-Sprache, damit der Compiler erkennt und die Analyzer lädt.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Sie können einen Analyzer mit Visual Basic, die auf C#-Code, implementieren und umgekehrt.  Es ist wichtiger bei der DiagnosticAnalyzerAttribute auswählen, ob Ihre Analyzer eine Sprache oder beides als Ziel verwendet.  Komplexere Analysen, die detaillierte Modellierung der Sprache erfordern, können nur eine einzelne Sprache abzielen.  Wenn Ihre Analyzer, z. B. nur Typnamen oder öffentlichen Elementnamen überprüft, kann es möglich, verwenden Sie das Datenmodell der common Language Roslyn in Visual Basic und c# bietet.  Z. B. FxCop wird gewarnt, dass eine Klasse implementiert <xref:System.Runtime.Serialization.ISerializable>, aber die Klasse verfügt nicht über die <xref:System.SerializableAttribute> Attribut ist unabhängig von Sprache und eignet sich für Visual Basic- und C#-Code.

## <a name="initalizing-the-analyzer"></a>Initialisieren der Analyzer

 Führen Sie einen Bildlauf nach unten etwas der `DiagnosticAnalyzer` Klasse finden Sie unter der `Initialize` Methode.  Der Compiler ruft diese Methode einen Analyzer aktivieren möchten.  Die Methode nimmt ein `AnalysisContext` Objekt, das ermöglicht Ihrem Analyzer Kontextinformationen nutzen und Rückrufe für Ereignisse für die Arten von Code registrieren Sie analysieren möchten.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Öffnen Sie eine neue Zeile in dieser Methode und Typ "Kontext." eine IntelliSense-Vervollständigungsliste angezeigt.  Sehen Sie in der Vervollständigungsliste stehen viele `Register...` Methoden, um verschiedene Arten von Ereignissen zu behandeln.  Z. B. die erste Vorlage `RegisterCodeBlockAction`, Aufrufe zurück an den Code für ein Block, der in der Regel wird der Code zwischen den geschweiften Klammern.  Registrieren für einen Block ruft auch wieder in den Code für die Initialisierung eines Felds, der auf ein Attribut angegebene Wert oder den Wert eines optionalen Parameters.

Wenn Sie beispielsweise `RegisterCompilationStartAction`, Aufrufe zurück an den Code am Anfang einer Kompilierung, was nützlich ist, wenn Sie über viele Speicherorte erfassen müssen.  Sie können eine Datenstruktur, z. B. zum Erstellen erfassen alle Symbole verwendet, und jedes Mal, wenn Ihre Analyzer für einige Syntax oder Symbole und aufgerufen wird, können Sie Informationen zu jedem Speicherort in der Datenstruktur speichern.  Wenn Sie wieder aufgrund der Kompilierung Ende aufgerufen, können Sie die Speicherorte, die Sie gespeichert haben, z. B. um welche Symbole zu melden, der Code von jedem verwendet, Analysieren `using` Anweisung.

Mithilfe der **Syntax Schnellansicht**, haben Sie gelernt, die aufgerufen werden, wenn der Compiler eine ObjectCreationExpression verarbeitet werden sollen.  Der Rückruf einrichten, verwenden Sie diesen Code:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Registrieren Sie sich für einen Syntax-Knoten und Filter für nur Erstellung Syntax Objektknoten.  Gemäß der Konvention verwenden Analyzer Autoren ein Lambda-Ausdrucks, beim Registrieren von Aktionen, bei denen hilft, um Analyzern zustandslos zu schützen.  Können Sie die Visual Studio-Funktionalität **Generate From Usage** zum Erstellen der `AnalyzeObjectCreation` Methode.  Dies erzeugt den richtigen Typ des Context-Parameters zu.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Festlegen von Eigenschaften für Benutzer von Ihrem Analyzer

So, dass Ihre Analyzer in Visual Studio-Benutzeroberfläche entsprechend wird angezeigt, suchen Sie nach, und ändern Sie die folgende Codezeile zur Identifizierung Ihrer Analyzer:

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

Als Nächstes suchen und öffnen Sie die `Resources.resx` Datei in Ihrem Projekt mithilfe der **Projektmappen-Explorer**.  Sie können eine Beschreibung für den Analyzer, Titel usw. einfügen.  Ändern Sie den Wert für alle Attribute auf `"Don't use ImmutableArray<T> constructor"` vorläufig.  Können Sie Argumente in der Zeichenfolge ({0}, \ {1\} usw.), für die zeichenfolgenformatierung einfügen und höher, wenn Sie aufrufen `Diagnostic.Create()`, Sie können angeben, ein `params` Array von Argumenten, die übergeben werden.

## <a name="analyzing-an-object-creation-expression"></a>Analysieren einer Objekterstellungsausdruck

Die `AnalyzeObjectCreation` Methode nimmt einen anderen Typ des Kontexts, die vom Code-Analyzer-Framework bereitgestellt.  Der Initialize-Methode `AnalysisContext` ermöglicht Ihnen, Aktion Rückrufe zum Einrichten Ihrer Analyzer zu registrieren.  Die `SyntaxNodeAnalysisContext`, hat beispielsweise eine `CancellationToken` , die Sie Um übergeben können.  Wenn ein Benutzer startet die Eingabe im Editor, Abbrechen Roslyn ausgeführte Analysen, um die Arbeit zu speichern und zu verbessern.  Ein weiteres Beispiel ist diesem Kontext eine Knoteneigenschaft, die den Objekt Erstellung Syntax-Knoten zurückgibt.

Rufen Sie den Knoten, der für Sie davon ausgehen können, der Typ ist für den Aktion der Syntax-Knoten gefiltert:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Starten Visual Studio mit der Analyzer erstmalig

Starten Sie Visual Studio durch Erstellen und Ausführen Ihrer Analyzer (drücken Sie **F5**).  Weil das Startup-Projekt in der **Projektmappen-Explorer** Builds Code ausführen, Code und eine VSIX VSIX-Projekts ist, und startet anschließend Visual Studio mit diesem VSIX installiert.  Beim Starten von Visual Studio auf diese Weise gestartet mit einer unterschiedlichen Registrierungsstruktur, damit der Hauptverwendungszweck von Visual Studio nicht von Ihrer testen Instanzen betroffen sind beim Erstellen von Analysen.  Beim ersten Starten Sie auf diese Weise wird Visual Studio mehrere Initialisierungen ähnelt, wenn Sie zuerst Visual Studio gestartet haben sie nach der Installation.

Erstellen eines Konsolen-Projekts, und geben Sie dann den Array-Code in der Konsole Anwendungen Main-Methode:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Die Zeilen des Codes mit `ImmutableArray` Wellenlinien haben, da müssen Sie erhalten das unveränderliche NuGet-Paket und Hinzufügen einer `using` Anweisung, um Ihren Code.  Drücken Sie die Schaltfläche mit den Zeiger nach rechts auf den Projektknoten in der **Projektmappen-Explorer** , und wählen Sie **NuGet-Pakete verwalten...** .  Klicken Sie in der NuGet-Manager "Unveränderlich" in das Suchfeld eingeben, und wählen Sie das Element "System.Collections.Immutable" (Wählen Sie nicht "Microsoft.Bcl.Immutable") im linken Bereich, und drücken Sie im rechten Bereich die Schaltfläche "installieren".  Installieren des Pakets Fügt einen Verweis auf Ihre Projektverweise auf.

Rote Wellenlinien unter weiterhin angezeigt `ImmutableArray`, sodass Einfügen des Caretzeichens in dieser Bezeichner, und drücken Sie **STRG +.** (Punkt), um die vorgeschlagene Korrektur Menü öffnen, und wählen die entsprechende hinzufügen `using` Anweisung.

**Speichern und schließen** die zweite Instanz von Visual Studio jetzt, Sie in einen fehlerfreien Zustand zu fortfahren eingefügt werden soll.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Beenden den Analyzer mit bearbeiten und fortfahren

In der ersten Instanz von Visual Studio, legen Sie einen Haltepunkt am Anfang der `AnalyzeObjectCreation` Methode durch Drücken von **F9** mit dem Caretzeichen auf der ersten Zeile.

Starten Sie Ihre Analyzer mit **F5**, und in der zweiten Instanz von Visual Studio, öffnen Sie erneut die Konsolenanwendung, die Sie zuletzt erstellt.

Sie zurück an die erste Instanz von Visual Studio am Haltepunkt, da der Roslyn-Compiler gesehen eine Objekterstellungsausdruck haben und in Ihre Analyzer aufgerufen.

**Rufen Sie die Erstellung Objektknoten.** Prozedurschritt in der Zeile, der festlegt der `objectCreation` Variable durch Drücken von **F10**, und klicken Sie in der **"Direktfenster"** wertet den Ausdruck `"objectCreation.ToString()"`.  Sie sehen, dass die Syntax-Knoten, die die Variable verweist auf den Code `"new ImmutableArray<int>()"`, nur wonach Sie suchen.

**ImmutableArray Get < T\> Typobjekt.** Sie müssen überprüfen, ob der erstellte Typ wird ImmutableArray ist.  Zunächst erhalten Sie das Objekt, das diesen Typ darstellt.  Sie überprüfen Sie Typen, die das Semantikmodell verwenden, um sicherzustellen, dass Sie genau den richtigen Typ haben und Sie nicht die Zeichenfolge aus ToString() vergleichen.  Geben Sie die folgende Codezeile am Ende der Funktion:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Generische Typen in den Metadaten mit Backquotes (') und die Anzahl der generischen Parameter legen Sie fest.  Aus diesem Grund nicht angezeigt "… ist ImmutableArray\<T > "in der Name der Metadaten.

Das Semantikmodell enthält viele nützliche Informationen, mit denen Sie Fragen zu Symbole, den Datenfluss, die Lebensdauer der Variablen.  Roslyn trennt Syntax-Knoten aus dem Semantikmodell verschiedenen Gründen engineering (Leistung, Modellierung fehlerhaften Code usw.).  Das Kompilierungsmodell in Verweise für den Vergleich genau enthaltenen Informationen gesucht werden sollen.

Sie können auf der linken Seite des Editorfensters der gelben Ausführungszeiger ziehen.  Ziehen Sie es bis zu der Zeile aus, setzt der `objectCreation` Variable und Prozedurschritt in der neuen Zeile der Code mit **F10**.  Wenn Sie den Mauszeiger auf die Variable zeigen `immutableArrayOfType`, sehen Sie, dass wir im Semantikmodell der genaue Typ nicht gefunden.

**Ruft die Objekterstellungsausdruck-Typ ab.** "Type" in mehrere Möglichkeiten, die in diesem Artikel verwendet wird, aber dies bedeutet, wenn Sie "neue Foo" haben Ausdruck, benötigen Sie ein Modell von "Foo".  Ruft den Typ der Objekterstellungsausdruck auf, um festzustellen, ob es die ImmutableArray müssen Sie\<T > Typ.  Verwenden Sie das Semantikmodell erneut, um die Symbolinformationen für das Typsymbol (ImmutableArray) in der Objekterstellungsausdruck abzurufen.  Geben Sie die folgende Codezeile am Ende der Funktion:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Da Ihre Analyzer unvollständig oder falsch Code in Editor Puffern verarbeitet werden muss (z. B. besteht ein fehlendes `using` Anweisung), Sie sollten prüfen `symbolInfo` wird `null`.  Müssen Sie einen benannten Typ (INamedTypeSymbol) erhalten das Symbolobjekt Informationen zum Abschluss der Analyse.

**Vergleichen Sie die Typen.** Da es ist ein offener generischer Typ von T, die wir suchen und der Typ im Code eine konkrete generischer Typ ist, wird Sie Abfragen der Symbolinformationen für die Art von (ein offener generischer Typ) erstellt wird und vergleichen das Ergebnis mit `immutableArrayOfTType`.  Geben Sie Folgendes am Ende der Methode:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Die Diagnose zu melden.** Die Diagnose Reporting ist recht einfach.  Sie verwenden die Regel erstellt, wenn Sie in der Projektvorlage, die vor der Initialize-Methode definiert ist.  Da diese Situation, in der Code einen Fehler handelt, können, ändern Sie die Zeile, die mit dieser Regel werden ersetzen initialisiert `DiagnosticSeverity.Warning` (grüne Wellenlinie eingeblendet) mit `DiagnosticSeverity.Error` (rote Wellenlinie).  Der Rest der Regel werden von den Ressourcen, die Sie am Anfang der exemplarischen Vorgehensweise bearbeitet initialisiert.  Sie müssen auch den Speicherort für die Wellenlinie melden den Speicherort des Objekts Erstellung Aggregatspalte Typspezifikation.  Geben Sie diesen Code in die `if` blockieren:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Die Funktion sollte sieht (möglicherweise unterschiedlich formatiert) wie folgt aus:

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

Entfernen Sie den Haltepunkt, damit Sie können finden Sie unter der Analyzer verwenden (und die Rückgabe an die erste Instanz von Visual Studio beenden).  Ziehen Sie am Anfang der Methode, und drücken Sie die Ausführungszeiger **F5** um die Ausführung fortzusetzen.  Wenn Sie wieder auf die zweite Instanz von Visual Studio wechseln, startet des Compilers den Code erneut zu überprüfen, und er ruft in der Analyzer.  Sehen Sie eine Wellenlinie unter `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Hinzufügen von "Codekorrektur" für das Codeproblem

Bevor Sie beginnen, wird schließen Sie die zweite Instanz von Visual Studio zu, und beenden Sie des Debuggens in der ersten Instanz von Visual Studio (wobei Sie den Analyzer entwickeln).

**Fügen Sie eine neue Klasse hinzu.** Verwenden Sie das Kontextmenü (Schaltfläche Zeiger nach rechts) auf den Projektknoten im Projektmappen-Explorer, und wählen Sie ein neues Element hinzufügen.  Fügen Sie eine Klasse mit dem Namen `BuildCodeFixProvider`.  Diese Klasse muss abgeleitet sein `CodeFixProvider`, und Sie müssen verwenden **STRG +.** (Punkt), um den korrigierten Code aufzurufen, der den richtigen fügt `using` Anweisung.  Diese Klasse muss außerdem mit Anmerkung versehen sein `ExportCodeFixProvider` -Attribut, daher müssen Sie zum Hinzufügen einer `using` Anweisung zum Auflösen der `LanguageNames` Enum.  Sie müssen eine Klassendatei mit den folgenden Code:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub-abgeleitete Member.** Jetzt Zirkumflexzeichen des Editors im Bezeichner `CodeFixProvider` , und drücken Sie **STRG +.** (Punkt), um die Implementierung dieser abstrakten Basisklasse stub.  Dadurch wird eine Eigenschaft und eine Methode für Sie generiert.

**Implementieren Sie die Eigenschaft an.** Füllen Sie die `FixableDiagnosticIds` der Eigenschaft `get` Text mit den folgenden Code:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn vereint Diagnose und behebt, indem die Übereinstimmungen diese Bezeichner, die nur Zeichenfolgen sind.  Die Projektvorlage eine Diagnose-ID für Sie generiert, und Sie sind frei, um ihn zu ändern.  Der Code in der Eigenschaft gibt nur die ID aus der Analyzer-Klasse.

**Die RegisterCodeFixAsync-Methode nimmt einen Kontext.** Der Kontext ist wichtig, da eine Codekorrektur können Sie mehrere Diagnose anzuwenden, oder es mehr als ein Problem in einer Zeile des Codes kann.  Bei der Eingabe von "Kontext". im Text der Methode zeigt die IntelliSense-Vervollständigungsliste einige nützliche Member.  Es ist ein CancellationToken-Element, das Sie überprüfen können, um festzustellen, ob ein Element das Update abbrechen möchte.  Es wird ein Dokument-Element, das verfügt über viele nützliche Member und ermöglicht das an den modellobjekten Projekt- und Projektmappendateien abrufen.  Es ist ein Span-Element, das dem Start und Ende der Speicherort angegeben, wann Sie die Diagnose gemeldet.

**Stellen Sie die Methode asynchron sein.** Im ersten Schritt müssen Sie ist, korrigieren Sie die generierte Methodendeklaration, um eine `async` Methode.  Der korrigierten Code für das Ausführen eines Stubs für die Implementierung einer abstrakten Klasse umfasst jedoch nicht die `async` Schlüsselwort, obwohl die Methode gibt ein `Task`.

**Abrufen des Stamms der Syntaxstruktur.** Macht Ihre Codekorrektur, um Code zu ändern, Sie eine neue Syntaxstruktur mit den Änderungen zu erzeugen müssen.  Sie müssen die `Document` aus dem Kontext aufgerufen `GetSyntaxRootAsync`.  Dies ist eine asynchrone Methode, da die Syntaxstruktur, die möglicherweise auch die Datei vom Datenträger abrufen, analysiert sie und das Codemodell Roslyn dafür erstellen abzurufenden unbekannte Arbeit vorliegt.  Der Visual Studio-Benutzeroberfläche muss während dieser Zeit können hierbei die Reaktionsfähigkeit `async` ermöglicht.  Ersetzen Sie die Codezeile in der Methode, durch Folgendes:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Gefunden Sie der Knoten mit dem Problem werden.** Sie übergeben, in dem Kontext Spanne, aber der Knoten, den Sie finden den Code möglicherweise nicht zu ändern.  Die gemeldete Diagnose wird nur die Spanne für die Typ-ID (wobei die Wellenlinie gehörte) bereitgestellt, aber Sie müssen zum Ersetzen der gesamten Objekterstellungsausdruck einschließlich der `new` -Schlüsselwort am Anfang und die Klammern am Ende.  Fügen Sie den folgenden Code zu Ihrer Methode (und **STRG +.** Hinzufügen einer `using` -Anweisung für `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrieren Sie die korrigierten Code für die Glühbirne UI.** Wenn Sie Ihre Codekorrektur registrieren, Ausgabecacheanbieters Roslyn die Glühbirne für Visual Studio UI automatisch.  Endbenutzer sehen können **STRG +.** (Punkt), wenn Ihre Analyzer einen ungültigen Wellenlinien `ImmutableArray<T>` Konstruktor verwenden.  Da Ihre Korrektur Codeanbieter nur ausgeführt wird, wenn ein Problem vorliegt, können Sie davon ausgehen, dass Sie die Objekterstellungsausdruck verfügen, die Sie suchen.  Sie können die neue Codekorrektur aus dem Kontextparameter registrieren, durch den folgenden Code am Ende hinzufügen `RegisterCodeFixAsync` Methode:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Müssen Sie den Bezeichner des Editors Caretzeichen direktes `CodeAction`, verwenden Sie dann **STRG +.** (Punkt), um die entsprechende hinzufügen `using` -Anweisung für diesen Typ.

Platzieren Sie den Editor Caretzeichen an die `ChangeToImmutableArrayEmpty` Bezeichner und Verwendung **STRG +.** erneut aus, um diese Methodenstub generieren.

Dieses letzten Codeausschnitts, die Sie hinzugefügt haben registriert den korrigierten Code durch Übergeben einer `CodeAction` und die Diagnose-ID für die Art von Problem gefunden.  In diesem Beispiel ist nur ein Diagnose-ID, die mit diesem Code bereitstellt, repariert, sodass Sie nur das erste Element des Arrays diagnostische IDs übergeben können.  Beim Erstellen der `CodeAction`, Sie in den Text, der die Glühbirne UI, als eine Beschreibung für den korrigierten Code verwenden soll übergeben.  Sie übergeben außerdem in einer Funktion, die von einem CancellationToken, und gibt ein neues Dokument.  Das neue Dokument hat eine neue Syntaxstruktur, die gepatchten Code enthält, die aufruft `ImmutableArray.Empty`.  Diesen Codeausschnitt wird einen Lambda-Ausdruck verwendet, sodass es über den Knoten ObjectCreation und den Kontext Dokument zu schließen.

**Erstellen Sie die neue Syntaxstruktur.** In der `ChangeToImmutableArrayEmpty` Methode, deren Stub, die Sie einer Version generiert wurden, geben Sie die Codezeile: `ImmutableArray<int>.Empty;`.  Wenn Sie das Tool Syntax Schnellansichtsfenster wieder möchten anzeigen, können Sie sehen, dass diese Syntax einen SimpleMemberAccessExpression-Knoten ist.  Ist diese Methode herrscht erstellen und in ein neues Dokument zurückzugeben.

Die erste Änderung `ChangeToImmutableArrayEmpty` besteht im hinzufügen `async` vor `Task<Document>` , da der Code-Generatoren davon ausgehen können, sollte die Methode asynchron sein.

Füllen Sie den Text durch den folgenden Code, damit die Methode etwa wie folgt aussieht:

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

Sie müssen der Editor Caretzeichen gelagerte der `SyntaxGenerator` Bezeichner und die Verwendung **STRG +.** (Punkt), um die entsprechende hinzufügen `using` -Anweisung für diesen Typ.

Dieser Code verwendet `SyntaxGenerator`, also ein sehr nützlich zum Erstellen von neuen Code.  Nachdem der erste eines Generators für das Dokument, das das Codeproblem hat `ChangeToImmutableArrayEmpty` Aufrufe `MemberAccessExpression`, übergeben Sie den Typ, der das Element weist wir zugreifen möchten, und übergeben Sie den Namen des Elements als Zeichenfolge.

Als Nächstes die Methode ruft den Stamm des Dokuments, und da dies im allgemeinen Fall beliebige Arbeit umfassen kann, wird der Code wartet auf diesen Aufruf und übergibt das Abbruchtoken.  Roslyn Codemodelle sind unveränderlich, wie das Arbeiten mit einem Zeichenfolgen-.NET. Wenn Sie die Zeichenfolge aktualisieren, erhalten Sie ein neues Zeichenfolgenobjekt im Gegenzug.  Beim Aufruf `ReplaceNode`, erhalten Sie einen neuen Stammknoten.  Die meisten der Syntaxstruktur freigegeben ist (weil es unveränderlich wird), aber die `objectCreation` Knoten ersetzt wird, mit der `memberAccess` Knoten als auch die übergeordneten Knoten bis zum Stamm Syntax-Struktur.

## <a name="trying-your-code-fix"></a>Versuch der Codekorrektur

Sie können jetzt drücken **F5** Ihre Analyzer in eine zweite Instanz von Visual Studio ausführen.  Öffnen Sie die Konsolenprojekt wie vorher.  Nun Sie die Glühbirne angezeigt, in denen Ihre neuen Objekterstellungsausdruck sehen für ist `ImmutableArray<int>`.  Wenn Sie drücken **STRG +.** (Punkt), dann sehen Sie Ihren Code zu beheben, und sehen Sie eine automatisch generierte Code Unterschied Vorschau in die Glühbirne UI.  Roslyn wird dies für Sie erstellt.

**Pro-Tipps:** Wenn Sie die zweite Instanz von Visual Studio starten und Sie nicht die Glühbirne angezeigt, mit der Codekorrektur, müssen Sie möglicherweise den Visual Studio-Komponente-Cache zu leeren.  Das Löschen des Zwischenspeichers erzwingt, dass Visual Studio, um die Komponenten erneut überprüfen, damit Visual Studio dann von der aktuellen Komponente ausgewählt werden soll.  Fahren Sie zunächst die zweite Instanz von Visual Studio.  Wechseln Sie dann im Windows-Explorer zu Ihrem Benutzerverzeichnis (c:\users\\< Userid\>), und suchen Sie AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  Löschen Sie in diesem Verzeichnis das Sub-Verzeichnis ComponentModelCache.  Die "14" ändert sich je nach Version mit Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Wenden Sie sich Videos und Codeprojekt Fertig stellen

Sie finden dieses Beispiel entwickelt und erläutert in weiteren [dieser Talk](http://channel9.msdn.com/events/Build/2015/3-725).  Die Talk veranschaulicht den Analyzer arbeiten und führt Sie schrittweise durch die Erstellung.

Sie können den fertigen Code finden Sie unter [hier](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Der Unterordner DoNotUseImmutableArrayCollectionInitializer und DoNotUseImmutableArrayCtor haben eine C#-Datei für die Suche nach Problemen und einer C#-Datei, die vom Code behoben, die in der Visual Studio-Glühbirne Benutzeroberfläche angezeigt implementiert werden.  Beachten Sie, dass die fertige Code hat ein wenig mehr Abstraktionsebene, um zu vermeiden, das Abrufen der ImmutableArray\<T >-Objekt wiederholt und umfassend geben.  Geschachtelte registrierte Aktionen verwendet, um das Typobjekt in einem Kontext zu speichern, die verfügbar ist immer das Sub-Aktionen (objekterstellung zu analysieren und Analysieren der Auflistung Initialisierungen) ausführen.

## <a name="see-also"></a>Siehe auch

* [\\Wenden Sie sich \Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
* [Abgeschlossene Code auf GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Beispielen auf GitHub, die in drei Arten von Analysen gruppiert](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Andere Dokumente auf der GitHub-OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Implementiert mit Roslyn-Analyzer auf GitHub FxCop-Regeln](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
