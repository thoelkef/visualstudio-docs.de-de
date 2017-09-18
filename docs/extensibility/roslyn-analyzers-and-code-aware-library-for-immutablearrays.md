---
title: "Roslyn-Analyzer und Code unterst&#252;tzende Bibliothek f&#252;r ImmutableArrays | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Roslyn-Analyzer und Code unterst&#252;tzende Bibliothek f&#252;r ImmutableArrays
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die [.NET Compiler Platform](https://github.com/dotnet/roslyn) \("Roslyn"\) können Sie die Code\-fähigen Bibliotheken zu erstellen.  Eine Code unterstützende Bibliothek bietet Funktionalität, die Sie verwenden können, und Tools \(Roslyn\-Analyzer\) können Sie die Bibliothek verwenden, auf die bestmögliche Weise oder Fehler zu vermeiden.  In diesem Thema veranschaulicht das Erstellen einer realen Roslyn\-Analyzer, um häufige Fehler abzufangen, bei Verwendung der [Unveränderliche Auflistungen](../Topic/NIB:%20Immutable%20Collections.md) NuGet\-Paket.  Darüber hinaus wird veranschaulicht, wie ein Codeupdate für ein Codeproblem vom Analyzer gefunden werden.  Benutzer finden Sie unter Codekorrekturen in der Visual Studio\-Glühbirne Benutzeroberfläche und ein Update für den Code automatisch anwenden können.  
  
## In diesem Thema  
 Dieses Thema enthält die folgenden Abschnitte:  
  
-   Erste Schritte  
  
-   Was ist das Problem?  
  
-   Suchen nach relevanten Code Modelltypen das Analysemodul auslösen  
  
-   Erstellen des Analyzer\-Projekts  
  
-   Initialisieren des Analyzers  
  
-   Festlegen von Eigenschaften für Benutzer Ihres Analysemoduls  
  
-   Analysieren von Objektausdruck erstellen  
  
-   Starten von Visual Studio mit der Analyzer beim ersten  
  
-   Beenden der Analyzer mit bearbeiten und fortfahren  
  
-   Ein "Hotfix" hinzufügen für das Codeproblem  
  
-   Versuchen Ihr Codefix  
  
-   Wenden Sie sich Videos und abgeschlossenen Codeprojekt  
  
## Erste Schritte  
 Sie benötigen Folgendes zum Erstellen dieses Beispiels:  
  
-   Visual Studio 2015 \(keine Express Edition\) oder eine höhere Version.  Können Sie die kostenlose [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  Sie können auch bei der Installation von Visual Studio, Visual Studio Extensibility Tools unter Allgemeine Tools installieren des SDK zur gleichen Zeit überprüfen.  Wenn Sie Visual Studio bereits installiert haben, können Sie auch dieses SDK installieren, indem Sie das Hauptmenü **Datei &#124; Neue &#124; Projekt**, c\# im linken Navigationsbereich, klicken Sie dann auswählen und Erweiterbarkeit.  Bei der Auswahl der "**Installieren Sie die Visual Studio Extensibility Tools**" Breadcrumb\-Projektvorlage, sie werden aufgefordert, das SDK herunterladen und installieren.  
  
-   [.NET Compiler Platform \("Roslyn"\) SDK](http://aka.ms/roslynsdktemplates).  Sie können dieses SDK auch installieren, indem Sie das Hauptmenü **Datei &#124; Neue &#124; Projekt**, auswählen **c\#** im linken Navigationsbereich und anschließend **Erweiterbarkeit**.  Bei der Auswahl "**.NET Compiler Platform SDK downloaden**" Breadcrumb\-Projektvorlage, sie werden aufgefordert, das SDK herunterladen und installieren.  Dieses SDK enthält die [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Diesem äußerst nützliches Tool können Sie herausfinden, welche Modelltypen Code in Ihr Analysemodul Achten Sie.  Der Analyzer ruft in Ihren Code für bestimmten Code Modelltypen, damit Ihr Code nur führt bei Bedarf und nur für die Analyse relevante Code konzentrieren kann.  
  
## Was ist das Problem?  
 Angenommen, Sie bieten eine Bibliothek mit ImmutableArray \(z. B. <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) unterstützen.  C\#\-Entwickler haben viel Erfahrung mit .NET Arrays.  Allerdings dazu führen, dass aufgrund der Natur der ImmutableArrays und Optimierung von Techniken, die in der Implementierung verwendet, C\#\-Entwickler Intuitions Benutzer der Bibliothek fehlerhaften Code schreiben, wie nachstehend beschrieben.  Darüber hinaus werden Benutzer nicht ihre Fehler erst zur Laufzeit finden Sie unter die Qualität, die sie in Visual Studio mit .NET vertraut sind, nicht.  
  
 Benutzer, die mit dem Schreiben von Code wie den folgenden vertraut sind:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Leere Arrays Füllen mit nachfolgenden Zeilen des Codes erstellen und Verwenden von Auflistungsinitialisierer\-Syntax werden C\#\-Entwicklern vertraut.  Jedoch stürzt ab, die gleiche schreiben Code für eine ImmutableArray zur Laufzeit:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Der erste Fehler ist aufgrund von ImmutableArray\-Implementierung mit einer Struktur, um den zugrunde liegenden Datenspeicher zu umschließen.  Strukturen parameterlose Konstruktoren haben müssen, damit `default(T)` Ausdrücke können mit allen Strukturen geben 0 \(null\) oder null Elemente.  Wenn der Code greift auf `b1.Length`, es ist ein NULL\-Wert zur Laufzeit Fehler dereferenzieren, da keine zugrunde liegende Speicher\-Array in Struktur ImmutableArray vorhanden ist.  Ist die korrekte Methode zum Erstellen einer leeren ImmutableArray `ImmutableArray<int>.Empty`.  
  
 Der Fehler mit Auflistungsinitialisierer geschieht, weil der ImmutableArray.Add neue Instanzen jedes Mal Methodenrückgabe Sie aufgerufen werden.  Da ImmutableArrays sich nie ändern, wenn Sie ein neues Element hinzufügen, erhalten Sie ein neues ImmutableArray\-Objekt \(das eine bereits vorhandene ImmutableArray aus Leistungsgründen Speicher freigeben kann\).  Da `b2` verweist auf die erste ImmutableArray vor dem Aufruf von `Add()` fünf Mal `b2` ist ein Standardwert ImmutableArray.  Aufruf Länge auf diesem und auch Abstürze mit einer Null\-Fehler zu dereferenzieren.  Die richtige Methode, ein ImmutableArray zu initialisieren, ohne manuell aufrufen hinzufügen, verwenden Sie `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.  
  
## Suchen nach relevanten Syntaxknotentypen das Analysemodul auslösen  
 Um mit der Erstellung des Analyzers beginnen, zuerst herausfinden Sie, welche Art von SyntaxNode gesucht werden sollen.    Starten Sie den Syntax Visualizer aus dem Menü **anzeigen &#124; Andere Fenster &#124; Roslyn Syntax Visualizer**.  
  
 Platzieren Sie die Einfügemarke des Editors in der Zeile, die deklariert `b1`.  Sehen Sie den Syntax Visualizer zeigt Sie befinden sich in einem `LocalDeclarationStatement` Knoten der Syntaxstruktur.  Dieser Knoten verfügt über eine `VariableDeclaration`, wiederum hat einen `VariableDeclarator`, wiederum hat einen `EqualsValueClause`, und schließlich wird ein `ObjectCreationExpression`.  Wenn Sie in der Syntax Visualizer\-Struktur der Knoten klicken, markiert die Syntax im Editor\-Fenster den Code, der durch diesen Knoten dargestellt angezeigt.  Den Namen für die SyntaxNode\-Untertypen entsprechen die Namen, die in der C\#\-Grammatik verwendet.  
  
## Erstellen des Analyzer\-Projekts  
 Wählen Sie im Hauptmenü **Datei &#124; Neue &#124; Projekt**.  In der **Neues Projekt** Dialogfeld unter **c\#** Projekte in der linken Navigationsleiste auf Erweiterbarkeit auswählen, und wählen Sie im rechten Bereich die **Analyzer mit Code korrigieren** \-Projektvorlage.  Geben Sie einen Namen ein, und bestätigen Sie das Dialogfeld.  
  
 Die Vorlage öffnet die Datei "diagnosticanalyzer.cs".  Wählen Sie diesen Editor Puffer Registerkarte.  Diese Datei weist eine Analyzer\-Klasse \(gebildet aus dem Namen des Projekts gegeben haben\) abgeleitet `DiagnosticAnalyzer` \(eine Art von Roslyn\-API\).  Die neue Klasse verfügt über eine `DiagnosticAnalyzerAttribute` deklariert das Analysemodul ist der C\#\-Sprache relevant, damit der Compiler erkennt und das Analysemodul lädt.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Sie können einen Analyzer mit Visual Basic, die auf C\#\-Code implementieren und umgekehrt.  Es ist wichtiger bei der DiagnosticAnalyzerAttribute auszuwählen, ob Ihr Analysemodul eine Sprache oder beide abzielt.  Komplexere Analysen, die erfordern ausführliche Modellierung der Sprache können nur eine einzelne Sprache abzielen.  Wenn Ihr Analysemodul z. B. nur Typnamen oder öffentliche Elementnamen überprüft wird, kann es möglich, Roslyn in Visual Basic und c\# bietet, die common Language\-Modell verwenden.  Z. B. FxCop wird gewarnt, dass eine Klasse implementiert <xref:System.Runtime.Serialization.ISerializable>, aber die Klasse hat keine der <xref:System.SerializableAttribute> \-Attribut ist sprachunabhängig und für die Visual Basic\- und C\#\-Code funktioniert.  
  
## Initialisieren der Analyzer  
 Scrollen Sie nach unten ein wenig die `DiagnosticAnalyzer` Klasse finden Sie unter der `Initialize` Methode.  Der Compiler ruft diese Methode beim Aktivieren eines Analyzers.  Die Methode akzeptiert ein `AnalysisContext` \-Objekt, können das Analysemodul an Kontextinformationen abrufen und Rückrufe für Ereignisse für die Arten von Code zu registrieren, Sie analysieren möchten.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Öffnen Sie eine neue Zeile in dieser Methode und geben "Context". eine Intellisense\-Vervollständigungsliste angezeigt.  Sehen Sie in der Vervollständigungsliste viele `Register…` Methoden für verschiedene Arten von Ereignissen.  Z. B. den ersten `RegisterCodeBlockAction`, Aufrufe zurück an den Code für einen Block, in der Regel Code zwischen den geschweiften Klammern.  Registrieren für einen Block ruft auch wieder in den Code für die Initialisierung eines Felds, den Wert eines Attributs oder der Wert der optionalen Parameter.  
  
 Wenn Sie beispielsweise `RegisterCompilationStartAction`, Aufrufe zurück an den Code am Anfang einer Kompilierung hilfreich, ist Wenn Sie über viele Orte erfassen müssen.  Können eine Datenstruktur, beispielsweise zum Sammeln von alle Symbole verwendet, und jedes Mal, wenn das Analysemodul für einige Syntax oder Symbole und aufgerufen wird, können Sie Informationen zu jedem Speicherort in der Datenstruktur speichern.  Wenn Sie wieder aufgrund der Kompilierung Ende aufgerufen, können Sie alle Standorte, die Sie gespeichert haben, z. B. um welche Symbole zu melden, der Code von jedem verwendet, Analysieren `using` Anweisung.  
  
 Mithilfe der **Syntax Visualizer**, haben Sie gelernt, dass aufgerufen werden, wenn der Compiler eine ObjectCreationExpression verarbeitet werden soll.  Sie verwenden diesen Code, um den Rückruf einzurichten:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Registrieren Sie sich für eine syntaxknoten und Filter für nur Erstellung Syntax Objektknoten.  Gemäß der Konvention verwenden Analyzer Autoren einen Lambda\-Ausdruck beim Registrieren von Aktionen, die Analyzer statusfreie bleiben.  Mithilfe der Visual Studio\-Funktion **Generate From Usage** zum Erstellen der `AnalyzeObjectCreation` Methode.  Dies erzeugt die richtige Art der Context\-Parameter zu.  
  
## Festlegen von Eigenschaften für Benutzer Ihres Analysemoduls  
 Damit das Analysemodul in Visual Studio\-Benutzeroberfläche ordnungsgemäß angezeigt wird, suchen Sie nach, und ändern Sie die folgende Codezeile das Analysemodul zu identifizieren:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Änderung `"Naming"` auf `"API Guidance"`.  
  
 Als Nächstes suchen und öffnen Sie die Datei "Resources.resx" Ihres Projekts mithilfe der **Projektmappen\-Explorer**.  Sie können eine Beschreibung für den Analyzer, Titel usw. einfügen.  Ändern Sie den Wert für alle diese `“Don’t use ImmutableArray<T> constructor”` vorläufig.  Sie können Zeichenfolgen Argumente in der Zeichenfolge einfügen \({0}, \\{1\\} usw.\), und später beim Aufruf von `Diagnostic.Create()`, können Sie ein Parameterarray von zu übergebenden Argumente angeben.  
  
## Analysieren von Objektausdruck erstellen  
 Die `AnalyzeObjectCreation` Methode nimmt einen anderen Typ von Code Analyzer Framework bereitgestellten Kontext.  Der Initialize\-Methode `AnalysisContext` können Sie zum Einrichten Ihrer Analyzer Aktionsrückrufen registrieren.  Die `SyntaxNodeAnalysisContext`, hat beispielsweise eine `CancellationToken` die Sie Um übergeben können.  Wenn ein Benutzer beginnt, Eingabe im Editor, Abbrechen Roslyn ausgeführte Analysen, um Arbeit zu speichern und die Leistung verbessern.  Als weiteres Beispiel hat dabei eine Knoteneigenschaft, die Erstellung Syntax Objektknotens zurückgibt.  
  
 Rufen Sie den Knoten, der Sie davon ausgehen können, der Typ ist, für den die syntaxknotenaktion gefiltert:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### Starten von Visual Studio mit der Analyzer beim ersten  
 Starten Sie Visual Studio durch Erstellen und Ausführen Ihrer Analyzer \(drücken Sie **F5**\).  Weil die Startup\-Projekt in der **Projektmappen\-Explorer** wird das VSIX\-Projekt Code Builds ausführen, Code und einer VSIX\-Datei, und startet anschließend Visual Studio mit dieser VSIX installiert.  Wenn Sie Visual Studio auf diese Weise starten, wird gestartet mit einer unterschiedlichen Registrierungsstruktur, damit der Hauptverwendungszweck von Visual Studio beim Erstellen des Analyzer nicht durch Ihre testen Instanzen betroffen sind.  Beim ersten Sie auf diese Weise starten führt Visual Studio mehrere wie ähnelt, wenn Sie zunächst Start von Visual Studio nach der Installation.  
  
 Erstellen Sie ein Konsolenprojekt, und geben Sie dann den Array\-Code in der Konsole Applications Main\-Methode:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Die Zeilen des Codes mit `ImmutableArray` Wellenlinien ist, da Sie unveränderliche NuGet\-Paket erhalten und hinzuzufügen, müssen eine `using` Anweisung, um Ihren Code.  Drücken Sie die Pfeil nach rechts\-Taste auf den Projektknoten in der **Projektmappen\-Explorer** und wählen Sie **NuGet\-Pakete verwalten...**.  Klicken Sie im NuGet\-Manager "Unveränderliche" in das Suchfeld eingeben, und wählen Sie das Element "System.Collections.Immutable" \(Wählen Sie nicht "Microsoft.Bcl.Immutable"\) im linken Bereich, und klicken Sie im rechten Bereich auf die Schaltfläche installieren.  Installieren des Pakets Fügt einen Verweis auf den Projektverweisen hinzu.  
  
 Rote Wellenlinien unter weiterhin angezeigt `ImmutableArray`, also Einfügen des Caretzeichens in diesem Bezeichner, und drücken Sie **STRG \+.** \(Punkt\), um die vorgeschlagene Korrektur im Menü anzuzeigen, und wählen Sie die entsprechende hinzufügen `using` Anweisung.  
  
 **Speichern und schließen** die zweite Instanz von Visual Studio jetzt einzufügenden Sie in einen fehlerfreien Zustand aufweist, um den Vorgang fortzusetzen.  
  
## Beenden der Analyzer mit bearbeiten und fortfahren  
 In der ersten Instanz von Visual Studio, legen Sie einen Haltepunkt am Anfang der `AnalyzeObjectCreation` Methode durch Drücken von **F9** mit der Einfügemarke in der ersten Zeile.  
  
 Starten Sie Ihre Analyzer erneut mit **F5**, und in der zweiten Instanz von Visual Studio, und öffnen Sie erneut die Konsolenanwendung, die Sie zuletzt erstellt.  
  
 Sie zurück zur ersten Instanz von Visual Studio an dem Haltepunkt, da der Roslyn\-Compiler Objektausdruck erstellen und die Software in Ihrer Analyzer aufgerufen.  
  
 **Ruft den Knoten des Objekt erstellen.** Prozedurschritt in der Zeile, die `objectCreation` Variable durch Drücken von **F10**, und klicken Sie in der **Direktfenster** Auswerten des Ausdrucks `“objectCreation.ToString()”`.  Sie sehen, dass die syntaxknoten, die die Variable verweist auf den Code `"new ImmutableArray<int>()"`, nur wonach Sie suchen.  
  
 **Typ ImmutableArray \< T \>\-Objekt abzurufen.** Sie müssen überprüfen, ob der erstellte Typ wurde ImmutableArray ist.  Zuerst rufen Sie das Objekt, das diesen Typ darstellt.  Sie überprüfen das Semantikmodell sicherstellen, dass Sie genau den richtigen Typ aufweisen, und Sie nicht die Zeichenfolge aus ToString\(\) verglichen mit Typen.  Geben Sie die folgende Codezeile am Ende der Funktion:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Generische Typen in Metadaten mit Backquotes \('\) und die Anzahl der generischen Parameter werden sollen.  Deshalb nicht angezeigt werden... ImmutableArray \< T \> "in der Name der Metadaten.  
  
 Das Semantikmodell enthält viele nützliche Dinge, mit denen Sie Fragen über Symbole, den Datenfluss, die Lebensdauer der Variablen.  Roslyn trennt syntaxknoten aus dem Semantikmodell aus verschiedenen Gründen engineering \(Leistung, modellieren, fehlerhafte Code usw.\).  Das Kompilierungsmodell in Verweise für genaue Vergleiche enthaltenen Informationen gesucht werden soll.  
  
 Sie können den gelben Ausführungszeiger auf der linken Seite des Editorfensters ziehen.  Ziehen Sie es in der Zeile, die `objectCreation` Variable und die neue Codezeile von Code mit **F10**.  Wenn Sie den Mauszeiger über die Variable bewegen `immutableArrayOfType`, sehen Sie, dass wir den exakten Typ in das semantische Modell gefunden.  
  
 **Erste Objekt Erstellung des Typs eines Ausdrucks.** 'Typ' wird auf verschiedene Weise in diesem Artikel verwendet, aber das bedeutet, wenn Sie "Neues Foo" haben Expression, müssen Sie ein Modell von "Foo" abrufen.  Sie müssen den Typ des Ausdrucks Erstellung Objekt um festzustellen, ob er die ImmutableArray \< T \> ist abrufen.  Verwenden Sie das semantische Modell erneut, um Symbolinformationen für das Typsymbol \(ImmutableArray\) im Ausdruck Erstellung Objekt abzurufen.  Geben Sie die folgende Codezeile am Ende der Funktion:  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Da das Analysemodul unvollständigen oder falschen Code im Editor\-Puffern verarbeitet werden muss \(z. B. ist eine fehlende `using` Anweisung\), Sie sollten überprüfen, ob `symbolInfo` wird `null`.  Müssen Sie einen benannten Typ \(INamedTypeSymbol\) abrufen aus dem Objekt Symbol Information zum Abschluss der Analyse.  
  
 **Vergleichen Sie die Typen.** Da ist ein offener generischer Typ von T, die wir benötigen und der Typ im Code einen konkreten generischer Typ ist, wird Sie Abfragen die Symbolinformationen für Typ aus \(ein offener generischer Typ\) erstellt wird und vergleichen Sie das Ergebnis mit `immutableArrayOfTType`.  Geben Sie Folgendes am Ende der Methode:  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **Die Diagnose zu melden.** Die Diagnose Reporting ist recht einfach.  Sie verwenden die Regel für Sie erstellt werden, in der Projektvorlage, die vor der Initialize\-Methode definiert ist.  Da dies im Code einen Fehler handelt, können, ändern Sie die Zeile, die mit dieser Regel werden ersetzen initialisiert `DiagnosticSeverity.Warning` \(grünen Wellenlinie\) mit `DiagnosticSeverity.Error` \(rote Wellenlinie\).  Der Rest der Regel initialisiert aus den Ressourcen, die Sie am Anfang der exemplarischen Vorgehensweise bearbeitet.  Sie müssen auch den Speicherort für die Wellenlinie melden den Speicherort der Spezifikation für das Objekt Erstellung Aggregatspalte.  Geben Sie diesen Code in die `if` Block:  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 Die Funktion sollte \(möglicherweise unterschiedlich formatiert\) aussehen:  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 Entfernen Sie den Haltepunkt, damit Sie können finden Sie unter der Analyzer arbeiten \(und Beenden der Rückgabe an die erste Instanz von Visual Studio\).  Ziehen Sie am Anfang der Methode, und drücken Sie die Ausführungszeiger **F5** um die Ausführung fortzusetzen.  Wenn Sie zurück in die zweite Instanz von Visual Studio wechseln, der Compiler wird gestartet, um den Code erneut zu überprüfen, und er ruft in der Analyzer.  Sie sehen eine Wellenlinie unter `ImmutableType<int>`.  
  
## Ein "Hotfix" hinzufügen für das Codeproblem  
 Bevor Sie beginnen, schließen Sie die zweite Instanz von Visual Studio und beenden Sie das Debuggen in der ersten Instanz von Visual Studio \(wobei Sie den Analyzer entwickeln\).  
  
 **Fügen Sie eine neue Klasse hinzu.** Verwenden Sie das Kontextmenü \(Schaltfläche Pfeil nach rechts\) auf den Projektknoten im Projektmappen\-Explorer, und wählen Sie ein neues Element hinzufügen.  Fügen Sie eine Klasse namens `BuildCodeFixProvider`.  Diese Klasse muss vom ableiten `CodeFixProvider`, und Sie müssen mit **STRG \+.** \(Punkt\), um den korrigierten Code aufzurufen, der die richtige fügt `using` Anweisung.  Diese Klasse muss angemerkt werden `ExportCodeFixProvider` \-Attribut, und Sie müssen hinzufügen eine `using` Anweisung zum Auflösen der `LanguageNames` Enum.  Sie benötigen eine Klassendatei mit dem folgenden Code:  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **Abgeleitete Elemente ersetzen.** Jetzt Zirkumflexzeichen des Editors im Bezeichner `CodeFixProvider` und drücken Sie die **STRG \+.** \(Punkt\), um die Implementierung dieser abstrakten Basisklasse stub.  Dadurch wird eine Eigenschaft und eine Methode für Sie generiert.  
  
 **Implementieren Sie die Eigenschaft.** Füllen Sie die `FixableDiagnosticIds` Eigenschaft `get` Text durch den folgenden Code:  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn vereint Diagnose und korrigiert, indem der entsprechende Bezeichner, die nur Zeichenfolgen sind.  Die Projektvorlage eine Diagnose\-ID für Sie generiert, und Sie ändern.  Der Code in der Eigenschaft gibt nur die ID von der Analyzer\-Klasse zurück.  
  
 **Die RegisterCodeFixAsync\-Methode nimmt einen Kontext.** Der Kontext ist wichtig, da ein Codeupdate kann für mehrere Diagnose, oder es mehr als ein Problem in einer Zeile des Codes kann.  Bei der Eingabe von "Context". im Text der Methode werden die Intellisense\-Vervollständigungsliste Sie einige nützliche Member anzeigen  Es ist ein CancellationToken\-Element, das Sie überprüfen können, um festzustellen, ob etwas das Update abbrechen möchte.  Es ist ein Dokument\-Element, das viele nützliche Member und können Sie auf die Modellobjekte von Projekt\- und Projektmappendateien abrufen.  Es ist ein Span\-Element, das den Beginn und Ende der Speicherort des angegeben, wenn Sie die Diagnose gemeldet.  
  
 **Stellen Sie die Methode asynchron sein.** Als Erstes müssen Sie ist, beheben Sie die generierte Methodendeklaration werden eine `async` Methode.  Der korrigierten Code für die Implementierung einer abstrakten Klasse Stubs umfasst nicht die `async` \-Schlüsselwort enthalten, obwohl die Methode gibt ein `Task`.  
  
 **Abrufen der Stamm der Syntaxstruktur.** Macht Ihren Codefix Code ändern, Sie eine neue Syntaxstruktur mit den Änderungen zu erzeugen müssen.  Sie müssen die `Document` aus dem Kontext aufrufen `GetSyntaxRootAsync`.  Dies ist eine asynchrone Methode, da unbekannte Arbeit zum Abrufen der Syntaxstruktur, einschließlich möglicherweise die Datei vom Datenträger abrufen, zu analysieren und erstellen das Roslyn\-Codemodell dafür vorliegt.  Visual Studio\-Benutzeroberfläche sollte während dieses Zeitraums hierbei die Reaktionsfähigkeit `async` ermöglicht.  Ersetzen Sie die Codezeile in der Methode durch Folgendes:  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **Suchen Sie den Knoten mit dem Problem.** Übergeben Sie den Kontext Spanne, aber den Knoten, den Sie finden den Code möglicherweise nicht zu ändern.  Die gemeldeten Diagnose die Spanne nur für die Typ\-ID \(wobei die Wellenlinie gehörte\) bereitgestellt, jedoch müssen Sie den gesamte Objektausdruck ersetzen einschließlich der `new` Keywoard am Anfang und die Klammern am Ende.  Fügen Sie den folgenden Code zur Methode \(und **STRG \+.** Hinzufügen einer `using` \-Anweisung für `ObjectCreationExpressionSyntax`\):  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **Registrieren Sie Ihr Codefix für die Glühbirne Benutzeroberfläche.** Wenn Sie Ihren Codefix registrieren, schließt Roslyn automatisch an die Visual Studio\-Glühbirne Benutzeroberfläche an.  Endbenutzer erhalten, können Sie **STRG \+.** \(Punkt\), wenn Ihr Analysemodul ein ungültiger Wellenlinien `ImmutableArray<T>` Konstruktor verwenden.  Da der Anbieter nur ausgeführt wird, wenn ein Problem vorliegt, können Sie davon ausgehen, dass Sie die Erstellung Objektausdruck verfügen, die Sie suchen.  Durch den Kontextparameter, können Sie der neuen Codekorrektur registrieren, indem Sie den folgenden Code am Ende hinzufügen `RegisterCodeFixAsync` Methode:  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 Sie müssen an der Einfügemarke des Editors in der ID `CodeAction`, dann **STRG \+.** \(Punkt\), um die entsprechenden hinzufügen `using` Anweisung für diesen Typ.  
  
 Platzieren Sie die Einfügemarke des Editors, in der `ChangeToImmutableArrayEmpty` Bezeichner und Verwendung **STRG \+.** erneut aus, um diese Methodenstub für Sie generiert werden.  
  
 Dieser letzten Codeausschnitt hinzufügen registriert den korrigierten Code durch Übergeben einer `CodeAction` und die Diagnose\-ID für die Art von Problem gefunden.  In diesem Beispiel ist nur eine Diagnose\-ID, die diesen Code enthält, Updates, übergeben Sie einfach das erste Element des Arrays diagnostische IDs können.  Beim Erstellen der `CodeAction`, übergeben Sie den Text, der die Glühbirne Benutzeroberfläche als eine Beschreibung für den korrigierten Code verwenden soll.  Sie übergeben ebenfalls in einer Funktion, die von einem CancellationToken und gibt ein neues Dokument.  Das neue Dokument verfügt über eine neue Syntaxstruktur, die gepatchten Code enthält, die Aufrufe `ImmutableArray.Empty`.  Dieser Codeausschnitt verwendet einen Lambda\-Ausdruck, sodass es über den ObjectCreation\-Knoten und den Kontext Dokument schließen kann.  
  
 **Erstellen Sie die neue Syntaxstruktur.** In der `ChangeToImmutableArrayEmpty` Methode, deren Stub, die Sie zuvor generiert die Codezeile eingeben: `ImmutableArray<int>.Empty;`.  Wenn Sie die Syntax Visualizer\-Toolfenster erneut anzeigen, sehen Sie sich diese Syntax einen Knoten "simplememberaccessexpression" klicken.  Das ist Was muss diese Methode erstellen und in einem neuen Dokument zurückzukehren.  
  
 Die erste Änderung an `ChangeToImmutableArrayEmpty` Hinzufügen `async` vor `Task<Document>` da der Code\-Generatoren davon ausgehen können, sollte die Methode asynchron sein.  
  
 Geben Sie den Text durch den folgenden Code, damit Ihre Methode etwa wie folgt aussieht:  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 Sie benötigen, setzen Sie die Einfügemarke des Editors in die `SyntaxGenerator` \-ID und Verwendung **STRG \+.** \(Punkt\), um die entsprechenden hinzufügen `using` Anweisung für diesen Typ.  
  
 Dieser Code verwendet `SyntaxGenerator`, ist ein sehr nützlich für neuen Code erstellen.  Nach der erste eines Generators für das Dokument, das das Codeproblem hat `ChangeToImmutableArrayEmpty` Aufrufe `MemberAccessExpression`, übergeben Sie den Typ, die das Element zugreifen soll, und übergeben Sie den Namen des Elements als Zeichenfolge.  
  
 Als Nächstes die Methode ruft den Stammknoten des Dokuments, und da dies beliebige Arbeit im Allgemeinen umfassen kann, wird der Code wartet auf diesen Aufruf und übergibt das Abbruchtoken.  Roslyn Codemodelle sind unveränderlich, wie das Arbeiten mit einer Zeichenfolge .NET. Wenn Sie die Zeichenfolge aktualisieren, erhalten Sie im Gegenzug ein neues Zeichenfolgenobjekt.  Beim Aufruf von `ReplaceNode`, erhalten Sie einen neuen Stammknoten.  Die meisten der Syntaxstruktur freigegeben ist \(weil er unveränderlich ist\), aber die `objectCreation` Knoten wird durch ersetzt die `memberAccess` Knoten als auch die übergeordneten Knoten bis zum Stamm Syntax\-Struktur.  
  
## Versuchen Ihr Codefix  
 Sie können jetzt drücken **F5** das Analysemodul in einer zweiten Instanz von Visual Studio ausführen.  Öffnen Sie die Konsolenprojekt verwendet.  Nun sollte die Glühbirne angezeigt, in dem die neue Erstellung Objektausdruck ist `ImmutableArray<int>`.  Wenn Sie drücken **STRG \+.** \(Punkt\), dann sehen Sie den Code zu beheben, und sehen Sie eine Vorschau auf automatisch generierten Code Unterschied in der Glühbirne Benutzeroberfläche.  Roslyn wird dies für Sie erstellt.  
  
 Pro\-Tipp: Wenn Sie die zweite Instanz von Visual Studio starten und mit Ihr Codefix die Glühbirne angezeigt, dann müssen Sie den Visual Studio\-Komponente\-Cache löschen.  Löschen des Zwischenspeichers erzwingt, dass Visual Studio die Komponenten neu zu überprüfen, damit Visual Studio die neueste Komponente dann übernehmen soll.  Fahren Sie zunächst die zweite Instanz von Visual Studio.  Klicken Sie dann in Windows\-Explorer, wechseln Sie zu Ihrem Verzeichnis \(c:\\users\\ \< Userid \>\) und finden Sie AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\.  Löschen Sie in diesem Verzeichnis das Unterverzeichnis ComponentModelCache.  Die "14" ändert sich je nach Version von Visual Studio.  
  
## Vortrag Video\- und Codeprojekt Fertig stellen  
 Sie finden dieses Beispiel entwickelt und erläutert weiter in [dieser Vortrag](http://channel9.msdn.com/events/Build/2015/3-725).  Die Rede veranschaulicht den Analyzer arbeiten und führt Sie durch diese zu erstellen.  
  
 Sie können alle der fertige Code finden Sie unter [hier](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Die untergeordneten Ordner DoNotUseImmutableArrayCollectionInitializer und DoNotUseImmutableArrayCtor haben eine C\#\-Datei für die Suche nach Problemen und eine c\#\-Datei, die Code\-Updates, die in der Visual Studio\-Glühbirne UI angezeigt implementiert werden.  Beachten Sie, dass der fertige Code etwas mehr Abstraktion zu vermeiden, das Typobjekt ImmutableArray \< T \> immer wieder abgerufen wurde.  Geschachtelte registrierte Aktionen verwendet, um das Type\-Objekt in einem Kontext zu speichern, die verfügbar ist immer die Sub\-Aktionen \(Erstellung analysieren und Analysieren der Auflistung wie\) ausführen.  
  
## Siehe auch  
 [\\\\Build 2015 sprechen](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Vollständiger Code auf github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Einige Beispiele für Github, gruppiert nach drei Arten von Analysen](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Andere Dokumente auf der Github OSS\-Website](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [FxCop\-Regeln, die mit Roslyn\-Analyzer auf Github implementiert](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)