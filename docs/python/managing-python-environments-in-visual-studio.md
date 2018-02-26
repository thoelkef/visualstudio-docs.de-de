---
title: Verwalten von Python-Umgebungen in Visual Studio | Microsoft-Dokumentation
description: "Erfahren Sie, wie über das Fenster „Python-Umgebungen“ in Visual Studio globale und virtuelle Umgebungen verwaltet, benutzerdefinierte Umgebungen eingerichtet, Python-Interpreter und Pakete installiert, Suchpfade festgelegt und Umgebungen für Visual Studio-Projekte verwaltet werden."
ms.custom: 
ms.date: 02/13/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6abf950f7af86bf65b14752bd1cd9df4a6e292e5
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="python-environments"></a>Python-Umgebungen

Eine Python-*Umgebung* ist ein Kontext, in dem Python-Code ausgeführt wird. Eine Umgebung besteht aus einem Interpreter, einer Bibliothek (in der Regel die Python-Standardbibliothek) und mehreren installierten Paketen. Diese Komponenten bestimmen gemeinsam, welche Sprachkonstrukte und Syntax gültig sind, auf welche Betriebssystemfunktionen Sie zugreifen können und welche Pakete Sie verwenden können.

Wie in diesem Artikel beschrieben, können Sie in Visual Studio all Ihre Umgebungen im [Fenster Python-Umgebungen](#managing-python-environments-in-visual-studio) verwalten. Für jedes verfügbare Projekt können Sie eine Umgebung zum Ausführen von Code, Debuggen, Überprüfen der Syntax, Anzeigen der Import- und Membervervollständigung und Ausführen von anderen Aufgaben, die für spezifische Interpreter und installierte Bibliotheken gelten, aussuchen. Visual Studio verwaltet eine IntelliSense-Datenbank für jede Umgebung, die automatische Vervollständigung beim Eingeben von Code bereitstellt.

Visual Studio bietet auch Unterstützung für virtuelle Umgebungen, `requirements.txt`-Dateien und Suchpfade.

**Hinweis**: Wenn Sie noch nicht mit Python in Visual Studio vertraut sind, finden Sie das erforderliche Hintergrundwissen in den folgenden Artikeln:

- [Arbeiten mit Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installieren von Python-Unterstützung für Visual Studio](installing-python-support-in-visual-studio.md)

## <a name="global-and-virtual-environments"></a>Globale und virtuelle Umgebungen

Es gibt zwei Arten von Python-Umgebungen: globale und virtuelle Umgebungen.

**Globale Umgebungen**: Jede Python-Installation (z.B. Python 2.7, Python 3.6 und Anaconda 4.4.0, siehe [Auswählen und Installieren von Python-Interpretern](#selecting-and-installing-python-interpreters)) verwaltet ihre eigene Umgebung. Jede Umgebung besteht aus dem spezifischen Python-Interpreter, einer Standardbibliothek und einer Reihe von vorinstallierten Paketen. Das Installieren eines Pakets in einer globalen Umgebung macht das Paket für alle Projekte verfügbar, die dieselbe Umgebung verwenden. Wenn sich die Umgebung in einem geschützten Bereich des Dateisystems befindet (z.B. in `c:\program files`), sind für die Installation von Paketen Administratorrechte erforderlich.

Globale Umgebungen sind für alle Projekte auf dem Computer verfügbar. Wählen Sie in Visual Studio eine globale Umgebung als Standardumgebung aus, die für alle Projekte genutzt wird, wenn Sie keine spezifische Umgebung für ein Projekt aussuchen. Weitere Informationen finden Sie unter [Auswählen einer Umgebung für ein Projekt](#selecting-an-environment-for-a-project).

**Virtuelle Umgebungen**: Da in einer globalen Umgebung installierte Pakete für alle Projekte verfügbar sind, die diese Umgebung verwenden, können Konflikte auftreten, wenn zwei Projekte inkompatible Pakete oder verschiedene Versionen des gleichen Pakets erfordern. Virtuelle Umgebungen umgehen diese Konflikte, indem sie den Interpreter und die Standardbibliothek einer globalen Umgebung verwenden, dabei aber ihre eigenen Pakete in isolierten Ordnern speichern und verwalten.

Sie können in Visual Studio eine virtuelle Umgebung für ein spezifisches Projekt erstellen, die in einem Unterordner des Projekts gespeichert wird (siehe [Erstellen von virtuellen Umgebungen](#creating-virtual-environments)). Die Projektdatei identifiziert auch die virtuelle Umgebung. Sämtliche Pakete, die Sie in der virtuellen Umgebung installieren, werden von Visual Studio in der `requirements.txt`-Datei des Projekts aufgezeichnet. Wenn Sie das Projekt anschließend teilen und andere Entwickler es auf ihren Computern öffnen, bietet Visual Studio die Option, die virtuelle Umgebung neu zu erstellen.

### <a name="selecting-and-installing-python-interpreters"></a>Auswählen und Installieren von Python-Interpretern

Bei der Installation der Workload für die Python-Entwicklung in Visual Studio 2017 wird standardmäßig auch Python 3 (64-Bit) installiert. Optional können Sie auch die 32-Bit- und 64-Bit-Versionen von Python 2, Python 3, Anaconda 2 und Anaconda 3 installieren, wie unter [Installation](installing-python-support-in-visual-studio.md) beschrieben. Sie können die in der folgenden Tabelle aufgelisteten Interpreter auch manuell installieren, diese werden dann von Visual Studio erkannt. (Wenn Sie beispielsweise Anaconda 3 vor Visual Studio installiert haben, ist keine erneute Installation über den Visual Studio-Installer erforderlich.)

Für Visual Studio 2015 und frühere Versionen müssen Sie einen der Interpreter manuell installieren.

Visual Studio (alle Versionen) erstellt automatisch für jeden installierten Python-Interpreter eine Umgebung durch Überprüfen der Registrierung (gemäß den Angaben unter [PEP 514 - Python registration in the Windows registry [PEP 514 – Registrieren von Python in der Windows-Registrierung]](https://www.python.org/dev/peps/pep-0514/)). Wenn Visual Studio keine installierte Umgebung findet, folgen Sie den Anweisungen unter [Erstellen einer Umgebung für einen vorhandenen Interpreter](#creating-an-environment-for-an-existing-interpreter).

| Interpreter | Beschreibung |
| --- | --- |
| [CPython](https://www.python.org/) | Der „native“ und am häufigsten verwendete Interpreter, verfügbar in 32- und 64-Bit-Versionen (32-Bit wird empfohlen). Er umfasst die neuesten Sprachfeatures, die maximale Python-Paketkompatibilität, vollständige Unterstützung für das Debuggen und Interoperabilität mit [IPython](http://ipython.org/). Siehe auch: [Should I use Python 2 or Python 3? (Sollte ich Python 2 oder Python 3 verwenden?)](http://wiki.python.org/moin/Python2orPython3). Beachten Sie, dass Visual Studio 2015 und frühere Versionen Python 3.6 nicht unterstützen, und den Fehler „Unsupported python version 3.6“ (Nicht unterstützte Python-Version 3.6) ausgeben können. Verwenden Sie stattdessen Python 3.5 oder frühere Versionen. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Eine .NET-Implementierung von Python, verfügbar in 32-Bit- und 64-Bit-Versionen, die C#-/F#-/Visual Basic-Interoperabilität, Zugriff auf .NET APIs, Python-Standarddebuggen (jedoch kein C++-Debuggen im gemischten Modus) und IronPython-/C#-Debuggen im gemischten Modus bietet. IronPython unterstützt jedoch keine virtuelle Umgebungen. |
| [Anaconda](https://www.continuum.io) | Eine offene Data Science-Plattform, die von Python unterstützt wird und die neueste Version von CPython sowie die meisten der nicht leicht zu installierenden Pakete enthält. Wir empfehlen diesen Interpreter, wenn keine andere Entscheidung möglich ist. |
| [PyPy](http://www.pypy.org/) | Eine leistungsstarke JIT-Implementierung für die Ablaufverfolgung von Python, die gut für Programme mit langer Ausführungszeit und Situationen, in denen Sie Leistungsprobleme identifizieren, jedoch keine anderen Lösungen finden können, geeignet ist. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |
| [Jython](http://www.jython.org/) | Eine Implementierung von Python auf der Java Virtual Machine (JVM). Ähnlich wie bei IronPython kann in Jython ausgeführter Code mit Java-Klassen und -Bibliotheken interagieren, aber möglicherweise viele für CPython vorgesehene Bibliotheken nicht verwenden. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |

Wenn Sie als Entwickler neue Formen der Erkennung für Python-Umgebungen bereitstellen möchten, finden Sie unter [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (PTVS-Umgebungserkennung, github.com) weitere Informationen.

## <a name="managing-python-environments-in-visual-studio"></a>Verwalten von Python-Umgebungen in Visual Studio

Wählen Sie den Menübefehl **Ansicht > Weitere Fenster > Python-Umgebungen** aus, oder führen Sie einen Rechtsklick auf den Knoten **Python-Umgebungen** für ein Projekt im Projektmappen-Explorer aus, und klicken Sie auf **Alle Python-Umgebungen anzeigen**:

    ![View All Environments command in Solution Explorer](media/environments-view-all.png)

In jedem Fall wird das Fenster „Python-Umgebungen“ als gleichgeordnete Registerkarte des Projektmappen-Explorers angezeigt:

![Fenster „Python-Umgebungen“](media/environments-default-view.png)

Im Beispiel oben wird Python 3.4 (32-Bit-CPython) zusammen mit den 32-Bit- und 64-Bit-Versionen von IronPython 2.7 installiert. Die fettgedruckte Standardumgebung Python 3.4, die für alle neuen Projekte verwendet wird. Wenn keine Umgebungen angezeigt werden, bedeutet dies, dass Sie Python-Tools für Visual Studio in Visual Studio 2015 oder früher installiert haben, aber noch keinen Python-Interpreter (siehe [Auswählen und Installieren von Python-Interpretern](#selecting-and-installing-python-interpreters) oben). Der Befehl **+ Benutzerdefiniert** erlaubt Ihnen das [Erstellen einer Umgebung für einen vorhandenen Interpreter](#create-an-environment-for-an-existing-interpreter).

> [!Tip]
> Visual Studio erkennt Updates auf einen vorhandenen Interpreter, z.B. ein Upgrade von Python 2.7.11 auf 2.7.14 mit den Installationsprogrammen von python.org. Während des Installationsvorgangs wird die ältere Umgebung aus der Liste der **Python-Umgebungen** entfernt und dann durch das Update ersetzt.

Rechts neben jeder aufgelisteten Umgebung befindet sich ein Steuerelement, das ein interaktives Fenster für die jeweilige Umgebung öffnet. Möglicherweise wird ein weiteres Steuerelement angezeigt, das die IntelliSense-Datenbank der jeweiligen Umgebung aktualisiert.

Unter der Liste der Umgebungen befindet sich eine Dropdownauswahl für die Optionen **Übersicht**, **Pakete** und **IntelliSense**, die weiter unten in diesem Abschnitt beschrieben werden. Wenn Sie das Fenster **Python-Umgebungen** weit genug erweitern, werden diese Optionen als Registerkarten angezeigt, was Ihre Arbeit damit erleichtern kann:

![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments-expanded-view.png)

> [!Note]
> Obwohl Visual Studio die Option „system-site-packages“ beachtet, gibt es keine Möglichkeit, sie in Visual Studio zu ändern.

|   |   |
|---|---|
| ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen") | [Sehen Sie sich ein Video (Microsoft Virtual Academy](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) zu Python-Umgebungen in Visual Studio an (2 Minuten, 35 Sekunden).|

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Erstellen eine Umgebung für einen vorhandenen Interpreter

Wenn Visual Studio keinen Interpreter findet (wenn er beispielsweise an einem Speicherort installiert ist, der nicht dem Standard entspricht), können Sie wie folgt eine Umgebung erstellen:

1. Wählen Sie im [Fenster „Python-Umgebungen“](#managing-python-environments-in-visual-studio) **+ Benutzerdefiniert** aus. Damit wird eine neue Umgebung erstellt, und die im folgenden beschriebene [Registerkarte **Konfigurieren**](#configure-tab) wird geöffnet.)

    ![Standardansicht für eine neue benutzerdefinierte Umgebung](media/environments-custom-1.png)

1. Geben Sie einen Namen für die Umgebung in das Feld **Beschreibung** ein.
1. Geben Sie den Pfad des Interpreters in das Feld **Präfixpfad** ein, oder navigieren Sie dahin.
1. Wählen Sie **Automatisch erkennen** aus, damit Visual Studio die verbleibenden Felder ausfüllt, oder füllen Sie sie manuell aus.
1. Wählen Sie **Übernehmen** aus, um die Umgebung zu speichern.
1. Wenn Sie die Umgebung entfernen möchten, wählen Sie auf der Registerkarte **Konfigurieren** den Befehl **Entfernen** aus. Umgebungen mit automatischer Erkennung bieten diese Option nicht. Weitere Informationen finden Sie im nächsten Abschnitt.

### <a name="moving-an-existing-interpreter"></a>Verschieben eines vorhandenen Interpreters

Wenn Sie einen vorhandenen Interpreter an einen neuen Speicherort im Dateisystem verschieben, erkennt Visual Studio diese Änderung nicht automatisch, und Sie müssen seine zugehörige Umgebung manuell aktualisieren:

- Wenn Sie ursprünglich eine Umgebung für diesen Interpreter erstellt haben, bearbeiten Sie diese Umgebung, sodass diese auf den neuen Speicherort zeigt.

- Wenn die Umgebung ursprünglich automatisch erkannt wurde, wurde sie mit einem bestimmten Installationsprogramm auf dem Computer installiert, das die von Visual Studio überprüften Registrierungseinträge erstellt hat. In diesem Fall stellen Sie den Python-Interpreter zunächst an seinem ursprünglichen Speicherort wieder her. Danach deinstallieren Sie den Interpreter mithilfe des Installationsprogramms; dabei werden die Registrierungseinträge gelöscht. Installieren Sie den Interpreter dann am gewünschten Speicherort. Starten Sie Visual Studio neu – jetzt sollte der neue Speicherort automatisch erkannt werden. Dieses Verfahren stellt sicher, dass alle Nebeneffekte des Installationsprogramms ordnungsgemäß verarbeitet werden.

### <a name="overview-tab"></a>Registerkarte „Übersicht“

Bietet grundlegende Informationen und Befehle für die Umgebung:

![Registerkarte „Übersicht“ von Python-Umgebungen](media/environments-overview-tab.png)

| Befehl | Beschreibung |
| --- | --- |
| Diese Umgebung zum Standard für neue Projekte machen | Legt die aktive Umgebung fest, die möglicherweise dazu führt, dass Visual Studio kurz nicht mehr reagiert, während die IntelliSense-Datenbank geladen wird. Umgebungen mit vielen Paketen reagieren möglicherweise längere Zeit nicht mehr. |
| Website des Verteilers besuchen | Öffnen eine von der Python-Verteilung bereitgestellt URL in einem Browser. Python 3.x öffnet beispielsweise python.org. |
| Interaktives Fenster öffnen | Öffnet das [interaktive Fenster (REPL)](python-interactive-repl-in-visual-studio.md) für diese Umgebung in Visual Studio und wendet alle [Startskripts (siehe unten)](#startup-scripts) an. |
| Interaktive Skripts | Siehe [Startskripte](#startup-scripts). |
| Interaktiven IPython-Modus verwenden | Wenn diese Option aktiviert ist, wird das interaktive Fenster standardmäßig mit Python geöffnet. Dadurch sind Inline-Plots und erweiterte IPython-Syntax möglich, wie z.B. `name?` zum Anzeigen der Hilfe und `!command` für Shellbefehle. Diese Option wird empfohlen, wenn Sie eine Verteilung von Anaconda verwenden, da diese zusätzliche Pakete erfordert. Weitere Informationen finden Sie unter [Verwenden von Python im interaktiven Fenster](interactive-repl-ipython.md). |
| In PowerShell öffnen | Öffnet den Interpreter in einem Befehlsfenster von PowerShell. |
| (Ordnerlinks) | Bieten Ihnen schnellen Zugriff auf den Installationsordner der Umgebung und die Interpreter „python.exe“ und „pythonw.exe“. Ersterer wird im Windows Explorer geöffnet, die anderen beiden in einem Konsolenfenster. |

#### <a name="startup-scripts"></a>Startskripte

Beim Verwenden von interaktiven Fenstern in ihrem alltäglichen Workflow entwickeln Sie mit hoher Wahrscheinlichkeit Hilfsfunktionen, die Sie häufig verwenden. Möglicherweise erstellen Sie z.B. eine Funktion, die einen Datenrahmen in Excel öffnet. Dann können Sie den Code als Startskript speichern, sodass dieser immer über das interaktive Fenster verfügbar ist.

Startskripts enthalten Code, der vom interaktiven Fenster automatisch geladen und ausgeführt wird, einschließlich Importe, Funktionsdefinitionen und vieles mehr. Auf derartige Skripts kann auf zwei Weisen verwiesen werden:

1. Wenn Sie eine Umgebung installieren, erstellt Visual Studio einen Ordner `Documents\Visual Studio 2017\Python Scripts\<environment>`, in dem &lt;environment&gt' dem Namen der Umgebung entspricht. Sie können mit dem Befehl **Interaktive Skripts untersuchen** ganz leicht zum umgebungsspezifischen Ordner navigieren. Wenn Sie das interaktive Fenster für diese Umgebung starten, lädt es alle hier gefundenen `.py`-Dateien und führt diese in alphabetischer Reihenfolge aus.

1. Das Steuerelement **Skripts** auf der Registerkarte **Extras > Optionen > Python Tools > Interaktives Fenster** (siehe [Optionen für das interaktive Fenster](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) soll einen zusätzlichen Ordner für Startskripts angeben, die in allen Umgebungen geladen und ausgeführt werden. Diese Funktion funktioniert aktuell noch nicht.

### <a name="configure-tab"></a>Registerkarte „Konfigurieren“

Wenn sie angezeigt wird, enthält sie Details, wie die in der folgenden Tabelle beschriebenen. Wenn diese Registerkarte nicht vorhanden ist, bedeutet dies, dass alle Details von Visual Studio automatisch verwaltet werden.

![Registerkarte „Konfigurieren“ von Python-Umgebungen](media/environments-configure-tab.png)

| Feld | Beschreibung |
| --- | --- |
| **Beschreibung** | Der Name für die Umgebung. |
| **Präfixpfad** | Der Speicherort des Basisordners des Interpreters. Durch Festlegen dieses Werts und Klicken auf **Automatisch erkennen** versucht Visual Studio, die anderen Felder für Sie auszufüllen. |
| **Interpreterpfad** | Der Pfad zur ausführbaren Datei des Interpreters, üblicherweise der Präfixpfad gefolgt von `python.exe`. |
| **Fenstermodus-Interpreter** | Der Pfad zur ausführbaren Datei ohne Konsole, häufig der Präfixpfad gefolgt von `pythonw.exe`. |
| **Bibliothekspfad** | Gibt den Stamm der Standardbibliothek an. Dieser Wert kann allerdings ignoriert werden, wenn Visual Studio einen genaueren Pfad vom Interpreter anfordern kann. |
| **Sprachversion** | Wird im Dropdownmenü ausgewählt |
| **Architektur** | Wird normalerweise automatisch erkannt und ausgefüllt, andernfalls 32-Bit oder 64-Bit. |
| **Pfadumgebungsvariable** | Die Umgebungsvariable, die der Interpreter verwendet, um Suchpfade zu finden. Visual Studio ändert den Wert der Variablen, wenn Python gestartet wird, sodass sie die Suchpfade des Projekts enthält. In der Regel sollte diese Eigenschaft auf `PYTHONPATH` festgelegt werden, aber einige Interpreter verwenden einen anderen Wert. |

### <a name="pip-tab"></a>Registerkarte „pip“

Verwaltet die in der Umgebung installierten Pakete und ermöglicht Ihnen auch, neue Pakete zu suchen und zu installieren (einschließlich dazugehöriger Abhängigkeiten). Das Suchen filtert Ihre aktuell installierten Pakete und [PyPI](https://pypi.python.org). Sie können auch einen `pip install`-Befehl direkt in das Suchfeld eingeben, einschließlich der Flags wie z.B. `--user` oder `--no-deps`.

![Registerkarte „pip“ von Python-Umgebungen](media/environments-pip-tab.png)

Durch das Installieren eines Pakets wird ein Unterordner im `Lib`-Ordner der Umgebung im Dateisystem erstellt. Wenn Sie z.B. Python 3.6 in `c:\Python36` installiert haben, werden Pakete in `c:\Python36\Lib` installiert. Wenn Sie Anaconda 3 in `c:\Program Files\Anaconda3` installiert haben, werden Pakete in `c:\Program Files\Anaconda3\Lib` installiert.

Im letzteren Fall muss Visual Studio `pip install` erhöht ausführen, damit es Unterordner erstellen kann, da die Umgebung sich in einem geschützten Bereich des Dateisystems befindet `c:\Program Files`. Wenn erhöhte Rechte erforderlich sind, zeigt Visual Studio folgende Aufforderung an: „Es sind möglicherweise Administratorberechtigungen erforderlich, um Pakete für diese Umgebung zu installieren, zu aktualisieren oder zu entfernen“:

![Eingabeaufforderung für erhöhte Rechte](media/environments-pip-elevate.png)

**Jetzt Rechte erweitern** erteilt Administratorrechte an „pip“ für einen einzigen Vorgang, auch gemäß Aufforderungen des Betriebssystems nach Berechtigungen. Wenn Sie **Ohne Administratorberechtigungen fortfahren** auswählen, wird die Installation des Pakets versucht, „pip“ schlägt allerdings beim Erstellen von Ordnern fehl. Die Ausgabe kann z.B. so aussehen: „error: could not create 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': Permission denied“ (Fehler: 'C:\Programme\Anaconda3\Lib\site-packages\png.py' konnte nicht erstellt werden: Berechtigung verweigert).

Wenn Sie **Beim Installieren oder Entfernen von Paketen immer Rechte erweitern** auswählen, wird verhindert, dass das Dialogfeld für die entsprechende Umgebung angezeigt wird. Wenn Sie möchten, dass das Dialogfeld wieder angezeigt wird, gehen Sie zu **Extras > Optionen > Python Tools > Allgemein**, und klicken Sie auf die Schaltfläche **Alle dauerhaft ausgeblendeten Dialogfelder zurücksetzen**.

Auf der gleichen Optionsregisterkarte können Sie auf **„pip“ immer als Administrator ausführen** klicken, um das Dialogfeld für alle Umgebungen zu unterdrücken. Weitere Informationen finden Sie unter [Optionen > Registerkarte „Allgemein“](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="intellisense-tab"></a>Registerkarte „IntelliSense“

Zeigt den aktuellen Status der IntelliSense-Vervollständigungsdatenbank:

![Registerkarte „IntelliSense“ von Python-Umgebungen](media/environments-intellisense-tab.png)

Die Datenbank enthält Metadaten für alle Bibliotheken der Umgebung, verbessert die Geschwindigkeit von IntelliSense und verringert die Speicherauslastung. Wenn Visual Studio eine neue Umgebung erkennt (oder wenn Sie eine hinzufügen), wird die Datenbank automatisch kompiliert, indem die Quelldateien der Bibliothek analysiert werden. Dieser Prozess kann eine Minute oder bis zu einer Stunde oder noch länger dauern, je nachdem, was installiert ist. (Zu Anaconda gehören z.B. viele Bibliotheken, und es dauert einige Zeit, die Datenbank zu kompilieren.) Wenn der Vorgang abgeschlossen ist, erhalten Sie detaillierte IntelliSense-Daten und müssen die Datenbank erst erneut aktualisieren (mit der Schaltfläche **DB aktualisieren**), wenn Sie weitere Bibliotheken installieren.

Bibliotheken, für die noch keine Daten kompiliert wurden, werden mit einem **!** gekennzeichnet. Wenn die Datenbank einer Umgebung nicht vollständig ist, wird daneben auch ein **!** in der Liste der wichtigsten Umgebungen angezeigt.

## <a name="selecting-an-environment-for-a-project"></a>Auswählen einer Umgebung für ein Projekt

Mit projektspezifischen Umgebungen stellen Sie sicher, dass ein Projekt immer in einer bestimmten Umgebung ausgeführt und die globale Standardumgebung ignoriert wird. Wenn die globale Standardumgebung beispielsweise CPython ist, aber ein Projekt IronPython und bestimmte Bibliotheken erfordert, die in der globalen Umgebung nicht installiert sind, ist eine projektspezifische-Umgebung erforderlich.

Projektumgebungen werden im Projektmappen-Explorer unter dem Knoten für Python-Umgebungen aufgelistet. Der fett formatierte Eintrag ist derzeit aktiv. Visual Studio verwendet ihn für das Debugging, Import- und Membervervollständigungen, Syntaxüberprüfungen und andere Tasks, die eine Umgebung erfordern:

![Projektumgebungen im Projektmappen-Explorer](media/environments-project.png)

Um eine andere Umgebung für das Projekt zu aktivieren, klicken Sie mit der rechten Maustaste auf die Umgebung, und wählen Sie **Umgebung aktivieren** aus.

Jede globale Umgebung kann als Projektumgebung hinzugefügt werden, indem Sie mit der rechten Maustaste auf **Python-Umgebungen** klicken und **Python-Umgebungen hinzufügen/entfernen** auswählen. In der angezeigten Liste können Sie die Umgebungen aktivieren oder deaktivieren, die in Ihrem Projekt verfügbar sind.

![Dialogfeld „Python-Umgebungen hinzufügen/entfernen“](media/environments-add-remove.png)

Im Projektmappen-Explorer können Sie die Umgebung auch erweitern, um die installierten Pakete anzuzeigen (die Sie importieren und in Ihrem Code verwenden können, wenn die Umgebung aktiv ist):

![Python-Pakete für eine Umgebung im Projektmappen-Explorer](media/environments-installed-packages.png)

Klicken Sie zum Installieren neuer Paketen mit der rechten Maustaste auf die Umgebung, wählen Sie **Python-Paket installieren** aus, und geben Sie den Namen des gewünschten Pakets ein. Pakete (und Abhängigkeiten) werden von [Python Package Index (PyPI)](https://pypi.python.org/pypi) heruntergeladen. Dort können Sie auch nach verfügbaren Paketen suchen. Statusleiste und Ausgabefenster von Visual Studio zeigen Informationen über die Installation an. Um ein Paket zu deinstallieren, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Entfernen** aus.

> [!Note]
> Die Unterstützung für die Python-Paketverwaltung wird derzeit vom zentralen Python-Entwicklungsteam bearbeitet. Die angezeigten Einträge sind nicht immer unbedingt richtig, und eine Installation oder Deinstallation ist möglicherweise nicht zuverlässig oder nicht möglich. Visual Studio verwendet den pip-Paket-Manager, falls verfügbar, und lädt ihn bei Bedarf herunter und installiert ihn. Visual Studio kann auch den easy_install-Paket-Manager verwenden. Pakete, die mit pip oder easy_install über die Befehlszeile installiert wurden, werden ebenfalls angezeigt.

> [!Tip]
> Eine gängige Situation, in der pip ein Paket nicht installieren kann, liegt vor, wenn das Paket Quellcode für native Komponenten in `*.pyd`-Dateien enthält. Wenn die erforderliche Version von Visual Studio nicht installiert ist, kann pip diese Komponenten nicht kompilieren. Die Fehlermeldung, die in derartigen Situationen angezeigt wird, ist `error: Unable to find vcvarsall.bat`. `easy_install` ist häufig in der Lage, vorkompilierte Binärdateien herunterzuladen, und Sie können einen geeigneten Compiler für ältere Python-Versionen von [http://aka.ms/VCPython27](http://aka.ms/VCPython27) herunterladen. Weitere Informationen finden Sie unter [How to deal with the pain of „unable to find vcvarsallbat“](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Umgang mit der Fehlermeldung, dass vcvarsallbat nicht gefunden werden konnte) im Teamblog zu Python-Tools.

## <a name="creating-virtual-environments"></a>Erstellen virtueller Umgebungen

1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen** aus. Dann wird Folgendes angezeigt:

    ![Erstellen einer virtuellen Umgebung](media/environments-add-virtual-1.png)

1. Geben Sie einen Namen an, um die virtuelle Umgebung im Projektpfad zu erstellen, oder einen vollständigen Pfad, um sie an anderer Stelle zu erstellen. (Um maximale Kompatibilität mit anderen Tools zu gewährleisten, verwenden Sie nur Buchstaben und Zahlen im Namen.)

1. Wählen Sie als Basisinterpreter eine globale Umgebung aus, und klicken Sie auf **Erstellen**. Wenn `pip`- und `virtualenv`- oder `venv`-Pakete nicht verfügbar sind, werden sie heruntergeladen und installiert.

    Wenn der angegebene Pfad eine vorhandene virtuelle Umgebung ist, wird der Basisinterpreter erkannt, und die Schaltfläche „Erstellen“ ändert sich in **Hinzufügen**:

    ![Hinzufügen einer vorhandenen virtuellen Umgebung](media/environments-add-virtual-2.png)

Eine vorhandene virtuelle Umgebung kann auch hinzugefügt werden, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Python-Umgebungen** klicken und **Vorhandene virtuelle Umgebung hinzufügen** auswählen. Visual Studio erkennt den Basisinterpreter anhand der Datei `orig-prefix.txt` im Verzeichnis `lib` der Umgebung automatisch.

Sobald eine virtuelle Umgebung Ihrem Projekt hinzugefügt wurde, erscheint sie im Fenster **Python-Umgebungen**. Sie können sie wie jede andere Umgebung aktivieren, und Sie können ihre Pakete verwalten. Wenn Sie darauf mit der rechten Maustaste klicken und **Entfernen** auswählen, wird der Verweis auf die Umgebung entfernt, oder die Umgebung und alle Dateien werden vom Datenträger gelöscht (jedoch nicht der Basisinterpreter).

Beachten Sie, dass ein Nachteil virtueller Umgebungen darin besteht, dass sie hartcodierte Dateipfade enthalten und somit nicht problemlos freigegeben oder auf andere Entwicklungscomputer übertragen werden können. Wie im nächsten Abschnitt beschrieben, können Sie die `requirements.txt`-Datei verwenden, um Empfängern Ihres Projekts zu erlauben, die Umgebung problemlos wiederherzustellen.

## <a name="managing-required-packages-requirementstxt"></a>Verwalten von erforderlichen Paketen („requirements.txt“)

Wenn Sie ein Projekt über ein Buildsystem für andere Benutzer freigeben oder planen, um es [in Microsoft Azure zu veröffentlichen](python-azure-cloud-service-project-template.md), müssen Sie die externen Pakete angeben, die das Projekt benötigt. Der empfohlene Ansatz ist die Verwendung einer [requirements.txt-Datei](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), die eine Liste der Befehle für pip enthält, mit denen die erforderlichen Versionen der abhängigen Pakete installiert werden.

Eigentlich kann jeder Dateiname zum Nachverfolgen von Anforderungen verwendet werden (mit `-r <full path to file>` beim Installieren eines Pakets), aber Visual Studio bietet spezielle Unterstützung für `requirements.txt`:

- Wenn Sie ein Projekt geladen haben, das `requirements.txt` enthält, und alle in der Datei aufgeführten Pakete installieren möchten, erweitern Sie den Knoten **Python-Umgebungen** im **Projektmappen-Explorer**, klicken Sie dann mit der rechten Maustaste auf den Umgebungsknoten, und wählen Sie **Aus „requirements.txt“ installieren** aus:

    ![Installieren aus „requirements.txt“](media/environments-requirements-txt-install.png)

- Wenn Sie alle erforderlichen Pakete bereits in einem Projekt installiert haben, können Sie im Projektmappen-Explorer mit der rechten Maustaste auf eine Umgebung klicken und **„requirements.txt“ generieren** auswählen, um die erforderliche Datei zu erstellen. Wenn die Datei bereits vorhanden ist, werden Sie zum Aktualisieren der Datei aufgefordert:

    ![Optionen für die Aktualisierung von „requirements.txt“](media/environments-requirements-txt-replace.png)

  - **Gesamte Datei ersetzen** entfernt alle vorhandenen Elemente, Kommentare und Optionen.
  - **Vorhandene Einträge aktualisieren** erkennt Paketanforderungen und aktualisiert die Versionsbezeichner entsprechend der derzeit installierten Version.
  - **Aktualisieren und Einträge hinzufügen** aktualisiert alle gefundenen Anforderungen und fügt alle anderen Pakete am Ende der Datei hinzu.

Da mit `requirements.txt`-Dateien die Anforderungen des Projekts fixiert werden sollen, werden alle installierten Pakete mit genauen Versionen aufgeführt. Wenn Sie genaue Versionen verwenden, wird sichergestellt, dass Sie Ihre Umgebung leicht auf einem anderen Computer reproduzieren können. Pakete werden aufgenommen, selbst wenn sie mit einem Versionsbereich, als Abhängigkeit von einem anderen Paket oder mit einen anderen Installationsprogramm als pip installiert wurden.

Wenn Sie eine neue virtuelle Umgebung hinzufügen und eine `requirements.txt`-Datei vorhanden ist, zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** eine Option zur automatischen Paketinstallation an. Auf diese Weise kann eine Umgebung leicht auf einem anderen Computer neu erstellt werden:

![Erstellen einer virtuellen Umgebung mit „requirements.txt“](media/environments-requirements-txt.png)

Wenn ein Paket nicht von pip installiert werden kann und in einer `requirements.txt`-Datei enthalten ist, schlägt die gesamte Installation fehl. Bearbeiten Sie in diesem Fall die Datei manuell, um dieses Paket ausschließen oder [pip-Optionen](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) zu verwenden, um auf eine installierbare Version des Pakets zu verweisen. Sie könnten beispielsweise [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) verwenden, um eine Abhängigkeit zu kompilieren und die Option `--find-links <path>` Ihrer Datei `requirements.txt` hinzuzufügen:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>Suchpfade

Bei der typischen Python-Nutzung stellt die `PYTHONPATH`-Umgebungsvariable (oder `IRONPYTHONPATH` usw.) den Standardsuchpfad für Moduldateien bereit. Wenn Sie also die Anweisungen `from <name> import...` oder `import <name>` verwenden, durchsucht Python der Reihe nach die folgenden Speicherorte nach einem übereinstimmenden Namen:

1. Die integrierten Python-Module.
1. Den Ordner, der den Python-Code enthält, den Sie ausführen.
1. Den „Modulsuchpfad“, gemäß der Definition durch die entsprechenden Umgebungsvariablen. (Weitere Informationen finden Sie unter [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Modulsuchpfad) und [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Umgebungsvariablen) in der Python-Hauptdokumentation.)

Die Umgebungsvariable für den Suchpfad wird von Visual Studio jedoch ignoriert, auch wenn sie für das gesamte System festgelegt wurde. Tatsächlich wird sie ignoriert, gerade *weil* sie für das gesamte System festgelegt wurde und sich daher bestimmte Fragen stellen, die nicht automatisch beantwortet werden können: Sind die referenzierten Module für Python 2.7 oder Python 3.3 vorgesehen? Werden sie die standardmäßigen Bibliotheksmodule überschreiben? Weiß der Entwickler das, oder handelt es sich um einen böswilligen Hijackingversuch?

Visual Studio bietet daher eine Möglichkeit, Suchpfade direkt in Umgebungen und Projekten anzugeben. Suchpfade werden als Wert von `PYTHONPATH` (oder anderen entsprechenden Variablen) beim Debuggen oder Ausführen des Skripts in Visual Studio übergeben. Durch das Hinzufügen von Suchpfaden überprüft Visual Studio die Bibliotheken an diesen Speicherorten und erstellt entsprechende IntelliSense-Datenbanken (das Erstellen der Datenbank kann je nach Anzahl von Bibliotheken einige Zeit in Anspruch nehmen).

Um einen Suchpfad hinzuzufügen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Element **Suchpfade**, wählen Sie **Ordner zu Suchpfad hinzufügen** aus, und wählen Sie den aufzunehmenden Ordner aus. Dieser Pfad wird für alle Umgebungen verwendet, die dem Projekt zugeordnet sind. (Möglicherweise werden Ihnen Fehlermeldungen angezeigt, wenn die Umgebung auf Python 3 basiert, und Sie versuchen, Python 2.7-Modulen einen Suchpfad hinzuzufügen.)

Dateien mit der Erweiterung `.zip` oder `.egg` können auch als Suchpfade hinzugefügt werden. Wählen Sie dazu **ZIP-Archiv zu Suchpfad hinzufügen** aus. Wie bei Ordnern wird der Inhalt dieser Dateien geprüft und IntelliSense zur Verfügung gestellt.

Wenn Sie regelmäßig die gleichen Suchpfade verwenden und der Inhalt nicht häufig geändert wird, kann es effizienter sein, ihn im Ordner „site-packages“ zu installieren. Der Suchpfad wird dann analysiert, in der IntelliSense-Datenbank gespeichert und immer der vorgesehenen Umgebung zugeordnet. So ist es nicht erforderlich, dass jedem Projekt ein Suchpfad hinzugefügt wird.
