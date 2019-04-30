---
title: Regelschweregrad Analyzer und unterdrücken
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
ms.openlocfilehash: 56637ee7826b944d739e170faf22ae354abd8adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821423"
---
# <a name="use-roslyn-analyzers"></a>Verwenden von Roslyn-Analysetools

.NET Compiler Platform ("Roslyn") Analyzer-Regeln, oder *Diagnose*, Ihren C#- oder Visual Basic-Code analysieren, während der Eingabe. Jeder Diagnose enthält einen Standardzustand Schweregrad und unterdrücken, der für Ihr Projekt überschrieben werden kann. Dieser Artikel behandelt die Einstellung Schweregrad für Regelsatz, verwenden von Regelsätzen und Unterdrücken von Verletzungen.

## <a name="analyzers-in-solution-explorer"></a>Analyzer im Projektmappen-Explorer

Sie können nicht viel die Anpassung der Analyzer eine Diagnose aus **Projektmappen-Explorer**. Wenn Sie [installieren Analysetools](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket, ein **Analysen** Knoten befindet sich unter dem **Verweise** oder **Abhängigkeiten** Knoten  **Projektmappen-Explorer**. Wenn Sie erweitern **Analysen**, und erweitern Sie dann eine der Assemblys Analyzer, alle Diagnosen in der Assembly.

![Knoten "Analyzer" im Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Sehen Sie die Eigenschaften einer Diagnose, einschließlich einer Beschreibung und den standardschweregrad, in der **Eigenschaften** Fenster. Zum Anzeigen der Eigenschaften, mit der Maustaste, auf die Regel, und wählen **Eigenschaften**, oder wählen Sie die Regel, und drücken Sie dann die **Alt**+**EINGABETASTE**.

![Diagnose Eigenschaften im Fenster "Eigenschaften"](media/analyzer-diagnostic-properties.png)

Um Onlinedokumentation für eine Diagnose anzuzeigen, mit der rechten Maustaste auf die Diagnose, und wählen Sie **Sicht Ihnen helfen,**.

Die Symbole neben jeder Diagnose in **Projektmappen-Explorer** entsprechen den Symbolen, die Sie in der Regel festgelegt, wenn Sie im Editor zu öffnen. finden Sie unter:

- Gibt an, das "i" in einem Kreis eine [Schweregrad](#rule-severity) von **Informationen**
- die "!" in einem Dreieck bedeutet eine [Schweregrad](#rule-severity) von **Warnung**
- Gibt an, das "X" in einem Kreis eine [Schweregrad](#rule-severity) von **Fehler**
- Gibt an, das "i" in einem Kreis auf einem hellen Hintergrund einer [Schweregrad](#rule-severity) von **ausgeblendet**
- der nach unten zeigenden Pfeil im Kreis gibt an, dass die Diagnose unterdrückt werden

![Diagnose-Symbole im Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Regelsätze

Ein [Regelsatz](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) ist eine XML-Datei, die den Schweregrad und Unterdrücken von Status für die einzelnen-Diagnose speichert.

> [!NOTE]
> Regelsätze können Regeln von Roslyn-Analysetools und Analyse von statischem (binären) Code enthalten.

Um den aktiven Regelsatz, der in dem Regelsatz-Editor zu bearbeiten, mit der Maustaste auf die **Verweise** > **Analysen** Knoten **Projektmappen-Explorer** , und wählen Sie **Öffnen aktiven Regelsatz**. Ist dies beim ersten bearbeiten Sie den Regelsatz, Visual Studio erstellt eine Kopie der Standardregel, die Datei festlegen, das den Namen  *\<Projektname > ruleSet*, und fügt sie dem Projekt hinzu. Diese benutzerdefinierte Regel, die auch festgelegt wird, den aktiven Regelsatz, der für Ihr Projekt.

Navigieren Sie zu, um den aktiven Regelsatz für ein Projekt zu ändern, die **Codeanalyse** auf der Registerkarte Eigenschaften des Projekts. Wählen Sie den Regelsatz aus der Liste unter **diesen Regelsatz ausführen**. Wählen Sie zum Öffnen des Regelsatzes **öffnen**.

> [!NOTE]
> .NET Core und .NET Standard-Projekte unterstützen nicht die Befehle im Menü aus, für die Regelsätze im **Projektmappen-Explorer**, z. B. **öffnen aktiven Regelsatz**. An einen nicht standardmäßigen Regelsatz für ein .NET Core oder .NET Standard-Projekt manuell [Hinzufügen der **CodeAnalysisRuleSet** Eigenschaft, um die Projektdatei](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project). Sie können die Regeln in der Regel in der Visual Studio festgelegt, dass die Regelsatz-Editor-Benutzeroberfläche konfigurieren.

## <a name="rule-severity"></a>Regelschweregrad

Sie können den Schweregrad der Analyzer-Regeln konfigurieren oder *Diagnose*, wenn Sie [installieren Sie die Analysetools](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket. Die folgende Tabelle zeigt die Schweregrad-Optionen für die Diagnose:

|Schweregrad|Buildzeit-Verhalten|Editor-Verhalten|
|-|-|-|
|Fehler|Verletzungen angezeigt werden, als *Fehler* in die **Fehlerliste** in Befehlszeile Buildausgabe und dazu führen, dass Builds fehlschlagen.|Problematische Code ist mit einem roten Wellenlinie, und von einem kleinen roten Feld in der Bildlaufleiste markierte unterstrichen.|
|Warnung|Verletzungen angezeigt werden, als *Warnungen* in die **Fehlerliste** und in der Befehlszeile Buildausgabe, verursachen jedoch keine Builds fehlschlagen.|Problematische Code ist mit einem grünen durch ein kleines grünes Feld auf der Schiebeleiste markiert und Wellenlinien unterstrichen.|
|Info|Verletzungen angezeigt werden, als *Nachrichten* in die **Fehlerliste**, und nicht in Build per Befehlszeile Ausgabe.|Problematische Code ist mit einem grau markiert, indem eine kleine graue Feld in der Bildlaufleiste und Wellenlinien unterstrichen.|
|Hidden|Nicht sichtbare für Benutzer.|Nicht sichtbare für Benutzer. Die Diagnose wird jedoch an die IDE-Diagnose-Engine gemeldet.|
|Keiner|Unterdrückt vollständig.|Unterdrückt vollständig.|

Darüber hinaus, Sie können "Zurücksetzen" des Schweregrads einer Regel durch Festlegung auf **Standard**. Jede Diagnose weist einen standardschweregrad, die in angezeigt werden die **Eigenschaften** Fenster.

Der folgende Screenshot zeigt drei verschiedene diagnostische Verstöße im Code-Editor, mit drei unterschiedlichem Schweregrad. Beachten Sie die Farbe der Wellenlinien, als auch das kleine Feld in der Bildlaufleiste auf der rechten Seite aus.

![Verletzung der Fehler-, Warn- und Informationen im Code-editor](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt die gleichen drei Verstöße an, wie in der **Fehlerliste**:

![Verletzung der Fehler-, Warn- und Informationen in der Fehlerliste](media/diagnostics-severities-in-error-list.png)

Sie können ändern, den Schweregrad einer Regel aus **Projektmappen-Explorer**, oder innerhalb der  *\<Projektname > ruleSet* -Datei, die der Projektmappe hinzugefügt wird, nachdem Sie den Schweregrad einer Regel in Ändern **Projektmappen-Explorer**.

![Die Regelsatzdatei im Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen Sie Schweregrad für Regelsatz, im Projektmappen-Explorer

1. In **Projektmappen-Explorer**, erweitern Sie **Verweise** > **Analysen** (**Abhängigkeiten**  >  **Analysen** für .NET Core-Projekte).

1. Erweitern Sie die Assembly, die die Regel enthält, die, der Sie den Schweregrad für festlegen möchten.

1. Mit der rechten Maustaste auf die Regel, und wählen **Schweregrad für Regelsatz festlegen**. Wählen Sie im eingeblendeten Menü eine der Optionen Schweregrad aus.

   Der Schweregrad für die Regel wird in der aktiven Regelsatzdatei gespeichert.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Festlegen Sie Schweregrad für Regelsatz, in der Regelsatzdatei

1. Öffnen der [Regelsatz](analyzer-rule-sets.md) Datei durch Doppelklick im **Projektmappen-Explorer**, wählen **öffnen aktiven Regelsatz** auf das Kontextmenü des der **Analysen** Knoten, oder indem **öffnen** auf die **Codeanalyse** Eigenschaftenseite für das Projekt.

1. Navigieren Sie zu der Regel durch Erweitern der enthaltenden Assembly.

1. In der **Aktion** Spalte wählen Sie den Wert auf eine Dropdown-Liste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste.

   ![Regelsatzdatei in Editor öffnen](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Unterdrücken von Verstößen

Es gibt mehrere Möglichkeiten, um Verletzungen zu unterdrücken:

- Von der **analysieren** Menü

   Wählen Sie **analysieren** > **Codeanalyse ausführen und aktive Probleme unterdrücken** in der Menüleiste, um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

- Von **Projektmappen-Explorer**

   Um einen Verstoß in zu unterdrücken, **Projektmappen-Explorer**, legen Sie den Schweregrad der Regel auf **keine**.

- Von der **Regelsatz-Editor**

   Um einen Verstoß aus dem Regelsatz-Editor zu unterdrücken, deaktivieren Sie das Kontrollkästchen neben seinem Namen aus, oder legen Sie **Aktion** zu **keine**.

- Von der **Code-Editor**

   Um einen Verstoß im Code-Editor zu unterdrücken, platzieren Sie den Cursor in die Zeile des Codes, mit der Verletzung und drücken Sie **STRG**+**.** zum Öffnen der **Schnellaktionen** Menü. Wählen Sie **unterdrücken CAXXXX** > **in Quelle/in Unterdrückungsdatei**.

   ![Vom Menü "schnelle Aktionen" Diagnose unterdrücken](media/suppress-diagnostic-from-editor.png)

- Von der **Fehlerliste**

   Können Sie eine Diagnose aus einem oder mehreren Unterdrücken der **Fehlerliste** durch Auswählen der gewünschten unterdrückt werden sollen, und klicken Sie dann mit der rechten Maustaste und Auswählen von **unterdrücken** > **In Source/In Unterdrückungsdatei**.

   - Wenn Sie unterdrücken **In Quelle**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau des der C# [#pragma-Warnung](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) oder Visual Basic [#Disable Warnung](/dotnet/visual-basic/language-reference/directives/directives) Richtlinie, die den Quellcode hinzugefügt wird.

      ![Vorschau der #pragma-Warnung in der Codedatei hinzufügen](media/pragma-warning-preview.png)

   - Bei Auswahl von **In Unterdrückungsdatei**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau des der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut, das die globale Unterdrückungen-Datei hinzugefügt wird.

      ![Vorschau der Unterdrückungsdatei SuppressMessage-Attributs hinzugefügt](media/preview-changes-in-suppression-file.png)

   In der **Vorschau der Änderungen** wählen Sie im Dialogfeld **übernehmen**.

   > [!NOTE]
   > Wenn Sie nicht sehen die **unterdrücken** Menüoption im **Projektmappen-Explorer**, die Verletzung stammt wahrscheinlich von Build und nicht als live-Analyse. Die **Fehlerliste** zeigt Diagnose oder die Regel Verletzungen, sowohl live-Codeanalyse und erstellen. Da die Build-Diagnose veraltet sein können, z. B. Wenn Sie haben den Code zur Behebung des Verstoßes bearbeitet, aber noch nicht neu erstellt, Sie können nicht unterdrücken, diese Diagnose von der **Fehlerliste**. Diagnose von live-Analyse und IntelliSense, sind immer auf dem neuesten Stand mit aktuellen Datenquellen und kann unterdrückt werden, aus der **Fehlerliste**. Auszuschließende *erstellen* eine Diagnose aus der Auswahl wechseln die **Fehlerliste** Quellfilter aus **erstellen + IntelliSense** zu **Intellisense nur**. Wählen Sie die Diagnose zu unterdrücken, und fahren Sie fort, wie zuvor beschrieben.
   >
   > ![Fehler Quelle Listenfilter in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Die Verwendung der Befehlszeile

Wenn Sie Ihr Projekt in der Befehlszeile erstellen, werden in der Buildausgabe Verletzungen der Schwellenwertregeln angezeigt, wenn die folgenden Bedingungen erfüllt sind:

- Die Analysen werden als Nuget-Paket und nicht als VSIX-Erweiterung installiert.

- Eine oder mehrere Regeln, die in den Projektcode verletzt werden.

- Die [Schweregrad](#rule-severity) einer Verletzung Regel festgelegt ist entweder **Warnung**, in diesem Fall Verstöße Build nicht ausgeführt wird, führen nicht oder **Fehler**, in diesem Fall Verstöße dazu führen, dass der Build fehlschlägt.

Die Ausführlichkeit der Buildausgabe wirkt sich nicht, ob Verletzungen der Schwellenwertregeln angezeigt werden. Selbst bei **quiet** Ausführlichkeit bei, der Verletzungen von Namensregeln erscheinen in der Buildausgabe.

> [!TIP]
> Wenn Sie daran gewöhnt sind für die Ausführung der Analyse von statischem Code über die Befehlszeile, entweder mit *FxCopCmd.exe* oder mithilfe von Msbuild mit der **RunCodeAnalysis** kennzeichnen, wie dies mit Roslyn-Analyzern.

Um Analyzer Verstöße in der Befehlszeile anzuzeigen, wenn Sie Ihr Projekt mit Msbuild erstellen, führen Sie einen Befehl wie diesen:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Die folgende Abbildung zeigt die Ausgabe erstellen über die Befehlszeile beim Erstellen eines Projekts, das einen Regelverstoß Analyzer enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Abhängige Projekte

In einem .NET Core-Projekt Wenn Sie einen Verweis auf ein Projekt hinzufügen, die NuGet-Analysetools, werden diese Analysen automatisch das abhängige Projekt zu hinzugefügt. So deaktivieren Sie dieses Verhalten, z. B. das abhängige Projekt ist ein Komponententestprojekt, markieren Sie das NuGet-Paket als privat in der *csproj* oder *vbproj* -Datei des Projekts auf die verwiesen wird durch Festlegen der **PrivateAssets** Attribut:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analysetools in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Fehlers der Roslyn-analyzer](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Unterdrücken von codeanalysewarnungen](../code-quality/in-source-suppression-overview.md)