---
title: Verwenden und konfigurieren Sie in Visual Studio Analyzer Roslyn | Microsoft Docs
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 4f2929771d6aa50931a9e84dea8806d2fbe8db39
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Konfigurieren und Verwenden von Roslyn Analyzer-Regeln

.NET Compiler Platform ("Roslyn")-Analyzer-Regeln oder *Diagnose*, Analysieren von c# oder Visual Basic Code während der Eingabe. Jeder Diagnose hat eine Standardstatus Schweregrad und unterdrücken, die für Ihr Projekt überschrieben werden kann. In diesem Artikel wird die Einstellung Regel Schweregrad, verwenden von Regelsätzen und Unterdrücken von Verletzungen behandelt.

## <a name="analyzers-in-solution-explorer"></a>Analyzer im Projektmappen-Explorer

Führen Sie ein Großteil der Anpassung der Analyzer Diagnose von **Projektmappen-Explorer**. Wenn Sie [installieren Analysen](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket, ein **Analysen** Knoten befindet sich unter der **Verweise** oder **Abhängigkeiten** Knoten  **Projektmappen-Explorer**. Wenn Sie erweitern **Analysen**, und erweitern Sie dann eine der Assemblys Analyzer, alle Diagnosen in der Assembly.

![Analysen für Knoten im Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Sehen Sie die Eigenschaften einer Diagnose, einschließlich Beschreibung und standardschweregrad, in der **Eigenschaften** Fenster. Zum Anzeigen der Eigenschaften mit der Maustaste, auf die Regel, und wählen **Eigenschaften**, oder wählen Sie die Regel, und drücken Sie dann die **Alt**+**EINGABETASTE**.

![Diagnose Eigenschaften im Fenster "Eigenschaften"](media/analyzer-diagnostic-properties.png)

Um Onlinedokumentation für eine Diagnose anzuzeigen, mit der rechten Maustaste auf die Diagnose, und wählen Sie **Sicht Ihnen helfen,**.

Die Symbole neben jeder Diagnose im **Projektmappen-Explorer** entsprechen den Symbolen, die Sie, in der Regel festgelegt sehen, wenn Sie im Editor zu öffnen:

- Gibt an, das "i" in einem Kreis eine [Schweregrad](#rule-severity) von **Info**
- die "!" in einem Dreieck gibt eine [Schweregrad](#rule-severity) von **Warnung**
- Gibt an, das "X" in einem Kreis eine [Schweregrad](#rule-severity) der **Fehler**
- Gibt an, das "i" in einem Kreis in einem Hintergrundthread hellen eine [Schweregrad](#rule-severity) von **ausgeblendet**
- die zeigenden Pfeil in einem Kreis gibt an, dass die Diagnose unterdrückt wird

![Diagnose-Symbole im Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Regelsätze

Ein [Regelsatz](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) ist eine XML-Datei, die den Schweregrad und Unterdrücken von Status für die einzelnen Diagnose speichert. Regelsätze in ein einzelnes Projekt gelten, und ein Projekt kann mehrere Regelsätze verfügen. Zum Anzeigen der aktiven Regelsatzes, der im Editor mit der Maustaste auf die **Analysen** Knoten **Projektmappen-Explorer** , und wählen Sie **öffnen Active Regelsatz**. Ist dies der erstmaligen Sie greifen auf die Regel festzulegen, eine Datei namens  *\<Projektname > ruleSet* wird dem Projekt hinzugefügt und wird im **Projektmappen-Explorer**.

> [!NOTE]
> Regel umfassen statische Codeanalyse aus (binär) und Roslyn-Analyzer-Regeln.

Sie können ändern, den aktiven Regelsatz für ein Projekt auf die **Codeanalyse** auf der Registerkarte Eigenschaften des Projekts. Wählen Sie den Regelsatz in der **diesen Regelsatz ausführen** Dropdown-Liste. Sie können auch den Regelsatz aus öffnen die **Codeanalyse** Eigenschaftenseite dazu **öffnen**.

## <a name="rule-severity"></a>Schweregrad der Regel

Sie können den Schweregrad der Analyzer-Regeln konfigurieren oder *Diagnose*, sofern Sie [installieren Analysen](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket. Die folgende Tabelle zeigt die Schweregrad-Optionen für die Diagnose:

|Schweregrad|Zur Buildzeit Verhalten|Editor-Verhalten|
|-|-|-|
|Fehler|Verletzungen angezeigt werden, als *Fehler* in der **Fehlerliste** in Befehlszeilen Buildausgabe und dazu führen, dass Builds fehlschlagen.|-Verstoßes Code ist mit einem roten Wellenlinie und durch ein kleines rotes Feld auf der Bildlaufleiste markierte unterstrichen.|
|Warnung|Verletzungen angezeigt werden, als *Warnungen* in der **Fehlerliste** und in der Befehlszeile Buildausgabe, verursachen jedoch keine Builds fehlschlagen.|-Verstoßes Code ist mit einem grünen Wellenlinie und durch ein kleines grünes Feld in der Bildlaufleiste markierte unterstrichen.|
|Info|Verletzungen angezeigt werden, als *Nachrichten* in der **Fehlerliste**, und im Befehlszeilen Buildausgabe gar nicht.|-Verstoßes Code ist mit einem grau Wellenlinie und durch ein kleines graues Feld in der Bildlaufleiste markierte unterstrichen.|
|Hidden|Nicht-für Benutzer sichtbar.|Nicht-für Benutzer sichtbar. Die Diagnose ist jedoch mit dem IDE-Diagnose-Datenbankmodul gemeldet.|
|Keiner|Vollständig unterdrückt.|Vollständig unterdrückt.|

Darüber hinaus, Sie können "Zurücksetzen" Schweregrad der Regel durch Festlegen auf **Standard**. Jeder Diagnose hat einen standardschweregrad, die in angezeigt werden, kann die **Eigenschaften** Fenster.

Der folgende Screenshot zeigt drei verschiedene diagnostische Verstöße im Code-Editor mit drei verschiedenen Schweregraden an. Beachten Sie die Farbe der Wellenlinie als auch das kleine Feld in der Bildlaufleiste auf der rechten Seite aus.

![Fehler, Warnung und Info Verstoß innerhalb des Code-editor](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt die gleichen drei Verstöße, wie in der **Fehlerliste**:

![Verletzung des Fehler-, Warn- und Informationen in der Fehlerliste](media/diagnostics-severities-in-error-list.png)

Sie können ändern, den Schweregrad einer Regel aus **Projektmappen-Explorer**, oder innerhalb der  *\<Projektname > ruleSet* -Datei, die der Projektmappe hinzugefügt wird, nachdem Sie den Schweregrad einer Regel in Ändern **Projektmappen-Explorer**.

![RULESET-Datei im Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Festzulegende Regel Schweregrad vom Projektmappen-Explorer

1. In **Projektmappen-Explorer**, erweitern Sie **Verweise** > **Analysen** (**Abhängigkeiten**  >  **Analysen** für Projekte von .NET Core).

1. Erweitern Sie die Assembly, die die Regel enthält, Schweregrad für festgelegt werden soll.

1. Mit der rechten Maustaste auf die Regel, und wählen **festgelegt Regel festgelegt Schweregrad**. Wählen Sie im Flyout-Menü eine der Optionen Schweregrad aus.

   Der Schweregrad für die Regel wird in die aktive Regelsatzdatei gespeichert.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Um Regelsatz Regelsatzdatei Schweregrad in der Regel

1. Öffnen der Regelsatz Datei durch Doppelklick im **Projektmappen-Explorer**auswählen **öffnen Active Regelsatz** auf das Kontextmenü des der **Analysen** Knoten oder durch auswählen **Öffnen** auf die **Codeanalyse** Eigenschaftenseite für das Projekt.

1. Navigieren Sie zu der Regel durch Erweitern der enthaltenden Assembly.

1. In der **Aktion** Spalte, wählen Sie den Wert um eine Dropdownliste öffnen, und wählen Sie aus der Liste den gewünschten Schweregrad.

   ![RULESET-Datei in Editor geöffnet](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Unterdrücken von Verstößen

Es gibt mehrere Möglichkeiten, Verletzungen von Schwellenwertregeln unterdrücken:

- Um alle aktuellen Verstöße zu unterdrücken, wählen Sie **analysieren** > **Codeanalyse ausführen und aktive Probleme unterdrückt** in der Menüleiste. Dies wird manchmal als "Basislinien" bezeichnet.

- Unterdrücken Sie eine Diagnose aus **Projektmappen-Explorer**, legen Sie ihren Schweregrad auf **keine**.

- Um eine Diagnose aus dem Regelsatz-Editor zu unterdrücken, deaktivieren Sie das Kontrollkästchen neben dem Namen, oder legen Sie **Aktion** auf **keine**.

- Um eine Diagnose im Code-Editor zu unterdrücken, platzieren Sie den Cursor in die Zeile des Codes, mit der Verletzung, und drücken Sie **STRG**+**.** So öffnen die **Schnellaktionen** Menü. Wählen Sie **unterdrücken CAxxxx** > **In der Quelle** oder **unterdrücken CAxxxx** > **In Unterdrückungsdatei**.

   ![Unterdrücken von schnellen Aktionen im Menü Diagnose](media/suppress-diagnostic-from-editor.png)

- Unterdrücken Sie eine Diagnose aus der **Fehlerliste**mit der rechten Maustaste auf den Fehler, Warnung oder Meldung, und wählen Sie **unterdrücken** > **In Quelle** oder **Unterdrücken** > **In Unterdrückungsdatei**.

   - Bei Auswahl des **In Quelle**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau der C#- [#pragma Warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) oder Visual Basic [#Disable Warning](/dotnet/visual-basic/language-reference/directives/directives) -Direktive, die auf den Quellcode hinzugefügt wird.

      ![Vorschau der Codedatei "" #pragma Warning hinzufügen](media/pragma-warning-preview.png)

   - Bei Auswahl des **In Unterdrückungsdatei**, **Vorschau der Änderungen** Dialogfeld wird geöffnet und zeigt eine Vorschau der der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut, das für die globale Unterdrückungen-Datei hinzugefügt wird.

      ![Vorschau der Unterdrückungsdatei SuppressMessage-Attribut hinzugefügt](media/preview-changes-in-suppression-file.png)

   In der **Vorschau der Änderungen** wählen Sie im Dialogfeld **übernehmen**.

> [!NOTE]
> In einem Projekt auf .NET Core, wenn Sie einen Verweis auf ein Projekt hinzufügen, die NuGet-Analysen, werden diese Analysen automatisch das abhängige Projekt zu hinzugefügt. So deaktivieren Sie dieses Verhalten, z. B. das abhängige Projekt ist ein Komponententestprojekt, markieren Sie das NuGet-Paket als privat in der *csproj* oder *vbproj* -Datei des Projekts verwiesen wird:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analyzer in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Fehlers der Roslyn-analyzer](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Unterdrücken der codeanalysewarnungen](../code-quality/in-source-suppression-overview.md)