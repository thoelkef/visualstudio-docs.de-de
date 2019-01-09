---
title: Neues in der Vorschauversion von Visual Studio 2019
titleSuffix: ''
description: Informationen zu den neuen Features in der Vorschauversion von Visual Studio 2019
ms.date: 12/19/2018
ms.prod: visual-studio-dev16
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e387485d2a11867944e980a9bad26261fd4a707c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848547"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Neues in der Vorschauversion von Visual Studio 2019

**Aktualisiert für das [Release 16.0 Vorschauversion 1](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

Die Vorschauversion von Visual Studio 2019 enthält viele allgemeine Verbesserungen und neue Features, die Entwicklerproduktivität und Zusammenarbeit im Team optimieren. Egal, ob Sie Visual Studio zum ersten Mal verwenden oder schon seit Jahren: Sie können die Features für alle Aspekte des Entwicklungslebenszyklus nutzen &mdash; von der vereinfachten Projekterstellung und der Verwaltung der Codeintegrität bis hin zu kollaborativen Team- und Open-Source-Workflows.

Im Folgenden finden Sie eine allgemeine Zusammenfassung der Funktionen von Visual Studio:

* **[Persönliche Produktivität und Teamproduktivität](#personal-and-team-productivity)**. Produktivität für sämtliche Benutzer, bei denen dies am wichtigsten ist.
* **[Unterstützung für moderne Entwicklung](#modern-development-support)**. Unterstützung für Ihre aktuellen Projekte und zukünftige Lösungen.
* **[Ständige Innovation](#continuous-innovation)**. Code mit intelligenter, cloudbasierter Unterstützung.

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in der Vorschauversion von Visual Studio 2019 finden Sie in den [Versionshinweisen](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017).

## <a name="personal-and-team-productivity"></a>Persönliche Produktivität und Teamproduktivität

Natürlich haben Leistungsverbesserungen bei jedem Release von Visual Studio immer Priorität. Verbesserungen der Produktivität haben jedoch auch einen hohen Stellenwert. Im Folgenden erfahren Sie, wie wir dabei helfen können.

### <a name="new-start-window"></a>Neues Startfenster

Wenn Sie Visual Studio 2019 öffnen, wird Ihnen zuerst das neue Startfenster auffallen.

   ![Das neue Startfenster in Visual Studio 2019](../ide/media/start-window.png)

Diese neue Startfenster bietet Ihnen Optionen zum Klonen oder Auschecken von Code, zum Öffnen eines Projekts oder einer Projektmappe, zum Öffnen eines lokalen Ordners oder zum Erstellen eines neuen Projekts. Durch die Darstellung dieser Optionen in einem einfache Dialogfeld können Beginner und fortgeschrittene Benutzer von Visual Studio ohne großen Aufwand Code abrufen.

Weitere Informationen finden Sie im Blogbeitrag [Get to code: How we designed the new Visual Studio start window (Entwurf des neuen Visual Studio-Startfensters)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/).

### <a name="better-search"></a>Bessere Suchergebnisse

Unsere neue Suche, die bisher als Schnellstart bezeichnet wurde, ist jetzt schneller und effektiver. Suchergebnisse werden jetzt dynamisch während der Eingabe angezeigt. Zudem sind in den Suchergebnissen Tastenkombinationen für Befehle inbegriffen, sodass Sie diese für die zukünftige Verwendung leichter speichern können.

   ![Das neue Suchfeature in Visual Studio 2019](../ide/media/search-feature.png)

Egal, ob Sie nach Befehlen, Einstellungen, Dokumentation oder anderen nützlichen Dingen suchen: Mithilfe des neuen Suchfeatures finden Sie schneller, wonach Sie suchen.

### <a name="one-click-code-cleanup"></a>Codebereinigung mit nur einem Klick

Neben einem neuen Integritätsindikator für Dokumente gibt es auch einen neuen Befehl für die Codebereinigung. Mit diesem neuen Befehl können Sie Warnungen und Vorschläge mit nur einem Knopfdruck ermitteln und anschließend beheben bzw. umsetzen.

   ![Das neue Feature für die Codebereinigung in Visual Studio 2019](../ide/media/code-cleanup.png)

Bei der Bereinigung wird der Code formatiert, und es werden sämtliche Codekorrekturen vorgenommen, die unter [aktuelle Einstellungen](../ide/code-styles-and-quick-actions.md), [EDITORCONFIG-Dateien](../ide/create-portable-custom-editor-options.md) oder [Roslyn-Analysetools](../code-quality/roslyn-analyzers-overview.md) vorgeschlagen werden.

### <a name="debugger-improvements"></a>Debugger-Verbesserungen

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Suche in einem Überwachungsfenster und Formatieren von Überwachungswerten

Sie haben sicher schon mal im Überwachungsfenster unter einer Reihe von Werten nach einer Zeichenfolge gesucht. In der Vorschauversion von Visual Studio 2019 haben wir die Suche in den Fenstern „Überwachung“, „Lokal“ und „Auto“ hinzugefügt, damit Sie die Objekte und Werte, nach denen Sie suchen, besser finden können.

Sie können auch formatieren, wie ein Wert in den Fenstern „Überwachung“, „Lokal“ und „Auto“ angezeigt wird.  Doppelklicken Sie in einem Fenster auf eines der Elemente, und fügen Sie ein Komma („,“) hinzu, um auf die Dropdown-Liste der möglichen Formatbezeichner Zugriff zu haben, von denen jeder eine Beschreibung des erwarteten Ergebnisses enthält.

   ![Das neue Überwachungsfenster und das Feature zur Wertformatierung in Visual Studio 2019](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) ist ein Entwicklerdienst, mit dem Sie eine Codebasis und deren Kontext für ein anderes Teammitglied freigeben können und direkt in Visual Studio eine sofortige bidirektionale Kollaboration erhalten. Mithilfe von Live Share können Ihre Teammitglieder ohne Probleme und auf sichere Weise ein Projekt, das Sie für sie freigegeben haben, lesen, bearbeiten und debuggen sowie darin navigieren.

In der Vorschauversion von Visual Studio 2019 ist dieser Dienst standardmäßig installiert.

Weitere Informationen finden Sie im Blogbeitrag [Visual Studio Live Share for real-time code reviews and interactive education (Visual Studio Live Share für Echtzeit-Code Reviews und interaktiven Unterricht)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/).

## <a name="modern-development-support"></a>Unterstützung für moderne Entwicklung

### <a name="manage-pull-requests-prs-from-the-ide"></a>Verwalten von Pull Requests (PRs) über die IDE

Es wurde eine neue Erweiterung eingeführt, die Sie für die Verwendung mit der Vorschauversion von Visual Studio 2019 herunterladen können. Mit dieser neuen Erweiterung können Sie Pull Requests Ihres Teams überprüfen, ausführen und sogar debuggen, ohne die Visual Studio IDE [(Integrated Development Environment, integrierte Entwicklungsumgebung)](../get-started/visual-studio-ide.md) verlassen zu müssen. Aktuell wird Code in Azure Repos unterstützt. Es wird jedoch eine Erweiterung auf die Unterstützung von GitHub durchgeführt. Zudem wird die Benutzerfreundlichkeit insgesamt verbessert.

Als erste Schritte laden Sie die [Pull Requests für Visual Studio](https://aka.ms/pr4vs)-Erweiterung aus dem Visual Studio Marketplace herunter.

### <a name="develop-with-net-core-3-preview-1"></a>Entwickeln mit .NET Core 3 Vorschauversion 1

Die Vorschauversion von Visual Studio 2019 unterstützt die Erstellung von [.NET Core 3](http://aka.ms/netcore3preview1)-Anwendungen für beliebige Plattformen. Die plattformübergreifende C++-Entwicklung wird weiterhin unterstützt und verbessert, ebenso wie die mobile .NET-Entwicklung für iOS und Android mit Xamarin.

   ![Entwickeln von Apps mit .NET Core 3 Vorschauversion 1 in Visual Studio 2019](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>Ständige Innovation

### <a name="per-monitor-aware-pma-rendering"></a>PMA-Rendering (PMA = Per-Monitor Aware)

Wenn Sie Monitore verwenden, die mit unterschiedlichen Anzeigeskalierungsfaktoren konfiguriert sind, oder eine Remoteverbindung mit einem Computer herstellen, bei dem die Anzeigeskalierungsfaktoren von denen auf Ihrem Hauptgerät abweichen, werden Sie vielleicht feststellen, dass Visual Studio unscharf aussieht oder bei der falschen Skalierung gerendert wird.

Mit dem Release der Vorschauversion 1 von Visual Studio 2019 werden die ersten Schritte unternommen, mit denen Visual Studio zu einer PMA-fähigen Anwendung wird. Es wird die Grundlage dafür geschaffen, dass Visual Studio unabhängig von den verwendeten Anzeigeskalierungsfaktoren korrekt gerendert wird.

   ![PMA-Rendering (PMA = Per-Monitor Aware) in Visual Studio 2019](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) ist eine Erweiterung, die Ihre Bemühungen bei der Softwareentwicklung mithilfe von künstlicher Intelligenz (KI) verbessert. IntelliCode trainiert über 2.000 Open Source-Projekte auf GitHub &mdash; jedes mit über 100 Sternen &mdash; zum Generieren von Empfehlungen.

Im Folgenden werden einige Möglichkeiten aufgeführt, wie Sie mit Visual Studio IntelliCode Ihre Produktivität steigern können:

* Bereitstellen von kontextabhängigen Codevervollständigungen
* Hilfe für Entwickler, sich an die Muster und Konventionen ihres Teams zu halten
* Suche nach schwer auffindbaren Codeproblemen
* Schwerpunkt auf Code Reviews, indem die Aufmerksamkeit auf die wichtigen Bereiche gerichtet wird

Bei der ersten Vorschauversion der IntelliCode-Erweiterung für Visual Studio wurde zunächst nur C# unterstützt. Jetzt wurde in Visual Studio auch Unterstützung für C++ und XAML hinzugefügt.

Und bei Verwendung von C# können Sie jetzt auch ein benutzerdefiniertes Modell für Ihren eigenen Code trainieren.

Weitere Informationen zu den neuesten Updates finden Sie im Blogbeitrag [Visual Studio IntelliCode supports more languages and learns from your code (Visual Studio IntelliCode unterstützt weitere Sprachen und lernt von Ihrem Code)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/). Weitere Informationen zur Erweiterung und zum Herunterladen der Erweiterung finden Sie auf der Seite [Visual Studio IntelliCode – Preview (Visual Studio IntelliCode (Vorschauversion))](https://go.microsoft.com/fwlink/?linkid=872707) in Microsoft DevLabs.

## <a name="give-us-feedback"></a>Geben Sie uns Feedback

Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.

* Wenn Sie einen Vorschlag zur Verbesserung von Visual Studio haben, können Sie diesen mithilfe des Tools [Vorschlag senden](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) einreichen.

* Wenn bei Ihnen Hängen, Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien auf einfache Weise mithilfe des Tools [Problem melden](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) mit uns teilen.

## <a name="see-also"></a>Siehe auch

* [Visual Studio 2019 – Versionshinweise](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); 2018 conference (Microsoft Connect(); 2018-Konferenz)](https://www.microsoft.com/connectevent)
* [Neuerungen in Visual Studio 2017](whats-new-in-visual-studio.md)
