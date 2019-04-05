---
title: Neues in Visual Studio 2019
titleSuffix: ''
description: Informationen zu den neuen Features in Visual Studio 2019
ms.date: 04/03/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: b38f75f1172e96e3dc2576a199949fdbb0c32f68
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866743"
---
# <a name="whats-new-in-visual-studio-2019"></a>Neues in Visual Studio 2019

**Für [Release 16.0](/visualstudio/releases/2019/release-notes/) aktualisiert**

>[!div class="button"]
>[Herunterladen von Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

Visual Studio 2019 bietet branchenführende Tools und Dienste für jeden Entwickler, jede App und jede Plattform. Ob Sie Visual Studio zum ersten Mal oder schon seit Jahren nutzen, Sie werden von der neuen Version überzeugt sein.

Im Folgenden erhalten Sie einen allgemeinen Überblick über die Neuheiten:

* **[Entwickeln:](#develop)** Arbeiten Sie fokussiert und effizient mit verbesserter Leistung, sofortiger Codebereinigung und besseren Suchergebnissen.
* **[Zusammenarbeiten:](#collaborate)** Profitieren Sie von intuitiver Zusammenarbeit über einen Cloud-First-Workflow, Bearbeitung und Debuggen in Echtzeit sowie von Code Reviews direkt in Visual Studio.
* **[Debuggen:](#debug)** Heben Sie bestimmte Werte hervor, oder navigieren Sie zu diesen, optimieren Sie die Arbeitsspeichernutzung, und erstellen Sie automatische Momentaufnahmen von der Ausführung Ihrer Anwendung.

Eine ausführliche Liste aller Neuheiten in dieser Version finden Sie in den [Versionshinweisen](/visualstudio/releases/2019/release-notes/). 

## <a name="develop"></a>Entwicklung

Sparen Sie Zeit mit den neuen Features.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Verbesserte Suche

Unsere neue Suche, die bisher als Schnellstart bezeichnet wurde, ist jetzt schneller und effektiver. Suchergebnisse werden jetzt dynamisch während der Eingabe angezeigt. Zudem können in den Suchergebnissen oft Tastenkombinationen für Befehle inbegriffen sein, sodass Sie diese für die zukünftige Verwendung leichter speichern können.

   ![Animation: Die neue Suche in Visual Studio 2019](media/vs-2019/new-search-feature.gif)

Mit der neuen unscharfen Suchlogik finden Sie die gewünschten Ergebnisse, auch wenn Sie sich vertippen. Egal, ob Sie nach Befehlen, Einstellungen, einer Dokumentation oder anderen nützlichen Funktionen suchen: Mithilfe des neuen Suchfeatures finden Sie noch unkomplizierter, wonach Sie suchen.

### <a name="refactorings"></a>Refactorings

Mithilfe der neuen C#-Refactorings wird die Organisation Ihres Codes noch einfacher. Rufen Sie die Refactorings einfach auf, indem Sie **STRG+.** drücken und die Aktion auswählen, die Sie ausführen möchten. 

   ![Animation: Die neuen Refactorings in Visual Studio 2019](media/vs-2019/refactorings.gif)

Viele neue Refactorings wurden hinzugefügt, darunter eines, mit dem Sie Methodenparameter umschließen können.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) ist eine Erweiterung, die Sie bei der Softwareentwicklung mithilfe von künstlicher Intelligenz (KI) unterstützt. IntelliCode trainiert über 2.000 Open Source-Projekte auf GitHub &mdash; jedes mit über 100 Sternen &mdash; zum Generieren von Empfehlungen.

 ![Animation: IntelliCode in Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Im Folgenden werden einige Möglichkeiten aufgeführt, wie Sie mit Visual Studio IntelliCode Ihre Produktivität steigern können:

* Bereitstellen von kontextabhängigen Codevervollständigungen
* Hilfe für Entwickler, sich an die Muster und Konventionen ihres Teams zu halten
* Suche nach schwer auffindbaren Codeproblemen
* Schwerpunkt auf Code Reviews, indem die Aufmerksamkeit auf die wichtigen Bereiche gerichtet wird

Bei der ersten Vorschauversion der IntelliCode-Erweiterung für Visual Studio wurde zunächst nur C# unterstützt. Jetzt wurde in Visual Studio auch Unterstützung für C++ und XAML hinzugefügt.

Und bei Verwendung von C# können Sie jetzt auch ein benutzerdefiniertes Modell für Ihren eigenen Code trainieren.

Weitere Informationen zu IntelliCode finden Sie im Blogbeitrag [Code more, scroll less with Visual Studio IntelliCode (Mehr Code schreiben, weniger scrollen mit Visual Studio IntelliCode)](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/). 

### <a name="code-cleanup"></a>Codebereinigung

Neben einem neuen Integritätsindikator für Dokumente gibt es auch einen neuen Befehl für die Codebereinigung. Mit diesem neuen Befehl können Sie Warnungen und Vorschläge mit nur einem Knopfdruck ermitteln und anschließend beheben bzw. umsetzen.

Bei der Bereinigung wird der Code formatiert, und es werden sämtliche Codekorrekturen vorgenommen, die unter [aktuelle Einstellungen](code-styles-and-quick-actions.md), [EDITORCONFIG-Dateien](create-portable-custom-editor-options.md) oder [Roslyn-Analysetools](../code-quality/roslyn-analyzers-overview.md) vorgeschlagen werden.

   ![Screenshot: Das neue Steuerelement für die Codebereinigung in Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Sie können auch Korrektursammlungen als Profil speichern. Wenn Sie z.B. einige spezielle Korrekturen haben, die Sie beim Programmieren häufig anwenden, und eine weitere umfangreiche Korrektursammlung, die vor einem Code Review angewendet wird, können Sie Profile für diese verschiedenen Aufgaben konfigurieren.

   ![Screenshot: das neue Steuerelement für die Codebereinigung in Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Zusammenarbeiten

Arbeiten Sie im Team, um Probleme zu lösen.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Cloud im Workflow an erster Stelle

Wenn Sie Visual Studio 2019 öffnen, wird Ihnen u.a. das neue Startfenster auffallen.

   ![Screenshot: das neue Startfenster in Visual Studio 2019](media/vs-2019/start-window-dark.png)

Im Startfenster stehen mehrere Optionen zur Verfügung, um schnell zum Code zu gelangen. Die Option zum Klonen oder Auschecken von Code aus einem Repository wird nun als erste dargestellt.  

   ![Animation: Git in Visual Studio 2019 nun an oberster Position](media/vs-2019/git-first.gif)

Im Startfenster gibt es außerdem Optionen zum Öffnen eines Projekts oder einer Projektmappe, zum Öffnen eines lokalen Ordners oder zum Erstellen eines neuen Projekts.

Weitere Informationen finden Sie im Blogbeitrag [Get to code: How we designed the new Visual Studio start window (Entwurf des neuen Visual Studio-Startfensters)](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share:](https://visualstudio.microsoft.com/services/live-share/) ist ein Entwicklerdienst, mit dem Sie eine Codebasis und deren Kontext für ein anderes Teammitglied freigeben können und direkt in Visual Studio eine sofortige bidirektionale Kollaboration erhalten. Mithilfe von Live Share können Ihre Teammitglieder ohne Probleme und auf sichere Weise ein Projekt, das Sie für sie freigegeben haben, lesen, bearbeiten und debuggen sowie darin navigieren.

In Visual Studio 2019 ist dieser Dienst standardmäßig installiert.

![Animation: das Feature „Live Share“ für die Zusammenarbeit in Visual Studio 2019](media/vs-2019/live-share.gif)

Weitere Informationen finden Sie in den Blogbeiträgen [Visual Studio Live Share for real-time code reviews and interactive education (Visual Studio Live Share für Echtzeit-Code Reviews und interaktiven Unterricht)](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) und [Live Share now included with Visual Studio 2019 (Live Share jetzt in Visual Studio 2019 verfügbar)](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/).

### <a name="integrated-code-reviews"></a>Integrierte Code Reviews

Es wurde eine neue Erweiterung eingeführt, die Sie für die Verwendung mit Visual Studio 2019 herunterladen können. Mit dieser neuen Erweiterung können Sie Pull Requests Ihres Teams überprüfen, ausführen und sogar debuggen, ohne Visual Studio verlassen zu müssen. Code wird sowohl in GitHub- als auch in Azure DevOps-Repositorys unterstützt.

   ![Screenshot: das neue Startfenster in Visual Studio 2019](media/vs-2019/pr-experience.png)

Als erste Schritte laden Sie die [Pull Requests für Visual Studio](https://aka.ms/pr4vs)-Erweiterung aus dem Visual Studio Marketplace herunter.

## <a name="debug"></a>Debug

Konzentrieren Sie sich auf präzises, zielgerichtetes Arbeiten.
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Leistungsverbesserungen

Wir haben die Datenbreakpoints, die ursprünglich nur für C++ ausgerichtet waren, nun auch für .NET Core-Anwendungen angepasst.

   ![Animation: Datenbreakpoints für das Debuggen in Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Datenbreakpoints können nun also unabhängig davon, ob Sie in C++ oder in .NET Core programmieren, eine gute Alternative zu regulären Breakpoints darstellen. Datenbreakpoints eignen sich auch ideal für Szenarios wie für die Suche nach der Position, an der ein globales Objekt bearbeitet, hinzugefügt oder aus einer Liste entfernt wird. 

Wenn Sie in C++ große Anwendungen entwickeln, hat Visual Studio 2019 nun außerdem Symbole lokal verfügbar gemacht, mithilfe derer Sie diese Anwendungen debuggen können, ohne dass es zu arbeitsspeicherbezogenen Problemen kommt.

### <a name="search-while-debugging"></a>Suche während des Debuggens

Sie haben sicher schon mal im Überwachungsfenster unter einer Reihe von Werten nach einer Zeichenfolge gesucht. In Visual Studio 2019 haben wir die Suche in den Fenstern „Überwachung“, „Lokal“ und „Auto“ hinzugefügt, damit Sie die Objekte und Werte, nach denen Sie suchen, besser finden können.

   ![Animation: das Fenster für die Suche während des Debuggens in Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Sie können auch formatieren, wie ein Wert in den Fenstern „Überwachung“, „Lokal“ und „Auto“ angezeigt wird.  Doppelklicken Sie in einem Fenster auf eines der Elemente, und fügen Sie ein Komma („,“) hinzu, um auf die Dropdown-Liste der möglichen Formatbezeichner Zugriff zu haben, von denen jeder eine Beschreibung des erwarteten Ergebnisses enthält.

   ![Das neue Überwachungsfenster und das Feature zur Wertformatierung in Visual Studio 2019](media/search-watch-window.png)

Weitere Informationen finden Sie im Blogbeitrag [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows (Erweiterungen in Visual Studio 2019: Suchen nach Objekten und Eigenschaften in den Fenstern „Überwachen“, „Auto“ und „Lokal“)](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="snapshot-debugger"></a>Momentaufnahmedebugger

Sie können eine Momentaufnahme der Ausführung Ihrer App in der Cloud abrufen, um genau zu sehen, was gerade geschieht. (Dieses Feature ist nur in Visual Studio Enterprise verfügbar.)

   ![Animation: der Momentaufnahmedebugger in Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

ASP.NET Core-Anwendungen und Desktopanwendungen, die auf einem virtuellen Azure Computer ausgeführt werden, werden nun unterstützt. Außerdem werden nun Anwendungen unterstützt, die in Azure Kubernetes Service ausgeführt werden. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Weitere Informationen finden Sie unter [Debug live ASP.NET Azure apps using the Snapshot Debugger (Debuggen von ASP.NET-Azure-Live-Apps mithilfe des Momentaufnahmedebuggers)](../debugger/debug-live-azure-applications.md).

## <a name="give-us-feedback"></a>Geben Sie uns Feedback

Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.

* Wenn Sie einen Vorschlag zur Verbesserung von Visual Studio haben, können Sie diesen mithilfe des Tools [Vorschlag senden](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) einreichen.

* Wenn bei Ihnen Hängen, Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien auf einfache Weise mithilfe des Tools [Problem melden](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) mit uns teilen.

## <a name="see-also"></a>Siehe auch

* [Ankündigung von Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Visual Studio 2019 – Versionshinweise](/visualstudio/releases/2019/release-notes/)
* [Neuigkeiten im Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Die Vorschauversion von Visual Studio 2019 für Mac ist jetzt verfügbar.](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Microsoft Connect(); 2018](https://www.microsoft.com/connectevent)
