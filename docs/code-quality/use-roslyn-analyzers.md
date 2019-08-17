---
title: Schweregrad und Unterdrückung der Analyse Regel
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6362d3f14065aaf9661e85266753642e4201ca48
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548037"
---
# <a name="use-code-analyzers"></a>Verwenden von Code Analysemodulen

.NET Compiler Platform ("Roslyn")-Code-Analysen C# analysieren Ihren-oder-Visual Basic Code, während Sie eingeben. Jede *Diagnose* oder Regel weist einen Standard Schweregrad und Unterdrückungs Status auf, der für Ihr Projekt überschrieben werden kann. In diesem Artikel werden der Schweregrad der Regel, die Verwendung von Regelsätzen und das Unterdrücken von Verletzungen behandelt

## <a name="analyzers-in-solution-explorer"></a>Analyzers in Projektmappen-Explorer

Sie können einen Großteil der Anpassung der Analyzer-Diagnose von **Projektmappen-Explorer**erledigen. Wenn Sie [Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren, wird in **Projektmappen-Explorer**unter dem Knoten **Verweise** oder **Abhängigkeiten** ein **Analysen** -Knoten angezeigt. Wenn Sie **Analyzers**erweitern und dann eine der Analyzer-Assemblys erweitern, werden alle Diagnosen in der Assembly angezeigt.

![Analyzers-Knoten in Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Im **Eigenschaften** Fenster können Sie die Eigenschaften einer Diagnose einschließlich der Beschreibung und des Standard schwere Grads anzeigen. Um die Eigenschaften anzuzeigen, klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Eigenschaften**aus, oder wählen Sie die Regel aus, und drücken Sie die**Eingabe** **Taste**+

![Diagnose Eigenschaften in Eigenschaftenfenster](media/analyzer-diagnostic-properties.png)

Um die Online Dokumentation für eine Diagnose anzuzeigen, klicken Sie mit der rechten Maustaste auf die Diagnose, und wählen Sie **Hilfe anzeigen**aus.

Die Symbole neben den einzelnen Diagnose in **Projektmappen-Explorer** entsprechen den Symbolen, die im Regelsatz angezeigt werden, wenn Sie Sie im Editor öffnen:

- "i" in einem Kreis zeigt den [Schweregrad](#rule-severity) der **Informationen** an.
- "!" in einem Dreieck weist auf den [Schweregrad](#rule-severity) " **Warnung** " hin.
- Das "x" in einem Kreis zeigt den [Schweregrad](#rule-severity) " **Fehler** " an.
- Das "i" in einem Kreis in einem hellfarbigen Hintergrund weist auf den [Schweregrad](#rule-severity) " **ausgeblendet** " hin.
- der nach unten zeigende Pfeil in einem Kreis gibt an, dass die Diagnose unterdrückt wird.

![Diagnose Symbole in Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Regelsätze

Bei einem [Regelsatz](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) handelt es sich um eine XML-Datei, in der der Schweregrad und der Unterdrückungs Zustand für einzelne

> [!NOTE]
> Regelsätze können Regeln aus der Legacy-und Code Analyse enthalten.

Um den aktiven Regelsatz im Regelsatz-Editor zu bearbeiten, klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** > -**Analyzers** , und wählen Sie **aktiven Regelsatz öffnen**aus. Wenn Sie den Regelsatz zum ersten Mal bearbeiten, erstellt Visual Studio eine Kopie der standardmäßigen Regel Satz Datei, benennt Sie  *\<mit ProjectName >. RuleSet*und fügt Sie dem Projekt hinzu. Dieser benutzerdefinierte Regelsatz wird auch zum aktiven Regelsatz für Ihr Projekt.

Zum Ändern des aktiven Regelsatzes für ein Projekt navigieren Sie zur Registerkarte **Code Analyse** der Eigenschaften eines Projekts. Wählen Sie in der Liste unter **diesen Regelsatz ausführen**den Regelsatz aus. Wählen Sie **Öffnen**aus, um den Regelsatz zu öffnen.

> [!NOTE]
> .Net Core-und .NET Standard-Projekte unterstützen nicht die Menübefehle für Regelsätze in **Projektmappen-Explorer**, z. b. **Öffnen des aktiven Regelsatzes**. Wenn Sie einen nicht standardmäßigen Regelsatz für ein .net Core-oder .NET Standard-Projekt angeben möchten, [fügen Sie die Eigenschaft " **codeanalysisruleset** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) " manuell zur Projektdatei hinzu. Sie können die Regeln im Regelsatz weiterhin in der Benutzeroberfläche von Visual Studio-Regelsatz-Editor konfigurieren.

## <a name="rule-severity"></a>Regelschweregrad

Sie können den Schweregrad der Analyzer-Regeln oder der *Diagnose*konfigurieren, wenn Sie [die-Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren. In der folgenden Tabelle werden die Optionen für den Schweregrad der Diagnose angezeigt:

|Schweregrad|Build-Zeitverhalten|Editor-Verhalten|
|-|-|-|
|Fehler|Verstöße werden im **Fehlerliste** und in der Befehlszeilen-Buildausgabe als *Fehler* angezeigt und bewirken, dass Builds fehlschlagen.|Das verletzen von Code wird mit einer roten Wellenlinie unterstrichen und in der Bild Lauf Leiste durch ein kleines rotes Feld markiert.|
|Warnung|Verstöße werden im **Fehlerliste** und in der Befehlszeilen-Buildausgabe als *Warnungen* angezeigt, bewirken jedoch nicht, dass Builds fehlschlagen.|Das verletzen von Code wird mit einer grünen Wellenlinie unterstrichen und in der Bild Lauf Leiste durch ein kleines grünes Feld markiert.|
|Info|Verstöße werden im **Fehlerliste**als *Meldungen* und nicht in der Befehlszeilen-Buildausgabe angezeigt.|Das verletzen von Code wird mit einem grauen Wellenlinien unterstrichen und in der Bild Lauf Leiste durch ein kleines graues Feld markiert.|
|Ausgeblendet|Für den Benutzer nicht sichtbar.|Für den Benutzer nicht sichtbar. Die Diagnose wird jedoch der IDE-Diagnose-Engine gemeldet.|
|None|Vollständig unterdrückt.|Vollständig unterdrückt.|

Außerdem können Sie den Schweregrad einer Regel "Zurücksetzen", indem Sie ihn auf " **default**" festlegen. Jede Diagnose hat einen Standard Schweregrad, der im **Eigenschaften** Fenster angezeigt werden kann.

Der folgende Screenshot zeigt drei verschiedene Diagnose Verstöße im Code-Editor mit drei unterschiedlichen Schweregraden. Beachten Sie die Farbe der Wellenlinie und das kleine Feld in der Bild Lauf Leiste auf der rechten Seite.

![Fehler-, Warn-und Informations Verstoß im Code-Editor](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt dieselben drei Verstöße, wie Sie im **Fehlerliste**angezeigt werden:

![Fehler-, Warn-und Informations Verstoß in Fehlerliste](media/diagnostics-severities-in-error-list.png)

Sie können den Schweregrad einer Regel von **Projektmappen-Explorer**oder innerhalb der  *\<Datei ProjectName >. RuleSet* ändern, die der Projekt Mappe hinzugefügt wird, nachdem Sie den Schweregrad einer Regel in **Projektmappen-Explorer**geändert haben.

![Regel Satz Datei in Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen des schwere Grads der Regel Projektmappen-Explorer

1. Erweitern Sie in **Projektmappen-Explorer**den Eintrag **References** > Analyzer (**Abhängigkeits** >  **Analyse** für .net Core-Projekte).

1. Erweitern Sie die Assembly, die die Regel enthält, für die Sie den Schweregrad festlegen möchten.

1. Klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Regelsatz Schweregrad festlegen**. Wählen Sie im Menü für die Ausführung eine der Optionen für den Schweregrad aus.

   Der Schweregrad für die Regel wird in der aktiven Regel Satz Datei gespeichert.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Festlegen des Regel schwere Grads in der Regel Satz Datei

1. Öffnen Sie die [Regel Satz](analyzer-rule-sets.md) Datei, indem Sie in **Projektmappen-Explorer**auf die Datei doppelklicken und im Kontextmenü des **Analyzers** -Knotens die Option **aktiven Regelsatz öffnen** auswählen, oder indem Sie auf der Eigenschaften Seite **Code Analyse** die Option **Öffnen** auswählen. Das Projekt.

1. Navigieren Sie zu der Regel, indem Sie die enthaltende Assembly erweitern.

1. Wählen Sie in der Spalte **Aktion** den Wert aus, um eine Dropdown Liste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste aus.

   ![Regel Satz Datei in Editor öffnen](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Verstöße unterdrücken

Es gibt mehrere Möglichkeiten, Regel Verletzungen zu unterdrücken:

- Über das Menü " **analysieren** "

  Wählen Sie in der Menüleiste **Analyse** > **Ausführen Code Analyse und unterdrücken aktiver Probleme** aus, um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

- Von **Projektmappen-Explorer**

  Um einen Verstoß in **Projektmappen-Explorer**zu unterdrücken, legen Sie den Schweregrad der Regel auf " **keine**" fest.

- Aus dem **Regelsatz-Editor**

  Um einen Verstoß gegen den Regelsatz-Editor zu unterdrücken, deaktivieren Sie das Kontrollkästchen neben dem Namen, oder legen Sie die **Aktion** auf **keine**fest.

- Im **Code-Editor**

  Um einen Verstoß im Code-Editor zu unterdrücken, platzieren Sie den Cursor in der Codezeile mit der Verletzung, und drücken Sie die **STRG**+-Taste **.** um das Menü **schnell Aktionen** zu öffnen. Wählen Sie **CAXXXX** > **in Quelle/in Unterdrückungs Datei unter**drücken.

  ![Diagnose über das Menü "schnelle Aktionen" unterdrücken](media/suppress-diagnostic-from-editor.png)

- Aus der **Fehlerliste**

  Sie können eine oder mehrere Diagnosen aus dem **Fehlerliste** unterdrücken, indem Sie die zu unterdrückenden Daten auswählen und dann mit der rechten Maustaste klicken und**in der Quelle/in der Unterdrückungs Datei**unter **drücken** > auswählen.

  - Wenn Sie **in Quelle**unterdrücken, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, und C# es wird eine Vorschau der [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) -oder Visual Basic [#Disable Warning](/dotnet/visual-basic/language-reference/directives/directives) -Direktive angezeigt, die dem Quellcode hinzugefügt wird.

    ![Vorschau der Hinzufügung von #pragma Warnung in der Codedatei](media/pragma-warning-preview.png)

  - Wenn Sie **in Unterdrückungs Datei**auswählen, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, und <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> es wird eine Vorschau des Attributs angezeigt, das der globalen Unterdrückungs Datei hinzugefügt wird.

    ![Vorschau zum Hinzufügen des SuppressMessage-Attributs zur Unterdrückungs Datei](media/preview-changes-in-suppression-file.png)

  Wählen Sie im Dialogfeld Vorschau der **Änderungen** übernehmen aus.

  > [!NOTE]
  > Wenn die Option Menü unter **drücken** in **Projektmappen-Explorer**nicht angezeigt wird, wird die Verletzung wahrscheinlich von Build und nicht von Live-Analyse stammt. In der **Fehlerliste** werden Diagnose-oder Regelverstöße sowohl aus der Live Code Analyse als auch aus dem Build angezeigt. Da die builddiagnose beispielsweise veraltet sein kann, wenn Sie z. b. den Code bearbeitet haben, um den Verstoß zu beheben, aber nicht neu erstellt wurde, können Sie diese Diagnose nicht im **Fehlerliste**unterdrücken. Die Diagnose aus Live Analyse oder IntelliSense sind immer auf dem neuesten Stand mit aktuellen Quellen und können vom **Fehlerliste**unterdrückt werden. Um die builddiagnose von Ihrer Auswahl auszuschließen, ändern Sie den **Fehlerliste** Quellen Filter von **Build + IntelliSense** **nur in IntelliSense**. Wählen Sie dann die Diagnose aus, die Sie unterdrücken möchten, und fahren Sie wie zuvor beschrieben fort.
  >
  > ![Fehlerliste Quellen Filter in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Befehlszeilen Verwendung

Wenn Sie das Projekt in der Befehlszeile erstellen, werden Regelverstöße in der Buildausgabe angezeigt, wenn die folgenden Bedingungen erfüllt sind:

- Die Analysen werden als nuget-Paket und nicht als VSIX-Erweiterung installiert.

- Mindestens eine Regel wird im Code des Projekts verletzt.

- Der [Schweregrad](#rule-severity) einer verletzten Regel ist auf " **Warnung**" festgelegt. in diesem Fall bewirken Verstöße nicht, dass der Buildvorgang fehlschlägt oder dass ein **Fehler**auftritt.

Die Ausführlichkeit der Buildausgabe wirkt sich nicht darauf aus, ob Regelverstöße angezeigt werden. Auch mit der **stillen** Ausführlichkeit werden Regel Verletzungen in der Buildausgabe angezeigt.

> [!TIP]
> Wenn Sie daran gewöhnt sind, eine Legacy Analyse von der Befehlszeile aus durchzuführen, entweder mit " *FxCopCmd. exe* " oder über MSBuild mit dem **RunCodeAnalysis** -Flag, gehen Sie wie folgt vor: Code-Analyzers.

Um Analyzer-Verstöße in der Befehlszeile anzuzeigen, wenn Sie das Projekt mithilfe von MSBuild erstellen, führen Sie einen Befehl wie den folgenden aus:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Die folgende Abbildung zeigt die Befehlszeilen-Buildausgabe der Erstellung eines Projekts, das eine Verletzung der Analyse Regel enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Abhängige Projekte

Wenn Sie in einem .net Core-Projekt einen Verweis auf ein Projekt hinzufügen, das über nuget-Analysen verfügt, werden diese Analysen dem abhängigen Projekt ebenfalls automatisch hinzugefügt. Um dieses Verhalten zu deaktivieren, z. b. wenn das abhängige Projekt ein Komponenten Testprojekt ist, markieren Sie das nuget-Paket als privat in der *csproj* -oder *vbproj* -Datei des referenzierten Projekts, indem Sie das **privateassets** -Attribut festlegen:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Code Analyzer-Fehlers](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Code Analyse Warnungen unterdrücken](../code-quality/in-source-suppression-overview.md)
