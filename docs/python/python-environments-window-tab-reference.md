---
title: "Referenz zum Fenster „Python-Umgebungen – Visual Studio | Microsoft-Dokumentation"
description: "Dieser Artikel beschreibt jede der Registerkarten, die im Fenster „Python-Umgebungen“ in Visual Studio angezeigt werden."
ms.custom: 
ms.date: 02/20/2018
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
ms.openlocfilehash: 92d5014c257cf35e556eca1928e1c5612f4913eb
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="python-environments-window-tabs-reference"></a>Referenz zu den Registerkarten im Fenster „Python-Umgebungen“

So öffnen Sie das Fenster **Python-Umgebungen**:

- Wählen Sie den Menübefehl **Ansicht > Weitere Fenster > Python-Umgebungen** aus.
- Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Python-Umgebungen** für ein Projekt, und wählen Sie **Alle Python-Umgebungen anzeigen** aus.

Wenn Sie das Fenster **Python-Umgebungen** weit genug erweitern, werden diese Optionen als Registerkarten angezeigt, was Ihre Arbeit damit erleichtern kann. Zur besseren Übersicht werden die Registerkarten in diesem Artikel in der erweiterten Ansicht angezeigt.

![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Registerkarte „Übersicht“

Bietet grundlegende Informationen und Befehle für die Umgebung:

![Registerkarte „Übersicht“ von Python-Umgebungen](media/environments-overview-tab.png)

| Befehl | description |
| --- | --- |
| Diese Umgebung zum Standard für neue Projekte machen | Legt die aktive Umgebung fest, die möglicherweise dazu führt, dass Visual Studio kurz nicht mehr reagiert, während die IntelliSense-Datenbank geladen wird. Umgebungen mit vielen Paketen reagieren möglicherweise längere Zeit nicht mehr. |
| Website des Verteilers besuchen | Öffnen eine von der Python-Verteilung bereitgestellt URL in einem Browser. Python 3.x öffnet beispielsweise python.org. |
| Interaktives Fenster öffnen | Öffnet das [interaktive Fenster (REPL)](python-interactive-repl-in-visual-studio.md) für diese Umgebung in Visual Studio und wendet alle [Startskripts (siehe unten)](#startup-scripts) an. |
| Interaktive Skripts | Siehe [Startskripte](#startup-scripts). |
| Interaktiven IPython-Modus verwenden | Wenn diese Option aktiviert ist, wird das interaktive Fenster standardmäßig mit Python geöffnet. Dadurch sind Inline-Plots und erweiterte IPython-Syntax möglich, wie z.B. `name?` zum Anzeigen der Hilfe und `!command` für Shellbefehle. Diese Option wird empfohlen, wenn Sie eine Verteilung von Anaconda verwenden, da diese zusätzliche Pakete erfordert. Weitere Informationen finden Sie unter [Verwenden von Python im interaktiven Fenster](interactive-repl-ipython.md). |
| In PowerShell öffnen | Öffnet den Interpreter in einem Befehlsfenster von PowerShell. |
| (Ordner- und Programmverknüpfungen) | Bieten Ihnen schnellen Zugriff auf den Installationsordner der Umgebung und die Interpreter „python.exe“ und „pythonw.exe“. Ersterer wird im Windows Explorer geöffnet, die anderen beiden in einem Konsolenfenster. |

### <a name="startup-scripts"></a>Startskripte

Beim Verwenden von interaktiven Fenstern in ihrem alltäglichen Workflow entwickeln Sie mit hoher Wahrscheinlichkeit Hilfsfunktionen, die Sie häufig verwenden. Möglicherweise erstellen Sie z.B. eine Funktion, die einen Datenrahmen in Excel öffnet. Dann können Sie den Code als Startskript speichern, sodass dieser immer über das interaktive Fenster verfügbar ist.

Startskripts enthalten Code, der vom interaktiven Fenster automatisch geladen und ausgeführt wird, einschließlich Importe, Funktionsdefinitionen und vieles mehr. Auf derartige Skripts kann auf zwei Weisen verwiesen werden:

1. Wenn Sie eine Umgebung installieren, erstellt Visual Studio einen Ordner `Documents\Visual Studio 2017\Python Scripts\<environment>`, in dem &lt;environment&gt' dem Namen der Umgebung entspricht. Sie können mit dem Befehl **Interaktive Skripts untersuchen** ganz leicht zum umgebungsspezifischen Ordner navigieren. Wenn Sie das interaktive Fenster für diese Umgebung starten, lädt es alle hier gefundenen `.py`-Dateien und führt diese in alphabetischer Reihenfolge aus.

1. Das Steuerelement **Skripts** auf der Registerkarte **Extras > Optionen > Python Tools > Interaktives Fenster** (siehe [Optionen für das interaktive Fenster](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) soll einen zusätzlichen Ordner für Startskripts angeben, die in allen Umgebungen geladen und ausgeführt werden. Diese Funktion funktioniert aktuell noch nicht.

## <a name="configure-tab"></a>Registerkarte „Konfigurieren“

Wenn diese Registerkarte verfügbar ist, enthält sie die in der folgenden Tabelle beschriebenen Details. Wenn diese Registerkarte nicht vorhanden ist, bedeutet dies, dass alle Details von Visual Studio automatisch verwaltet werden.

![Registerkarte „Konfigurieren“ von Python-Umgebungen](media/environments-configure-tab.png)

| Feld | description |
| --- | --- |
| **Beschreibung** | Der Name für die Umgebung. |
| **Präfixpfad** | Der Speicherort des Basisordners des Interpreters. Durch Festlegen dieses Werts und Klicken auf **Automatisch erkennen** versucht Visual Studio, die anderen Felder für Sie auszufüllen. |
| **Interpreterpfad** | Der Pfad zur ausführbaren Datei des Interpreters, üblicherweise der Präfixpfad gefolgt von `python.exe`. |
| **Fenstermodus-Interpreter** | Der Pfad zur ausführbaren Datei ohne Konsole, häufig der Präfixpfad gefolgt von `pythonw.exe`. |
| **Bibliothekspfad**<br/>(sofern verfügbar) | Gibt den Stamm der Standardbibliothek an. Dieser Wert kann allerdings ignoriert werden, wenn Visual Studio einen genaueren Pfad vom Interpreter anfordern kann. |
| **Sprachversion** | Wird im Dropdownmenü ausgewählt |
| **Architektur** | Wird normalerweise automatisch erkannt und ausgefüllt, andernfalls 32-Bit oder 64-Bit. |
| **Pfadumgebungsvariable** | Die Umgebungsvariable, die der Interpreter verwendet, um Suchpfade zu finden. Visual Studio ändert den Wert der Variablen, wenn Python gestartet wird, sodass sie die Suchpfade des Projekts enthält. In der Regel sollte diese Eigenschaft auf `PYTHONPATH` festgelegt werden, aber einige Interpreter verwenden einen anderen Wert. |

## <a name="packages-tab"></a>Registerkarte „Pakete“

*In früheren Versionen auch als „pip“ bezeichnet.*

Verwaltet die in der Umgebung installierten Pakete und ermöglicht Ihnen auch, neue Pakete zu suchen und zu installieren (einschließlich dazugehöriger Abhängigkeiten). Das Suchen filtert Ihre aktuell installierten Pakete und [PyPI](https://pypi.python.org). Sie können auch einen `pip install`-Befehl direkt in das Suchfeld eingeben, einschließlich der Flags wie z.B. `--user` oder `--no-deps`.

![Registerkarte mit Paketen in Python-Umgebungen](media/environments-pip-tab.png)

Durch das Installieren eines Pakets wird ein Unterordner im `Lib`-Ordner der Umgebung im Dateisystem erstellt. Wenn Sie z.B. Python 3.6 in `c:\Python36` installiert haben, werden Pakete in `c:\Python36\Lib` installiert. Wenn Sie Anaconda 3 in `c:\Program Files\Anaconda3` installiert haben, werden Pakete in `c:\Program Files\Anaconda3\Lib` installiert.

Im letzteren Fall muss Visual Studio `pip install` erhöht ausführen, damit es Unterordner erstellen kann, da die Umgebung sich in einem geschützten Bereich des Dateisystems befindet `c:\Program Files`. Wenn erhöhte Rechte erforderlich sind, zeigt Visual Studio folgende Aufforderung an: „Es sind möglicherweise Administratorberechtigungen erforderlich, um Pakete für diese Umgebung zu installieren, zu aktualisieren oder zu entfernen“:

![Eingabeaufforderung für erhöhte Rechte](media/environments-pip-elevate.png)

**Jetzt Rechte erweitern** erteilt Administratorrechte an „pip“ für einen einzigen Vorgang, auch gemäß Aufforderungen des Betriebssystems nach Berechtigungen. Wenn Sie **Ohne Administratorberechtigungen fortfahren** auswählen, wird die Installation des Pakets versucht, „pip“ schlägt allerdings beim Erstellen von Ordnern fehl. Die Ausgabe kann z.B. so aussehen: „error: could not create 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': Permission denied“ (Fehler: 'C:\Programme\Anaconda3\Lib\site-packages\png.py' konnte nicht erstellt werden: Berechtigung verweigert).

Wenn Sie **Beim Installieren oder Entfernen von Paketen immer Rechte erweitern** auswählen, wird verhindert, dass das Dialogfeld für die entsprechende Umgebung angezeigt wird. Wenn Sie möchten, dass das Dialogfeld wieder angezeigt wird, gehen Sie zu **Extras > Optionen > Python Tools > Allgemein**, und klicken Sie auf die Schaltfläche **Alle dauerhaft ausgeblendeten Dialogfelder zurücksetzen**.

Auf der gleichen Optionsregisterkarte können Sie auf **" pip" immer als Administrator ausführen** klicken, um das Dialogfeld für alle Umgebungen zu unterdrücken. Weitere Informationen finden Sie unter [Optionen > Registerkarte „Allgemein“](python-support-options-and-settings-in-visual-studio.md#general-options).

## <a name="intellisense-tab"></a>Registerkarte „IntelliSense“

Zeigt den aktuellen Status der IntelliSense-Vervollständigungsdatenbank:

![Registerkarte „IntelliSense“ von Python-Umgebungen](media/environments-intellisense-tab.png)

Die Datenbank enthält Metadaten für alle Bibliotheken der Umgebung, verbessert die Geschwindigkeit von IntelliSense und verringert die Speicherauslastung. Wenn Visual Studio eine neue Umgebung erkennt (oder wenn Sie eine hinzufügen), wird die Datenbank automatisch kompiliert, indem die Quelldateien der Bibliothek analysiert werden. Dieser Prozess kann eine Minute oder bis zu einer Stunde oder noch länger dauern, je nachdem, was installiert ist. (Zu Anaconda gehören z.B. viele Bibliotheken, und es dauert einige Zeit, die Datenbank zu kompilieren.) Wenn der Vorgang abgeschlossen ist, erhalten Sie detaillierte IntelliSense-Daten und müssen die Datenbank erst erneut aktualisieren (mit der Schaltfläche **DB aktualisieren**), wenn Sie weitere Bibliotheken installieren.

Bibliotheken, für die noch keine Daten kompiliert wurden, werden mit einem **!** gekennzeichnet. Wenn die Datenbank einer Umgebung nicht vollständig ist, wird daneben auch ein **!** in der Liste der wichtigsten Umgebungen angezeigt.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von "requirements.txt" für Abhängigkeiten](managing-required-packages-with-requirements-txt.md) 
- [Suchpfade](search-paths.md)
