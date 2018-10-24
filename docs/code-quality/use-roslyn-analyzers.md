---
title: Verwenden Sie und konfigurieren Sie die Roslyn-Analysetools
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 47dc7d38a2ae9b842891d2e36aebd9b009297cbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817040"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Konfigurieren und Verwenden von Roslyn-Analyzer-Regeln

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

Ein [Regelsatz](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) ist eine XML-Datei, die den Schweregrad und Unterdrücken von Status für die einzelnen-Diagnose speichert. Regelsätze gelten, in ein einzelnes Projekt, und ein Projekt kann mehrere Regelsätze aufweisen. Um den aktiven Regelsatz, der im Editor anzuzeigen, mit der Maustaste auf die **Analysen** Knoten **Projektmappen-Explorer** , und wählen Sie **öffnen aktiven Regelsatz**. In diesem ersten Sie greifen auf die Regel festlegen, eine Datei namens  *\<Projektname > ruleSet* wird dem Projekt hinzugefügt und wird im **Projektmappen-Explorer**.

> [!NOTE]
> Regelsätze gehören sowohl die Analyse von statischem (binären) Code als auch die Roslyn-Analyzer-Regeln.

Sie können ändern, den aktiven Regelsatz für ein Projekt auf die **Codeanalyse** auf der Registerkarte Eigenschaften des Projekts. Wählen Sie den Regelsatz in der **diesen Regelsatz ausführen** Dropdown-Liste. Sie können auch den Regelsatz aus öffnen die **Codeanalyse** Eigenschaftenseite dazu **öffnen**.

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

### <a name="to-set-rule-severity-from-solution-explorer"></a>Projektmappen-Explorer Schweregrad für Regelsatz festlegen

1. In **Projektmappen-Explorer**, erweitern Sie **Verweise** > **Analysen** (**Abhängigkeiten**  >  **Analysen** für .NET Core-Projekte).

1. Erweitern Sie die Assembly, die die Regel enthält, die, der Sie den Schweregrad für festlegen möchten.

1. Mit der rechten Maustaste auf die Regel, und wählen **Schweregrad für Regelsatz festlegen**. Wählen Sie im eingeblendeten Menü eine der Optionen Schweregrad aus.

   Der Schweregrad für die Regel wird in der aktiven Regelsatzdatei gespeichert.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Festzulegende Regel Regelsatzdatei Schweregrad in der Regel

1. Öffnen die Regel legen-Datei durch Doppelklick im **Projektmappen-Explorer**, wählen **öffnen aktiven Regelsatz** auf das Kontextmenü des der **Analysen** Knoten oder durch auswählen **Öffnen** auf die **Codeanalyse** Eigenschaftenseite für das Projekt.

1. Navigieren Sie zu der Regel durch Erweitern der enthaltenden Assembly.

1. In der **Aktion** Spalte wählen Sie den Wert auf eine Dropdown-Liste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste.

   ![Regelsatzdatei in Editor öffnen](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Unterdrücken von Verstößen

Es gibt mehrere Möglichkeiten, um Verletzungen zu unterdrücken:

- Um alle aktuellen Verstöße zu unterdrücken, wählen Sie **analysieren** > **Codeanalyse ausführen und aktive Probleme unterdrücken** in der Menüleiste. Dies wird manchmal als "Baselining" bezeichnet.

- Um eine Diagnose aus zu unterdrücken, **Projektmappen-Explorer**, legen Sie den Schweregrad auf **keine**.

- Um eine Diagnose aus dem Regelsatz-Editor zu unterdrücken, deaktivieren Sie das Kontrollkästchen neben seinem Namen aus, oder legen Sie **Aktion** zu **keine**.

- Um eine Diagnose im Code-Editor zu unterdrücken, platzieren Sie den Cursor in die Zeile des Codes, mit der Verletzung und drücken Sie **STRG**+**.** zum Öffnen der **Schnellaktionen** Menü. Wählen Sie **unterdrücken CAxxxx** > **In Quelle** oder **unterdrücken CAxxxx** > **In Unterdrückungsdatei**.

   ![Vom Menü "schnelle Aktionen" Diagnose unterdrücken](media/suppress-diagnostic-from-editor.png)

- Um eine Diagnose aus zu unterdrücken, die **Fehlerliste**, finden Sie unter [unterdrücken Verstöße aus der Fehlerliste](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Unterdrücken von Verletzungen, aus der Fehlerliste

Können Sie eine Diagnose aus einem oder mehreren Unterdrücken der **Fehlerliste** durch Auswählen der gewünschten unterdrückt werden sollen, und klicken Sie dann mit der rechten Maustaste und Auswählen von **unterdrücken** > **In Quelle**  oder **unterdrücken** > **In Unterdrückungsdatei**.

- Bei Auswahl von **In Quelle**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau der C#- [#pragma-Warnung](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) oder Visual Basic [#Disable Warning](/dotnet/visual-basic/language-reference/directives/directives) Richtlinie, die den Quellcode hinzugefügt wird.

   ![Vorschau der #pragma-Warnung in der Codedatei hinzufügen](media/pragma-warning-preview.png)

- Bei Auswahl von **In Unterdrückungsdatei**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau des der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut, das die globale Unterdrückungen-Datei hinzugefügt wird.

   ![Vorschau der Unterdrückungsdatei SuppressMessage-Attributs hinzugefügt](media/preview-changes-in-suppression-file.png)

In der **Vorschau der Änderungen** wählen Sie im Dialogfeld **übernehmen**.

Die **Fehlerliste** zeigt Diagnose oder die Regel Verletzungen, sowohl live-Codeanalyse und erstellen. Da die Build-Diagnose veraltet sein können, z. B. Wenn Sie haben den Code zur Behebung des Verstoßes bearbeitet, aber noch nicht neu erstellt, Sie können nicht unterdrücken, diese Diagnose von der **Fehlerliste**. Allerdings Diagnose von live-Analyse oder IntelliSense, sind immer auf dem neuesten Stand mit aktuellen Datenquellen und kann unterdrückt werden, aus der **Fehlerliste**. Wenn die Unterdrückung-Option im Menü mit der rechten Maustaste noch ein Kontext deaktiviert ist, ist es wahrscheinlich, weil Sie eine oder mehrere-Diagnose in Ihrer Auswahl Build. Wechseln Sie zum Ausschließen der Build-Diagnose in die Auswahl der **Fehlerliste** Quellfilter aus **erstellen + IntelliSense** zu **Intellisense nur**. Wählen Sie die Diagnose zu unterdrücken, und fahren Sie fort, wie zuvor beschrieben.

![Fehler Quelle Listenfilter in Visual Studio](media/error-list-filter.png)

> [!NOTE]
> In einem .NET Core-Projekt Wenn Sie einen Verweis auf ein Projekt hinzufügen, die NuGet-Analysetools, werden diese Analysen automatisch das abhängige Projekt zu hinzugefügt. So deaktivieren Sie dieses Verhalten, z. B. das abhängige Projekt ist ein Komponententestprojekt, markieren Sie das NuGet-Paket als privat in der *csproj* oder *vbproj* -Datei des Projekts auf die verwiesen wird:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

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

![MSBuild-Ausgabe Regelverstoß zugeordnet](media/command-line-build-analyzers.png)

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analysetools in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Fehlers der Roslyn-analyzer](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Unterdrücken von codeanalysewarnungen](../code-quality/in-source-suppression-overview.md)