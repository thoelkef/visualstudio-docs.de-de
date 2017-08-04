---
title: Arbeiten mit C++ und Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 3/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "Der Prozess und die Schritte zum Schreiben einer C++-Erweiterung oder eines -Moduls für Python in Visual Studio"
caps.latest.revision: 1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: f8a0bef07667e5f876473c966ed3d14a1b84dd0b
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="creating-a-c-extension-for-python"></a>Erstellen einer C++-Erweiterung für Python

Module, die in C++ (oder C#) geschrieben werden, werden häufig verwendet, um die Funktionen eines Python-Übersetzers zu erweitern sowie den Zugriff auf Fähigkeiten des Betriebssystem auf niedriger Ebene zu aktivieren. Es gibt drei Haupttypen von Modulen:

- Accelerator-Modul: Da Python eine interpretierte Sprache ist, können bestimmte Teile des Codes in C++ für höhere Leistung geschrieben werden. 
- Wrapper-Module: Legt vorhandene C/C++-Schnittstellen für Python-Code offen oder legt eine „Python-ähnlichere“ API offen, die Python-Sprachfeatures verwendet, um die Verwendung der API zu vereinfachen.
- Systemzugriffsmodule auf niedriger Ebene: Diese werden erstellt, um auf Features der CPython-Laufzeit auf niedriger Ebene, auf das Betriebssystem oder auf die zugrunde liegende Hardware zuzugreifen. 

Dieses Thema führt Sie durch die Erstellung eines C++-Erweiterungsmoduls für CPython, das einen Hyperbeltangens berechnet und diesen aus dem Python-Code abruft. Sie erstellen und testen die Routine zunächst in Python, um den Leistungsunterschied zu demonstrieren.

Der Ansatz hier gilt für CPython-Standarderweiterungen, so wie in der [Python-Dokumentation](https://docs.python.org/3/c-api/) beschrieben. Ein Vergleich zwischen dieser und anderen Maßnahmen ist unter [Alternative Ansätze](#alternative-approaches) am Ende dieses Themas beschrieben.

## <a name="prerequisites"></a>Erforderliche Komponenten

Diese exemplarische Vorgehensweise wurde für Visual Studio 2017 mit jeweils den Arbeitsauslastungen **Desktopentwicklung mit C++** und **Python-Entwicklung** mit den Standardoptionen (z.B. Python 3.6 als Standardinterpreter) geschrieben. Überprüfen Sie in der Arbeitsauslastung der **Python-Entwicklung** auch das Feld auf der rechten Seite für **Native Python-Entwicklungstools**, was den Großteil der in diesem Thema beschriebenen Optionen festlegt. (Diese Option enthält automatisch auch die C++-Arbeitsauslastung.) 

![Auswählen der Option „Native Python-Entwicklungstools“](~/python/media/cpp-install-native.png)

Weitere Details finden Sie unter [Installieren von Python-Unterstützung für Visual Studio](installation.md), einschließlich der Verwendung anderer Versionen von Visual Studio. Wenn Sie Python separat installieren, stellen Sie sicher, dass Sie **Download debugging symbols** (Debugsymbole herunterladen) und **Download debug binaries** (Debugbinärdateien herunterladen) unter **Erweiterte Optionen** im Installer auswählen. Dadurch wird sichergestellt, dass Sie über die erforderlichen Debugbibliotheken verfügen, wenn Sie einen Debugbuild ausführen.

> [!Note]
> Python ist auch über die Arbeitsauslastung **Data Science und analytische Anwendungen** verfügbar, zu der standardmäßig Anaconda 3 64-Bit (mit der neuesten Version von CPython) und die Option **Native Python-Entwicklungstools** gehören.

## <a name="create-the-python-application"></a>Erstellen der Python-Anwendung

1. Erstellen Sie ein neues Python-Projekt in Visual Studio durch Auswählen des Menübefehls **Datei > Neu > Projekt**. Anschließend suchen Sie nach „Python“ und wählen die Vorlage **Python-Anwendung** aus. Nachdem Sie sie benannt haben und einen passenden Speicherort ausgewählt haben, wählen Sie **OK** aus.

1. Fügen Sie in der `.py`-Datei des Projekts den folgenden Code ein, der die Berechnung eines Hyperbeltangens durchführt (Dieser wird ohne Verwendung der mathematischen Bibliothek zum einfacheren Vergleich implementiert). Geben Sie den Code gerne manuell ein, um einige der [Bearbeitungsfunktionen von Python](code-editing.md) kennenzulernen.

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
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
        '''Applies the hyperbolic tanger function to map all values in
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
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Führen Sie das Programm mit **Debuggen > Starten ohne Debuggen** (STRG + F5) aus, um die Ergebnisse anzuzeigen. Sie sehen, dass jeder Vergleichstest einige Sekunden benötigt, bis er abgeschlossen ist.

## <a name="create-the-core-c-project"></a>Erstellen des wesentlichen C++-Projekts

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Hinzufügen > Neues Projekt...** aus. Eine Visual Studio-Projektmappe kann jeweils Python- und C++-Projekte enthalten.

1. Wählen Sie in der „C++“-Suche **Leeres Projekt** aus, geben Sie ihm einen Namen (z.B: TanhBenchmark), und wählen Sie **OK** aus. Hinweis: Wenn Sie **Native Python-Entwicklungstools** mit Visual Studio 2017 installiert haben, können Sie mit der Vorlage **Python-Erweiterungsmodul** beginnen, das zum größten Teil schon hier beschrieben wird. In dieser Vorgehensweise zeigt jedoch der Start mit einem leeren Projekt ausführlich die Erstellung des Erweiterungsmoduls.

1. Erstellen Sie eine C++-Datei im neuen Projekt, indem Sie mit der rechten Maustaste auf den Knoten **Quelldateien** klicken, **Hinzufügen > Neues Element...** und dann **C++-Datei** auswählen und ihm anschließend einen Namen geben (z.B. `module.cpp`). Klicken Sie dann auf **OK**. Dieser Schritt ist erforderlich, um die C++-Eigenschaftenseiten in den nächsten Schritten zu aktivieren.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Am oberen Ende des Dialogfelds **Eigenschaftenseiten**, das daraufhin angezeigt wird, legen Sie **Konfiguration** auf **Alle Konfigurationen** fest.

1. Legen Sie die spezifischen Eigenschaften so wie unten beschrieben fest, und wählen Sie **Anwenden** aus (möglicherweise müssen Sie außerhalb eines editierbaren Felds klicken, damit die Schaltfläche **Anwenden** aktiviert wird).

    | Registerkarte | Eigenschaft | Wert | 
    | --- | --- | --- |
    | Allgemein | Allgemein > Zielname | Legen Sie diesen fest, damit er genau mit dem Namen des Moduls übereinstimmt, so wie es bei Python angezeigt wird. |
    | | Allgemein > Zielerweiterung | .pyd |
    | | Projektstandards > Konfigurationstyp | Dynamische Bibliothek (.dll) |
    | C/C++ > Allgemein | Zusätzliche Includeverzeichnisse | Fügen Sie den für Ihre Installation geeigneten Python `include`-Ordner hinzu, z.B. `c:\Python36\include`. |     
    | C/C++ > Codegenerierung | Laufzeitbibliothek | Multithreaded-DLL (/MD) (siehe Warnung unten) |
    | C/C++ > Präprozessor | Präprozessordefinitionen | Fügen Sie `Py_LIMITED_API;` zum Anfang der Zeichenfolge hinzu. Dadurch werden einige Funktionen eingeschränkt, die Sie aus Python aufrufen können. Dadurch wird der Code zwischen unterschiedlichen Python-Versionen portabler. |
    | Linker > Allgemein | Zusätzliche Bibliotheksverzeichnisse | Fügen Sie den für Ihre Installation geeigneten Python `lib`-Ordner hinzu, der `.lib`-Dateien enthält, z.B. `c:\Python36\libs`. (Achten Sie darauf, dass Sie auf den `libs`-Ordner zeigen, der `.lib`-Dateien enthält und *nicht* auf den `Lib`-Ordner, der `.py`-Dateien enthält.) | 

    > [!Tip]
    > Wenn die C/C++-Registerkarte nicht angezeigt wird, ist dafür der Grund, dass das Projekt keine Dateien enthält, die als C/C++-Quelldateien identifiziert werden. Dies kann geschehen, wenn Sie eine Quelldatei ohne eine `.c`- oder `.cpp`-Erweiterung. Wenn Sie zuvor versehentlich `module.coo` statt `module.cpp` im Dialogfeld „Neues Element“ eingegeben haben, erstellt Visual Studio die Datei, legt den Dateityp jedoch nicht auf „C/C++-Code“ fest, was die Registerkarte „C/C++-Eigenschaften“ aktiviert. Wenn Sie die Datei mit `.cpp` umbenennen, bleibt dies auch der Fall. Zum Beheben dieses Fehlers klicken Sie mit der rechten Maustaste auf die Datei im Projektmappen-Explorer, wählen **Eigenschaften** aus und legen **Dateityp** auf **C/C++-Code** fest.

    > [!Warning]
    > Legen Sie die Option **C/C++ > Codegenerierung > Runtime Library** nicht auf „Multithreaded-Debug-DLL (/MDd)“ fest, auch nicht für eine Debugkonfiguration. Sie müssen die Laufzeit „Multithreaded-DLL (/MD)“ auswählen, denn aus dieser wurden die Nichtdebug-Binärdateien von Python erstellt. Wenn Sie die /MDd-Option festlegen, wird ein Fehler angezeigt *C1189: Py_LIMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS, and Py_REF_DEBUG* (C1189: Py_LIMITED_API ist nicht mit Py_DEBUG, Py_TRACE_REFS und Py_REF_DEBUG kompatibel), wenn Sie eine Debugkonfiguration Ihrer DLL erstellen. Wenn Sie darüber hinaus `Py_LIMITED_API` entfernen, um den Buildfehler zu vermeiden, stürzt Python beim Versuch, das Modul zu importieren, ab. (Der Absturz geschieht, so wie später beschrieben, innerhalb des DLL-Aufrufs von `PyModule_Create`, mit der Ausgabemeldung *Fatal Python error: PyThreadState_Get: no current thread* (Schwerwiegender Python-Fehler: PyThreadState_Get: kein aktueller Thread).
    >
    > Beachten Sie, dass die /MDd-Option zum Erstellen der Python-Debugbinärdateien (z.B. „python_d.exe“) verwendet wird. Wenn Sie sie jedoch für eine Erweiterungs-DLL verwenden, wird weiterhin der Buildfehler mit `Py_LIMITED_API` erstellt.
   
1. Klicken Sie mit der mit der rechten Maustaste auf das C++-Projekt, und wählen Sie **Erstellen**aus, um Ihre Konfigurationen (Debug und Release) zu testen. Beachten Sie, dass Sie die `.pyd`-Dateien im Ordner *Lösung* unter **Debug** und **Release** und nicht im C++-Projektordner selbst finden.

1. Fügen Sie der Hauptdatei `.cpp` des C++-Projekts folgenden Code hinzu:

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

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. Erstellen Sie das C++-Projekt erneut, um zu bestätigen, dass Ihr Code korrekt ist.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Konvertieren des C++-Projekts in eine Erweiterung für Python

Sie müssen die exportierte Methode so verändern, dass Sie mit den Python-Typen interagiert, damit Sie die C++-DLL in eine Erweiterung für Python konvertieren können. Anschließend müssen Sie eine Funktion hinzufügen, die das Modul zusammen mit Definitionen der Modulmethoden exportiert. Um weitere Hintergrundinformationen zu dem hier Gezeigten zu erhalten, lesen Sie das [Python/C API Reference Manual (Python(C-API-Referenzhandbuch)](https://docs.python.org/3/c-api/index.html) und vor allem die Seite [Module Objects (Modulobjekte)](https://docs.python.org/3/c-api/module.html) auf python.org. (Denken Sie daran, Ihre Python-Versionen aus dem Dropdown-Steuerelement in der oberen rechten Ecke auszuwählen.)

1. Fügen Sie `Python.h` oben zur C++-Datei hinzu:

    ```cpp
    include <Python.h>
    ```

1. Ändern Sie die `tanh`-Methode, um die Python-Typen zu akzeptieren und zurückzugeben:

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Fügen Sie eine Struktur hinzu, die definiert, wie die `tanh`-Funktion von C++ Python angezeigt wird:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Fügen Sie eine Struktur hinzu, die das Modul definiert, wie es Python angezeigt wird:

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Fügen Sie eine Methode hinzu, die Python aufruft, wenn das Modul geladen wird, die `PyInit_<module-name>` genannt werden muss, wobei *&lt;module_name&gt;* genau mit der Eigenschaft **Allgemein > Zielname** des C++-Projekts übereinstimmt (das bedeutet, dass sie mit dem Dateinamen von `.pyd` übereinstimmt, der vom Projekt erstellt wird).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Erstellen Sie die DLL erneut, um Ihren Code zu überprüfen.

## <a name="test-the-code-and-compare-the-results"></a>Testen des Codes und Vergleichen der Ergebnisse

Da Sie nun die DLL als Python-Erweiterung strukturiert haben, können Sie sich vom Python-Projekt auf sie beziehen, das Modul importieren und die Methoden verwenden.

Es gibt zwei Methoden, um die DLL Python zur Verfügung zu stellen. Sie können eine Referenz des Python-Projekts zum C++-Projekt hinzufügen, vorausgesetzt, sie befinden sich in derselben Visual Studio-Projektmappe:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Python-Projekt, und wählen Sie **Verweise** aus. Wählen Sie im Dialogfeld die Registerkarte **Projekte** aus, wählen Sie **superfastcode** aus und anschließend **OK**.

Sie können das Modul alternativ in der globalen Python-Umgebung installieren, wodurch es auch für andere Python-Projekte verfügbar wird. Beachten Sie, dass diese Methode in der Regel vorsieht, dass Sie die IntelliSense-Vervollständigungsdatenbank für diese Umgebung aktualisieren und das Modul aus der Umgebung entfernen.

1. Wenn Sie Visual Studio 2017 verwenden, führen Sie den Visual Studio-Installer aus, wählen Sie **Ändern** aus und anschließend **Einzelne Komponenten > Compiler, Buildtools und Runtimes > Visual C++ 2015.3 v140-Toolset**. Der Grund dafür ist, dass Python (für Windows) selbst mit Visual Studio 2015 (Version 14.0) erstellt wurde und erwartet, dass diese Tools beim Erstellen einer Erweiterung über die hier beschriebene Methode verfügbar ist.

1. Erstellen Sie eine Datei mit dem Namen `setup.py` in Ihrem C++-Projekt, indem Sie mit der rechten Maustaste auf das Projekt klicken, *Hinzufügen > Neue Elemente...* auswählen, nach „Python“ suchen und **Python-Datei** auswählen. Nennen Sie diese „setup.py“, und klicken Sie auf **OK**. Wenn die Datei im Editor angezeigt wird, fügen Sie den nachstehenden Code ein:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Weitere Informationen zur Dokumentation für diese Skript finden Sie unter [Building C and C++ Extentions (Erstellen von C- und C++-Erweiterungen)](https://docs.python.org/3/extending/building.html) (python.org).

1. Der `setup.py`-Code weist Python an, die Erweiterung (mithilfe des C++-Toolsets von Visual Studio 2015) zu erstellen, was auf der Befehlszeile geschieht. Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten, und navigieren Sie zum Ordner mit dem C++-Projekt (und `setup.py`), und geben Sie den folgenden Befehl ein:

    ```bash
    pip install .
    ```

Sie können nun den `tanh`-Code des Moduls aufrufen und dessen Leistung mit der Python-Implementierung vergleichen:

1. Fügen Sie die folgenden Zeilen zu `tanhbenchmark.py` hinzu, um die `fast_tanh`-Methode aufzurufen, die aus der DLL exportiert wurde. Fügen Sie diese anschließend der Vergleichstestausgabe hinzu. Wenn Sie die `from s`-Anweisung manuell eingeben, wird `superfastcode` in der Liste angezeigt. Nachdem Sie `import` eingegeben haben, wird die `fast_tanh`-Methode angezeigt.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Führen Sie das Python-Programm aus, und Sie sehen, dass die C++-Routine etwa 15 bis 20 mal schneller als die Python-Implementierung ausgeführt wird.

## <a name="debug-the-c-code"></a>Debuggen des C++-Codes

[Die Unterstützung von Python in Visual Studio](debugging-mixed-mode.md) bietet die Möglichkeit, [Python- und C++-Code zusammen zu debuggen](installation.md). Um dies zu tun, führen Sie die folgenden Schritte aus:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Python-Projekt, wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus, und wählen Sie anschließend die Option **Debuggen > Debuggen von nativem Code aktivieren** aus.

    > [!Tip]
    > Wenn Sie das Debuggen von nativem Code aktivieren, kann das Python-Ausgabefenster möglicherweise sofort verschwinden, wenn das Programm ohne die übliche Pause „Drücken Sie eine beliebige Taste, um fortzufahren...“ abgeschlossen wurde. Um eine Pause zu erzwingen, fügen Sie die `-i`-Option dem Feld **Ausführen > Interpreterargumente** auf der Registerkarte **Debuggen** hinzu, wenn Sie das Debuggen von nativem Code aktivieren. Dadurch wird der Python-Interpreter in den aktiven Modus versetzt, nachdem der Code beendet wurde. Zu diesem Zeitpunkt wartet er, dass Sie STRG + Z, EINGABETASTE drücken, um die Anwendung zu beenden. (Wenn es Ihnen nichts ausmacht, Ihren Python-Code zu ändern, können Sie auch `import os`- und `os.system("pause")`-Anweisungen an das Ende Ihres Programms hinzufügen. Dadurch wird die ursprüngliche Aufforderung zur Pause dupliziert.)

1. Legen Sie einen Haltepunkt auf der ersten Zeile innerhalb der `tanh`-Methode in Ihrem C++-Code fest, und starten Sie anschließend den Debugger. Der Debugger wird angehalten, wenn folgender Code aufgerufen wird:

    ![Anhalten an einem Haltepunkt im C++-Code](~/python/media/cpp-debugging.png)

1. An diesem Punkt können Sie den C++-Code schrittweise durchlaufen, Variablen untersuchen, usw., so wie in [Debugging C++ and Python Together (Gleichzeitiges Debuggen von C++ und Python)](debugging-mixed-mode.md) beschrieben.

## <a name="alternative-approaches"></a>Alternative Ansätze 

Es gibt andere Methoden, um Python-Erweiterungen zu erstellen, wie in der folgenden Tabelle beschrieben. Der erste Eintrag für CPython wurde bereits in diesem Thema behandelt.

| Ansatz | Generation | Rechtsvertreter | Pro(s) | Kon(s) |
| --- | --- | --- | --- | --- |
| C/C++-Erweiterungsmodule für CPython | 1991 | Standardbibliothek | [Ausführliche Dokumentation und Tutorials](https://docs.python.org/3/c-api/) Vollständige Kontrolle. | Kompilierung, Portabilität, Verweisverwaltung Hohe C-Kenntnisse. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generieren von Bindungen gleichzeitig für mehrere Sprachen | Übermäßiger Mehraufwand, wenn Python das einzige Ziel darstellt |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Keine Kompilierung, breite Verfügbarkeit | Unpraktisches und fehleranfälliges Zugreifen und Mutieren von C-Strukturen |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Python-ähnlich. Sehr fortgeschrittenen. Hohe Leistung. | Kompilierung, neue Syntax und Toolkette |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Einfache Integration, PyPy-Kompatibilität | Neu, weniger ausgefeilt |

