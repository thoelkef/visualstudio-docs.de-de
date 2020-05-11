---
title: Roslyn Analyzers und Code-aware Library for ImmutableArrays | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444894"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn-Analyzer und codeabhängige Bibliothek für ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [.NET Compiler platform](https://github.com/dotnet/roslyn) ("Roslyn") hilft Ihnen beim Erstellen von codebewussten Bibliotheken. Eine codefähige Bibliothek bietet Funktionen, die Sie verwenden können, und Tools (Roslyn-Analysatoren), um Ihnen zu helfen, die Bibliothek optimal zu nutzen oder Fehler zu vermeiden. In diesem Thema erfahren Sie, wie Sie einen realen Roslyn-Analysator erstellen, um häufige Fehler bei der Verwendung des [NIB: Immutable Collections](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet-Pakets zu erfassen. Im Beispiel wird auch veranschaulicht, wie ein Codefix für ein Codeproblem vom Analyzer gefunden wird. Benutzer sehen Codekorrekturen in der Visual Studio-Glühbirnenbenutzeroberfläche und können automatisch eine Korrektur für den Code anwenden.

## <a name="getting-started"></a>Erste Schritte
Sie benötigen Folgendes, um dieses Beispiel zu erstellen:

- Visual Studio 2015 (keine Express Edition) oder eine neuere Version. Sie können die kostenlose [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Sie können auch bei der Installation von Visual Studio Visual Studio Extensibility Tools unter Allgemeine Tools überprüfen, um das SDK gleichzeitig zu installieren. Wenn Sie Visual Studio bereits installiert haben, können Sie dieses SDK auch installieren, indem Sie zum Hauptmenü **Datei &#124; Neues &#124;Projekt ...** wechseln, im linken Navigationsbereich die Option "C" auswählen und dann die Option Erweiterbarkeit auswählen. Wenn Sie die Breadcrumb-Projektvorlage "**Installieren der Visual Studio Extensibility Tools**" auswählen, werden Sie aufgefordert, das SDK herunterzuladen und zu installieren.

- [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Sie können dieses SDK auch installieren, indem Sie zum Hauptmenü **Datei &#124; Neues &#124; Projekt ...** wechseln, im linken Navigationsbereich die Option **"C"** auswählen und dann **Erweiterbarkeit**auswählen. Wenn Sie "**Download the .NET Compiler Platform SDK**" breadcrumb project template auswählen, werden Sie aufgefordert, das SDK herunterzuladen und zu installieren. Dieses SDK enthält den [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Mit diesem äußerst nützlichen Tool können Sie herausfinden, nach welchen Codemodelltypen Sie in Ihrem Analyzer suchen sollten. Die Analyzer-Infrastruktur ruft Ihren Code für bestimmte Codemodelltypen auf, sodass der Code nur bei Bedarf ausgeführt wird und sich nur auf die Analyse relevanten Codes konzentrieren kann.

## <a name="whats-the-problem"></a>Was ist das Problem?
Stellen Sie sich vor, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>Sie bieten eine Bibliothek mit ImmutableArray (z. B. ) Unterstützung. Die Entwickler von C-Code verfügen über viel Erfahrung mit .NET-Arrays. Aufgrund der Art von ImmutableArrays und Optimierungstechniken, die in der Implementierung verwendet werden, führen die Intuitionen von Entwicklern jedoch dazu, dass Benutzer Ihrer Bibliothek fehlerhaften Code schreiben, wie unten erläutert. Darüber hinaus sehen Benutzer ihre Fehler erst zur Laufzeit, was nicht die Qualitätserfahrung ist, die sie in Visual Studio mit .NET gewohnt sind.

Benutzer sind mit dem Schreiben von Code wie dem folgenden vertraut:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Das Erstellen leerer Arrays zum Ausfüllen mit nachfolgenden Codezeilen und zum Verwenden der Auflistungsinitialisierersyntax ist den Entwicklern von C-Entwicklern sehr vertraut. Das Schreiben des gleichen Codes für ein ImmutableArray stürzt jedoch zur Laufzeit ab:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

Der erste Fehler ist darauf zurückzuführen, dass die ImmutableArray-Implementierung eine Struktur verwendet, um den zugrunde liegenden Datenspeicher umzuschließen. Strukturen müssen über parameterlose Konstruktoren verfügen, `default(T)` damit Ausdrücke Strukturen mit allen Null- oder Nullmembern zurückgeben können. Wenn der Code `b1.Length`auf zugreift, liegt ein Nulldereferenzierungsfehler für die Laufzeit vor, da in der ImmutableArray-Struktur kein zugrunde liegendes Speicherarray vorhanden ist. Der richtige Weg zum Erstellen eines `ImmutableArray<int>.Empty`leeren ImmutableArray ist .

 Der Fehler bei Auflistungsinitialisierern tritt auf, weil die ImmutableArray.Add-Methode jedes Mal, wenn Sie sie aufrufen, neue Instanzen zurückgibt. Da sich ImmutableArrays nie ändern, erhalten Sie beim Hinzufügen eines neuen Elements ein neues ImmutableArray-Objekt (das Speicher aus Leistungsgründen mit einem zuvor vorhandenen ImmutableArray gemeinsam nutzen kann). Da `b2` punktet auf das erste `Add()` ImmutableArray vor dem Aufruf fünfmal, `b2` ist ein Standard ImmutableArray. AufrufLänge auf sie stürzt auch mit einem Null-Dereferenzierungsfehler ab. Der richtige Weg, um ein ImmutableArray zu initialisieren, ohne Add manuell aufzurufen, ist die Verwendung `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`von .

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Suchen relevanter Syntaxknotentypen zum Auslösen des Analyzers
Um mit dem Erstellen des Analyzers zu beginnen, finden Sie zunächst heraus, nach welchem SyntaxNode-Typ Sie suchen müssen.   Starten Sie die Syntax-Visualisierung über das Menü **Ansicht &#124; andere Windows &#124; Roslyn Syntax Visualizer**.

Platzieren Sie die Einserstelle des `b1`Editors in der Zeile, in der deklariert wird. Sie sehen, dass sich die Syntax-Visualisierung zeigt, dass Sie sich in einem `LocalDeclarationStatement` Knoten der Syntaxstruktur befinden. Dieser Knoten `VariableDeclaration`hat eine , `VariableDeclarator`die wiederum eine `EqualsValueClause`hat, die wiederum `ObjectCreationExpression`eine hat, und schließlich gibt es eine . Wenn Sie in der Syntax Visualizer-Struktur von Knoten klicken, wird die Syntax im Editorfenster angezeigt, um den Code anzuzeigen, der durch diesen Knoten dargestellt wird. Die Namen der SyntaxNode-Untertypen stimmen mit den Namen überein, die in der Grammatik von C- verwendet werden.

## <a name="creating-the-analyzer-project"></a>Erstellen des Analyzer-Projekts
Wählen Sie im Hauptmenü **Datei &#124; Neues &#124; Projekt ...**. Wählen Sie im Dialogfeld **Neues Projekt** unter **C-Projekte** in der linken Navigationsleiste Die Option Erweiterbarkeit aus, und wählen Sie im rechten Bereich die Projektvorlage **Analyzer mit Code Fix** aus. Geben Sie einen Namen ein, und bestätigen Sie das Dialogfeld.

Die Vorlage öffnet eine DiagnosticAnalyzer.cs Datei. Wählen Sie diese Editor-Puffer-Registerkarte aus. Diese Datei verfügt über eine Analyzer-Klasse (gebildet aus dem `DiagnosticAnalyzer` Namen, den Sie dem Projekt gegeben haben), die von (einem Roslyn-API-Typ) stammt. Ihre neue Klasse `DiagnosticAnalyzerAttribute` verfügt über einen deklarierenden Analyzer, der für die Sprache "C" relevant ist, sodass der Compiler den Analyzer erkennt und lädt.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Sie können einen Analyzer mithilfe von Visual Basic implementieren, der auf C-Code abzielt, und umgekehrt. Im DiagnosticAnalyzerAttribute ist es wichtiger zu wählen, ob Ihr Analysator auf eine Oder eine Sprache oder beides abzielt. Anspruchsvollere Analysatoren, die eine detaillierte Modellierung der Sprache erfordern, können nur auf eine einzige Sprache abzielen. Wenn Ihr Analyzer z. B. nur Typnamen oder öffentliche Membernamen überprüft, kann es möglich sein, das Common Language Model zu verwenden, das Roslyn in Visual Basic und C. anbietet. FxCop warnt z. B., <xref:System.Runtime.Serialization.ISerializable>dass eine Klasse implementiert, die Klasse jedoch nicht über das <xref:System.SerializableAttribute> Attribut sprachunabhängig ist und sowohl für Visual Basic als auch für C-Code funktioniert.

## <a name="initalizing-the-analyzer"></a>Initalisierung des Analyzers
Scrollen Sie in `DiagnosticAnalyzer` der Klasse `Initialize` ein wenig nach unten, um die Methode anzuzeigen. Der Compiler ruft diese Methode auf, wenn er einen Analyzer aktiviert. Die Methode `AnalysisContext` verwendet ein Objekt, mit dem der Analyzer Kontextinformationen abrufen und Rückrufe für Ereignisse für die Arten von Code registrieren kann, die Sie analysieren möchten.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Öffnen Sie eine neue Zeile in dieser Methode, und geben Sie "kontext" ein. , um eine Intellisense-Vervollständigungsliste anzuzeigen. Sie können in der Abschlussliste `Register…` sehen, dass es viele Methoden gibt, um verschiedene Arten von Ereignissen zu behandeln. Beispielsweise ruft der erste, `RegisterCodeBlockAction`, ihren Code für einen Block zurück, der normalerweise Code zwischen geschweiften Klammern ist. Beim Registrieren eines Blocks wird auch der Code für den Initialisierer eines Felds, der Wert, der einem Attribut gegeben wird, oder der Wert eines optionalen Parameters zurückgefordert.

Als weiteres `RegisterCompilationStartAction`Beispiel ruft , zu Beginn einer Kompilierung ihren Code zurück, was nützlich ist, wenn Sie den Status über viele Speicherorte erfassen müssen. Sie können z. B. eine Datenstruktur erstellen, um alle verwendeten Symbole zu sammeln, und jedes Mal, wenn Ihr Analyzer für eine Syntax oder ein Symbol zurückgerufen wird, können Sie Informationen zu jedem Speicherort in Ihrer Datenstruktur speichern. Wenn Sie aufgrund der Kompilierungsendliste zurückgerufen werden, können Sie alle Speicherorte analysieren, `using` z. B. um zu melden, welche Symbole der Code aus jeder Anweisung verwendet.

Mit der **Syntax Visualizer**haben Sie gelernt, dass Sie aufgerufen werden sollen, wenn der Compiler eine ObjectCreationExpression verarbeitet. Sie verwenden diesen Code, um den Rückruf einzurichten:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Sie registrieren sich für einen Syntaxknoten und filtern nur für Objekterstellungssyntaxknoten. Auf der Konvention verwenden Analyzer-Autoren einen Lambda beim Registrieren von Aktionen, wodurch Analysatoren zustandslos bleiben. Sie können die Visual Studio-Funktion **"Aus Verwendung generieren"** verwenden, um die `AnalyzeObjectCreation` Methode zu erstellen. Dadurch wird auch für Sie der richtige Kontextparametertyp generiert.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Festlegen von Eigenschaften für Benutzer Ihres Analyzers
Damit Ihr Analyzer in visual Studio-Benutzeroberfläche angezeigt wird, suchen Sie nach der folgenden Codezeile, und ändern Sie sie, um Ihren Analyzer zu identifizieren:

```csharp
internal const string Category = "Naming";
```

Ändern Sie `"Naming"` in `"API Guidance"`.

Suchen und öffnen Sie als Nächstes die Datei Resources.resx in Ihrem Projekt mit dem **Projektmappen-Explorer**. Sie können eine Beschreibung für Ihren Analyzer, Titel usw. einsehen. Sie können den Wert für `“Don’t use ImmutableArray<T> constructor”` alle diese jetzt ändern. Sie können Zeichenfolgenformatierungsargumente{0} {1}in Ihre Zeichenfolge ( , `Diagnostic.Create()`, usw.) eingeben, und später, wenn Sie aufrufen, können Sie ein params-Array von Argumenten angeben, die übergeben werden sollen.

## <a name="analyzing-an-object-creation-expression"></a>Analysieren eines Objekterstellungsausdrucks
Die `AnalyzeObjectCreation` Methode verwendet einen anderen Kontexttyp, der vom Codeanalyzer-Framework bereitgestellt wird. Mit `AnalysisContext` der Initialize-Methode können Sie Aktionsrückrufe registrieren, um Ihren Analyzer einzurichten. Die `SyntaxNodeAnalysisContext`hat z. `CancellationToken` B. eine, die Sie passieren können. Wenn ein Benutzer mit der Eingabe im Editor beginnt, bricht Roslyn laufende Analysatoren ab, um Arbeit zu sparen und die Leistung zu verbessern. Als weiteres Beispiel verfügt dieser Kontext über eine Node-Eigenschaft, die den Syntaxknoten für die Objekterstellung zurückgibt.

Abrufen des Knotens, von dem Sie annehmen können, dass er der Typ ist, für den Sie die Syntaxknotenaktion gefiltert haben:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Visual Studio zum ersten Mal mit Ihrem Analyzer starten
Starten Sie Visual Studio, indem Sie Ihren Analyzer erstellen und ausführen (drücken Sie **F5**). Da das Startprojekt im **Projektmappen-Explorer** das VSIX-Projekt ist, erstellt das Ausführen des Codes Ihren Code und einen VSIX und startet dann Visual Studio mit installiertem VSIX. Wenn Sie Visual Studio auf diese Weise starten, wird es mit einer eindeutigen Registrierungsstruktur gestartet, sodass die Hauptverwendung von Visual Studio nicht von Ihren Testinstanzen beeinflusst wird, während Sie Analysatoren erstellen. Wenn Sie auf diese Weise zum ersten Mal starten, führt Visual Studio mehrere Initialisierungen aus, die dem beim ersten Start von Visual Studio nach der Installation ähneln.

 Erstellen Sie ein Konsolenprojekt, und geben Sie dann den Arraycode in Ihre Konsolenanwendungen ein Hauptmethode:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Die Codezeilen `ImmutableArray` mit haben Wellen, da Sie das unveränderliche NuGet-Paket abrufen und Ihrem Code eine `using` Anweisung hinzufügen müssen. Drücken Sie die rechte Zeigertaste auf dem Projektknoten im **Projektmappen-Explorer** und wählen **NuGet-Pakete verwalten ...**. Geben Sie im NuGet-Manager "Unmutierbar" in das Suchfeld ein, und wählen Sie im linken Bereich das Element "System.Collections.Immutable" (nicht "Microsoft.Bcl.Immutable") aus, und drücken Sie die Schaltfläche Installieren im rechten Bereich. Durch die Installation des Pakets wird ein Verweis auf Ihre Projektreferenzen hinzugefügt.

Sie sehen immer noch rote `ImmutableArray`Wellen unter , also platzieren Sie die Einstelle in diesem Bezeichner und drücken **Sie STRG+.** (Zeitraum), um das vorgeschlagene Fix-Menü aufzurufen `using` und die entsprechende Anweisung hinzuzufügen.

**Speichern Sie Alle und schließen Sie** die zweite Instanz von Visual Studio vorerst, um Den Fortstand fortzusetzen.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Beenden des Analyzers mit Bearbeiten und Fortfahren
Legen Sie in der ersten Instanz von Visual Studio `AnalyzeObjectCreation` einen Haltepunkt am Anfang der Methode fest, indem Sie **F9** mit der Einfügez in der ersten Zeile drücken.

Starten Sie den Analyzer erneut mit **F5**, und öffnen Sie in der zweiten Instanz von Visual Studio die Konsolenanwendung, die Sie zuletzt erstellt haben, erneut.

Sie kehren zur ersten Instanz von Visual Studio am Haltepunkt zurück, da der Roslyn-Compiler einen Objekterstellungsausdruck gesehen und in Ihren Analyzer aufgerufen hat.

**Abrufen des Objekterstellungsknotens.** Gehen Sie über die `objectCreation` Zeile, die die Variable festlegt, indem `“objectCreation.ToString()”`Sie **F10**drücken, und werten Sie im **Direktfenster** den Ausdruck aus. Sie sehen, dass der Syntaxknoten, `"new ImmutableArray<int>()"`auf den die Variable verweist, der Code ist, genau das, was Sie suchen.

**Holen Sie SichmutableArray\<T> Type-Objekt ab.** Sie müssen überprüfen, ob der zu erstellende Typ ImmutableArray ist. Zuerst erhalten Sie das Objekt, das diesen Typ darstellt. Sie überprüfen Typen, die das semantische Modell verwenden, um sicherzustellen, dass Sie genau den richtigen Typ haben, und Vergleichen Sie die Zeichenfolge nicht aus ToString(). Geben Sie die folgende Codezeile am Ende der Funktion ein:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Sie legen generische Typen in Metadaten mit Backquotes (') und der Anzahl der generischen Parameter fest. Deshalb sehen Sie nicht "... ImmutableArray\<T>" im Metadatennamen.

Das semantische Modell hat viele nützliche Dinge auf ihm, die Sie Fragen über Symbole, Datenfluss, variable Lebensdauer, etc. stellen können. Roslyn trennt Syntaxknoten aus verschiedenen technischen Gründen (Leistung, Modellierung fehlerhafter Code usw.) vom semantischen Modell. Sie möchten, dass das Kompilierungsmodell Informationen in Referenzen sucht, um einen genauen Vergleich zu erhalten.

Sie können den gelben Ausführungszeiger auf der linken Seite des Editorfensters ziehen. Ziehen Sie es bis zu `objectCreation` der Zeile, die die Variable festlegt, und schritt über die neue Codezeile mit **F10**. Wenn Sie den Mauszeiger über `immutableArrayOfType`die Variable bewegen, sehen Sie, dass wir den genauen Typ im semantischen Modell gefunden haben.

**Abrufen des Objekterstellungsausdruckstyps.** "Typ" wird in diesem Artikel auf wenige Arten verwendet, aber das bedeutet, wenn Sie den Ausdruck "new Foo" haben, müssen Sie ein Modell von Foo erhalten. Sie müssen den Typ des Objekterstellungsausdrucks abrufen, um\<zu sehen, ob es sich um den Typ ImmutableArray T> handelt. Verwenden Sie das semantische Modell erneut, um Symbolinformationen für das Typsymbol (ImmutableArray) im Objekterstellungsausdruck abzurufen. Geben Sie die folgende Codezeile am Ende der Funktion ein:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Da Ihr Analyzer unvollständigen oder falschen Code in Editorpuffern verarbeiten `using` muss (z. `symbolInfo` B. eine fehlende Anweisung), sollten Sie überprüfen, ob sie `null`. Sie müssen einen benannten Typ (INamedTypeSymbol) aus dem Symbolinformationsobjekt abrufen, um die Analyse abzuschließen.

**Vergleichen Sie die Typen.** Da es einen offenen generischen Typ von T gibt, nach dem wir suchen, und der Typ im Code ein konkreter generischer Typ ist, fragen Sie die Symbolinformationen nach dem, woraus der Typ erstellt wird (ein offener generischer Typ), und vergleichen dieses Ergebnis mit `immutableArrayOfTType`. Geben Sie am Ende der Methode Folgendes ein:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Melden Sie die Diagnose.** Die Diagnose ist ziemlich einfach. Sie verwenden die für Sie erstellte Regel in der Projektvorlage, die vor der Initialize-Methode definiert wird. Da es sich bei dieser Situation im Code um einen Fehler `DiagnosticSeverity.Warning` handelt, können Sie `DiagnosticSeverity.Error` die Zeile ändern, die Regel initialisiert hat, um sie durch (rote Wellenlinie) zu ersetzen. Der Rest der Regel wird aus den Ressourcen initialisiert, die Sie am Anfang der exemplarischen Vorgehensweise bearbeitet haben. Sie müssen auch die Position für die Squiggle melden, die die Position der Typspezifikation der Objekterstellungsexpression darstellt. Geben Sie diesen `if` Code in den Block ein:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Ihre Funktion sollte wie folgt aussehen (vielleicht anders formatiert):

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

Entfernen Sie den Haltepunkt, damit Sie sehen können, dass Ihr Analyzer funktioniert (und nicht mehr zur ersten Instanz von Visual Studio zurückkehrt). Ziehen Sie den Ausführungszeiger an den Anfang der Methode, und drücken Sie **F5,** um die Ausführung fortzusetzen. Wenn Sie zur zweiten Instanz von Visual Studio zurückkehren, beginnt der Compiler mit der erneuten Prüfung des Codes und ruft den Analyzer auf. Sie können eine Wellenlinie `ImmutableType<int>`unter sehen.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Hinzufügen eines "Code Fix" für das Codeproblem
Bevor Sie beginnen, schließen Sie die zweite Instanz von Visual Studio, und beenden Sie das Debuggen in der ersten Instanz von Visual Studio (wo Sie den Analyzer entwickeln).

**Fügen Sie eine neue Klasse hinzu.** Verwenden Sie das Kontextmenü (rechte Zeigerschaltfläche) auf Ihrem Projektknoten im Projektmappen-Explorer, und wählen Sie ein neues Element hinzu. Fügen Sie `BuildCodeFixProvider`eine Klasse mit dem Namen hinzu. Diese Klasse muss von `CodeFixProvider`ableiten, und Sie müssen **STRG+ verwenden.** (zeitraum), um den Codefix aufzurufen, der die richtige `using` Anweisung hinzufügt. Diese Klasse muss auch mit `ExportCodeFixProvider` dem Attribut mit Anmerkungen versehen `using` werden, `LanguageNames` und Sie müssen eine Anweisung hinzufügen, um die Enumerat aufzulösen. Sie sollten eine Klassendatei mit folgendem Code haben:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub-out abgeleitete Member.** Platzieren Sie nun die Einsenstelle `CodeFixProvider` des Editors in der Kennung, und drücken Sie **STRG+.** (Zeitraum), um die Implementierung für diese abstrakte Basisklasse zu benachersten. Dadurch werden eine Eigenschaft und eine Methode für Sie generiert.

**Implementieren Sie die Eigenschaft.** Füllen Sie `FixableDiagnosticIds` den `get` Text der Eigenschaft mit dem folgenden Code aus:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn vereint Diagnosen und Korrekturen, indem diese Bezeichner, bei denen es sich nur um Zeichenfolgen handelt, übereinstimmen. Die Projektvorlage hat eine Diagnose-ID für Sie generiert, und Sie können sie ändern. Der Code in der Eigenschaft gibt nur die ID aus der Analyzer-Klasse zurück.

**Die RegisterCodeFixAsync-Methode nimmt einen Kontext an.** Der Kontext ist wichtig, da ein Codefix auf mehrere Diagnosen angewendet werden kann, oder es kann mehr als ein Problem in einer Codezeile geben. Wenn Sie "Kontext" eingeben. im Text der Methode zeigt Ihnen die Intellisense-Vervollständigungsliste einige nützliche Mitglieder an. Es gibt ein CancellationToken-Mitglied, das Sie überprüfen können, um zu sehen, ob etwas die Korrektur abbrechen möchte. Es gibt ein Dokumentmitglied, das viele nützliche Mitglieder hat und mit dem Sie zu den Projekt- und Projektmappenmodellobjekten gelangen können. Es gibt ein Span-Member, das den Anfang und das Ende des Codespeicherorts ist, der angegeben wurde, als Sie die Diagnose gemeldet haben.

**Machen Sie die Methode asynchron.** Als Erstes müssen Sie die generierte Methodendeklaration als `async` Methode fixieren. Der Codefix zum Stuben der Implementierung einer abstrakten `async` Klasse enthält das `Task`Schlüsselwort nicht, obwohl die Methode eine zurückgibt.

**Abrufen des Stamms der Syntaxstruktur.** Um Code zu ändern, müssen Sie eine neue Syntaxstruktur mit den Änderungen erstellen, die Ihr Codefix vornimmt. Sie benötigen `Document` die aus `GetSyntaxRootAsync`dem Kontext aufrufen . Dies ist eine asynchrone Methode, da es unbekannte Arbeit gibt, um die Syntaxstruktur abzubekommen, möglicherweise einschließlich des Abrufens der Datei vom Datenträger, des Analysierens und des Erstellens des Roslyn-Codemodells dafür. Die Visual Studio-Benutzeroberfläche sollte während `async` dieser Zeit reaktionsfähig sein, was aktiviert wird. Ersetzen Sie die Codezeile in der Methode durch Folgendes:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Suchen Sie den Knoten mit dem Problem.** Sie übergeben den Kontext, aber der Knoten, den Sie finden, ist möglicherweise nicht der Code, den Sie ändern müssen. Die gemeldete Diagnose lieferte nur die Spanne für den Typbezeichner (wo die Squiggle `new` gehörte), aber Sie müssen den gesamten Objekterstellungsausdruck ersetzen, einschließlich der Keywoard am Anfang und der Klammern am Ende. Fügen Sie der Methode den folgenden Code hinzu (und verwenden Sie **STRG+.** , um `using` eine `ObjectCreationExpressionSyntax`Anweisung hinzuzufügen für ):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Registrieren Sie den Codefix für die Glühbirnen-Benutzeroberfläche.** Wenn Sie den Codefix registrieren, wird Roslyn automatisch an die Visual Studio-Benutzeroberfläche für Glühbirnen agestellt. Endbenutzer werden sehen, dass sie **STRG+** verwenden können. (Zeitraum), wenn Ihr Analysator eine `ImmutableArray<T>` schlechte Konstruktorverwendung umkreist. Da Ihr Codefixanbieter nur ausgeführt wird, wenn ein Problem vorliegt, können Sie davon ausgehen, dass Sie über den gesuchten Objekterstellungsausdruck verfügen. Aus dem Kontextparameter können Sie den neuen Codefix registrieren, `RegisterCodeFixAsync` indem Sie den folgenden Code am Ende der Methode hinzufügen:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Sie müssen die Einserstelle des Editors `CodeAction`in den Bezeichner platzieren, und dann **STRG+ verwenden.** (Zeitraum), um die `using` entsprechende Anweisung für diesen Typ hinzuzufügen.

Platzieren Sie dann die Einsenstelle des Editors in der `ChangeToImmutableArrayEmpty` Kennung und verwenden Sie **STRG+.** , um diesen Methodenstub für Sie zu generieren.

Dieser letzte Codeausschnitt, den Sie hinzugefügt haben, `CodeAction` registriert den Codefix, indem er eine und die Diagnose-ID für die Art des gefundenen Problems übergeben. In diesem Beispiel gibt es nur eine Diagnose-ID, für die dieser Code Korrekturen bereitstellt, sodass Sie einfach das erste Element des Diagnose-IDs-Arrays übergeben können. Wenn Sie `CodeAction`die erstellen, übergeben Sie den Text, den die Glühbirnenbenutzeroberfläche als Beschreibung des Codefixes verwenden soll. Sie übergeben auch eine Funktion, die ein CancellationToken nimmt und ein neues Dokument zurückgibt. Das neue Dokument verfügt über eine neue Syntaxstruktur, die Ihren gepatchten Code enthält, der aufruft. `ImmutableArray.Empty` Dieser Codeausschnitt verwendet einen Lambda, damit er über den objectCreation-Knoten und das Dokument des Kontexts geschlossen werden kann.

**Erstellen Sie die neue Syntaxstruktur.** Geben `ChangeToImmutableArrayEmpty` Sie in der Methode, deren Stub `ImmutableArray<int>.Empty;`Sie zuvor generiert haben, die Codezeile ein: . Wenn Sie das Toolfenster Syntax Visualizer erneut anzeigen, können Sie sehen, dass es sich bei dieser Syntax um einen SimpleMemberAccessExpression-Knoten handelt. Das ist es, was diese Methode zum Erstellen und Zurückgeben in einem neuen Dokument benötigt.

Die erste `ChangeToImmutableArrayEmpty` Änderung besteht `async` `Task<Document>` darin, zuvor hinzuzufügen, da die Codegeneratoren nicht davon ausgehen können, dass die Methode async sein sollte.

Füllen Sie den Text mit dem folgenden Code aus, damit Ihre Methode wie folgt aussieht:

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

Sie müssen die Einserstelle des `SyntaxGenerator` Editors in die Kennung einstecken und **STRG+ verwenden.** (Zeitraum), um die `using` entsprechende Anweisung für diesen Typ hinzuzufügen.

Dieser Code `SyntaxGenerator`verwendet , was ein sehr nützlicher Typ zum Erstellen von neuem Code ist. Nachdem Sie einen Generator für das Dokument `ChangeToImmutableArrayEmpty` `MemberAccessExpression`mit dem Codeproblem erhalten haben, ruft der Name des Members, auf den wir zugreifen möchten, übergibt und übergibt den Namen des Elements als Zeichenfolge.

Als Nächstes ruft die Methode den Stamm des Dokuments ab, und da dies im allgemeinen Fall willkürliche Arbeit erfordern kann, wartet der Code auf diesen Aufruf und übergibt das Abbruchtoken. Roslyn-Codemodelle sind unveränderlich, z. B. die Arbeit mit einer .NET-Zeichenfolge. Wenn Sie die Zeichenfolge aktualisieren, erhalten Sie im Gegenzug ein neues Zeichenfolgenobjekt. Wenn Sie `ReplaceNode`aufrufen, erhalten Sie einen neuen Stammknoten zurück. Der größte Teil der Syntaxstruktur wird freigegeben (da `objectCreation` sie unveränderlich ist), aber der Knoten wird durch den `memberAccess` Knoten ersetzt, sowie alle übergeordneten Knoten bis zum Syntaxbaumstamm.

## <a name="trying-your-code-fix"></a>Versuchen Sie Ihren Code Fix
Sie können jetzt **F5** drücken, um Ihren Analyzer in einer zweiten Instanz von Visual Studio auszuführen. Öffnen Sie das Konsolenprojekt, das Sie zuvor verwendet haben. Nun sollten Sie sehen, dass die Glühbirne an `ImmutableArray<int>`der Stelle erscheint, für die sich ihr neuer Objekterstellungsausdruck befindet. Wenn Sie **STRG+ drücken.** (Zeitraum), dann sehen Sie Ihren Code-Fix, und Sie werden eine automatisch generierte Codedifferenz-Vorschau in der Glühbirne UI sehen. Roslyn schafft dies für Sie.

Pro-Tipp: Wenn Sie die zweite Instanz von Visual Studio starten und die Glühbirne mit dem Codefix nicht angezeigt wird, müssen Sie möglicherweise den Visual Studio-Komponentencache löschen. Wenn Sie den Cache löschen, muss Visual Studio die Komponenten erneut untersuchen, daher sollte Visual Studio dann Die neueste Komponente aufnehmen. Fahren Sie zunächst die zweite Instanz von Visual Studio herunter. Wechseln Sie dann im Windows Explorer zu Ihrem\\ Benutzerverzeichnis\>(c:-Benutzer<Benutzer-ID ), und suchen Sie\\appData-Lokal-Microsoft-VisualStudio-14.0Roslyn . Löschen Sie in diesem Verzeichnis das Unterverzeichnis ComponentModelCache. Die Version "14" ändert die Version in version mit Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Talk Video und Finish Code Project
Sie können dieses Beispiel in [diesem Vortrag](https://channel9.msdn.com/events/Build/2015/3-725)weiter entwickelt und diskutiert sehen. Der Vortrag zeigt den funktionierenden Analysator und führt Sie durch den Aufbau.

Sie können den gesamten fertigen Code [hier](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)sehen. Die Unterordner DoNotUseImmutableArrayCollectionInitializer und DoNotUseImmutableArrayCtor verfügen jeweils über eine C-Datei zum Suchen von Problemen und eine C-Datei, die die Codefixes implementiert, die in der Visual Studio-Glühbirnenbenutzeroberfläche angezeigt werden. Beachten Sie, dass der fertige Code etwas mehr Abstraktion\<hat, um das Abrufen des ImmutableArray T->-Typobjekts zu vermeiden. Es verwendet geschachtelte registrierte Aktionen, um das Typobjekt in einem Kontext zu speichern, der verfügbar ist, wenn die Unteraktionen (Analysieren der Objekterstellung und Analyse von Auflistungsinitialisierungen) ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
[\\Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
[Abgeschlossener Code auf GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[Mehrere Beispiele auf GitHub, gruppiert in drei Arten von Analysatoren](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
[Andere Dokumente auf der GitHub OSS-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[FxCop-Regeln implementiert mit Roslyn-Analysatoren auf GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
