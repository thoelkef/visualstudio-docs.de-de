---
title: Visual Studio 2017 für .NET-Entwickler | Microsoft-Dokumentation
description: Übersicht über Features von Visual Studio 2017, mit denen Sie .NET-Code schneller und besser schreiben können.
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 31291814c2158c9aeb8d48b1b7b3073a4ccbcaf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Produktivitätsleitfaden für Visual Studio 2017 für .NET-Entwickler

Mit [Visual Studio 2017](https://www.visualstudio.com/downloads/) sind Entwickler produktiver als je zuvor! Wir haben die Leistung und Zuverlässigkeit für den Start und das Laden von Projektmappen, die Testermittlung und die Eingabelatenz verbessert. Wir haben auch Features hinzugefügt und erweitert, mit denen Sie schneller besseren Code schreiben können. Zu diesen Features zählen: Navigation zu dekompilierten Assemblys, Namensvorschläge für Variablen während der Eingabe, eine Hierarchieansicht im Test-Explorer, „Gehe zu allen“ (**STRG + T**) zur Navigation zu Datei- / Typ- / Member- / Symboldeklarationen, eine intelligente Hilfe bei Ausnahmen, Konfiguration und Erzwingung des Codeformats und viele Refactorings und Codekorrekturen. 

Folgen Sie dieser Anleitung, um Ihre Produktivität zu optimieren.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Ich bin an meine Tastenkombinationen aus einer anderen Erweiterung/einem anderen Editor/einer anderen IDE gewöhnt.

Wenn Sie eine andere IDE oder Kodierungsumgebung gewohnt sind, kann es hilfreich sein, eine der folgenden Erweiterungen zu installieren:

- [Emacs-Emulation](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [HotKeys für Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Im Folgenden finden Sie beliebte Tastenkombinationen für Visual Studio: 

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

> [!NOTE]
> Einige Erweiterungen heben die Tastenzuordnungen von Visual Studio auf. Um die folgenden Befehle verwenden zu können, stellen Sie zuerst die Standardtastenzuordnungen von Visual Studio wieder her. Navigieren Sie dazu zu **Extras > Einstellungen importieren und exportieren... > Alle Einstellungen zurücksetzen** oder zu **Extras > Optionen > Tastatur > Zurücksetzen**.

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Ich benötige eine Möglichkeit, schnell zu Dateien oder Dateitypen zu navigieren.
Visual Studio 2017 verfügt über ein Feature namens _Gehe zu allen_ (**STRG + T**). „Gehe zu allen“ ermöglicht Ihnen einen schnellen Wechsel zu jeder Datei-, Typ-, Member- oder Symboldeklaration.
- Ändern Sie den Speicherort dieser Suchleiste oder deaktivieren Sie die „Livenavigationsvorschau“ mit dem **Zahnradsymbol**.
- Filtern Sie die Ergebnisse mithilfe unserer Abfragesyntax (z.B. „t mytype“). Sie können Ihre Suche auch nur auf das aktuelle Dokument beschränken.
- camelCase-Zuordnung wird unterstützt!

![„Gehe zu allen“ in Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mein Team erzwingt Codeformatregeln für unsere Codebasis.
Sie können eine EDITORCONFIG-Datei zum Codieren von Codierungskonventionen verwenden und diese in Ihrer Quelle beibehalten.
- Wir empfehlen die Installation der [EditorConfig-Sprachdiensteerweiterung](https://aka.ms/editorconfig) für das Hinzufügen und Bearbeiten einer EDITORCONFIG-Datei in Visual Studio. 
- Sehen Sie sich die [Dokumentation](https://aka.ms/editorconfigDocs) für alle .NET-Codierungskonventionsoptionen an.
- Sehen Sie sich diese [Zusammenfassung](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) für eine EDITORCONFIG-Beispieldatei an.

![Codeformaterzwingung in Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Ich benötige weitere Refactorings und Codekorrekturen.
Visual Studio 2017 bietet eine Vielzahl von Refactorings, Aktionen zum Generieren von Code und Codekorrekturen. Rote Wellenlinien stellen Fehler dar, grüne Wellenlinien Warnungen, und drei graue Punkte stellen Codevorschläge dar. Sie erhalten Zugang zu Codekorrekturen, indem Sie auf das Glühbirnen- bzw. Schraubendrehersymbol klicken oder **STRG+.** oder **ALT+EINGABETASTE** drücken. Jede Korrektur enthält ein Vorschaufenster, das einen Livecodevergleich und die Funktionsweise der Lösung anzeigt.

- Zu gängigen schnellen Problembehebungen und Refactorings zählen Folgende: 
  - *Umbenennen*
  - *Methode extrahieren*
  - *Methodensignatur ändern* 
  - *Konstruktor generieren*
  - *Methode generieren*
  - *Typ in Datei verschieben*
  - *NULL-Überprüfung hinzufügen*
  - *Parameter hinzufügen*
  - *Nicht erforderliche using-Direktiven entfernen*
  - Weitere Informationen finden Sie in unserer [Dokumentation](https://aka.ms/refactorings).
- Schreiben Sie mit [Roslyn-Analysetools](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix) Ihr eigenes Refactoring oder Ihre eigene Codefehlerbehebung. 
- Mehrere Communitymitglieder haben *kostenlose* Erweiterungen geschrieben, die zusätzliche Codeüberprüfungen hinzufügen: 
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refactorings in Visual Studio](../ide/media/VSGuide_CodeAnalysis.png "VSGuide_CodeAnalysis")

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Ich benötige die Features „Find Usages“ (Verwendungen finden), „Gehe zu Implementierung“, „Navigate To Decompiled Assemblies“ (Navigieren zu dekompilierten Assemblys)
Visual Studio 2017 weist viele Features zum Suchen und Navigieren in Ihrer Codebasis auf. Erfahren Sie mehr über die [Features zum Navigieren in Code](../ide/navigating-code.md).

| Feature | Verknüpfung | Details oder Verbesserungen |
|- | - | -| 
| Alle Verweise suchen | **UMSCHALT+F12**| Ergebnisse werden farbig hervorgehoben und können nach Projekt, Definition usw. gruppiert werden. Sie können Ergebnisse auch sperren. |
| Gehe zu Implementierung | **STRG+F12** | Mit „Gehe zu Definition“ für das Schlüsselwort `override` können Sie zum überschriebenen Member navigieren. |
| Gehe zu Definition | **F12** oder **STRG+Klicken**| Sie können bei gedrückter **STRG**-TASTE klicken, um zur Definition zu navigieren. | 
| Peek-Definition | **ALT+F12** | Inlineansicht einer Definition |
| Strukturschnellansicht | Graue, gepunktete Linien zwischen geschweiften Klammern | Zeigen Sie darauf, um Ihre Codestruktur anzuzeigen. |
| Navigation zu dekompilierten Assemblys | **F12** oder **STRG+Klicken** | Navigieren Sie zur externen Quelle (mit ILSpy dekompiliert), indem Sie folgendes Feature aktivieren: **Extras > Optionen > Text-Editor > C# > Erweitert > Navigation zu dekompilierten Quellen aktivieren**. |

![„Gehe zu allen“ und „Alle Verweise suchen“](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Ich möchte meine Komponententests ausführen und anzeigen.
Wir haben bei den Testfunktionen in Visual Studio 2017 viele Verbesserungen vorgenommen. Verwenden Sie eine unserer Unittestoberflächen mit den Testframeworks MSTest v1, MSTest v2, NUnit oder XUnit.
- Die Testermittlung des *Test-Explorers* ist in Version 15.6 schnell. (Führen Sie ein Upgrade auf die neueste Version Ihres Testadapters durch, um optimale Ergebnisse zu erhalten.)
- Organisieren Sie Ihre Tests im Test-Explorer mit unserer neuen *hierarchischen Sortierung* in Version 15.6.
- [Live Unit Testing](../test/live-unit-testing.md) führt laufend Tests aus, die durch Ihre Codeänderungen beeinflusst werden, und aktualisiert Inline-Editor-Symbole, um Sie über den Status Ihres Tests zu informieren. Schließen Sie bestimmte Tests oder Testprojekte in Ihren *aktiven Testsatz* ein oder von diesem aus.

![Hierarchieansicht für den Test-Explorer in Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Ich möchte meinen Code debuggen.
Wir haben Visual Studio 2017 um unzählige neue Funktionen zum Debuggen erweitert. 
- Durch *Ausführung bis Klick* können Sie auf eine Stelle neben einer Codezeile zeigen, auf das angezeigte grüne Wiedergabesymbol klicken und das Programm ausführen, bis es diese Zeile erreicht. 
- Die neue *Ausnahmen-Hilfe* setzt die wichtigsten Informationen (z.B. die als NULL festzulegende Variable in NullReferenceException) auf die oberste Ebene im Dialogfeld.
- Durch Debuggen mit der Funktion [Schritt zurück](../debugger/how-to-use-intellitrace-step-back.md) können Sie zu den vorherigen Breakpoints oder Schritten zurückkehren und den zuvor vorhandenen Status der Anwendung anzeigen.
- Durch [Debuggen von Momentaufnahmen](/azure/application-insights/app-insights-snapshot-debugger) können Sie den Status einer aktiven Webanwendung bei Auslösung einer Ausnahme (muss in Azure erfolgen) untersuchen.

![Neue Ausnahmen-Hilfe in VS2017](../ide/media/VSGuide_Debugging.png "VSGuide_Debugging")

## <a name="i-want-to-use-version-control-with-my-projects"></a>Ich möchte die Versionskontrolle bei meinen Projekten verwenden.
Sie können mithilfe von Git oder der TFVC Ihren Code in Visual Studio speichern und aktualisieren. 
- Organisieren Sie Ihre lokalen Änderungen mit dem *Team Explorer*, und verfolgen Sie ausstehende Commits und Änderungen mit der Statusleiste nach. 
- Richten Sie mit unserer Erweiterung [Continuous Delivery Tools für Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) Continuous Integration und Delivery für Ihre Projekte in Visual Studio ein, und führen Sie den agilen Workflow für Entwickler ein.

![Quellcodeverwaltung in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Welche anderen Features sollte ich kennen?
Hier ist eine Liste an Editor- und Produktivitätsfeatures zum einfacheren Schreiben von Code. Einige Features müssen aktiviert werden, da sie standardmäßig deaktiviert sind (sie indizieren möglicherweise Dinge auf dem Computer, sind kontrovers oder derzeit experimentell).

| Feature | Details | Vorgehensweise zum Aktivieren |
|-|-|-|
| Suchen von Dateien im Projektmappen-Explorer | Markiert die aktive Datei im Projektmappen-Explorer. | **Extras > Optionen > Projekte und Projektmappen > Aktives Element im Projektmappen-Explorer überwachen** |
| Hinzufügen von using-Direktiven für Typen in Referenzassemblys und NuGet-Paketen | Zeigt eine Glühbirne mit einer Codefehlerbehebung zum Installieren eines NuGet-Pakets für einen nicht referenzierten Typ an. | **Extras > Optionen > Text-Editor > C# > Erweitert > using-Direktiven für Typen in Referenzassemblys vorschlagen** und **using-Direktiven für Typen in NuGet-Paketen vorschlagen** |
| Vollständige Projektmappenanalyse aktivieren | Zeigt alle Fehler in der Projektmappe in der Fehlerliste an. | **Extras > Optionen > Text-Editor > C# > Erweitert > Vollständige Projektmappenanalyse aktivieren** |
| Aktivieren der Navigation zu dekompilierten Quellen | Lässt die Aktivierung von „Gehe zu Definition“ für Typen/Member aus externen Quellen zu und verwendet den ILSpy-Decompiler zur Anzeige von Methodentexten. | **Extras > Optionen > Text-Editor > C# > Erweitert > Navigation zu dekompilierten Quellen aktivieren** |
| Vervollständigungs-/Vorschlagsmodus | Ändert das Vervollständigungsverhalten in IntelliSense (Entwickler mit IntelliJ-Hintergründen ändern meist die Einstellung des Standardwerts). | **Menü > Bearbeiten > IntelliSense > Vervollständigungsmodus umschalten** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Zeigt Codereferenzinformationen an und ändert den Änderungsverlauf im Editor. | **Extras > Optionen > Text-Editor > Alle Sprachen > CodeLens** |
| [Codeausschnitte](../ide/visual-csharp-code-snippets.md) | Unterstützt beim Ausdrücken allgemeiner Bausteine. |  Geben Sie einen Codeausschnittnamen ein, und drücken Sie dann zweimal die TAB-TASTE. |

![Codeausschnitte in Visual Studio](../ide/media/VSGuide_SmartEditor.png)

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Fehlt ein Feature, das Ihre Produktivität erhöht oder treten Leistungsprobleme auf?
Es stehen Ihnen verschiedene Feedbackmöglichkeiten zur Verfügung:
- Sie können .NET-Features über unser [GitHub-Repository](https://github.com/dotnet/roslyn/issues) anfordern.
- Visual Studio-Featureanforderungen, Fehler und Leistungsprobleme können mit dem Symbol **Feedback senden** am oberen rechten Rand des Visual Studio-Fensters erfasst werden.
