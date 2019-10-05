---
title: Schweregrad und Unterdrückung der Analyse Regel
ms.date: 09/23/2019
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
ms.openlocfilehash: 3222509ccc5ec20cd1433d215ca3d69609af6bcb
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975021"
---
# <a name="use-code-analyzers"></a>Verwenden von Code Analysemodulen

.NET Compiler Platform ("Roslyn")-Code-Analysen C# analysieren Ihren-oder-Visual Basic Code, während Sie eingeben. Jede *Diagnose* oder Regel weist einen Standard Schweregrad und Unterdrückungs Status auf, der für Ihr Projekt überschrieben werden kann. In diesem Artikel werden der Schweregrad der Regel, die Verwendung von Regelsätzen und das Unterdrücken von Verletzungen behandelt

## <a name="analyzers-in-solution-explorer"></a>Analyzers in Projektmappen-Explorer

Sie können einen Großteil der Anpassung der Analyzer-Diagnose von **Projektmappen-Explorer**erledigen. Wenn Sie [Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren, wird in **Projektmappen-Explorer**unter dem Knoten **Verweise** oder **Abhängigkeiten** ein **Analysen** -Knoten angezeigt. Wenn Sie **Analyzers**erweitern und dann eine der Analyzer-Assemblys erweitern, werden alle Diagnosen in der Assembly angezeigt.

![Analyzers-Knoten in Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Im **Eigenschaften** Fenster können Sie die Eigenschaften einer Diagnose einschließlich der Beschreibung und des Standard schwere Grads anzeigen. Um die Eigenschaften anzuzeigen, klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Eigenschaften**aus, oder wählen Sie die Regel aus, und drücken Sie dann **alt**+**eingeben**.

![Diagnose Eigenschaften in Eigenschaftenfenster](media/analyzer-diagnostic-properties.png)

Um die Online Dokumentation für eine Diagnose anzuzeigen, klicken Sie mit der rechten Maustaste auf die Diagnose, und wählen Sie **Hilfe anzeigen**aus.

Die Symbole neben den einzelnen Diagnose in **Projektmappen-Explorer** entsprechen den Symbolen, die im Regelsatz angezeigt werden, wenn Sie Sie im Editor öffnen:

- Das "x" in einem Kreis zeigt den [Schweregrad](#rule-severity) " **Fehler** " an.
- "!" in einem Dreieck weist auf den [Schweregrad](#rule-severity) " **Warnung** " hin.
- "i" in einem Kreis zeigt den [Schweregrad](#rule-severity) der **Informationen** an.
- Das "i" in einem Kreis in einem hellfarbigen Hintergrund weist auf den [Schweregrad](#rule-severity) " **ausgeblendet** " hin.
- der nach unten zeigende Pfeil in einem Kreis gibt an, dass die Diagnose unterdrückt wird.

![Diagnose Symbole in Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Regelschweregrad

::: moniker range=">=vs-2019"

Sie können den Schweregrad der Analyzer-Regeln oder der *Diagnose*konfigurieren, wenn Sie [die-Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren. Ab Visual Studio 2019 Version 16,3 können Sie den Schweregrad einer Regel [in einer Editor config-Datei](#set-rule-severity-in-an-editorconfig-file)konfigurieren. Sie können den Schweregrad einer Regel auch [von Projektmappen-Explorer](#set-rule-severity-from-solution-explorer) oder [einer Regel Satz Datei](#set-rule-severity-in-the-rule-set-file)aus ändern.

::: moniker-end

::: moniker range="vs-2017"

Sie können den Schweregrad der Analyzer-Regeln oder der *Diagnose*konfigurieren, wenn Sie [die-Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren. Sie können den Schweregrad einer Regel [von Projektmappen-Explorer](#set-rule-severity-from-solution-explorer) oder [einer Regel Satz Datei](#set-rule-severity-in-the-rule-set-file)aus ändern.

::: moniker-end

In der folgenden Tabelle werden die verschiedenen Optionen für den Schweregrad angezeigt:

| Schweregrad (Projektmappen-Explorer) | Schweregrad (Editor config-Datei) | Build-Zeitverhalten | Editor-Verhalten |
|-|-|-|
| Fehler | `error` | Verstöße werden im Fehlerliste und in der Befehlszeilen-Buildausgabe als *Fehler* angezeigt und bewirken, dass Builds fehlschlagen.| Das verletzen von Code wird mit einer roten Wellenlinie unterstrichen und in der Bild Lauf Leiste durch ein kleines rotes Feld markiert. |
| Warnung | `warning` | Verstöße werden im Fehlerliste und in der Befehlszeilen-Buildausgabe als *Warnungen* angezeigt, bewirken jedoch nicht, dass Builds fehlschlagen. | Das verletzen von Code wird mit einer grünen Wellenlinie unterstrichen und in der Bild Lauf Leiste durch ein kleines grünes Feld markiert. |
| Info | `suggestion` | Verstöße werden im Fehlerliste als *Meldungen* und nicht in der Befehlszeilen-Buildausgabe angezeigt. | Das verletzen von Code wird mit einem grauen Wellenlinien unterstrichen und in der Bild Lauf Leiste durch ein kleines graues Feld markiert. |
| Ausgeblendet | `silent` | Für den Benutzer nicht sichtbar. | Für den Benutzer nicht sichtbar. Die Diagnose wird jedoch der IDE-Diagnose-Engine gemeldet. |
| None | `none` | Vollständig unterdrückt. | Vollständig unterdrückt. |
| Default | `default` | Entspricht dem Standard Schweregrad der Regel. Um den Standardwert für eine Regel zu ermitteln, suchen Sie in der Eigenschaftenfenster. | Entspricht dem Standard Schweregrad der Regel. |

Der folgende Screenshot des Code-Editors zeigt drei verschiedene Verstöße gegen verschiedene Schweregrade. Beachten Sie die Farbe der Wellenlinie und das kleine farbige Quadrat in der Bild Lauf Leiste auf der rechten Seite.

![Fehler-, Warn-und Informations Verstoß im Code-Editor](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt dieselben drei Verstöße, wie Sie im Fehlerliste angezeigt werden:

![Fehler-, Warn-und Informations Verstoß in Fehlerliste](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Festlegen des schwere Grads der Regel in einer Editor config-Datei

(Visual Studio 2019, Version 16,3 und höher)

Die allgemeine Syntax zum Angeben des schwere Grads einer Regel in einer editorconfig-Datei lautet wie folgt:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Das Festlegen des schwere Grads einer Regel in einer Editor config-Datei hat Vorrang vor einem Schweregrad, der in einem Regelsatz oder in Projektmappen-Explorer festgelegt ist. Sie können den Schweregrad [manuell](#manually-configure-rule-severity) in einer Editor config-Datei oder [automatisch](#automatically-configure-rule-severity) über die Glühbirne konfigurieren, die neben einem Verstoß angezeigt wird.

#### <a name="manually-configure-rule-severity"></a>Regel Schweregrad manuell konfigurieren

1. Wenn Sie nicht bereits über eine Editor config-Datei für Ihr Projekt verfügen, [fügen Sie eine hinzu](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Fügen Sie unter der entsprechenden Dateierweiterung einen Eintrag für jede Regel hinzu, die Sie konfigurieren möchten. Um z. b. den Schweregrad für [CA1822](ca1822-mark-members-as-static.md) auf `error` C# für Dateien festzulegen, sieht der Eintrag wie folgt aus:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Bei IDE-Code Analysetools können Sie Sie auch in einer editorconfig-Datei mit einer anderen Syntax konfigurieren, z. b. `dotnet_style_qualification_for_field = false:suggestion`. Wenn Sie jedoch einen Schweregrad mit der `dotnet_diagnostic`-Syntax festlegen, hat dies Vorrang. Weitere Informationen finden Sie unter [sprach Konventionen für Editor config](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Regel Schweregrad automatisch konfigurieren

Visual Studio bietet eine bequeme Möglichkeit, den Schweregrad einer Regel im Glühbirnen Menü [schnell Aktionen](../ide/quick-actions.md) zu konfigurieren.

1. Nachdem eine Verletzung aufgetreten ist, bewegen Sie den Mauszeiger über die Verletzungs Wellenlinie im Editor, und öffnen Sie das Glühbirnen Menü. Oder platzieren Sie den Cursor in der Zeile, und drücken Sie **STRG**+ **.** (Punkt).

2. Wählen Sie im Glühbirnen Menü **Probleme konfigurieren oder unterdrücken** aus > **Konfigurieren Sie \<rule-ID > Schweregrad**.

   ![Konfigurieren des schwere Grads von Regeln über das Glühbirnen Menü in Visual Studio](media/configure-rule-severity.png)

3. Wählen Sie von dort eine der Optionen für den Schweregrad aus.

   ![Regel Schweregrad als Vorschlag konfigurieren](media/configure-rule-severity-suggestion.png)

   Visual Studio fügt der Datei Editor config einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren, wie im Feld Vorschau angezeigt.

   > [!TIP]
   > Wenn Sie noch nicht über eine Editor config-Datei im Projekt verfügen, erstellt Visual Studio einen für Sie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen des schwere Grads der Regel Projektmappen-Explorer

1. ErweiternSie in Projektmappen-Explorer **Verweise** > -**Analyzers** (oder **Abhängigkeiten** > -**Analyzers** für .net Core-Projekte).

1. Erweitern Sie die Assembly, die die Regel enthält, für die Sie den Schweregrad festlegen möchten.

1. Klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Regelsatz Schweregrad festlegen**. Wählen Sie im Menü für die Ausführung eine der Optionen für den Schweregrad aus.

   Der Schweregrad für die Regel wird in der aktiven Regel Satz Datei gespeichert.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Festlegen des Regel schwere Grads in der Regel Satz Datei

![Regel Satz Datei in Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

1. Öffnen Sie die aktive [Regel Satz](analyzer-rule-sets.md) Datei, indem Sie in **Projektmappen-Explorer**auf die Datei doppelklicken. Wählen Sie dazu im Kontextmenü des Knotens **@no__t-** 4-**Analyzers** den Knoten **aktive Regel Satz öffnen** aus, oder klicken **Sie auf der** **Seite Code Analyse** -Eigenschaften Seite für das Projekt.

   Wenn Sie den Regelsatz zum ersten Mal bearbeiten, erstellt Visual Studio eine Kopie der Standardregel Satz-Datei, benennt Sie *\<projectname >. RuleSet*und fügt Sie dem Projekt hinzu. Dieser benutzerdefinierte Regelsatz wird auch zum aktiven Regelsatz für Ihr Projekt.

   > [!NOTE]
   > .Net Core-und .NET Standard-Projekte unterstützen nicht die Menübefehle für Regelsätze in **Projektmappen-Explorer**, z. b. **Öffnen des aktiven Regelsatzes**. Wenn Sie einen nicht standardmäßigen Regelsatz für ein .net Core-oder .NET Standard-Projekt angeben möchten, [fügen Sie die Eigenschaft " **codeanalysisruleset** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) " manuell zur Projektdatei hinzu. Sie können die Regeln im Regelsatz weiterhin in der Benutzeroberfläche von Visual Studio-Regelsatz-Editor konfigurieren.

1. Navigieren Sie zu der Regel, indem Sie die enthaltende Assembly erweitern.

1. Wählen Sie in der Spalte **Aktion** den Wert aus, um eine Dropdown Liste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste aus.

   ![Regel Satz Datei in Editor öffnen](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Verstöße unterdrücken

Es gibt mehrere Möglichkeiten, Regel Verletzungen zu unterdrücken:

::: moniker range=">=vs-2019"

- In einer **Editor config-Datei**

  Legen Sie den Schweregrad auf `none` fest, z. b. `dotnet_diagnostic.CA1822.severity = none`.

- Über das Menü " **analysieren** "

  Wählen Sie  > -Build **analysieren**aus, und unterdrücken Sie in der Menüleiste**aktive Probleme** , um alle aktuellen Verstöße zu unterdrücken Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

::: moniker range="vs-2017"

- Über das Menü " **analysieren** "

  Wählen Sie  >  **analysieren**,**Code Analyse ausführen und aktive Probleme unterdrücken** in der Menüleiste aus, um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

- Von **Projektmappen-Explorer**

  Legen Sie den Schweregrad der Regel auf **None**fest.

- Aus dem **Regelsatz-Editor**

  Deaktivieren Sie das Kontrollkästchen neben dem Namen, oder legen Sie die **Aktion** auf **keine**fest.

- Im **Code-Editor**

  Platzieren Sie den Cursor in der Codezeile mit der Verletzung, und drücken Sie **STRG**+ Punkt **(.)** , um das Menü **schnell Aktionen** zu öffnen. Wählen Sie **CAXXXX** > **in der Quelle/in Unterdrückungs Datei unterdrücken aus**.

  ![Diagnose über das Menü "schnelle Aktionen" unterdrücken](media/suppress-diagnostic-from-editor.png)

- Aus der **Fehlerliste**

  Wählen Sie die zu unterdrückenden Regeln aus, und klicken Sie dann mit der rechten Maustaste, und wählen Sie  > **in der Quelle/in Unterdrückungs Datei unter** **drücken**

  - Wenn Sie **in Quelle**unterdrücken, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, und C# es wird eine Vorschau der [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) -oder Visual Basic [#Disable Warning](/dotnet/visual-basic/language-reference/directives/directives) -Direktive angezeigt, die dem Quellcode hinzugefügt wird.

    ![Vorschau der Hinzufügung von #pragma Warnung in der Codedatei](media/pragma-warning-preview.png)

  - Wenn Sie **in Unterdrückungs Datei**auswählen, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, und es wird eine Vorschau des <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>-Attributs angezeigt, das der globalen Unterdrückungs Datei hinzugefügt wird.

    ![Vorschau zum Hinzufügen des SuppressMessage-Attributs zur Unterdrückungs Datei](media/preview-changes-in-suppression-file.png)

  **Wählen Sie**im Dialogfeld **Vorschau der Änderungen** übernehmen aus.

  > [!NOTE]
  > Wenn die Option Menü unter **drücken** in **Projektmappen-Explorer**nicht angezeigt wird, wird die Verletzung wahrscheinlich von Build und nicht von Live-Analyse stammt. In der **Fehlerliste** werden Diagnose-oder Regelverstöße sowohl aus der Live Code Analyse als auch aus dem Build angezeigt. Da die builddiagnose beispielsweise veraltet sein kann, wenn Sie z. b. den Code bearbeitet haben, um den Verstoß zu beheben, aber nicht neu erstellt wurde, können Sie diese Diagnose nicht im **Fehlerliste**unterdrücken. Die Diagnose aus Live Analyse oder IntelliSense sind immer auf dem neuesten Stand mit aktuellen Quellen und können vom **Fehlerliste**unterdrückt werden. Um die *builddiagnose von* Ihrer Auswahl auszuschließen, ändern Sie den **Fehlerliste** Quellen Filter von **Build + IntelliSense** **nur in IntelliSense**. Wählen Sie dann die Diagnose aus, die Sie unterdrücken möchten, und fahren Sie wie zuvor beschrieben fort.
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
