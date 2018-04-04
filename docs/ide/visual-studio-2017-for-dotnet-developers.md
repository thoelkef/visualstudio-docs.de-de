---
title: Visual Studio 2017 für .NET-Entwickler | Microsoft-Dokumentation
description: Übersicht über Features von Visual Studio 2017, mit denen Sie .NET-Code schneller und besser schreiben können.
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Produktivitätsleitfaden für Visual Studio 2017 für .NET-Entwickler

- [Produktivitätshandbuch](#guide)
- [Übersicht über Visual Studio 2017](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/> Produktivitätshandbuch
Mit [Visual Studio 2017](https://www.visualstudio.com/downloads/) sind Entwickler produktiver als je zuvor! Wir haben die Leistung und Zuverlässigkeit für den Start und das Laden von Projektmappen, die Testermittlung und die Eingabelatenz verbessert. Wir haben auch Features hinzugefügt und erweitert, mit denen Sie schneller besseren Code schreiben können. Zu diesen Features zählen: Navigation zu dekompilierten Assemblys, Namensvorschläge für Variablen während der Eingabe, eine Hierarchieansicht im Test-Explorer, „Gehe zu allen“ (**STRG + T**) zur Navigation zu Datei- / Typ- / Member- / Symboldeklarationen, eine intelligente Hilfe bei Ausnahmen, Konfiguration und Erzwingung des Codeformats und viele Refactorings und Codekorrekturen. 

Folgen Sie dieser Anleitung, um Ihre Produktivität zu optimieren.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Ich bin an meine Tastenkombinationen aus einer anderen Erweiterung/einem anderen Editor/einer anderen IDE gewöhnt.

Wenn Sie eine andere IDE oder Kodierungsumgebung gewohnt sind, kann es hilfreich sein, eine der folgenden Erweiterungen zu installieren:

- [Emacs-Emulation](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [HotKeys für Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Im Folgenden finden Sie beliebte Tastenkombinationen für Visual Studio. 

> [!NOTE]
> Einige Erweiterungen heben die Standardtastenzuordnungen von Visual Studio auf. Sie müssen sie wiederherstellen, um die im Folgenden aufgeführten Befehle zu verwenden. Stellen Sie die Standardtastenzuordnungen von Visual Studio wieder her. Navigieren Sie dazu zu **Extras > Einstellungen importieren und exportieren... > Alle Einstellungen zurücksetzen** oder zu **Extras > Optionen > Tastatur > Zurücksetzen**.

| Tastenkombination (Alle Profile) | Befehl | description |
|-|-|-|
| **STRG+T** | Gehe zu allen | Navigieren zu einer beliebigen Datei-/Typ-/Member-/Symboldeklaration |
| **F12** (oder **STRG+Klicken**) | Gehe zu Definition | Navigieren zum Ort, an dem ein Symbol definiert ist |
| **STRG+F12** | Gehe zu Implementierung | Navigieren von einem Basistyp oder Member zu seinen verschiedenen Implementierungen |
| **UMSCHALT+F12** | Alle Verweise suchen | Alle Symbol- oder Literalverweise ansehen |
| **STRG**+**.** (auch **Alt+EINGABETASTE** in C# Profile) | Schnellaktionen und Refactorings | Ansehen, welche Codekorrekturen, Aktionen zum Generieren von Code, Refactorings oder anderen Schnellaktionen an der Cursorposition oder für den markierten Code zur Verfügung stehen. |
| **STRG**+**D** | Zeile duplizieren | Die Codezeile, in der sich der Cursor befindet, wird dupliziert (verfügbar in **Visual Studio 2017 Version 15.6** und höher) |
| **UMSCHALT**+**ALT**+**+**/**-** | Erweitern/Reduzieren | Erweitert oder reduziert die aktuelle Auswahl im Editor (verfügbar in **Visual Studio 2017 Version 15.5** und höher) |
| **STRG+Q** | Schnellstart | Durchsuchen aller Visual Studio-Einstellungen |
| **F5** | Debugging starten | Debugging der Anwendung starten |
| **STRG+F5** | Ohne Debuggen ausführen | Anwendung lokal ausführen, ohne Debuggen |
| **STRG+K, D** (Standardprofil) oder **STRG+E, D** (C# Profile) | Dokument formatieren | Bereinigt Formatierungsverstöße in Ihrer Datei anhand Ihrer Einstellungen für Zeilenumbruch, Abstand und Einzug |
| **STRG+\\,E** (Standardprofil) oder **STRG+W, E** (C#-Profil) | Fehlerliste anzeigen | Alle Fehler in Ihrem Dokument, Projekt oder Ihrer Projektmappe ansehen |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Ich benötige eine Möglichkeit, schnell zu Dateien oder Dateitypen zu navigieren.
Visual Studio 2017 verfügt über ein Feature namens _Gehe zu allen_ (**STRG + T**). „Gehe zu allen“ ermöglicht Ihnen einen schnellen Wechsel zu jeder Datei-, Typ-, Member- oder Symboldeklaration.
- Ändern Sie den Speicherort dieser Suchleiste oder deaktivieren Sie die „Livenavigationsvorschau“ mit dem **Zahnradsymbol**.
- Filtern Sie die Ergebnisse mithilfe unserer Abfragesyntax (z.B. „t mytype“). Sie können Ihre Suche auch nur auf das aktuelle Dokument beschränken.
- camelCase-Zuordnung wird unterstützt!

![„Gehe zu allen“ in Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mein Team erzwingt Codeformatregeln für unsere Codebasis.
Sie können eine EDITORCONFIG-Datei zum Codieren von Codierungskonventionen verwenden. Wir empfehlen die Installation der [EditorConfig-Sprachdiensteerweiterung](https://aka.ms/editorconfig) für das Hinzufügen und Bearbeiten einer EDITORCONFIG-Datei. Es wird empfohlen, sich die [Dokumentation](https://aka.ms/editorconfigDocs) für alle .NET-Codierungskonventionsoptionen anzusehen.

Sehen Sie sich diese [Zusammenfassung](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) für eine EDITORCONFIG-Beispieldatei an.

![Codeformaterzwingung in Visual Studio](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>Ich benötige weitere Refactorings und Codekorrekturen.
Visual Studio 2017 bietet eine Vielzahl von Refactorings, Aktionen zum Generieren von Code und Codekorrekturen, die Sie sich in der [Dokumentation](https://aka.ms/refactorings) ansehen können. Rote Wellenlinien stellen Fehler dar, grüne Wellenlinien Warnungen, und drei graue Punkte stellen Codevorschläge dar.

Sie erhalten Zugang zu Codekorrekturen, indem Sie auf das Glühbirnen- bzw. Schraubendrehersymbol klicken oder **STRG+.** oder **ALT+EINGABETASTE** drücken. Jede Korrektur enthält ein Vorschaufenster, das einen Livecodevergleich und die Funktionsweise der Lösung anzeigt.

Hier sehen Sie einige beliebte Schnellkorrekturen und Refactorings: Umbenennen, Methode extrahieren, Methodensignatur ändern, Konstruktor generieren, Methode generieren, Typ zur Datei verschieben, NULL-Überprüfung hinzufügen, Parameter hinzufügen, unnötige Using-Direktiven entfernen.

Refactorings und Codekorrekturen können problemlos mit [Roslyn-Analyzern](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix) geschrieben werden. Mehrere Communitymitglieder haben *kostenlose* Erweiterungen geschrieben, die zusätzliche Codeüberprüfungen hinzufügen: Roslynator und SonarLint für Visual Studio. 

![Refactorings in Visual Studio](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Ich benötige die Features „Find Usages“ (Verwendungen finden), „Gehe zu Implementierung“, „Navigate To Decompiled Assemblies“ (Navigieren zu dekompilierten Assemblys)
Visual Studio 2017 besitzt viele Features zum Suchen und Navigieren Ihrer Codebasis – einschließlich „Alle Verweise suchen“ (**UMSCHALT + F12**), „Gehe zu Implementierung“ (**STRG + F12**), „Gehe zu Definition“ (**F12** oder **STRG + Klicken**). Das Feature „Navigieren zu dekompilierten Assemblys“ wurde in Version 15.6 hinzugefügt. Um dieses Feature zu aktivieren, wechseln Sie zu **Extras > Optionen > Text-Editor > C# > Erweitert > Navigation zu dekompilierten Quellen aktivieren**.

![Navigieren zu dekompilierten Quellen in Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>Ich möchte meine Komponententests ausführen und anzeigen.
Es gibt zwei Angebote für Komponententests in Visual Studio 2017: Test-Explorer und _Live Unit Testing_. Wir haben die Geschwindigkeit der Testermittlung in Test-Explorer Version 15.6 erheblich verbessert. Wir haben außerdem die Benutzeroberfläche neu gestaltet, um hierarchische Sortierung zu ermöglichen.

Visual Studio verfügt auch über ein Feature für Komponententests namens [Live Unit Testing](/test/live-unit-testing). Live Unit Testing wird ständig im Hintergrund ausgeführt, führt Tests durch, die durch Ihre Codeänderung beeinflusst werden, und aktualisiert Inline-Editor-Symbole, um Sie über den Status Ihres Tests zu informieren.

![Hierarchieansicht für Text-Explorer in Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hierarchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>Welche anderen Features sollte ich kennen?
Hier ist eine Liste an Editor- und Produktivitätsfeatures zum einfacheren Schreiben von Code. Einige Features müssen aktiviert werden, da sie standardmäßig deaktiviert sind (sie indizieren möglicherweise Dinge auf dem Computer, sind kontrovers oder derzeit experimentell).
- *Suchen von Dateien im Projektmappen-Explorer* hebt die aktive Datei im Projektmappen-Explorer hervor.
  - **Extras>Optionen>Projekte und Projektmappen>Aktives Element im Projektmappen-Explorer überwachen**
- *Hinzufügen von Using-Direktiven für Typen in Verweisassemblys und NuGet-Paketen* zeigt eine Glühbirne mit einer Codekorrektur für die Installation eines NuGet-Pakets für einen unreferenzierten Typ.
  - **Extras>Optionen>Text-Editor>C#>Erweitert>Using-Direktiven für Typen in Verweisassemblys vorschlagen** und **Using-Direktiven für Typen in NuGet-Paketen vorschlagen**
- *Aktivieren der vollständigen Projektmappenanalyse*, um alle Fehler in der Projektmappe in der Fehlerliste anzuzeigen.
  - **Extras > Optionen > Text-Editor > C# > Erweitert > Vollständige Projektmappenanalyse aktivieren**
- *Aktivieren der Navigation zu dekompilierten Quellen* zur Aktivierung von „Gehe zu Definition“ auf Typen/Membern aus externen Quellen und Verwenden des ILSpy-Decompilers zur Anzeige von Methodentexten.
  - **Extras>Optionen>Text-Editor>C#>Erweitert>Navigation zu dekompilierten Quellen aktivieren**
- *Vervollständigung-/Vorschlagsmodus* in IntelliSense ändert das Vervollständigungsverhalten. Entwickler mit IntelliJ-Hintergründen ändern meist die Einstellung des Standardwerts.
  - **Menü > Bearbeiten > IntelliSense > Vervollständigungsmodus umschalten**
- Wir verfügen über *Codeausschnitte* zum Erstellen von allgemeinen Textbausteinen (zwei Mal „Tabstopp“ drücken). Siehe [vollständige Liste](/ide/visual-csharp-code-snippets).

![Codeausschnitte in Visual Studio](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Fehlt ein Feature, das Ihre Produktivität erhöht oder treten Leistungsprobleme auf?
Es stehen Ihnen verschiedene Feedbackmöglichkeiten zur Verfügung:
- Sie können .NET-Features über unser [GitHub-Repository](https://github.com/dotnet/roslyn/issues) anfordern.
- Visual Studio-Featureanforderungen, Fehler und Leistungsprobleme können mit dem Symbol **Feedback senden** am oberen Rand des Visual Studio-Fensters erfasst werden.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Überblick über Visual Studio 2017 für .NET-Entwickler

### <a name="smart-code-editor"></a>Intelligenter Code-Editor

- [Dokumentation: Verwenden von IntelliSense](using-intellisense.md)
- [Dokumentation: Features des intelligenten Editors](writing-code-in-the-code-and-text-editor.md)

Dank des .NET-Compilers (bzw. Roslyn-Compilers) ist Visual Studio auf das Schreiben von Code bestens ausgelegt und kann Ihnen intelligente Bearbeitungsfeatures bieten, z.B. farbige Syntaxhervorhebung, Codevervollständigung, Rechtschreibprüfung falsch geschriebener Variablen, Auflösung nicht importierter Typen, Gliederung, Strukturschnellansichten, [CodeLens](find-code-changes-and-other-history-with-codelens.md), Aufrufhierarchie, QuickInfos beim Zeigen auf ein Element, Parameterhilfe sowie Tools für Refactoring, zum Anwenden schneller Aktionen und zum Generieren von Code.

![Intelligenter Code-Editor für Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Navigieren und Durchsuchen Ihrer Codebasis

[Dokumentation: Navigieren im Code](navigating-code.md)

Sie können mühelos im .NET-Code navigieren, indem Sie mit der Tastenkombination *Gehe zu allen* (**STRG+T**) zu einer beliebigen Datei-, Typ-, Member- oder Symboldeklaration springen. Sie können im Code nach allen Verweisen eines Symbols oder Literals suchen lassen, auch nach Verweisen in verschiedenen .NET-Sprachen (**UMSCHALTTASTE+F12**). Mithilfe unserer gezielt ausgerichteten Navigationsbefehle können Sie leichter direkt zu Symboldefinitionen (**F12**) oder Implementierungen (**STRG + F12**) springen.

![„Gehe zu allen“ und „Alle Verweise suchen“](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Livecodeanalyse für hohe Codequalität

[Dokumentation: Refactorings und Schnelle Aktionen](refactoring-code-generation-quick-actions.md)

Visual Studio verfügt über Codediagnose in Echtzeit. Durch das Erkennen von Fehlern und potenziell problematischem Code unterstützt Visual Studio Sie dabei, die Qualität Ihres Codes zu verbessern. Sie können schnelle Aktionen (**STRG**+**.**) verwenden, um erkannte Probleme in Ihrem Dokument, Projekt oder in Ihrer Projektmappe zu beheben. Aktivieren Sie *full-solution analysis* (Vollständige Analyse der Projektmappe), um sämtliche Probleme Ihrer gesamten Projektmappe zu identifizieren, auch wenn die entsprechenden Dateien im Editor gerade nicht geöffnet sind.

Darüber hinaus können Sie Codevorschläge verwenden, um bewährte Methoden sowie das Verwenden von Stubs, das Generieren und Umgestalten von Code und das Übernehmen neuer Sprachfeatures mit der Tastenkombination **STRG**+**.** zu erlernen. .

![Schnellkorrekturen und Refactorings über das Glühbirnenmenü anwenden](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Unittest

[Dokumentation: Unit testing in Visual Studio](../test/improve-code-quality.md)

Sie können Ihre Komponententests auf Basis der Testframeworks MSTest, NUnit und XUnit ausführen und debuggen. Diese Frameworks eignen sich für jede beliebige Anwendung, die .NET Framework, .NET Standard oder .NET Core als Ziel verwendet. Sie können die Tests im *Test-Explorer* ausprobieren und überprüfen. Alternativ können Sie im Editor mithilfe von *Live Unit Testing* sofort sehen, wie sich Änderungen am Code auf Ihre Komponententests auswirken (nur bei Enterprise SKU möglich).

![Live Unit Testing in Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Codekonsistenz und -stil

- [Dokumentation: portable, benutzerdefinierte Editor-Optionen](create-portable-custom-editor-options.md)
- [Dokumentation: EditorConfig-Codeformateinstellungen für .NET](editorconfig-code-style-settings-reference.md)

Visual Studio ermöglicht das Konfigurieren von Codierungskonventionen, erkennt Verstöße gegen den Codierungsstil und ermöglicht Schnellkorrekturen zum Beheben von Stilproblemen über die Tastenkombination **STRG**+**.** . Mithilfe von *EditorConfig* können Sie die Konventionen Ihres Teams in puncto Formatieren, Benennen und Programmierstil für ein Repository konfigurieren und dort zwingend vorgeben. Ebenso können Sie damit das Überschreiben von Werten auf Projekt- und Dateiebene erlauben.

![Konfigurieren und Erzwingen von Codierungskonventionen mit EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Debuggen

[Dokumentation: Debuggen in Visual Studio](../debugger/index.md)

Visual Studio enthält einen erstklassigen Debugger, mit dem Sie die .NET-Anwendungen debuggen können, die .NET Framework, .NET Standard und .NET Core als Ziel verwenden. Sie können bedingte Haltepunkte umschalten und festlegen (**F9**), Methodenaufrufe durchlaufen, LINQ- und Lambdaausdrücke evaluieren, die Überwachung von Variablen einrichten, das Anfügen an Prozesse wiederholen, Ihre Aufrufliste überprüfen oder mithilfe von *Bearbeiten und Fortfahren* Code sogar während des Debuggens in Echtzeit bearbeiten.

Wenn Ihr Dienst in Azure ausgeführt wird, verwenden Sie *Momentaufnahmendebugging*, um in Visual Studio 2017 Enterprise bei Ihren bereitgestellten Cloud-Anwendungen, die sich im Livebetrieb befinden, Probleme zu diagnostizieren.

![Debuggen in Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Versionskontrolle

[Dokumentation: Versionskontrolle in Visual Studio](/vsts/index)

Verwenden Sie Git oder TFVC zum Speichern und Aktualisieren Ihres Codes in Visual Studio. Im Editor können Sie mit Team Explorer lokale Änderungen strukturieren und die Statusleiste verwenden, um ausstehende Commits und Änderungen nachzuverfolgen. Mit der Erweiterung [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) können Sie in Visual Studio Continuous Integration und Continuous Delivery einrichten, um den agilen Entwicklungsworkflow einzuführen.

![Quellcodeverwaltung in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Erweiterungen

[Dokumentation: Erweitern von Visual Studio](../extensibility/index.md)

Visual Studio verfügt über eine umfangreiche Anzahl an Erweiterungen, die Sie je nach Bedarf installieren oder erstellen können. Sie können Erweiterungen über den *Erweiterungskatalog* oder *Visual Studio Marketplace* installieren, mit dem *VS SDK* Ihr eigenes Editor-Plug-In erstellen oder mit dem *.NET Compiler Platform SDK* Ihren eigenen Echtzeit-Codeanalysetool oder Echtzeit-Umgestaltungstool erstellen. Für zusätzliche Codekorrekturen und Vorschläge können Sie die Erweiterung [Microsoft Code Analysis](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) herunterladen.

![Die Visual Studio-Erweiterungskatalog](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
