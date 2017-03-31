---
title: "Python-Umgebungen in Python-Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 69740c73cc133e08254fc546d2b59885270725f2
ms.lasthandoff: 03/10/2017

---

# <a name="python-environments"></a>Python-Umgebungen

Python-Code wird immer innerhalb einer bestimmten Python-*Umgebung* ausgeführt, die aus einem Interpreter, einer Bibliothek (in der Regel die Python-Standardbibliothek) und einem Satz von installierten Paketen besteht. Gemeinsam bestimmen diese Komponenten, welche Sprachkonstrukte und Syntax gültig sind, auf welche Betriebssystemfunktionen Sie zugreifen können und welche Pakete Sie verwenden können.

Die Python-Arbeitsauslastung in Visual Studio erleichtert das Verwalten mehrerer Python-Umgebungen und den Wechsel zwischen den Umgebungen für verschiedene Projekte. Eine Umgebung enthält auch eine IntelliSense-Datenbank für die Bibliotheken einer Umgebung. Wenn Sie also eine Anweisung wie `import` im Visual Studio-Editor eingeben, wird automatisch eine Liste der verfügbaren Bibliotheken sowie der Module in diesen Bibliotheken angezeigt.

Häufig nutzen Entwickler nur eine globale Python-Umgebung. Andere müssen aber mehrere globale Umgebungen, projektspezifische Umgebungen und vielleicht auch virtuelle Umgebungen verwalten, wie in diesem Thema erläutert:

- [Auswählen und Installieren von Python-Interpretern](#selecting-and-installing-python-interpreters)
- [Verwalten von Python-Umgebungen in Visual Studio](#managing-python-environments-in-visual-studio)
- [Globale Umgebungen](#global-environments)
- [Projektspezifische Umgebungen](#project-specific-environments)
- [Virtuelle Umgebungen](#virtual-environments)
- [Verwalten von erforderlichen Paketen](#managing-required-packages)
- [Suchpfade](#search-paths)

Ein Einführungsvideo finden Sie unter [Deep Dive: Python Interpreters](https://youtu.be/KY1GEOo3qy0) (youtube.com, 13 Min., 27 Sek.).

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>Auswählen und Installieren von Python-Interpretern

Außer bei Visual Studio 2017 Preview umfasst die Python-Unterstützung keinen Python-Interpreter. Sie müssen also einen der folgenden Interpreter zum Ausführen des Codes installieren. Im Allgemeinen erkennt Visual Studio neu installierte Interpreter automatisch und richtet eine Umgebung für sie ein. Wenn dies nicht der Fall ist, finden Sie unter [Erstellen einer Umgebung für einen vorhandenen Interpreter](#creating-an-environment-for-an-existing-interpreter) weiter unten weitere Informationen.

| Interpreter | Beschreibung | 
| --- | --- | 
| [CPython](https://www.python.org/) | Der „systemeigene“ und am häufigsten verwendete Interpreter, verfügbar in 32- und 64-Bit-Versionen (32-Bit wird empfohlen). Er umfasst die neuesten Sprachfeatures, die maximale Python-Paketkompatibilität, vollständige Unterstützung für das Debuggen und Interoperabilität mit [IPython](http://ipython.org/). Siehe auch: [Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (Sollte ich Python 2 oder Python 3 verwenden?) |
| [IronPython](http://ironpython.codeplex.com/) | Eine .NET-Implementierung von Python, verfügbar in 32- und 64-Bit-Versionen, die C#-/F#-/Visual Basic-Interoperabilität, Zugriff auf .NET APIs, standardmäßiges Python-Debuggen (jedoch kein C++-Debuggen im gemischten Modus) und IronPython-/C#-Debuggen im gemischten Modus bietet. IronPython unterstützt jedoch keine virtuelle Umgebungen. | 
| [Anaconda](https://www.continuum.io) | Eine offene Data Science-Plattform, die von Python unterstützt wird und die neueste Version von CPython sowie die meisten der nicht leicht zu installierenden Pakete enthält. Wir empfehlen diesen Interpreter, wenn keine andere Entscheidung möglich ist. |
| [PyPy](http://www.pypy.org/) | Eine leistungsstarke JIT-Implementierung für die Ablaufverfolgung von Python, die gut für Programme mit langer Ausführungszeit und Situationen, in denen Sie Leistungsprobleme identifizieren, jedoch keine anderen Lösungen finden können, geeignet ist. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |
| [Jython](http://www.jython.org/) | Eine Implementierung von Python auf der Java Virtual Machine (JVM). Ähnlich wie bei IronPython kann in Jython ausgeführter Code mit Java-Klassen und -Bibliotheken interagieren, aber möglicherweise viele für CPython vorgesehene Bibliotheken nicht verwenden. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |

Wenn Sie als Entwickler neue Formen der Erkennung für Python-Umgebungen bereitstellen möchten, finden Sie unter [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (PTVS-Umgebungserkennung, github.com) weitere Informationen.

## <a name="managing-python-environments-in-visual-studio"></a>Verwalten von Python-Umgebungen in Visual Studio

Um das Fenster „Python-Umgebungen“ zu öffnen, führen Sie einen der folgenden Schritte aus:

1. Wählen Sie den Menübefehl **Ansicht > Weitere Fenster > Python-Umgebungen** aus.
1. Klicken Sie für ein Projekt im Projektmappen-Explorer mit der rechten Maustaste auf **Python-Umgebungen**, und wählen Sie **Alle Python-Umgebungen anzeigen** aus:

    ![Befehl „Alle Umgebungen anzeigen“ im Projektmappen-Explorer](media/environments-view-all.png)
    
In jedem Fall wird das Fenster „Python-Umgebungen“ als gleichgeordnete Registerkarte des Projektmappen-Explorers angezeigt:

![Fenster „Python-Umgebungen“](media/environments-default-view.png)

Im Beispiel oben ist Python 3.4 (32-Bit-CPython) zusammen mit den 32- und 64-Bit-Versionen von IronPython installiert. Die Standardumgebung in Fettdruck ist Python 3.4, die für alle neuen Projekte verwendet wird. Wenn keine Umgebungen angezeigt werden, bedeutet dies, dass Sie Python-Tools für Visual Studio installiert haben, aber noch keinen Python-Interpreter (siehe [Auswählen und Installieren von Python-Interpretern](#selecting-and-installing-python-interpreters) oben).

> [!Tip]
> Wenn das Fenster **Python-Umgebungen* schmal ist, wie oben dargestellt ist, werden die Umgebungen oben und die verschiedenen Registerkarten unten aufgeführt. Wenn Sie das Fenster jedoch ausreichend erweitern, sehen Sie eine breite Ansicht, in der Sie möglicherweise bequemer arbeiten können.
>
> ![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments-expanded-view.png)

Visual Studio sucht normalerweise in der Registrierung nach einem installierten Python-Interpreter. Diese Suche ist jedoch möglicherweise nicht erfolgreich, wenn der Interpreter nicht auf standardisierte Weise installiert wurde. In solchen Fällen können Sie Visual Studio wie folgt direkt auf den Interpreter verweisen:

1. Wählen Sie im Fenster „Python-Umgebungen“ **+ Benutzerdefiniert** aus. Damit wird eine neue Umgebung erstellt, und die [Registerkarte **Konfigurieren**](#configure-tab) wird geöffnet, die weiter unten beschrieben wird.

    ![Standardansicht für eine neue benutzerdefinierte Umgebung](media/environments-custom-1.png)

1. Geben Sie einen Namen für die Umgebung in das Feld **Beschreibung** ein.
1. Geben Sie den Pfad des Interpreters in das Feld **Präfixpfad** ein, oder navigieren Sie dahin.
1. Wählen Sie **Automatisch erkennen** aus, damit Visual Studio die verbleibenden Felder ausfüllt, oder füllen Sie sie manuell aus.
1. Wählen Sie **Übernehmen** aus, um die Umgebung zu speichern.
1. Wenn Sie die Umgebung entfernen möchten, wählen Sie auf der Registerkarte **Konfigurieren** den Befehl **Entfernen** aus.

> [!Note]
> Obwohl Visual Studio die Option „system-site-packages“ beachtet, gibt es keine Möglichkeit, sie in Visual Studio zu ändern.

### <a name="overview-tab"></a>Registerkarte „Übersicht“

Enthält grundlegende Informationen und Befehle für die Umgebung. Sie können sie z.B. als Standard festlegen, ein [interaktives (REPL) Fenster](interactive-repl.md) mit der Umgebung öffnen und zu dem Dialogfeld springen, in dem Sie das interaktive Fenster konfigurieren (identisch mit dem Menübefehl **Extras > Optionen**, Auswählen von **Python-Tools > Interaktive Fenster** und des Namens der Umgebung).

![Registerkarte „Übersicht“ von Python-Umgebungen](media/environments-overview-tab.png)

> [!Note]
> Durch Ändern der aktiven Umgebung reagiert Visual Studio möglicherweise kurz nicht mehr, während die IntelliSense-Datenbank geladen wird. Umgebungen mit vielen Paketen reagieren möglicherweise längere Zeit nicht mehr.

### <a name="configure-tab"></a>Registerkarte „Konfigurieren“

Wenn sie angezeigt wird, enthält sie Details, wie die in der folgenden Tabelle beschriebenen. Wenn diese Registerkarte nicht vorhanden ist, bedeutet dies, dass alle Details von Visual Studio automatisch verwaltet werden.

![Registerkarte „Konfigurieren“ von Python-Umgebungen](media/environments-configure-tab.png)

| Feld | Beschreibung |
| --- | --- |
| **Beschreibung** | Der Name für die Umgebung. |
| **Präfixpfad** | Der Speicherort des Basisordners des Interpreters. Durch diese Eingabe und Klicken auf **Automatisch erkennen** versucht Visual Studio, die anderen Felder für Sie auszufüllen. |
| **Interpreterpfad** | Der Pfad zur ausführbaren Datei des Interpreters, üblicherweise der Präfixpfad gefolgt von `python.exe`. |
| **Fenstermodus-Interpreter** | Der Pfad zur ausführbaren Datei ohne Konsole, häufig der Präfixpfad gefolgt von `pythonw.exe`. |
| **Bibliothekspfad** | Gibt den Stamm der Standardbibliothek an. Dieser Wert kann allerdings ignoriert werden, wenn Visual Studio einen genaueren Pfad vom Interpreter anfordern kann. |
| **Sprachversion** | Ausgewählt aus dem Dropdownmenü. |
| **Architektur** | Wird normalerweise automatisch erkannt und ausgefüllt, andernfalls 32-Bit oder 64-Bit. |
| **Pfadumgebungsvariable** | Die Umgebungsvariable, die der Interpreter verwendet, um Suchpfade zu finden. Visual Studio ändert den Wert der Variablen, wenn Python gestartet wird, sodass sie die Suchpfade des Projekts enthält. In der Regel sollte diese Eigenschaft auf `PYTHONPATH` festgelegt werden, aber einige Interpreter verwenden einen anderen Wert. |

### <a name="pip-tab"></a>Registerkarte „pip“

Verwaltet die in der Umgebung installierten Pakete und ermöglicht Ihnen auch, neue Pakete zu suchen und zu installieren (einschließlich der Abhängigkeiten). Beim Suchen werden die installierten Pakete gefiltert und [PyPI](https://pypi.python.org) wird durchsucht. Sie können auch einen `pip install`-Befehl direkt in das Suchfeld eingeben, einschließlich der Flags wie z.B. `--user` oder `--no-deps`.

![Registerkarte „pip“ von Python-Umgebungen](media/environments-pip-tab.png)

### <a name="intellisense-tab"></a>Registerkarte „IntelliSense“

Zeigt den aktuellen Status der IntelliSense-Vervollständigungsdatenbank:

![Registerkarte „IntelliSense“ von Python-Umgebungen](media/environments-intellisense-tab.png)

Die Datenbank enthält Metadaten für alle Bibliotheken der Umgebung, verbessert die Geschwindigkeit von IntelliSense und verringert die Speicherauslastung. Wenn Visual Studio eine neue Umgebung erkennt (oder wenn Sie eine hinzufügen), wird die Datenbank automatisch kompiliert, indem die Quelldateien der Bibliothek analysiert werden. Dieser Prozess kann eine Minute oder bis zu einer Stunde oder noch länger dauern, je nachdem, was installiert ist. (Zu Anaconda gehören z.B. viele Bibliotheken, und es dauert einige Zeit, die Datenbank zu kompilieren.) Wenn der Vorgang abgeschlossen ist, erhalten Sie detaillierte IntelliSense-Daten und müssen die Datenbank erst erneut aktualisieren (mit der Schaltfläche **DB aktualisieren**), wenn Sie weitere Bibliotheken installieren.

Bibliotheken, für die noch keine Daten kompiliert wurden, werden mit einem **!** gekennzeichnet. Wenn die Datenbank einer Umgebung nicht vollständig ist, wird daneben auch ein **!** in der Liste der wichtigsten Umgebungen angezeigt.

## <a name="global-environments"></a>Globale Umgebungen

Globale (oder systemweite) Umgebungen sind für alle Projekte auf einem Computer verfügbar. Visual Studio erkennt normalerweise globale Umgebungen automatisch, und sie können im Fenster „Python-Umgebungen“ angezeigt werden. Falls nicht, können Sie eine Umgebung manuell hinzufügen, wie zuvor unter [Verwalten von Python-Umgebungen in Visual Studio](#managing-python-environments-in-visual-studio) beschrieben.

Visual Studio verwendet die Standardumgebung für alle neuen Projekte zum Ausführen, Debuggen und Überprüfen der Syntax, Anzeigen der Import- und Membervervollständigung und für andere Aufgaben, für die eine Umgebung erforderlich ist. Das Ändern der Standardumgebung wirkt sich auf alle Projekte aus, denen keine [projektspezifische Umgebung](#project-specific-environments) hinzugefügt wurde, wie im Folgenden beschrieben.

## <a name="project-specific-environments"></a>Projektspezifische Umgebungen

Mit projektspezifischen Umgebungen stellen Sie sicher, dass ein Projekt immer in einer bestimmten Umgebung ausgeführt und die globale Standardumgebung ignoriert wird. Wenn die globale Standardumgebung beispielsweise CPython ist, aber ein Projekt IronPython und bestimmte Bibliotheken erfordert, die in der globalen Umgebung nicht installiert sind, ist eine projektspezifische-Umgebung erforderlich.

Projektumgebungen werden im Projektmappen-Explorer unter dem Knoten für Python-Umgebungen aufgelistet. Der fett formatierte Eintrag ist derzeit aktiv und wird für das Debugging, Import- und Membervervollständigungen, Syntaxüberprüfungen und andere Aufgaben verwendet, die eine Umgebung erfordern:

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
> Eine gängige Situation, in der pip ein Paket nicht installieren kann, liegt vor, wenn das Paket Quellcode für systemeigene Komponenten in `*.pyd`-Dateien enthält. Wenn die erforderliche Version von Visual Studio nicht installiert ist, kann pip diese Komponenten nicht kompilieren. Die folgende Fehlermeldung wird in diesem Fall angezeigt: `error: Unable to find vcvarsall.bat.` `easy_install` ist häufig in der Lage, vorkompilierte Binärdateien herunterzuladen, und Sie können einen geeigneten Compiler für ältere Python-Versionen von [http://aka.ms/VCPython27](http://aka.ms/VCPython27) herunterladen. Weitere Informationen finden Sie unter [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Umgang mit der Fehlermeldung, dass vcvarsallbat nicht gefunden werden konnte) im Teamblog zu Python-Tools.


## <a name="virtual-environments"></a>Virtuelle Umgebungen

Da in einer globalen Umgebung installierte Pakete für alle Projekte verfügbar sind, die sie verwenden, können Konflikte auftreten, wenn zwei Projekte inkompatible Pakete oder verschiedene Versionen des gleichen Pakets erfordern. Um solche Konflikte zu vermeiden, bietet Visual Studio die Möglichkeit zum Erstellen *virtueller Umgebungen*, die in der Regel für ein Projekt gelten.

Wie alle anderen Python-Umgebungen besteht eine virtuelle Umgebung aus einem Python-Interpreter, einer Bibliothek und einem Satz von Paketen. Die virtuelle Umgebung verwendet jedoch den Interpreter und die Bibliothek aus einer Ihrer globalen Umgebungen (vorausgesetzt, sie unterstützt virtuelle Umgebungen), die Pakete sind allerdings von den globalen und allen anderen virtuellen Umgebungen getrennt und isoliert. Dadurch werden Konflikte vermieden, und der Speicherbedarf der virtuellen Umgebung wird auf die ungefähre Größe der Pakete minimiert. 

So erstellen Sie eine neue virtuelle Umgebung

1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen** aus. Dann wird Folgendes angezeigt:

    ![Erstellen einer virtuellen Umgebung](media/environments-add-virtual-1.png)

1. Geben Sie einen Namen an, um die virtuelle Umgebung im Projektpfad zu erstellen, oder einen vollständigen Pfad, um sie an anderer Stelle zu erstellen. (Um maximale Kompatibilität mit anderen Tools zu gewährleisten, verwenden Sie nur Buchstaben und Zahlen im Namen.)

1. Wählen Sie als Basisinterpreter eine globale Umgebung aus, und klicken Sie auf **Erstellen**. Wenn `pip`- und `virtualenv`- oder `venv`-Pakete nicht verfügbar sind, werden sie heruntergeladen und installiert.

    Wenn der angegebene Pfad eine vorhandene virtuelle Umgebung ist, wird der Basisinterpreter erkannt, und die Schaltfläche „Erstellen“ ändert sich in **Hinzufügen**:

    ![Hinzufügen einer vorhandenen virtuellen Umgebung](media/environments-add-virtual-2.png)

Eine vorhandene virtuelle Umgebung kann auch hinzugefügt werden, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Python-Umgebungen** klicken und **Vorhandene virtuelle Umgebung hinzufügen** auswählen. Visual Studio erkennt den Basisinterpreter anhand der Datei `orig-prefix.txt` im Verzeichnis `lib` der Umgebung automatisch.

Sobald eine virtuelle Umgebung Ihrem Projekt hinzugefügt wurde, erscheint sie im Fenster **Python-Umgebungen**. Sie können sie wie jede andere Umgebung aktivieren, und Sie können ihre Pakete verwalten. Wenn Sie mit der rechten Maustaste klicken und **Entfernen** auswählen, wird der Verweis auf die Umgebung entfernt, oder die Umgebung und alle Dateien werden vom Datenträger löscht (jedoch nicht der Basisinterpreter).

Beachten Sie, dass ein Nachteil von virtuellen Umgebungen darin besteht, dass sie hartcodierte Dateipfade enthalten und somit nicht problemlos freigegeben oder auf andere Entwicklungscomputer übertragen werden können. Glücklicherweise können Sie die Datei `requirements.txt` verwenden, wie im nächsten Abschnitt beschrieben.

## <a name="managing-required-packages"></a>Verwalten von erforderlichen Paketen

Wenn Sie ein Projekt über ein Buildsystem für andere Benutzer freigeben oder planen, es [in Microsoft Azure zu veröffentlichen](template-azure-cloud-service.md), müssen Sie die erforderlichen externen Pakete angeben. Der empfohlene Ansatz ist die Verwendung einer [requirements.txt-Datei](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), die eine Liste der Befehle für pip enthält, mit denen die erforderlichen Versionen der abhängigen Pakete installiert werden.

Eigentlich kann jeder Dateiname zum Nachverfolgen von Anforderungen verwendet werden (mit `-r <full path to file>` beim Installieren eines Pakets), aber Visual Studio bietet spezielle Unterstützung für `requirements.txt`:

- Wenn Sie ein Projekt geladen haben, das `requirements.txt` enthält, und alle in der Datei aufgeführten Pakete installieren möchten, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Aus „requirements.txt“ installieren** aus:

    ![Installieren aus „requirements.txt“](media/environments-requirements-txt-install.png)

- Wenn Sie alle erforderlichen Pakete in einem Projekt installiert haben, können Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und **„requirements.txt“ generieren** auswählen, um die erforderliche Datei zu erstellen. Wenn die Datei bereits vorhanden ist, werden Sie zum Aktualisieren der Datei aufgefordert:

    ![Optionen für die Aktualisierung von „requirements.txt“](media/environments-requirements-txt-replace.png)

    - **Gesamte Datei ersetzen** entfernt alle vorhandenen Elemente, Kommentare und Optionen.
    - **Vorhandene Einträge aktualisieren** erkennt Paketanforderungen und aktualisiert die Versionsbezeichner entsprechend der derzeit installierten Version.
    - **Aktualisieren und Einträge hinzufügen** aktualisiert alle gefundenen Anforderungen und fügt alle anderen Pakete am Ende der Datei hinzu.

Da mit `requirements.txt`-Dateien die Anforderungen des Projekts fixiert werden sollen, werden alle installierten Pakete mit genauen Versionen aufgeführt. Dadurch wird sichergestellt, dass Sie Ihre Umgebung leicht auf einem anderen Computer reproduzieren können. Pakete werden aufgenommen, selbst wenn sie mit einem Versionsbereich, als Abhängigkeit von einem anderen Paket oder mit einen anderen Installationsprogramm als pip installiert wurden.

Wenn Sie eine neue virtuelle Umgebung hinzufügen und eine ` requirements.txt`-Datei vorhanden ist, zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** eine Option an, um die Pakete automatisch zu installieren. Auf diese Weise kann eine Umgebung leicht auf einem anderen Computer neu erstellt werden:

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

# <a name="search-paths"></a>Suchpfade

Bei der typischen Python-Nutzung stellt die `PYTHONPATH`-Umgebungsvariable (oder `IRONPYTHONPATH` usw.) den Standardsuchpfad für Moduldateien bereit. Wenn Sie also eine `import <name>`-Anweisung verwenden, durchsucht Python zuerst die integrierten Module nach einem passenden Namen, dann Ordner mit dem Python-Code, den Sie ausführen, und dann den „Modulsuchpfad“ gemäß der Definition durch die entsprechenden Umgebungsvariablen. (Weitere Informationen finden Sie unter [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Modulsuchpfad) und [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Umgebungsvariablen) in der Python-Hauptdokumentation.)

Die Umgebungsvariable für den Suchpfad wird von Visual Studio jedoch ignoriert, auch wenn sie für das gesamte System festgelegt wurde. Tatsächlich wird sie ignoriert, gerade *weil* sie für das gesamte System festgelegt wurde und sich daher bestimmte Fragen stellen, die nicht automatisch beantwortet werden können: Sind die referenzierten Module für Python 2.7 oder Python 3.3 vorgesehen? Werden sie die standardmäßigen Bibliotheksmodule überschreiben? Weiß der Entwickler das, oder handelt es sich um einen böswilligen Hijacking-Versuch?

Die Python-Unterstützung in Visual Studio bietet daher eine Möglichkeit, Suchpfade direkt in Umgebungen und Projekten anzugeben. Diese werden als Wert von `PYTHONPATH` (oder einer entsprechenden Variablen) beim Debuggen oder Ausführen des Skripts in Visual Studio übergeben. Durch das Hinzufügen von Suchpfaden überprüft Visual Studio die Bibliotheken an diesen Speicherorten und erstellt entsprechende IntelliSense-Datenbanken (dies kann je nach Anzahl von Bibliotheken einige Zeit dauern).

Um einen Suchpfad hinzuzufügen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Element **Suchpfade**, wählen Sie **Ordner zu Suchpfad hinzufügen** aus, und wählen Sie den aufzunehmenden Ordner aus. Dieser Pfad wird für alle Umgebungen verwendet, die dem Projekt zugeordnet sind.

Dateien mit der Erweiterung `.zip` oder `.egg` können auch als Suchpfade hinzugefügt werden. Wählen Sie dazu **ZIP-Archiv zu Suchpfad hinzufügen** aus. Wie bei Ordnern wird der Inhalt dieser Dateien geprüft und IntelliSense zur Verfügung gestellt.

> [!Note]
> Es ist möglich, einen Suchpfad zu Python 2.7-Modulen hinzuzufügen, während Sie Python 3.3 verwenden. Das Ergebnis können Fehlermeldungen sein.

Wenn Sie regelmäßig die gleichen Suchpfade verwenden und der Inhalt nicht häufig geändert wird, kann es effizienter sein, ihn im Ordner „site-packages“ zu installieren. Er wird dann analysiert, in der IntelliSense-Datenbank gespeichert und immer der vorgesehenen Umgebung zugeordnet. Dann ist es nicht erforderlich, dass ein Suchpfad für jedes Projekt hinzugefügt wird.

