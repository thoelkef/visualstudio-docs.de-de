---
title: Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 8cd00fe33cf463227dd09f93047350a96cee3b92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-python-in-visual-studio"></a>Arbeiten mit Python in Visual Studio

Python ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und für alle Betriebssysteme kostenlos ist und sowohl von einer starken Entwicklercommunity als auch vielen kostenlosen Bibliotheken unterstützt wird. Python unterstützt alle Arten von Entwicklung, einschließlich Webanwendungen, Webdienste, Desktop-Apps, Skripts und wissenschaftliche Berechnungen, und wird von vielen Universitäten, Wissenschaftlern, gelegentlichen und professionellen Entwicklern gleichermaßen verwendet. Weitere Informationen zur Sprache finden Sie unter [python.org](https://www.python.org) und [Python for Beginners](https://www.python.org/about/gettingstarted/).

Visual Studio auf Windows bietet über die Arbeitsauslastungen „Python-Entwicklung“ und „Data Science“ (Visual Studio 2017) und die kostenlosen Python-Tools für die Visual Studio-Erweiterung (Visual Studio 2015 und früher) [Open-Source](https://github.com/Microsoft/ptvs)-Unterstützung für die Python-Sprache. Python wird gegenwärtig nicht von Visual Studio für Mac unterstützt, ist jedoch auf Mac und Linux über Visual Studio Code verfügbar (Siehe [untenstehende Fragen & Antworten](#questions-and-answers).

Einführung:

- Folgen Sie den [Installationsanweisungen](installation.md), um die Python-Workload einzurichten
- Befolgen Sie eine oder mehrere der Schnellstartanweisungen, um ein Projekt zu erstellen. Falls Sie sich nicht entscheiden können, womit Sie anfangen wollen, beginnen Sie mit [Create a project from a template (Erstellen eines Projekts aus einer Vorlage)](quickstart-02-project-from-template.md).
- Befolgen Sie das Tutorial [Working with Python in Visual Studio (Arbeiten mit Python in Visual Studio)](vs-tutorial-01-01.md) für ein vollständiges End-to-End-Erlebnis.
- Nutzen Sie anschließend die folgenden Links, um Python-bezogene Features und die Funktionen von Visual Studio zu erkunden.

| Funktion | description | Allgemeine Visual Studio-Dokumentation | 
| --- | --- | --- |
| [Visual Studio-Projektsystem](python-projects.md) | Übernimmt implizit eine Ordnerstruktur des Python-Codes und ermöglicht eine explizite Steuerung, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können. | [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Projektvorlagen](python-projects.md#project-templates) | Erstellt schnell die Projektstruktur für Konsolen-, Internet-, Azure- und Data Science-Projekte und für andere Projekttypen. | [Visual Studio-Vorlagen](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Unterstützung für mehrere Interpreter | Unterstützt verschiedene Versionen von CPython und IronPython. | n/v |
| IPython-Unterstützung | Umfasst Unterstützung für IPython/Jupyter in der REPL für Inlineplots, .NET und Windows Presentation Foundation (WPF). | n/v |
| [Vielfältige Funktionen für die Bearbeitung, IntelliSense und Kennzeichnung von Code](code-editing.md) | Umfasst Syntaxfarben, automatische Vervollständigung über den gesamten Code und allen Bibliotheken hinweg, [Codeformatierung](code-formatting.md), Signaturhilfe, Klassenansicht, „Gehe zu Definition“, „Alle Verweise suchen“, Codeausschnitte, [Refactoring](code-refactoring.md), [PyLint](code-pylint.md) und vieles mehr. | [Schreiben von Code im Code- und Text-Editor](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Interaktives Fenster](interactive-repl.md) | Bietet eine schnelle REPL-Umgebung für Python mit Funktionen, um problemlos einen Teil des Codes zu markieren und an das interaktive Fenster zu senden. | n/v |
| [Vollständige Debugfunktionen](debugging.md) | Debugging kann mit und ohne ein Visual Studio-Projekt ausgeführt werden, einschließlich der Möglichkeit zum Debuggen einer vorhandenen ausführbaren Datei, [Python/C++-Debugging im gemischten Modus](debugging-mixed-mode.md), [Remotedebugging](debugging-cross-platform-remote.md) für Windows/Linux/Mac, [Remotedebugging für Azure](debugging-azure-remote.md) und Debugging im interaktiven Fenster. | [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Profilerstellungstools mit umfassender Berichterstellung](profiling.md) | Untersucht, wie Zeit in Ihrer Anwendung aufgewendet wird. Dazu zählt auch die Möglichkeit, die Leistung von verschiedenen Ausführungen der Profilerstellung zu vergleichen. | [Profilerstellungstools](../profiling/profiling-tools.md) (nicht alle Funktionen von Visual Studio-Profilerstellungstools stehen für Python zur Verfügung) |
| [Tools für Unittests](unit-testing.md) | Sie können Tests im Test-Explorer von Visual Studio ermitteln, ausführen und verwalten und Unittests problemlos debuggen. | [Ausführen von Komponententests für Code](../test/unit-test-your-code.md) |

Die Python-Arbeitsauslastung umfasst auch das [Azure SDK für Python](azure-sdk-for-python.md), das die Nutzung von Azure-Diensten aus Windows-, Mac OS X- und Linux-Anwendungen vereinfacht.

Eine Videoeinführung finden Sie unter dem kurzen Kurs [Python Tools for Visual Studio (Python Tools für Visual Studio)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) in der Microsoft Virtual Academy (etwa 22 Minuten lang). 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]


## <a name="questions-and-answers"></a>Fragen und Antworten

**F. Wird Python von Visual Studio für Mac unterstützt?**

A. Noch nicht, obwohl es auf [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac) gefordert wird. Die [Visual Studio für Mac](https://docs.microsoft.com/visualstudio/mac/)-Dokumentation identifiziert die aktuellen Entwicklungstypen, die unterstützt werden. In der Zwischenzeit funktioniert Visual Studio-Code auf Windows, Mac und Linux [problemlos mit Python über die verfügbaren Erweiterungen](https://code.visualstudio.com/docs/languages/python).

**F. Was kann ich verwenden, um die Benutzeroberfläche mit Python zu erstellen?**

A. Das Hauptangebot in diesem Bereich ist das [Qt-Projekt](https://www.qt.io/qt-for-application-development/) mit Bindungen für Python mit dem Namen [PySide (die offizielle Bindung)](http://wiki.qt.io/PySide) (siehe auch [PySide-Downloads](https://download.qt.io/official_releases/pyside/.)) und [PyQt](https://wiki.python.org/moin/PyQt). Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

**F. Kann mit einem Python-Projekt eine eigenständige ausführbare Datei erzeugt werden?**

A. Python ist im Allgemeinen eine interpretierte Sprache, bei der Code nach Bedarf in einer geeigneten, Python-fähigen Umgebung wie Visual Studio und Webservern ausgeführt wird. Visual Studio selbst bietet derzeit keine Möglichkeit, eine eigenständige ausführbare Datei zu erstellen, was im Wesentlichen ein Programm mit einem eingebetteten Python-Interpreter bedeutet. Es gibt jedoch innerhalb der Python-Community verschiedene Möglichkeiten, ausführbare Dateien zu erstellen, wie unter [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben wird. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's Embeddable Zip File (Verwenden der eingebetteten ZIP-Datei von CPython)](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) beschrieben wird.

## <a name="features-matrix"></a>Funktionsmatrix

Python-Unterstützung kann in den folgenden Editionen von Visual Studio installiert werden, wie im [Installationshandbuch](installation.md) beschrieben:

- [Visual Studio 2017 (alle Editionen)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (alle Editionen)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express für Web, Update 2 oder höher
- Visual Studio 2013 Express für Desktop, Update 2 oder höher
- Visual Studio 2013 (Pro-Edition oder höher)
- Visual Studio 2012 (Pro-Edition oder höher)
- Visual Studio 2010 SP1 (Pro-Edition oder höher, .NET 4.5 ist erforderlich)

Unterstützte Funktionen nach Visual Studio-Version und -Edition:

| Python-Unterstützung | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Verwaltung mehrerer Interpreter | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Automatische Erkennung beliebte Interpreter | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Hinzufügen von benutzerdefinierten Interpretern | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Virtuelle Umgebungen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PIP/einfache Installation | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Projektsystem | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Neues Projekt aus vorhandenem Code | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Alle Dateien anzeigen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Quellcodeverwaltung | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Git-Integration | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Bearbeiten | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Syntaxhervorhebung | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Automatische Vervollständigung | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Signaturhilfe | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| QuickInfo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Objektkatalog/Klassenansicht | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Navigationsleiste | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Zur Definition wechseln | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Navigieren zu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Alle Verweise suchen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Automatischer Einzug | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Codeformatierung | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Umgestalten – Umbenennen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Umgestalten – Methode extrahieren | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Umgestalten – Import hinzufügen/entfernen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Interaktives Fenster | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Interaktives Fenster | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython mit Inlinediagrammen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Desktop | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Konsole/Windows-Anwendung | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython WPF (mit XAML-Designer) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython Windows Forms | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Django-Webprojekt | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Bottle-Webprojekt | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Flask-Webprojekt | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Generisches Webprojekt | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Bereitstellung auf einer Website | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Bereitstellung für eine Webrolle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Bereitstellung für eine Workerrolle | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Ausführen im Azure-Emulator | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Remotedebuggen | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Anfügen im Server-Explorer | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Django-Vorlagen | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debuggen | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Automatische Vervollständigung | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Automatische Vervollständigung für CSS und JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Debuggen | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debuggen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debuggen ohne ein Projekt | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debuggen – Anfügen an Bearbeitung | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debuggen im gemischten Modus | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Remotedebuggen (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debuggen im interaktiven Fenster | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Profilerstellung | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilerstellung | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Test | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Test-Explorer | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Test ausführen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Test debuggen | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Git-Unterstützung für VS 2012 steht in den Visual Studio-Tools für die Git-Erweiterung zur Verfügung (verfügbar in der [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c)).

2. Für die Bereitstellung auf der Azure-Website ist das [Azure SDK für .NET 2.1 – VS 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855) erforderlich.  Höhere Versionen unterstützen VS 2010 nicht.

3. Für die Unterstützung von Azure-Webrollen und -Workerrollen ist das [Azure SDK für .NET 2.3 – VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) oder höher erforderlich.

4. Für die Unterstützung von Azure-Webrollen und -Workerrollen ist das [Azure SDK für .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) oder höher erforderlich.

5. Der Django-Vorlagen-Editor in Visual Studio 2013 weist einige bekannte Probleme auf, die durch die Installation von Update 2 gelöst werden.

6. Erfordert mindestens Windows 8. Visual Studio 2013 Express für Web weist kein Dialogfeld „An den Prozess anhängen“ auf. Remotedebuggen für Azure-Websites ist allerdings über den Befehl „Debugger anfügen“ (Python) im Server-Explorer möglich. Remotedebuggen erfordert das [Azure SDK für .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) oder höher.

7. Erfordert mindestens Windows 8. Für den Befehl „Debugger anfügen“ (Python) im Server-Explorer ist das [Azure SDK für .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) oder höher erforderlich.

8. Erfordert mindestens Windows 8.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

- [Schreiben von Kinect-Spielen mit Python mithilfe von PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub-Wiki)
- [WFastCGI-Brücke zwischen IIS und Python](https://pypi.python.org/pypi/wfastcgi) (python.org)
- [Kostenlose Python-Kurse in der Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy (Meistgestellte Fragen an der Microsoft Virtual Academy)](https://aka.ms/mva-top-python-questions)
