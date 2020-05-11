---
title: Analyzer-Regelschweregrad und Unterdrückung
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431409"
---
# <a name="use-code-analyzers"></a>Verwenden von Codeanalysatoren

.NET Compiler Platform ("Roslyn") Codeanalysatoren analysieren Ihren C- oder Visual Basic-Code während der Eingabe. Jede *Diagnose* oder Regel verfügt über einen Standardschweregrad- und Unterdrückungsstatus, der für Ihr Projekt überschrieben werden kann. In diesem Artikel wird der Schweregrad der Regel festgelegt, Regelsätze verwendet und Verstöße unterdrückt.

## <a name="analyzers-in-solution-explorer"></a>Analysatoren im Projektmappen-Explorer

Sie können einen Großteil der Anpassung der Analyzer-Diagnose über **den Projektmappen-Explorer**vornehmen. Wenn Sie [Analysatoren](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket installieren, wird ein **Analyzers-Knoten** unter dem Knoten **Referenzen** oder **Abhängigkeiten** im **Projektmappen-Explorer**angezeigt. Wenn Sie **Analyzers**erweitern und dann eine der Analyzerassemblys erweitern, werden alle Diagnosen in der Assembly angezeigt.

![Analyzers-Knoten im Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Sie können die Eigenschaften einer Diagnose, einschließlich der Beschreibung und des Standardschweregrads, im Fenster **Eigenschaften** anzeigen. Um die Eigenschaften anzuzeigen, klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Eigenschaften**aus, oder wählen Sie die Regel aus, und **drücken**+Sie dann alt**eingeben**.

![Diagnoseeigenschaften im Fenster Eigenschaften](media/analyzer-diagnostic-properties.png)

Um die Onlinedokumentation für eine Diagnose anzuzeigen, klicken Sie mit der rechten Maustaste auf die Diagnose und wählen **Hilfe anzeigen**aus.

Die Symbole neben jeder Diagnose im **Projektmappen-Explorer** entsprechen den Symbolen, die im Regelsatz angezeigt werden, wenn Sie sie im Editor öffnen:

- Das "x" in einem Kreis gibt den [Schweregrad](#rule-severity) von **Fehler** an
- das "!" in einem Dreieck zeigt einen [Schweregrad](#rule-severity) der **Warnung** an
- das "i" in einem Kreis zeigt einen [Schweregrad](#rule-severity) von **Info** an
- das "i" in einem Kreis auf einem hellen Hintergrund zeigt einen [Schweregrad](#rule-severity) von **Versteckt** an
- Der nach unten zeigende Pfeil in einem Kreis zeigt an, dass die Diagnose unterdrückt wird

![Diagnosesymbole im Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Regelschweregrad

::: moniker range=">=vs-2019"

Sie können den Schweregrad von Analyzer-Regeln oder *Diagnosen*konfigurieren, wenn Sie [die Analyzer](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket installieren. Ab Visual Studio 2019 Version 16.3 können Sie den Schweregrad einer Regel [in einer EditorConfig-Datei](#set-rule-severity-in-an-editorconfig-file)konfigurieren. Sie können auch den Schweregrad einer Regel [aus dem Projektmappen-Explorer](#set-rule-severity-from-solution-explorer) oder [in einer Regelsatzdatei](#set-rule-severity-in-the-rule-set-file)ändern.

::: moniker-end

::: moniker range="vs-2017"

Sie können den Schweregrad von Analyzer-Regeln oder *Diagnosen*konfigurieren, wenn Sie [die Analyzer](../code-quality/install-roslyn-analyzers.md) als NuGet-Paket installieren. Sie können den Schweregrad einer Regel [aus dem Projektmappen-Explorer](#set-rule-severity-from-solution-explorer) oder [in einer Regelsatzdatei](#set-rule-severity-in-the-rule-set-file)ändern.

::: moniker-end

Die folgende Tabelle zeigt die verschiedenen Schweregradoptionen:

| Schweregrad (Projektmappen-Explorer) | Schweregrad (EditorConfig-Datei) | Buildzeitverhalten | Editor-Verhalten |
|-|-|-|
| Fehler | `error` | Verstöße werden in der Fehlerliste und in der Befehlszeilenerstellungsausgabe als *Fehler* angezeigt und führen dazu, dass Builds fehlschlagen.| Der beleidigende Code wird mit einer roten Wellenlinie unterstrichen und durch ein kleines rotes Kästchen in der Bildlaufleiste gekennzeichnet. |
| Warnung | `warning` | Verstöße werden in der Fehlerliste und in der Befehlszeilenerstellungsausgabe als *Warnungen* angezeigt, führen jedoch nicht dazu, dass Builds fehlschlagen. | Der beleidigende Code wird mit einer grünen Wellenlinie unterstrichen und durch ein kleines grünes Kästchen in der Bildlaufleiste gekennzeichnet. |
| Info | `suggestion` | Verstöße werden in der Fehlerliste als *Nachrichten* und in der Befehlszeilenerstellungsausgabe überhaupt nicht angezeigt. | Der beleidigende Code wird mit einer grauen Wellenlinie unterstrichen und durch ein kleines graues Feld in der Bildlaufleiste gekennzeichnet. |
| Ausgeblendet | `silent` | Für den Benutzer nicht sichtbar. | Für den Benutzer nicht sichtbar. Die Diagnose wird jedoch an das IDE-Diagnosemodul gemeldet. |
| Keine | `none` | Vollständig unterdrückt. | Vollständig unterdrückt. |
| Standard | `default` | Entspricht dem Standardschweregrad der Regel. Um den Standardwert für eine Regel zu bestimmen, suchen Sie im Eigenschaftenfenster nach. | Entspricht dem Standardschweregrad der Regel. |

Der folgende Screenshot des Code-Editors zeigt drei verschiedene Verstöße mit unterschiedlichen Schweregraden. Beachten Sie die Farbe der Wellenlinie und das kleine, farbige Quadrat in der Bildlaufleiste auf der rechten Seite.

![Fehler-, Warnungs- und Infoverletzung im Code-Editor](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt die drei Verletzungen, die in der Fehlerliste angezeigt werden:

![Fehler-, Warnungs- und Infoverletzung in der Fehlerliste](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Festlegen des Regelschweregrads in einer EditorConfig-Datei

(Visual Studio 2019 Version 16.3 und höher)

Sie können den Schweregrad für Compilerwarnungen oder Analyzerregeln in einer EditorConfig-Datei mit der folgenden Syntax festlegen:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Das Festlegen des Schweregrads einer Regel in einer EditorConfig-Datei hat Vorrang vor jedem Schweregrad, der in einem Regelsatz oder im Projektmappen-Explorer festgelegt ist. Sie [können](#manually-configure-rule-severity) den Schweregrad manuell in einer EditorConfig-Datei oder [automatisch](#automatically-configure-rule-severity) über die Glühbirne konfigurieren, die neben einer Verletzung angezeigt wird.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Festlegen des Regelschweregrads mehrerer Analyzer-Regeln gleichzeitig in einer EditorConfig-Datei

(Visual Studio 2019 Version 16.5 und höher)

Sie können den Schweregrad für eine bestimmte Kategorie von Analyzerregeln oder für alle Analyzerregeln mit einem einzelnen Eintrag in einer EditorConfig-Datei festlegen.

- Festlegen des Regelschweregrads für eine Kategorie von Analyzerregeln:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Festlegen des Regelschweregrads für alle Analyzerregeln:

`dotnet_analyzer_diagnostic.severity = <severity>`

Wenn Sie über mehrere Einträge verfügen, die auf eine bestimmte Regel-ID anwendbar sind, ist die folgende Rangfolge, um den entsprechenden Eintrag auszuwählen:

- Der Schweregradeintrag für eine einzelne Regel nach ID hat Vorrang vor dem Schweregradeintrag für eine Kategorie.
- Der Schweregradeintrag für eine Kategorie hat für alle Analyzerregeln Vorrang vor dem Schweregradeintrag.

Betrachten Sie das folgende EditorConfig-Beispiel, in dem [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) die Kategorie "Leistung" hat:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Im vorherigen Beispiel sind alle drei Einträge auf CA1822 anwendbar. Mit den angegebenen Prioritätsregeln gewinnt jedoch der erste regelID-basierte Schweregradeintrag die nächsten Einträge. In diesem Beispiel hat CA1822 den effektiven Schweregrad "error". Alle verbleibenden Regeln mit der Kategorie "Leistung" weisen den Schweregrad "Warnung" auf. Alle verbleibenden Analyzer-Regeln, die nicht die Kategorie "Leistung" haben, haben den Schweregrad "Vorschlag".

#### <a name="manually-configure-rule-severity"></a>Manuell konfigurieren regelschwere

1. Wenn Sie noch keine EditorConfig-Datei für Ihr Projekt haben, [fügen Sie eine hinzu.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Fügen Sie einen Eintrag für jede Regel hinzu, die Sie unter der entsprechenden Dateierweiterung konfigurieren möchten. Um z. B. den Schweregrad für `error` [CA1822](ca1822.md) auf C-Dateien festzulegen, sieht der Eintrag wie folgt aus:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Bei IDE-Code-Style-Analyzern können Sie sie auch in einer EditorConfig-Datei mit einer anderen Syntax konfigurieren, z. `dotnet_style_qualification_for_field = false:suggestion`B. . Wenn Sie jedoch einen Schweregrad `dotnet_diagnostic` mithilfe der Syntax festlegen, hat er Vorrang. Weitere Informationen finden Sie unter [Sprachkonventionen für EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Konvertieren einer vorhandenen Ruleset-Datei in die EditorConfig-Datei

Ab Visual Studio 2019 Version 16.5 sind Regelsatzdateien zugunsten der EditorConfig-Datei für die Analyzer-Konfiguration für verwalteten Code veraltet. Der großteil der Visual Studio-Tooling für die Konfiguration des Schweregrads der Analyzer-Regel wurde aktualisiert, um mit EditorConfig-Dateien anstelle von Regelsatzdateien zu arbeiten. Mit EditorConfig-Dateien können Sie sowohl die Schweregrade der Analyzer-Regel als auch die Analyseoptionen konfigurieren, einschließlich der Optionen für den Codestil von Visual Studio IDE. Es wird dringend empfohlen, die vorhandene Ruleset-Datei in eine EditorConfig-Datei zu konvertieren. Es wird auch empfohlen, die EditorConfig-Datei im Stammverzeichnis Ihres Repositorys oder im Projektmappenordner zu speichern. Wenn Sie den Stamm Ihres Repositorys oder Projektmappenordners verwenden, stellen Sie sicher, dass die Schweregradeinstellungen aus dieser Datei automatisch auf das gesamte Repository bzw. die gesamte Projektmappe angewendet werden.

Es gibt mehrere Möglichkeiten, eine vorhandene Rulesetdatei in eine EditorConfig-Datei zu konvertieren:

- Aus dem Regelsatz-Editor in Visual Studio (erfordert Visual Studio 2019 16.5 oder höher). Wenn Ihr Projekt bereits eine bestimmte `CodeAnalysisRuleSet`Regelsatzdatei als "" verwendet, können Sie sie in eine entsprechende EditorConfig-Datei aus dem Ruleset-Editor in Visual Studio konvertieren.

    1. Doppelklicken Sie im Projektmappen-Explorer auf die Regelsatzdatei.

       Die Ruleset-Datei sollte im Ruleset-Editor geöffnet werden. Oben im Regelsatz-Editor sollte eine anklickbare **Infoleiste** angezeigt werden.

       ![Konvertieren von Ruleset in EditorConfig-Datei im Ruleset-Editor](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Klicken Sie auf** den Link infoleiste.

       Dadurch sollte ein Dialogfeld **Speichern** unter geöffnet werden, in dem Sie das Verzeichnis auswählen können, in dem Sie die EditorConfig-Datei generieren möchten.

    3. **Klicken Sie auf** die Schaltfläche **Speichern,** um die EditorConfig-Datei zu generieren.

       Die generierte EditorConfig sollte im Editor geöffnet werden. Darüber hinaus wird `CodeAnalysisRuleSet` die MSBuild-Eigenschaft in der Projektdatei aktualisiert, sodass sie nicht mehr auf die ursprüngliche Regelsatzdatei verweist.

- Über die Befehlszeile:

    1. Installieren Sie das NuGet-Paket [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Führen `RulesetToEditorconfigConverter.exe` Sie aus dem installierten Paket mit Pfaden zur Ruleset-Datei und der EditorConfig-Datei als Befehlszeilenargumente aus.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Hier ist eine Beispiel-Ruleset-Datei zu konvertieren:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Hier ist die konvertierte EditorConfig-Datei:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Automatische Sendezeit der Regel konfigurieren

##### <a name="configure-from-light-bulb-menu"></a>Konfigurieren über Glühbirnenmenü

Visual Studio bietet eine bequeme Möglichkeit, den Schweregrad einer Regel über das Menü ["Schnellaktionen-Glühbirne"](../ide/quick-actions.md) zu konfigurieren.

1. Nachdem eine Verletzung auftritt, bewegen Sie den Mauszeiger im Editor und öffnen Sie das Glühbirnenmenü. Oder setzen Sie den Cursor auf die Zeile und drücken **Sie Strg**+**.** (Punkt).

2. Wählen Sie im Glühbirnenmenü **Probleme** > konfigurieren oder unterdrücken **Konfigurieren der \<Regel-ID> Schweregrad**.

   ![Konfigurieren des Regelschweregrads über das Glühbirnenmenü in Visual Studio](media/configure-rule-severity.png)

3. Wählen Sie von dort aus eine der Schweregradoptionen aus.

   ![Konfigurieren des Regelschweregrads als Vorschlag](media/configure-rule-severity-suggestion.png)

   Visual Studio fügt der EditorConfig-Datei einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren, wie im Vorschaufeld gezeigt.

   > [!TIP]
   > Wenn Sie noch keine EditorConfig-Datei im Projekt haben, erstellt Visual Studio eine für Sie.

##### <a name="configure-from-error-list"></a>Konfigurieren von der Fehlerliste

Visual Studio bietet auch eine bequeme Möglichkeit, den Schweregrad einer Regel über das Kontextmenü der Fehlerliste zu konfigurieren.

1. Nachdem eine Verletzung aufgetreten ist, klicken Sie mit der rechten Maustaste auf den Diagnoseeintrag in der Fehlerliste.

2. Wählen Sie im Kontextmenü **schwere Grade**festlegen aus.

   ![Konfigurieren des Regelschweregrads anhand der Fehlerliste in Visual Studio](media/configure-rule-severity-error-list.png)

3. Wählen Sie von dort aus eine der Schweregradoptionen aus.

   Visual Studio fügt der EditorConfig-Datei einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren.

   > [!TIP]
   > Wenn Sie noch keine EditorConfig-Datei im Projekt haben, erstellt Visual Studio eine für Sie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen des Regelschweregrads aus dem Projektmappen-Explorer

1. Erweitern Sie im Projektmappen-Explorer **References** > **Analyzers** (oder **Dependencies** > **Analyzers** für .NET Core-Projekte).

2. Erweitern Sie die Assembly, die die Regel enthält, für die Sie den Schweregrad festlegen möchten.

::: moniker range=">=vs-2019"
3. Klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Schweregrad festlegen**aus. Wählen Sie im Kontextmenü eine der Schweregradoptionen aus.

   Visual Studio fügt der EditorConfig-Datei einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren. Wenn Ihr Projekt anstelle einer EditorConfig-Datei eine Rulesetdatei verwendet, wird der Schweregradeintrag der Regelsatzdatei hinzugefügt.

   > [!TIP]
   > Wenn Sie noch keine EditorConfig-Datei oder Regelsatzdatei im Projekt haben, erstellt Visual Studio eine neue EditorConfig-Datei für Sie.
::: moniker-end

::: moniker range="vs-2017"
3. Klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Regelsatzschweregrad festlegen**aus. Wählen Sie im Kontextmenü eine der Schweregradoptionen aus.

   Der Schweregrad für die Regel wird in der aktiven Regelsatzdatei gespeichert.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Festlegen des Regelschweregrads in der Regelsatzdatei

![Regelsatzdatei im Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

1. Öffnen Sie die aktive Regelsatzdatei, indem Sie im **Projektmappen-Explorer**darauf doppelklicken, im Rechtsklickmenü des Knotens **References** > **Analyzers** die Option **Aktive Regelfestlegen** aktivieren auswählen oder auf der Eigenschaftenseite **Codeanalyse** für das Projekt **öffnen** auswählen.

   Wenn Sie den Regelsatz zum ersten Mal bearbeiten, erstellt Visual Studio eine Kopie der Standardregelsatzdatei, benennt sie * \<mit dem Projektnamen>.ruleset*und fügt sie Ihrem Projekt hinzu. Dieser benutzerdefinierte Regelsatz wird auch zum aktiven Regelsatz für Ihr Projekt.

   > [!NOTE]
   > .NET Core- und .NET Standard-Projekte unterstützen die Menübefehle für Regelsätze im **Projektmappen-Explorer**nicht , z. B. **Open Active Rule Set**. Um einen nicht standardmäßigen Regelsatz für ein .NET Core- oder .NET Standard-Projekt anzugeben, fügen Sie der Projektdatei manuell [die **CodeAnalysisRuleSet-Eigenschaft** hinzu.](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) Sie können die Regeln innerhalb des Regelsatzes in der Visual Studio-Regelsatz-Editor-Benutzeroberfläche weiterhin konfigurieren.

1. Navigieren Sie zur Regel, indem Sie die enthaltende Assembly erweitern.

1. Wählen Sie in der Spalte **Aktion** den Wert aus, um eine Dropdownliste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste aus.

   ![Regelsatzdatei im Editor geöffnet](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Unterdrücken von Verstößen

Es gibt mehrere Möglichkeiten, Regelverletzungen zu unterdrücken:

::: moniker range=">=vs-2019"

- In einer **EditorConfig-Datei**

  Legen Sie den `none`Schweregrad `dotnet_diagnostic.CA1822.severity = none`auf , z. B. .

- Aus dem Menü **Analysieren**

   > Wählen **Analyze**Sie Aktive Probleme analysieren**und unterdrücken** in der Menüleiste aus, um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

::: moniker range="vs-2017"

- Aus dem Menü **Analysieren**

  Wählen Sie **In** > der Menüleiste die Option**Ausführen der Codeanalyse analysieren und Aktive Probleme unterdrücken,** um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

- Aus **dem Projektmappen-Explorer**

  Legen Sie den Schweregrad der Regel auf **Keine**fest.

- Aus dem **Regelsatz-Editor**

  Deaktivieren Sie das Kontrollkästchen neben dem Namen, oder setzen Sie **Aktion** auf **Keine**fest.

- Aus dem **Code-Editor**

  Platzieren Sie den Cursor in der Codezeile mit der Verletzung, und drücken Sie **Strg-Periode**+**(.),** um das Menü **"Schnellaktionen"** zu öffnen. Wählen Sie **CAXXXX** > **in Source/in Suppression File**unterdrücken aus.

  ![Unterdrücken der Diagnose aus dem Schnellaktionsmenü](media/suppress-diagnostic-from-editor.png)

- Aus der **Fehlerliste**

  Wählen Sie die Regeln aus, die Sie unterdrücken möchten, und klicken Sie dann mit der rechten Maustaste, und wählen Sie In**Quelle/In Unterdrückungsdatei** **unterdrücken** > aus.

  - Wenn Sie **In Source**unterdrücken, wird das Dialogfeld **Vorschauänderungen** geöffnet und zeigt eine Vorschau der Warnung "C" [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) oder der Visual [Basic-#Disable-Warndirektive](/dotnet/visual-basic/language-reference/directives/directives) an, die dem Quellcode hinzugefügt wird.

    ![Vorschau des Hinzufügens #pragma Warnung in der Codedatei](media/pragma-warning-preview.png)

  - Wenn Sie **In Unterdrückungsdatei**auswählen, wird das Dialogfeld **Vorschauänderungen** geöffnet und zeigt eine Vorschau des Attributs an, das <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> der globalen Unterdrückungsdatei hinzugefügt wurde.

    ![Vorschau des Hinzufügens des SuppressMessage-Attributs zur Unterdrückungsdatei](media/preview-changes-in-suppression-file.png)

  Wählen Sie im Dialogfeld **Vorschauänderungen** die Option **Übernehmen**aus.

  > [!NOTE]
  > Wenn die Menüoption **Unterdrücken** im **Projektmappen-Explorer**nicht angezeigt wird, stammt die Verletzung wahrscheinlich von Build- und nicht live-Analysen. In **der Fehlerliste** werden Diagnosen oder Regelverletzungen sowohl aus der Livecodeanalyse als auch aus dem Build angezeigt. Da die Builddiagnose veraltet sein kann, z. B. wenn Sie den Code bearbeitet haben, um die Verletzung zu beheben, aber nicht neu erstellt wurden, können Sie diese Diagnose nicht aus der **Fehlerliste**unterdrücken. Diagnosen aus der Live-Analyse oder IntelliSense sind immer mit aktuellen Quellen auf dem neuesten Stand und können aus der **Fehlerliste**unterdrückt werden. Um *builddiagnostics* von Ihrer Auswahl auszuschließen, wechseln Sie den **Quellfilter Fehlerliste** von **Build + IntelliSense** zu **IntelliSense Only**. Wählen Sie dann die Diagnose aus, die Sie unterdrücken möchten, und fahren Sie wie zuvor beschrieben fort.
  >
  > ![Fehlerlistenquellfilter in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Befehlszeilennutzung

Wenn Sie Das Projekt in der Befehlszeile erstellen, werden Regelverletzungen in der Buildausgabe angezeigt, wenn die folgenden Bedingungen erfüllt sind:

- Die Analysatoren werden als NuGet-Paket und nicht als VSIX-Erweiterung installiert.

- Mindestens eine Regel wird im Projektcode verletzt.

- Der [Schweregrad](#rule-severity) einer verletzten Regel wird entweder auf **Warning**festgelegt, in diesem Fall führen Verstöße nicht zu einem Fehler beim Build, oder **Fehler**, in diesem Fall führen Verstöße dazu, dass build fehlschlägt.

Die Ausführlichkeit der Buildausgabe hat keinen Einfluss darauf, ob Regelverletzungen angezeigt werden. Selbst bei **ruhiger** Ausführlichkeit werden Regelverstöße in der Buildausgabe angezeigt.

> [!TIP]
> Wenn Sie daran gewöhnt sind, ältere Analysen über die Befehlszeile auszuführen, entweder mit *FxCopCmd.exe* oder über msbuild mit dem **RunCodeAnalysis-Flag,** erfahren Sie hier, wie Sie dies mit Codeanalysatoren tun.

Führen Sie einen Befehl wie folgt aus, um Die Analysatorverletzungen in der Befehlszeile anzuzeigen, wenn Sie Ihr Projekt mit msbuild erstellen:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Regelverstoß des Analysetools enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Abhängige Projekte

Wenn Sie in einem .NET Core-Projekt einen Verweis auf ein Projekt mit NuGet-Analysatoren hinzufügen, werden diese Analysatoren automatisch auch dem abhängigen Projekt hinzugefügt. Um dieses Verhalten zu deaktivieren, z. B. wenn es sich bei dem abhängigen Projekt um ein Komponententestprojekt handelt, markieren Sie das NuGet-Paket in der *.csproj-* oder *VBproj-Datei* des referenzierten Projekts als privat, indem Sie das **PrivateAssets-Attribut** festlegen:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Weitere Informationen

- [Übersicht der Codeanalysatoren in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Codeanalysefehlers](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Codeanalysewarnungen unterdrücken](../code-quality/in-source-suppression-overview.md)
