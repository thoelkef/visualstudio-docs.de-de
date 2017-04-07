---
title: Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 746dd25dde790d5e262e25a3702b49721edc3510
ms.lasthandoff: 03/22/2017

---

# <a name="working-with-python-in-visual-studio"></a>Arbeiten mit Python in Visual Studio

Python ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und für alle Betriebssysteme kostenlos ist und von einer starken Entwicklercommunity und vielen kostenlosen Bibliotheken unterstützt wird. Python unterstützt alle Arten von Entwicklung, einschließlich Webanwendungen, Webdienste, Desktop-Apps, Skripts und wissenschaftliche Berechnungen, und wird von vielen Universitäten, Wissenschaftlern, gelegentlichen und professionellen Entwicklern gleichermaßen verwendet. Weitere Informationen zur Sprache finden Sie unter [python.org](https://www.python.org) und [Python for Beginners](https://www.python.org/about/gettingstarted/).

Visual Studio bietet über die Python-Arbeitsauslastung (Visual Studio 2017) und die kostenlosen Python-Tools für die Visual Studio-Erweiterung (Visual Studio 2015 und früher) [Open-Source](https://github.com/Microsoft/ptvs)-Unterstützung für Python. 

Folgen Sie unseren [Installationsanweisungen](installation.md), um die Python-Arbeitsauslastung einzurichten. Verwenden Sie dann die folgenden Links, um weitere Informationen zu Python-bezogenen Funktionen sowie zu Funktionen von Visual Studio zu erhalten.

| Funktion | Beschreibung | Allgemeine Visual Studio-Dokumentation | 
| --- | --- | --- |
| [Visual Studio-Projektsystem](python-projects.md) | Übernimmt implizit eine Ordnerstruktur des Python-Codes und ermöglicht eine explizite Steuerung, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können. | [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Projektvorlagen](python-projects.md#project-templates) | Erstellt schnell die Projektstruktur für Konsolen-, Internet-, Azure- und Data Science-Projekte und für andere Projekttypen. | [Visual Studio-Vorlagen](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Unterstützung für mehrere Interpreter | Unterstützt verschiedene Versionen von CPython und IronPython. | n/v |
| IPython-Unterstützung | Umfasst Unterstützung für IPython/Jupyter in der REPL für Inlineplots, .NET und Windows Presentation Foundation (WPF). | n/v |
| [Vielfältige Funktionen für die Bearbeitung, IntelliSense und Kennzeichnung von Code](code-editing.md) | Umfasst Syntaxfarben, automatische Vervollständigung über den gesamten Code und allen Bibliotheken hinweg, [Codeformatierung](code-formatting.md), Signaturhilfe, Klassenansicht, „Gehe zu Definition“, „Alle Verweise suchen“, Codeausschnitte, [Refactoring](code-refactoring.md), [PyLint](code-pylint.md) und vieles mehr. | [Schreiben von Code im Code- und Text-Editor](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Interaktives Fenster](interactive-repl.md) | Bietet eine schnelle REPL-Umgebung für Python mit Funktionen, um problemlos einen Teil des Codes zu markieren und an das interaktive Fenster zu senden. | n/v |
| [Vollständige Debugfunktionen](debugging.md) | Debugging kann mit und ohne ein Visual Studio-Projekt ausgeführt werden, einschließlich der Möglichkeit zum Anfügen an eine vorhandene ausführbare Datei, [Python/C++-Debugging im gemischten Modus](debugging-mixed-mode.md), [Remotedebugging](debugging-cross-platform-remote.md) für Windows/Linux/Mac, [Remotedebugging für Azure](debugging-azure-remote.md) und Debugging im interaktiven Fenster. | [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Profilerstellungstools mit umfassender Berichterstellung](profiling.md) | Untersucht, wie Zeit in Ihrer Anwendung aufgewendet wird. Dazu zählt auch die Möglichkeit, die Leistung von verschiedenen Ausführungen der Profilerstellung zu vergleichen. | [Profilerstellungstools](../profiling/profiling-tools.md) (nicht alle Funktionen von Visual Studio-Profilerstellungstools stehen für Python zur Verfügung) |
| [Tools für Unittests](unit-testing.md) | Sie können Tests im Test-Explorer von Visual Studio ermitteln, ausführen und verwalten und Unittests problemlos debuggen. | [Komponententest für Code](../test/unit-test-your-code.md) |

Die Python-Arbeitsauslastung umfasst auch das [Azure SDK für Python](azure-sdk-for-python.md), das die Nutzung von Azure-Diensten mit Unterstützung für Windows, Mac OS X und Linux vereinfacht.

Sehen Sie sich auch unsere Reihe von [Videos mit den ersten Schritten und detaillierten Informationen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) auf YouTube an, um einen Überblick über die wichtigsten Funktionen zu erhalten.

[![Videos zu Python-Tools](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="features-matrix"></a>Funktionsmatrix

Python-Unterstützung kann in den folgenden Editionen von Visual Studio installiert werden, wie im [Installationshandbuch](installation.md) beschrieben:

- [Visual Studio 2017 Preview](https://www.visualstudio.com/vs/preview)
- [Visual Studio 2015 (alle Editionen)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community Edition] (https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)
- [Visual Studio 2013 Express für Web, Update 2 oder höher](http://www.microsoft.com/en-us/download/details.aspx?id=40747)
- [Visual Studio 2013 Express für Desktop, Update 2 oder höher](http://www.microsoft.com/en-us/download/details.aspx?id=40787)
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
| Webbereitstellung auf einer Website | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Webbereitstellung für eine Webrolle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Webbereitstellung für eine Workerrolle | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
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

6. Erfordert mindestens Windows 8. Visual Studio 2013 Express für Web weist kein Dialogfeld „An den Prozess anhängen“ auf. Remotedebuggen für Azure-Websites ist allerdings über den Befehl „Debugger anfügen“ (Python) im Server-Explorer möglich. Dies erfordert das [Azure SDK für .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) oder höher.

7. Erfordert mindestens Windows 8. Für den Befehl „Debugger anfügen“ (Python) im Server-Explorer ist das [Azure SDK für .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) oder höher erforderlich.

8. Erfordert mindestens Windows 8.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

- [Schreiben von Kinect-Spielen mit Python mithilfe von PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub-Wiki)
- [WFastCGI-Brücke zwischen IIS und Python](https://pypi.python.org/pypi/wfastcgi) (python.org)

