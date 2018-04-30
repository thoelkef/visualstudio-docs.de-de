---
title: Arbeiten mit C++ und Python
description: Eine exemplarische Vorgehensweise zum Erstellen einer C++-Erweiterung für Python mithilfe von Visual Studio, einschließlich einer exemplarischen Vorgehensweise zum Debuggen im gemischten Modus.
ms.date: 04/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2be78ab073d688e8882dcfdedceef6a6fc73bde3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="creating-a-c-extension-for-python"></a>Erstellen einer C++-Erweiterung für Python

Module, die in C++ (oder C#) geschrieben werden, werden häufig verwendet, um die Funktionen eines Python-Übersetzers zu erweitern sowie den Zugriff auf Fähigkeiten des Betriebssystem auf niedriger Ebene zu aktivieren. Es gibt drei Haupttypen von Modulen:

- Accelerator-Modul: Da Python eine interpretierte Sprache ist, können bestimmte Teile des Codes in C++ für höhere Leistung geschrieben werden.
- Wrapper-Module: machen bestehende C/C++-Schnittstellen für den Python-Code verfügbar oder stellen eine „Python-ähnlichere“ API zur Verfügung, die mit Python einfach zu verwenden ist.
- Systemzugriffsmodule auf niedriger Ebene: Diese werden erstellt, um auf Features der CPython-Laufzeit auf niedriger Ebene, auf das Betriebssystem oder auf die zugrunde liegende Hardware zuzugreifen.

Dieser Artikel führt Sie durch die Erstellung eines C++-Erweiterungsmoduls für CPython, das einen Hyperbeltangens berechnet und diesen aus dem Python-Code abruft. Die Routine wird zuerst in Python implementiert, um den relativen Leistungsgewinn durch Implementieren derselben Routine in C++ zu veranschaulichen.

Der Ansatz hier gilt für CPython-Standarderweiterungen, so wie in der [Python-Dokumentation](https://docs.python.org/3/c-api/) beschrieben. Ein Vergleich zwischen dieser und anderen Maßnahmen ist unter [Alternative Ansätze](#alternative-approaches) am Ende dieses Artikels beschrieben.

Das abgeschlossene Beispiel aus dieser exemplarischen Vorgehensweise finden Sie unter [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Visual Studio 2017, wobei die Workloads **Desktopentwicklung mit C++** und **Python-Entwicklung** mit den Standardoptionen installiert werden müssen.
- Aktivieren Sie in der Workload **Python-Entwicklung** ebenfalls das Kontrollkästchen **Native Python-Entwicklungstools** auf der rechten Seite. Durch diese Option wird der Großteil der Konfigurationen eingerichtet, die in diesem Artikel beschrieben werden. (Diese Option enthält automatisch auch die C++-Workload.)

    ![Auswählen der Option „Native Python-Entwicklungstools“](media/cpp-install-native.png)

    > [!Tip]
    > Die Installation der Workload **Data Science und analytische Anwendungen** umfasst standardmäßig außerdem Python und die Option **Native Python-Entwicklungstools**.

Weitere Informationen finden Sie unter [Installing Python Support for Visual Studio (Installieren von Python-Unterstützung für Visual Studio)](installing-python-support-in-visual-studio.md), einschließlich der Verwendung anderer Versionen von Visual Studio. Wenn Sie Python separat installieren, stellen Sie sicher, dass Sie **Download debugging symbols** (Debugsymbole herunterladen) und **Download debug binaries** (Debugbinärdateien herunterladen) unter **Erweiterte Optionen** im Installer auswählen. Durch diese Option wird sichergestellt, dass Sie über die erforderlichen Debugbibliotheken verfügen, wenn Sie einen Debugbuild ausführen.

## <a name="create-the-python-application"></a>Erstellen der Python-Anwendung

1. Erstellen Sie ein neues Python-Projekt in Visual Studio, indem Sie auf **Datei > Neu > Projekt** klicken. Suchen Sie nach "Python", wählen Sie die Vorlage **Python Application** (Python-Anwendung), weisen Sie ihr einen geeigneten Namen und Standort zu, und klicken Sie auf **OK**.

1. Das Arbeiten mit C++ erfordert, dass Sie einen 32-Bit-Python-Interpreter verwenden (Python 3.6 wird hier empfohlen). Erweitern Sie im **Projektmappen-Explorer** von Visual Studio den Projektknoten und anschließend den Knoten **Python-Umgebungen**. Wenn Keine 32-Bit-Umgebung als Standardumgebung angezeigt wird (entweder in Fettdruck oder als „globaler Standard“ gekennzeichnet), befolgen Sie die Anweisungen unter [Selecting a Python environment for a project (Auswählen einer Python-Umgebung für ein Projekt)](selecting-a-python-environment-for-a-project.md). Wenn Sie noch keinen 32-Bit-Interpreter installiert haben, finden Sie unter [Installing Python interpreters (Installieren von Python-Interpretern)](installing-python-interpreters.md) weitere Informationen.

1. Fügen Sie in der `.py`-Datei des Projekts den folgenden Code ein, der die Berechnung eines Hyperbeltangens durchführt (Dieser wird ohne Verwendung der mathematischen Bibliothek zum einfacheren Vergleich implementiert). Geben Sie den Code gerne manuell ein, um einige der [Bearbeitungsfunktionen von Python](editing-python-code-in-visual-studio.md) kennenzulernen.

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Führen Sie das Programm mit **Debuggen > Starten ohne Debuggen** (STRG+F5) aus, um die Ergebnisse anzuzeigen. Sie können die `COUNT`-Variable anpassen, um die Ausführungsdauer der Benchmarks zu ändern. Legen Sie für diese exemplarische Vorgehensweise die „Count“-Variable für jeden Benchmark fest, sodass diese jeweils etwa zwei Sekunden benötigen.

## <a name="create-the-core-c-project"></a>Erstellen des wesentlichen C++-Projekts

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Hinzufügen > Neues Projekt...** aus. Eine Visual Studio-Projektmappe kann sowohl Python- als auch C++-Projekte zusammen enthalten (was einer der Vorteile von Visual Studio für Python ist).

1. Suchen Sie nach „C++“, klicken Sie auf **Leeres Projekt**, geben Sie einen Namen an (in diesem Artikel wird „superfastcode“ verwendet), und klicken Sie auf **OK**.

    > [!Tip]
    > Wenn **Native Python-Entwicklungstools** in Visual Studio 2017 installiert ist, können Sie stattdessen mit der Vorlage **Python-Erweiterungsmodul** beginnen, die bereits vieles von dem enthält, was im Folgenden beschrieben wird. In dieser Vorgehensweise zeigt jedoch der Start mit einem leeren Projekt ausführlich die Erstellung des Erweiterungsmoduls. Sobald Sie den Prozess verstanden haben, spart Ihnen die Vorlage Zeit beim Schreiben Ihrer eigenen Erweiterungen.

1. Erstellen Sie eine C++-Datei im neuen Projekt, indem Sie mit der rechten Maustaste auf den Knoten **Quelldateien** klicken, **Hinzufügen > Neues Element...** und dann **C++-Datei** auswählen und es benennen (z.B. `module.cpp`). Klicken Sie dann auf **OK**.

    > [!Important]
    > Eine Datei mit der `.cpp`-Erweiterung wird benötigt, um die C++-Eigenschaftsseiten in den folgenden Schritten zu aktivieren.

1. Klicken Sie mit der rechten Maustaste auf das C++-Projekt in der Projektmappe, und klicken Sie auf **Eigenschaften**.

1. Legen Sie **Konfiguration** am oberen Rand des angezeigten Dialogfelds **Eigenschaftenseiten** auf **Alle Konfigurationen** und **Plattform** auf **Win32** fest.

1. Legen Sie die spezifischen Eigenschaften wie in der folgenden Tabelle beschrieben fest, und klicken Sie auf **OK**.

    | Registerkarte | Eigenschaft | Wert |
    | --- | --- | --- |
    | Allgemein | Allgemein > Zielname | Geben Sie den Namen des Moduls so an, wie er von Python in `from...import`-Anweisungen verwendet werden soll. Sie verwenden diesen Namen in C++, wenn Sie das Modul für Python definieren. Wenn Sie den Namen des Projekts als Modulnamen verwenden möchten, behalten Sie den Standardwert `$(ProjectName)` bei. |
    | | Allgemein > Zielerweiterung | .pyd |
    | | Projektstandards > Konfigurationstyp | Dynamische Bibliothek (.dll) |
    | C/C++ > Allgemein | Zusätzliche Includeverzeichnisse | Fügen Sie den für Ihre Installation geeigneten Python `include`-Ordner hinzu, z.B. `c:\Python36\include`.  |
    | C/C++ > Präprozessor | Präprozessordefinitionen | Fügen Sie `Py_LIMITED_API;` (einschließlich des Semikolons) zum Anfang der Zeichenfolge hinzu. Durch diese Definition werden einige Funktionen eingeschränkt, die Sie aus Python aufrufen können, und der Code wird zwischen unterschiedlichen Python-Versionen portabler. |
    | C/C++ > Codegenerierung | Laufzeitbibliothek | Multithreaded-DLL (/MD) (siehe Warnung unten) |
    | Linker > Allgemein | Zusätzliche Bibliotheksverzeichnisse | Fügen Sie den für Ihre Installation geeigneten Python `libs`-Ordner hinzu, der `.lib`-Dateien enthält, z.B. `c:\Python36\libs`. (Achten Sie darauf, dass Sie auf den `libs`-Ordner zeigen, der `.lib`-Dateien enthält und *nicht* auf den `Lib`-Ordner, der `.py`-Dateien enthält.) |

    > [!Tip]
    > Wenn die Registerkarte „C/C++“ nicht in den Projekteigenschaften angezeigt wird, enthält das Projekt keine Dateien, die als C/C++-Quelldateien identifiziert werden. Diese Bedingung kann auftreten, wenn Sie eine Quelldatei ohne eine `.c`- oder `.cpp`-Erweiterung erstellen. Wenn Sie zuvor versehentlich `module.coo` statt `module.cpp` im Dialogfeld „Neues Element“ eingegeben haben, erstellt Visual Studio die Datei, legt den Dateityp jedoch nicht auf „C/C++-Code“ fest, was die Registerkarte „C/C++-Eigenschaften“ aktiviert. Solche falschen Identifizierungen können auch auftreten, wenn Sie die Datei mit `.cpp` umbenennen. Zum Festlegen des korrekten Dateityps klicken Sie mit der rechten Maustaste auf die Datei im Projektmappen-Explorer, wählen **Eigenschaften** aus und legen **Dateityp** auf **C/C++-Code** fest.

    > [!Warning]
    > Legen Sie die Option **C/C++ > Codegenerierung > Runtimebibliothek** auch für eine Debugkonfiguration immer auf „Multithreaded-DLL (/MD)“ fest, da durch diese Einstellung die Python-Binärdateien erstellt werden, die nicht für das Debuggen verwendet werden. Wenn Sie die Option „Multithreaded-DLL (/MD)“ festlegen, wird durch das Erstellen einer Debugkonfiguration der Fehler *C1189: Py_LIMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS, and Py_REF_DEBUG* (C1189: Py_LIMITED_API ist nicht kompatibel mit Py_DEBUG, Py_TRACE_REFS und Py_REF_DEBUG.) ausgelöst. Wenn Sie darüber hinaus `Py_LIMITED_API` entfernen, um den Buildfehler zu vermeiden, stürzt Python beim Versuch, das Modul zu importieren, ab. (Der Absturz geschieht, so wie später beschrieben, innerhalb des DLL-Aufrufs von `PyModule_Create`, mit der Ausgabemeldung *Fatal Python error: PyThreadState_Get: no current thread* (Schwerwiegender Python-Fehler: PyThreadState_Get: kein aktueller Thread.))
    >
    > Die /MDd-Option wird zum Erstellen der Python-Debugbinärdateien (z.B. „python_d.exe“) verwendet. Wenn Sie sie jedoch für eine Erweiterungs-DLL verwenden, wird weiterhin der Buildfehler mit `Py_LIMITED_API` verursacht.

1. Klicken Sie mit der mit der rechten Maustaste auf das C++-Projekt, und wählen Sie **Erstellen**aus, um Ihre Konfigurationen (Debug und Release) zu testen. Die `.pyd`-Dateien sind im Ordner *Lösung* unter **Debug** und **Release** und nicht im C++-Projektordner selbst zu finden.

1. Fügen Sie der Datei `module.cpp` des C++-Projekts folgenden Code hinzu:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Erstellen Sie das C++-Projekt erneut, um zu bestätigen, dass Ihr Code korrekt ist.

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Konvertieren des C++-Projekts in eine Erweiterung für Python

Sie müssen die exportierten Methoden zunächst so anpassen, dass Sie mit den Python-Typen interagieren, um die C++-DLL in eine Python-Erweiterung konvertieren zu können. Anschließend fügen Sie eine Funktion hinzu, die das Modul zusammen mit den Definitionen der Modulmethoden exportiert.

Hintergrundinformationen zu dem, was in diesem Abschnitt für Python 3.x gezeigt wird, finden Sie im [Python/C++-API-Referenzhandbuch](https://docs.python.org/3/c-api/index.html) und insbesondere in den [Modulobjekten](https://docs.python.org/3/c-api/module.html) auf python.org. (Denken Sie daran, Ihre Python-Version oben rechts im Dropdownmenü auszuwählen, um die richtige Dokumentation anzuzeigen).

Beziehen Sie sich bei der Arbeit mit Python 2.7 stattdessen auf die Artikel [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html) (Erweitern von Python 2.7 mit C oder C++) und [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html) (Portierung von Erweiterungsmodulen auf Python 3) (python.org).

1. Fügen Sie `Python.h` oben zur C++-Datei hinzu:

    ```cpp
    #include <Python.h>
    ```

1. Ändern Sie die `tanh_impl`-Methode, um Python-Typen (d.h. ein `PyOjbect*`-Objekt) zu akzeptieren und zurückzugeben:

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Fügen Sie eine Struktur hinzu, die definiert, wie die `tanh_impl`-Funktion von C++ Python angezeigt wird:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Fügen Sie eine Struktur hinzu, die das Modul so definiert, wie Sie im Python-Code darauf verweisen möchten, insbesondere bei Verwendung der `from...import`-Anweisung. (Stellen Sie sicher, dass dies mit dem Wert in den Projekteigenschaften unter **Konfigurationseigenschaften > Allgemein > Zielname** übereinstimmt.) Im folgenden Beispiel bedeutet der Modulname „superfastcode“, dass Sie `from superfastcode import fast_tanh` in Python verwenden können, da `fast_tanh` in `superfastcode_methods` definiert ist. (Dateinamen innerhalb des C++-Projekts wie „module.cpp“ sind nicht von Bedeutung.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Fügen Sie eine Methode hinzu, die Python aufruft, wenn das Modul geladen wird, die `PyInit_<module-name>` genannt werden muss, wobei *&lt;module_name&gt;* genau mit der Eigenschaft **Allgemein > Zielname** des C++-Projekts übereinstimmt (das bedeutet, dass sie mit dem Dateinamen von `.pyd` übereinstimmt, der vom Projekt erstellt wird).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Legen Sie die Zielkonfiguration auf „Release“ fest, und erstellen Sie das C++-Projekt erneut, um Ihren Code zu überprüfen. Wenn Fehler auftreten, überprüfen Sie Folgendes:
    - Python.h kann nicht gefunden werden (*E1696: cannot open source file „Python.h“* (E1696: Die Quelldatei „Python.h“ kann nicht geöffnet werden.) und/oder *C1083: Cannot open include file: „Python.h“: No such file or directory* (C1083: Die Includedatei „Python.h“ kann nicht geöffnet werden: Datei oder Verzeichnis nicht vorhanden.): Stellen Sie sicher, dass der Pfad in **C/C++ > Allgemein > Zusätzliche Includeverzeichnisse** in den Projekteigenschaften auf den `include`-Ordner Ihrer Python-Installation festgelegt ist. Siehe Schritt 6 unter [Erstellen des wesentlichen C++-Projekts](#create-the-core-c-project).
    - Die Python-Bibliotheken konnten nicht gefunden werden: Überprüfen Sie, ob der Pfad in **Linker > Allgemein > Zusätzliche Bibliotheksverzeichnisse** in den Projekteigenschaften auf den `libs`-Ordner Ihrer Python-Installation zeigt. Siehe Schritt 6 unter [Erstellen des wesentlichen C++-Projekts](#create-the-core-c-project).
    - Linker-Fehler im Zusammenhang mit der Zielarchitektur: Ändern Sie die Zielarchitektur des C++-Projekts so, dass sie mit der Ihrer Python-Installation übereinstimmt. Wenn Sie z.B. mit dem C++-Projekt auf x64 abzielen, aber Ihre Python-Installation ein x86-System ist, ändern Sie das C++-Projekt auf x86 ab.

## <a name="test-the-code-and-compare-the-results"></a>Testen des Codes und Vergleichen der Ergebnisse

Da Sie nun die DLL als Python-Erweiterung strukturiert haben, können Sie sich vom Python-Projekt auf sie beziehen, das Modul importieren und die Methoden verwenden.

### <a name="make-the-dll-available-to-python"></a>Verfügbarmachen der DLL für Python

Es gibt zwei Methoden, um die DLL Python zur Verfügung zu stellen.

Die erste Methode funktioniert, wenn das Python-Projekt und das C++-Projekt sich in derselben Projektmappe befinden. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** Ihres Python-Projekts, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie in dem angezeigten Dialogfeld auf die Registerkarte **Projekte** und anschließend auf das**superfastcode**-Projekt (oder den von Ihnen festgelegten Namen) und **OK**.

![Hinzufügen eines Verweises auf das superfastcode-Projekt](media/cpp-add-reference.png)

Durch die alternative Methode, die in den folgenden Schritten beschrieben wird, wird das Modul in der globalen Python-Umgebung installiert. Dadurch wird es ebenfalls für andere Python-Projekte zur Verfügung gestellt. (In der Regel erfordert dies, dass Sie die IntelliSense-Vervollständigungsdatenbank für diese Umgebung in Visual Studio 2017 Version 15.5 und früher aktualisieren. Eine Aktualisierung ist ebenfalls erforderlich, wenn das Modul aus der Umgebung entfernt wird.)

1. Wenn Sie Visual Studio 2017 verwenden, führen Sie den Visual Studio-Installer aus, wählen Sie **Ändern** aus und anschließend **Einzelne Komponenten > Compiler, Buildtools und Runtimes > Visual C++ 2015.3 v140-Toolset**. Dieser Schritt ist notwendig, da Python (für Windows) selbst mit Visual Studio 2015 (Version 14.0) erstellt wurde und erwartet, dass diese Tools beim Erstellen einer Erweiterung über die hier beschriebene Methode verfügbar ist. (Beachten Sie, dass Sie möglicherweise eine 32-Bit-Version von Python installieren müssen, um die DLL auf Win32 statt x64 auszurichten.)

1. Erstellen Sie in Ihrem C++-Projekt eine Datei mit dem Namen `setup.py`, indem Sie mit der rechten Maustaste auf Projekt klicken und anschließend auf **Hinzufügen > Neues Element...**. Klicken Sie dann auf „C++-Datei (.cpp)“, nennen Sie die Datei `setup.py`, und klicken Sie anschließend auf **OK** (wenn Sie die Datei mit der `.py`-Erweiterung benennen, erkennt Visual Studio sie als Python an, obwohl die C++-Dateivorlage verwendet wird). Wenn die Datei im Editor angezeigt wird, fügen Sie den nachstehenden Code ein:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Weitere Informationen zur Dokumentation für dieses Skript finden Sie unter [Building C and C++ Extensions (Erstellen von C- und C++-Erweiterungen)](https://docs.python.org/3/extending/building.html) (python.org).

1. Der `setup.py`-Code weist Python an, die Erweiterung mithilfe des C++-Toolsets von Visual Studio 2015 zu erstellen, wenn Sie auf der Befehlszeile verwendet wird. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, navigieren Sie zum Ordner mit dem C++-Projekt (d.h. der Ordner, der `setup.py` enthält), und geben Sie den folgenden Befehl ein:

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Aufrufen der DLL von Python

Wenn Sie eine der oben genannten Methoden abgeschlossen haben, können Sie die `fast_tanh`-Funktion aus dem Python-Code aufrufen und deren Leistung mit der Python-Implementierung vergleichen:

1. Fügen Sie die folgenden Zeilen zu der `.py`-Datei hinzu, um die `fast_tanh`-Methode aufzurufen, die aus der DLL exportiert wurde, und zeigen Sie deren Ausgabe an.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Wenn Sie das Python-Programm ausführen (**Debuggen > Starten ohne Debuggen** oder STRG+F5), können Sie beobachten, dass die C++-Routine fünf- bis zwanzigmal schneller als die Python-Implementierung ausgeführt wird. Eine typische Ausgabe sieht wie folgt aus:

    ```output
    Running benchmarks with COUNT = 500000
    sequence_tanh took 1.542 seconds

    [tanh(x) for x in d] took 1.087 seconds

    [fast_tanh(x) for x in d] took 0.158 seconds
    ```

1. Versuchen Sie die `COUNT`-Variable zu vergrößern, sodass die Unterschiede deutlicher werden. Beachten Sie, dass ein Debugbuild des C++-Moduls zudem langsamer als ein Releasebuild ausgeführt wird, da der Debugbuild weniger optimiert ist und verschiedene Fehlerprüfungen enthält. Sie können zum Vergleich zwischen diesen Konfigurationen wechseln.

## <a name="debug-the-c-code"></a>Debuggen des C++-Codes

Visual Studio unterstützt das gemeinsame Debuggen von Python- und C++-Code.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Python-Projekt, wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus, und wählen Sie anschließend die Option **Debuggen > Debuggen von nativem Code aktivieren** aus.

    > [!Tip]
    > Wenn Sie das Debuggen von nativem Code aktivieren, kann das Python-Ausgabefenster möglicherweise sofort verschwinden, wenn das Programm ohne die übliche Pause „Drücken Sie eine beliebige Taste, um fortzufahren...“ abgeschlossen wurde. Um eine Pause zu erzwingen, fügen Sie die `-i`-Option dem Feld **Ausführen > Interpreterargumente** auf der Registerkarte **Debuggen** hinzu, wenn Sie das Debuggen von nativem Code aktivieren. Durch dieses Argument wird der Python-Interpreter in den interaktiven Modus versetzt, nachdem der Code beendet wurde. Zu diesem Zeitpunkt wartet er darauf, dass Sie zum Beenden STRG + Z, EINGABETASTE drücken. (Wenn es Ihnen nichts ausmacht, Ihren Python-Code zu ändern, können Sie auch `import os`- und `os.system("pause")`-Anweisungen an das Ende Ihres Programms hinzufügen. Durch diesen Code wird die ursprüngliche Aufforderung zur Pause dupliziert.)

1. Klicken Sie auf **Datei > Speichern**, um die Änderungen an den Eigenschaften zu speichern.

1. Legen Sie die Buildkonfiguration in der Visual Studio-Symbolleiste „Debuggen“ fest.

    ![Festlegen der Buildkonfiguration auf „Debuggen“](media/cpp-set-debug.png)

1. Da es in der Regel länger dauert, Code im Debugger auszuführen, sollten Sie die `COUNT`-Variable in der `.py`-Datei auf einen fünfmal niedrigeren Wert (z.B. von `500000` auf `100000`) festlegen.

1. Legen Sie einen Haltepunkt auf der ersten Zeile der `tanh_impl`-Methode in Ihrem C++-Code fest, und starten Sie anschließend den Debugger (F5 oder **Debuggen > Debuggen starten**). Der Debugger wird angehalten, wenn dieser Code aufgerufen wird. Wenn der Haltepunkt nicht getroffen wird, überprüfen Sie, ob die Konfiguration auf „Debuggen“ festgelegt ist und Sie das Projekt gespeichert haben. (Dies geschieht nicht automatisch beim Starten des Debuggers).

    ![Anhalten an einem Haltepunkt im C++-Code](media/cpp-debugging.png)

1. An diesem Punkt können Sie den C++-Code schrittweise durchgehen, Variablen prüfen, etc. Diese Funktionen werden detailliert unter [Gemeinsames Debuggen von Python und C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) beschrieben.

## <a name="alternative-approaches"></a>Alternative Ansätze

Es gibt wie in der folgenden Tabelle beschrieben verschiedene Methoden zum Erstellen von Python-Erweiterungen. Der erste Eintrag für CPython wurde in diesem Artikel bereits behandelt.

| Ansatz | Generation | Rechtsvertreter | Pro(s) | Kon(s) |
| --- | --- | --- | --- | --- |
| C/C++-Erweiterungsmodule für CPython | 1991 | Standardbibliothek | [Ausführliche Dokumentation und Tutorials](https://docs.python.org/3/c-api/) Vollständige Kontrolle. | Kompilierung, Portabilität, Verweisverwaltung Hohe C-Kenntnisse. |
| [pybind11](https://github.com/pybind/pybind11) (empfohlen für C++) | 2015 |  | Einfache, reine Headerbibliothek zur Erstellung von Python-Bindungen von bestehendem C++-Code Wenige Abhängigkeiten PyPy-Kompatibilität | Neuer, weniger ausgefeilt Vermehrter Einsatz von C++11-Features Kurze Liste unterstützter Compiler (Visual Studio ist enthalten) |
| Cython (empfohlen für C) | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Python-ähnlich. Sehr fortgeschrittenen. Hohe Leistung. | Kompilierung, neue Syntax, neue Toolkette. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Funktioniert mit nur nahezu jedem C++-Compiler. | Große und komplexe Sammlung von Bibliotheken; enthält viele Problemumgehungen für alte Compiler. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Keine Kompilierung, breite Verfügbarkeit | Unpraktisches und fehleranfälliges Zugreifen und Mutieren von C-Strukturen |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generieren von Bindungen gleichzeitig für mehrere Sprachen | Übermäßiger Mehraufwand, wenn Python das einzige Ziel darstellt |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Einfache Integration, PyPy-Kompatibilität | Neuer, weniger ausgefeilt |

## <a name="see-also"></a>Siehe auch

Das abgeschlossene Beispiel aus dieser exemplarischen Vorgehensweise finden Sie unter [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).