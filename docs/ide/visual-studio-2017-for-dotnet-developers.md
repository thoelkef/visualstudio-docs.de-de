---
title: "Visual Studio 2017 für .NET-Entwickler | Microsoft-Dokumentation"
description: "Übersicht über Features von Visual Studio 2017, mit denen Sie .NET-Code schneller und besser schreiben können."
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
ms.openlocfilehash: 053bd6077fa98142cd74eae58ce3df949291c326
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 für .NET-Entwickler

## <a name="smart-code-editor"></a>Intelligenter Code-Editor

- [Dokumentation: Verwenden von IntelliSense](using-intellisense.md)
- [Dokumentation: Features des intelligenten Editors](writing-code-in-the-code-and-text-editor.md)

Dank des .NET-Compilers (bzw. Roslyn-Compilers) ist Visual Studio auf das Schreiben von Code bestens ausgelegt und kann Ihnen intelligente Bearbeitungsfeatures bieten, z.B. farbige Syntaxhervorhebung, Codevervollständigung, Rechtschreibprüfung falsch geschriebener Variablen, Auflösung nicht importierter Typen, Gliederung, Strukturschnellansichten, [CodeLens](find-code-changes-and-other-history-with-codelens.md), Aufrufhierarchie, QuickInfos beim Zeigen auf ein Element, Parameterhilfe sowie Tools für Refactoring, zum Anwenden schneller Aktionen und zum Generieren von Code.

![Intelligenter Code-Editor für Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Navigieren und Durchsuchen Ihrer Codebasis

[Dokumentation: Navigieren im Code](navigating-code.md)

Sie können mühelos im .NET-Code navigieren, indem Sie mit der Tastenkombination *Gehe zu allen* (**STRG+T**) zu einer beliebigen Datei-, Typ-, Member- oder Symboldeklaration springen. Sie können im Code nach allen Verweisen eines Symbols oder Literals suchen lassen, auch nach Verweisen in verschiedenen .NET-Sprachen (**UMSCHALTTASTE+F12**). Mithilfe unserer gezielt ausgerichteten Navigationsbefehle können Sie leichter direkt zu Symboldefinitionen (**F12**) oder Implementierungen (**STRG + F12**) springen.

![„Gehe zu allen“ und „Alle Verweise suchen“](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Livecodeanalyse für hohe Codequalität

[Dokumentation: Refactorings und Schnelle Aktionen](refactoring-code-generation-quick-actions.md)

Visual Studio verfügt über Codediagnose in Echtzeit. Durch das Erkennen von Fehlern und potenziell problematischem Code unterstützt Visual Studio Sie dabei, die Qualität Ihres Codes zu verbessern. Sie können schnelle Aktionen (**STRG+.**) verwenden, um erkannte Probleme in Ihrem Dokument, Projekt oder in Ihrer Projektmappe zu beheben. Aktivieren Sie *full-solution analysis* (Vollständige Analyse der Projektmappe), um sämtliche Probleme Ihrer gesamten Projektmappe zu identifizieren, auch wenn die entsprechenden Dateien im Editor gerade nicht geöffnet sind.

Darüber hinaus können Sie Codevorschläge verwenden, um bewährte Methoden sowie das Verwenden von Stubs, das Generieren und Umgestalten von Code und das Übernehmen neuer Sprachfeatures mit der Tastenkombination **STRG+.** zu erlernen. .

![Schnellkorrekturen und Refactorings über das Glühbirnenmenü anwenden](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Unittest

[Dokumentation: Unit testing in Visual Studio](../test/improve-code-quality.md)

Sie können Ihre Komponententests auf Basis der Testframeworks MSTest, NUnit und XUnit ausführen und debuggen. Diese Frameworks eignen sich für jede beliebige Anwendung, die .NET Framework, .NET Standard oder .NET Core als Ziel verwendet. Sie können die Tests im *Test-Explorer* ausprobieren und überprüfen. Alternativ können Sie im Editor mithilfe von *Live Unit Testing* sofort sehen, wie sich Änderungen am Code auf Ihre Komponententests auswirken (nur bei Enterprise SKU möglich).

![Live Unit Testing in Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Codekonsistenz und -stil

- [Dokumentation: portable, benutzerdefinierte Editor-Optionen](create-portable-custom-editor-options.md)
- [Dokumentation: EditorConfig-Codeformateinstellungen für .NET](editorconfig-code-style-settings-reference.md)

Visual Studio ermöglicht das Konfigurieren von Codierungskonventionen, erkennt Verstöße gegen den Codierungsstil und ermöglicht Schnellkorrekturen zum Beheben von Stilproblemen über die Tastenkombination **STRG+.** . Mithilfe von *EditorConfig* können Sie die Konventionen Ihres Teams in puncto Formatieren, Benennen und Programmierstil für ein Repository konfigurieren und dort zwingend vorgeben. Ebenso können Sie damit das Überschreiben von Werten auf Projekt- und Dateiebene erlauben.

![Konfigurieren und Erzwingen von Codierungskonventionen mit EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Debuggen

[Dokumentation: Debuggen in Visual Studio](../debugger/index.md)

Visual Studio enthält einen erstklassigen Debugger, mit dem Sie die .NET-Anwendungen debuggen können, die .NET Framework, .NET Standard und .NET Core als Ziel verwenden. Sie können bedingte Haltepunkte umschalten und festlegen (**F9**), Methodenaufrufe durchlaufen, LINQ- und Lambdaausdrücke evaluieren, die Überwachung von Variablen einrichten, das Anfügen an Prozesse wiederholen, Ihre Aufrufliste überprüfen oder mithilfe von *Bearbeiten und Fortfahren* Code sogar während des Debuggens in Echtzeit bearbeiten.

Wenn Ihr Dienst in Azure ausgeführt wird, verwenden Sie *Momentaufnahmendebugging*, um in Visual Studio 2017 Enterprise bei Ihren bereitgestellten Cloud-Anwendungen, die sich im Livebetrieb befinden, Probleme zu diagnostizieren.

![Debuggen in Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Versionskontrolle

[Dokumentation: Versionskontrolle in Visual Studio](/vsts/index)

Verwenden Sie Git oder TFVC zum Speichern und Aktualisieren Ihres Codes in Visual Studio. Im Editor können Sie mit Team Explorer lokale Änderungen strukturieren und die Statusleiste verwenden, um ausstehende Commits und Änderungen nachzuverfolgen. Mit der Erweiterung [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) können Sie in Visual Studio Continuous Integration und Continuous Delivery einrichten, um den agilen Entwicklungsworkflow einzuführen.

![Quellcodeverwaltung in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Erweiterungen

[Dokumentation: Erweitern von Visual Studio](../extensibility/index.md)

Visual Studio verfügt über eine umfangreiche Anzahl an Erweiterungen, die Sie je nach Bedarf installieren oder erstellen können. Sie können Erweiterungen über den *Erweiterungskatalog* oder *Visual Studio Marketplace* installieren, mit dem *VS SDK* Ihr eigenes Editor-Plug-In erstellen oder mit dem *.NET Compiler Platform SDK* Ihren eigenen Echtzeit-Codeanalysetool oder Echtzeit-Umgestaltungstool erstellen. Für zusätzliche Codekorrekturen und Vorschläge können Sie die Erweiterung [Microsoft Code Analysis](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) herunterladen.

![Die Visual Studio-Erweiterungskatalog](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Beliebte Erweiterungen und Tastenkombinationen

Wenn Sie eine andere IDE oder Kodierungsumgebung gewohnt sind, kann es hilfreich sein, eine der folgenden Erweiterungen zu installieren:

- [Emacs-Emulation](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [HotKeys für Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Im Folgenden finden Sie beliebte Tastenkombinationen für Visual Studio. Beachten Sie, dass einige Erweiterungen die Standardtastenzuordnungen von Visual Studio aufheben. Sie müssen die Tastenzuordnungen wiederherstellen, um die im Folgenden aufgeführten Befehle zu verwenden. Navigieren Sie zu **Extras > Einstellungen importieren und exportieren > Alle Einstellungen zurücksetzen**, um die Standardeinstellungen für die Tastenkombinationen in Visual Studio wiederherzustellen.

| Tastenkombination (Alle Profile) | Befehl | description |
|-|-|-|
| **STRG+T** | Gehe zu allen | Navigieren zu einer beliebigen Datei-/Typ-/Member-/Symboldeklaration |
| **F12** (oder **STRG+Klicken**) | Gehe zu Definition | Navigieren zum Ort, an dem ein Symbol definiert ist |
| **STRG+F12** | Gehe zu Implementierung | Navigieren von einem Basistyp oder Member zu seinen verschiedenen Implementierungen |
| **UMSCHALT+F12** | Alle Verweise suchen | Alle Symbol- oder Literalverweise ansehen |
| **STRG+.** (auch **Alt+EINGABETASTE** in C# Profile) | Schnellaktionen und Refactorings | Ansehen, welche Codekorrekturen, Aktionen zum Generieren von Code, Refactorings oder anderen Schnellaktionen an der Cursorposition oder für den markierten Code zur Verfügung stehen. |
| **STRG**+**E**,**V** | Zeile duplizieren | Die Codezeile, in der sich der Cursor befindet, wird dupliziert (verfügbar in **Visual Studio 2017 Version 15.6 Vorschauversion 2** und höher) |
| **STRG+Q** | Schnellstart | Durchsuchen aller Visual Studio-Einstellungen |
| **F5** | Debugging starten | Debugging der Anwendung starten |
| **STRG+F5** | Ohne Debuggen ausführen | Anwendung lokal ausführen, ohne Debuggen |
| **STRG+K, D** (Standardprofil) oder **STRG+E, D** (C# Profile) | Dokument formatieren | Bereinigt Formatierungsverstöße in Ihrer Datei anhand Ihrer Einstellungen für Zeilenumbruch, Abstand und Einzug |
| **STRG+\\,E** (Standardprofil) oder **STRG+W, E** (C#-Profil) | Fehlerliste anzeigen | Alle Fehler in Ihrem Dokument, Projekt oder Ihrer Projektmappe ansehen |