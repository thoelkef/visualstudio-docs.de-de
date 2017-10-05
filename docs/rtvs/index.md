---
title: "R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="working-with-r-in-visual-studio"></a>Arbeiten mit R in Visual Studio

R ist eine hochgradig erweiterbare Sprache und Umgebung für die statistische Berechnungen und Grafiken. Die Sprache wird kostenlos unter der GNU General Public License (GNU GPL) bereitgestellt, wird von einer starken Community unterstützt und ist für ihre Fähigkeit bekannt, hochwertige Plots einschließlich mathematischer Symbole und Formeln zu erzeugen. Weitere Informationen zu R erhalten Sie unter [r-project.org](https://www.r-project.org/about.html) und [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Einführung in R).

R Tools für Visual Studio (RTVS) ist eine kostenlose [Open Source](https://github.com/microsoft/RTVS)-Erweiterung für Visual Studio 2017 und Visual Studio 2015 Update 3 (oder höher) und wurde unter der MIT-Lizenz veröffentlicht. (Eine zweite Open Source-Komponente namens [RHost](https://github.com/microsoft/R-Host), die eine Verknüpfung mit den Binärdateien des R-Interpreters bietet, wurde unter der GNU Public License V2 veröffentlicht.)

Gehen Sie folgendermaßen vor, um mit R in Visual Studio zu arbeiten:

- [Installieren Sie die R Tools](installation.md).
- Lesen Sie den Leitfaden [Erste Schritte](getting-started-with-r.md) sowie die Themen [Beispiele](getting-started-samples.md) und [Hilfe](getting-started-help.md).

Folgen Sie anschließend den Links, um mehr über R-Funktionen sowie über die allgemeinen Features von Visual Studio selbst zu erfahren.

| Funktion | Beschreibung | Allgemeine Visual Studio-Dokumentation | 
| --- | --- | --- |
| [Visual Studio-Projektsystem](projects.md) | Organisieren und verwalten Sie verknüpfte Dateien in einer praktischen Struktur, und profitieren Sie von nützlichen Vorlagen für Elemente wie R-Code, R-Dokumentation, R Markdown, SQL-Abfragen und gespeicherte Prozeduren. Nutzen Sie zudem den [Paket-Manager](package-manager.md) und die [SQL Server-Integration](sql-server.md).  | [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Arbeitsbereich](workspaces.md) | RTVS kann in lokale und Remotearbeitsbereiche eingebunden werden – so können Sie R-Code lokal mit kleineren Datasets entwickeln, den Code dann auf leistungsfähigeren cloudbasierten Computern mit wesentlich größeren Datasets ausführen. | n/v |
| [Optionen für R Tools](options.md) | Steuern Sie verschiedene Aspekte von RTVS. | [Dialogfeld „Optionen“](../ide/reference/options-dialog-box-visual-studio.md) |
| [Vielfältige Bearbeitungsfunktionen, IntelliSense und Codeausschnitte](code-editing.md) | Umfasst Syntaxfarben, [IntelliSense](code-intellisense.md) über den gesamten Code und allen Bibliotheken hinweg, Codeformatierung, Signaturhilfe, „Gehe zu Definition“, „Alle Verweise suchen“, [Codeausschnitte](code-snippets.md) und vieles mehr. | [Schreiben von Code im Code- und Text-Editor](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | Mit R Markdown-Dokumenten können Sie Ihre Datenergebnisse mit integriertem R-Code in Markdowncodeblöcken freigeben. | n/v |
| [Interaktives Fenster](interactive-repl.md) | Dieses Fenster bietet eine vollständige REPL-Oberfläche für R, mit der Sie Code in einer Quelldatei im interaktiven Fenster ausführen können. | n/v |
| [Visualisieren von Daten](visualizing-data.md) | Plotting ist ein wesentlicher Bestandteil von R, und RTVS unterstützt mehrere, voneinander unabhängige Plotfenster. Jedes Fenster bietet einen eigenen Verlauf, und Sie können Plots zwischen Fenstern verschieben. Plots können in Bitmap- und PDF-Dateien gespeichert oder als Bitmap- oder Metadatei in die Zwischenablage kopiert werden.  | n/v |
| [Variablen-Explorer](variable-explorer.md) | Untersuchen Sie Variablen auf globaler oder paketspezifischer Ebene, zeigen Sie sortierbare Tabellen an, und exportieren Sie diese in das CSV-Format. | n/v |
| [Vollständige Debugfunktionen](debugging.md) | Umfasst die Integration in das interaktive Fenster. | [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md) |

Das folgende Video (5 Min., 48 Sek.) zeigt eine kurze Übersicht über die Funktionen der R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen (FAQs)

**F. Funktioniert RTVS mit Visual Studio Express-Editionen?**

A. Nein.

**F. Mit welchen R-Interpretern arbeitet RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client und Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**F. Wo kann ich diese Interpreter herunterladen?**

A. Informationen hierzu finden Sie unter [Installation](installation.md).

**F. Kann ich Visual Studio-Erweiterungen mit RTVS verwenden?**

A. Unbedingt. Die folgenden Erweiterungen beispielsweise sind bei Benutzern sehr beliebt, die mit R arbeiten.

- [VsVim für Vim-Schlüsselbindungen](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Markdown-Editor mit Livevorschau](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Noch mehr Erweiterungen finden Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**F. Bedeutet die Tatsache, dass RTVS in Visual Studio integriert ist, dass R problemlos mit C#, C++ und anderen Microsoft-Sprachen eingesetzt werden kann?**

A. Nein. RTVS ist ein Tool für die Entwicklung von R-Code und verwendet die standardmäßigen nativen R-Interpreter. Zurzeit wird die Interoperabilität zwischen R und anderen Sprachen nicht unterstützt.

**F. Ich vermisse ein bestimmtes Feature, das in RStudio vorhanden ist!**

A. RStudio ist eine fantastische, ausgereifte IDE für R, die bereits seit vielen Jahren weiterentwickelt wird. Wir versuchen, alle wichtigen Funktionen, die Sie für eine erfolgreiche Entwicklung benötigen, in RTVS bereitzustellen. Unterstützen Sie uns dabei, indem Sie an der [RTVS-Umfrage](https://www.surveymonkey.com/r/RTVS1) teilnehmen.

**F. Funktioniert RTVS unter OS X oder Linux?**

A. Nein, RTVS setzt auf Visual Studio auf – eine reine Windows-Implementierung. Microsoft arbeitet allerdings an einem neuen Toolsatz, der auf [Visual Studio Code](https://code.visualstudio.com/) basiert – dem beliebten Plattform-Editor von Microsoft.

**F. Kann ich zu RTVS beitragen?**

A. Auf jeden Fall! Der Quellcode befindet sich auf [GitHub](https://github.com/microsoft/RTVS). Unter „Issues“ können Sie Bugs melden und bereits vorhandene Dateien kommentieren.

Wir freuen uns auch, wenn Sie zur Dokumentation beitragen&mdash;wählen Sie einfach den Befehl **Edit** (Bearbeiten) rechts oben auf jeder Seite in GitHub. Kommentare zu den Dokumenten sind ebenfalls gern gesehen – diese können Sie unten auf jeder Seite einfügen.

**F. Funktioniert RTVS mit meinem System für die Quellcodeverwaltung?**

A. Ja, Sie können jedes Quellcodeverwaltungssystem verwenden, das in Visual Studio integriert ist.

**F. Funktioniert RTVS mit einem nicht englischen Gebietsschema?**

A. Release 1.0 von RTVS ist nur auf Englisch verfügbar. Release 1.1 wird in die gleichen Sprachen lokalisiert wie Visual Studio selbst. Verwenden Sie in der Zwischenzeit das [Visual Studio 2015-Sprachpaket für Englisch](https://www.microsoft.com/download/details.aspx?id=48157), oder führen Sie in Visual Studio 2017 das Installationsprogramm aus und wählen auf der Registerkarte **Sprachpakete** Englisch aus.

![Internationale Einstellungen für Visual Studio 2017](media/FAQ-international-settings.png)

**F. Funktioniert RTVS mit 32-Bit-Editionen von R?**

A. Nein. RTVS unterstützt nur 64-Bit-Editionen von R, die auf 64-Bit-Editionen von Windows ausgeführt werden.

**F. Ich finde meine aktuellen Visual Studio-Einstellungen super, möchte aber auch die neuen Data Science-Einstellungen ausprobieren. Wie gehe ich vor?**

A. Speichern Sie Ihre aktuellen Visual Studio-Einstellungen mithilfe von **Tools > Einstellungen importieren und exportieren...**, und wechseln Sie dann zu den Data Science-Einstellungen. Um die gespeicherten Einstellungen wiederherzustellen, verwenden Sie erneut den Befehl **Einstellungen importieren und exportieren...**.

**F. Wie lauten die empfohlenen `.gitignore`-Einstellungen für ein RTVS-Projekt?**

A. GitHub verwaltet ein Masterrepository mit empfohlenen `.gitignore`-Dateien. Dieses finden Sie hier: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore).

**F. Kann ich mein Visual Studio-Projekt auf einer Netzwerkfreigabe speichern?**

A. Nein, Visual Studio unterstützt nicht das Laden von Projekten aus einer Netzwerkfreigabe.

## <a name="send-us-your-feedback"></a>Senden Sie uns Ihr Feedback!

1. **GitHub-Probleme**: Sie erreichen das RTVS-Team am besten, indem Sie ein [Problem auf GitHub melden](https://github.com/Microsoft/RTVS/issues) oder das Menü **R Tools > Feedback** verwenden.

1. **Ein Lächeln oder ein Stirnrunzeln senden**: Das Menü **R Tools > Feedback** bietet eine schnelle Möglichkeit, Feedback zu senden und RTVS-Protokolldateien anzufügen, die bei der Diagnose Ihres Problems helfen können. (Protokolle werden in `%temp%/RTVSlogs.zip` geschrieben, falls Sie sie separat senden möchten.) Die Protokollierung ist deaktiviert, falls Sie die Visual Studio-Telemetrie über den Menübefehl **Hilfe > Feedback > Einstellungen** oder während der Installation deaktiviert haben.

1. **E-Mail**: Sie können unter *rtvsuserfeedback (at) microsoft.com* direktes Feedback an das Team senden.

