---
title: "Debuggen im gemischten Modus in Python Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca86a87-e254-4ab7-b3ba-a0ab99c1da93
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
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: ddbac5b8ed52e6ed7afae7e7b04dc2fa15f7a0c2
ms.lasthandoff: 03/27/2017

---

# <a name="debugging-python-and-c-together"></a>Gemeinsames Debuggen von Python und C++

Die meisten Python-Debugger unterstützten das Debuggen nur von Python-Code. In der Praxis wird Python jedoch zusammen mit C oder C++ verwendet, wenn eine hohe Leistung erforderlich ist oder Plattform-APIs direkt aufgerufen werden müssen (Ein Beispiel finden Sie unter [Erstellen einer C++-Erweiterung für Python](cpp-and-python.md)). Visual Studio (unter Verwendung von Python-Tools für Visual Studio 2.0 und höher) bietet ein integriertes, simultanes Debuggen im gemischten Modus für Python und natives C/C++ mit folgenden Funktionen: kombinierte Aufruflisten, abwechselnde Einzelschrittausführung in Python und nativem Code, Haltepunkte in jedem Codetyp sowie die Möglichkeit, Python-Darstellungen von Objekten in nativen Frames und umgekehrt anzuzeigen:

![Debuggen im gemischten Modus](media/mixed-mode-debugging.png) 

Eine Einführung in das Erstellen, Testen und Debuggen von nativen C-Modulen mit Visual Studio sehen Sie in diesem Video: [Deep Dive: Creating Native Modules](https://youtu.be/D9RlT06a1EI) (youtube.com, 9 Minuten, 9 Sekunden).

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

## <a name="enabling-mixed-mode-debugging"></a>Aktivieren des Debuggens im gemischten Modus

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus, und aktivieren Sie die Option **Debuggen von nativem Code aktivieren**. Dadurch wird der gemischte Modus für alle Debugsitzungen aktiviert.

    ![Aktivieren des Debuggens von nativem Code](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > Wenn Sie das Debuggen von nativem Code aktivieren, kann das Python-Ausgabefenster möglicherweise sofort verschwinden, wenn das Programm ohne die übliche Pause „Drücken Sie eine beliebige Taste, um fortzufahren...“ abgeschlossen wurde. Um eine Pause zu erzwingen, fügen Sie die `-i`-Option dem Feld **Ausführen > Interpreterargumente** auf der Registerkarte **Debuggen** hinzu, wenn Sie das Debuggen von nativem Code aktivieren. Dadurch wird der Python-Interpreter in den aktiven Modus versetzt, nachdem der Code beendet wurde. Zu diesem Zeitpunkt wartet er, dass Sie STRG + Z, EINGABETASTE drücken, um die Anwendung zu beenden.

1. Wenn Sie den Debugger für den gemischten Modus an einen vorhandenen Prozess anfügen (**Debuggen > An den Prozess anhängen...**), wählen Sie die Schaltfläche **Auswählen...** aus, um das Dialogfeld **Codetyp auswählen** zu öffnen. Wählen Sie die Option **Diese Codetypen debuggen** aus, und wählen Sie in der Liste sowohl **Nativ** als auch **Python** aus:

    ![Auswählen der Codetypen „Nativ“ und „Python“](media/mixed-mode-debugging-code-type.png)

    Die Einstellungen für den Codetyp bleiben sitzungsübergreifend bestehen. Wenn Sie also den gemischten Modus später beim Anfügen an einen anderen Prozess deaktivieren möchten, wiederholen Sie diese Schritte und deaktivieren den Codetyp „Python“.

    Sie können anstelle von oder zusätzlich zu **Nativ** auch weitere Codetypen auswählen. Wenn eine verwaltete Anwendung z.B. den Interpreter CPython hostet, der wiederum native Erweiterungsmodule verwendet, und Sie alle drei Elemente debuggen möchten, können Sie die Optionen **Python**, **Nativ** und *Verwaltet* zusammen aktivieren. So erhalten Sie eine einheitliche Debugleistung einschließlich kombinierter Aufruflisten und abwechselnder Einzelschrittausführung zwischen allen drei Laufzeiten.

1. Wenn Sie das Debuggen im gemischten Modus zum ersten Mal starten, wird womöglich das Dialogfeld **Python-Symbole erforderlich** angezeigt. Weitere Informationen hierzu finden Sie unter [Symbole für das Debuggen im gemischten Modus](debugging-symbols-for-mixed-mode.md). Sie müssen Symbole für jede Python-Umgebung nur einmal installieren. Beachten Sie, dass wenn Sie die Python-Unterstützung über den Visual Studio 2017-Installer installieren, Symbole automatisch hinzugefügt werden.

1. Sie möchten womöglich auch den Python-Quellcode selbst zur Verfügung haben. Für die Python-Standardsprache kann dieser von [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) abgerufen werden. Laden Sie das für Ihre Version passende Archiv herunter, und extrahieren Sie es in einen Ordner. Sie verweisen Visual Studio auf bestimmte Dateien in diesem Ordner, egal zu welchem Punkt Sie aufgefordert werden.

## <a name="mixed-mode-specific-features"></a>Spezifische Funktionen des gemischten Modus

- [Kombinierte Aufrufliste](#combined-call-stack)
- [Abwechselnde Einzelschrittausführung zwischen Python und nativem Code](#stepping-between-python-and-native-code)
- [Ansicht der PyObject-Werte im nativen Code](#pyobject-values-in-native-code)
- [Ansicht der nativen Werte im Python-Code](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Kombinierte Aufrufliste

Das Aufruflistenfenster zeigt die Aufruflistenrahmen für den nativen und den Python-Code überlappend und mit markierten Übergängen zwischen beiden Codetypen:

![Kombinierte Aufrufliste](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> Übergänge werden ohne Angabe der Übergangsrichtung als „[External Code]“ angezeigt, wenn die Option **Tools > Optionen > Debuggen > Allgemein > Nur meinen Code aktivieren** festgelegt ist.

Durch Doppelklicken auf einen beliebigen Aufruflistenrahmen wird dieser Rahmen aktiv, und es wird der entsprechende Quellcode geöffnet, sofern möglich. Wenn kein Quellcode verfügbar ist, wird der Rahmen dennoch aktiv, und die lokalen Variablen können überprüft werden.

### <a name="stepping-between-python-and-native-code"></a>Abwechselnde Einzelschrittausführung zwischen Python und nativem Code

Beim Verwenden der Befehle „Einzelschritt“ (F11) oder „Ausführen bis Rücksprung“ (UMSCHALT+F11) verarbeitet der Debugger im gemischten Modus Änderungen zwischen Codetypen ordnungsgemäß. Ein Beispiel: Wenn Python eine Methode eines Typs aufruft, der in C implementiert ist, wird die Einzelschrittausführung eines Aufrufs dieser Methode am Beginn der nativen Funktion angehalten, die die Methode implementiert. Gleiches gilt, wenn nativer Code eine Python-API-Funktion aufruft, die zu einem Aufruf von Python-Code führt. Die Einzelschrittausführung eines `PyObject_CallObject`-Objekts in einem Funktionswert, der ursprünglich in Python definiert wurde, wird am Beginn der Python-Funktion angehalten. Die Einzelschrittausführung von nativem Code aus Python heraus wird ebenfalls für native Funktionen unterstützt, die über [ctypes](http://docs.python.org/3/library/ctypes.html) von Python aufgerufen wurden.

### <a name="pyobject-values-view-in-native-code"></a>Ansicht der PyObject-Werte im nativen Code

Wenn ein nativer Rahmen (C oder C++) aktiv ist, werden die zugehörigen lokalen Variablen im Debuggerfenster für lokale Variablen angezeigt. In nativen Python-Erweiterungsmodulen weisen viele dieser Variablen den Typ `PyObject` (eine typedef für `_object`) oder einen anderen grundlegenden Python-Typ auf (siehe unten stehende Liste). Beim Debuggen im gemischten Modus zeigen diese Werte einen zusätzlichen untergeordneten Knoten mit der Bezeichnung „Python view“ an. Nach Erweitern zeigt dieser Knoten die Python-Darstellung der Variablen an – wenn eine lokale Variable, die auf dasselbe Objekt verweist, in einem Python-Rahmen vorhanden wäre, wäre die Darstellung die gleiche. Die untergeordneten Elemente dieses Knotens können bearbeitet werden.

![Python-Ansicht](media/mixed-mode-debugging-python-view.png)

Um diese Funktion zu deaktivieren, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Fenster für lokale Variablen und deaktivieren die Menüoption **Python > Python-Ansichtsknoten anzeigen**:

![Aktivieren der Python-Ansicht](media/mixed-mode-debugging-enable-python-view.png)

C-Typen, die „[Python View]“-Knoten anzeigen (sofern aktiviert):

- `PyObject `
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

„[Python View]“ wird nicht automatisch für Typen angezeigt, die Sie selbst erstellen. Wenn Sie Erweiterungen für Python 3.x erstellen, ist dies in der Regel kein Problem, da jedes Objekt letztlich über ein `ob_base`-Feld für einen der oben genannten Typen verfügt, wodurch „[Python View]“ angezeigt wird. 

Bei Python 2.x allerdings deklariert jeder Objekttyp seinen Header üblicherweise als Auflistung von Inlinefeldern, und es gibt keine Verknüpfung auf Typsystemebene im C/C++-Code zwischen benutzerdefiniert erstellten Typen und `PyObject`. Um „[Python View]“-Knoten für solche benutzerdefinierten Typen zu aktivieren, bearbeiten Sie die Datei `PythonDkm.natvis` im [Installationsverzeichnis von Python Tools](installation.md#install-locations), und fügen Sie einfach im XML-Code ein weiteres Element für Ihre C-Struktur oder C++-Klasse hinzu.

Eine alternative (und bessere) Möglichkeit ist es, den Anweisungen unter [PEP 3123](http://www.python.org/dev/peps/pep-3123/) zu folgen und statt `PyObject_HEAD` ein explizites `PyObject ob_base;`-Feld zu verwenden. Allerdings ist dieses Vorgehen aus Gründen der Abwärtskompatibilität nicht immer möglich.


### <a name="native-values-view-in-python-code"></a>Ansicht der nativen Werte im Python-Code

Ähnlich wie im vorherigen Abschnitt können Sie eine „[C++ View]“-Ansicht für native Werte im Fenster für lokale Variablen aktivieren, wenn ein Python-Rahmen aktiv ist. Diese Funktion ist nicht standardmäßig aktiviert. Klicken Sie mit der rechten Maustaste auf das Fenster für lokale Variablen, und aktivieren Sie die Menüoption **Python > C++-Ansichtsknoten anzeigen**.

![Aktivieren der C++-Ansicht](media/mixed-mode-debugging-enable-cpp-view.png)

Der „[C++ View]“-Knoten bietet eine Darstellung der zugrunde liegenden C/C++-Struktur für einen Wert. Dies entspricht der Darstellung, die in einem nativen Rahmen angezeigt würde. Der Knoten zeigt eine Instanz von `_longobject` (wofür `PyLongObject` eine typedef ist) für einen langen ganzzahligen Python-Wert an und versucht, Typen für native Klassen abzuleiten, die Sie selbst erstellt haben. Die untergeordneten Elemente dieses Knotens können bearbeitet werden.

![C++-Ansicht](media/mixed-mode-debugging-cpp-view.png)

Wenn ein untergeordnetes Feld eines Objekts den Typ `PyObject` oder einen der anderen unterstützten Typen aufweist, enthält es einen „[Python View]“-Darstellungsknoten (sofern diese aktiviert sind). Auf diese Weise können Sie in Objektdiagrammen navigieren, wenn Verknüpfungen nicht direkt in Python verfügbar sind.

Anders als bei „[Python View]“-Knoten, die Python-Objektmetadaten zum Ermitteln des Objekttyps verwenden, gibt es keinen ähnlich zuverlässigen Mechanismus für „[C++ View]“. Allgemein gesagt: Es ist nicht möglich, für einen bestimmten Python-Wert (also einen `PyObject`-Verweis) zuverlässig zu ermitteln, welche C/C++-Struktur diesem zugrunde liegt. Der Debugger im gemischten Modus versucht, den Typ zu „erraten“. Dazu durchsucht der Debugger verschiedene Felder des Objekttyps (z.B. dem `PyTypeObject`, auf das durch das Feld `ob_type` verwiesen wird), die über Funktionszeigertypen verfügen. Wenn einer dieser Funktionszeiger auf eine Funktion verweist, die aufgelöst werden kann, und wenn diese Funktion über einen `self`-Parameter verfügt, dessen Typ spezifischer ist als `PyObject*`, wird angenommen, dass es sich bei diesem um den zugrunde liegenden Typ handelt. Ein Beispiel: `ob_type->tp_init` für ein bestimmtes Objekt zeigt auf die folgende Funktion:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

In diesem Fall kann der Debugger ordnungsgemäß herleiten, dass der C-Typ des Objekts `FobObject` lautet. Wenn kein genauerer Typ aus `tp_init` ermittelt werden kann, sucht der Debugger in anderen Feldern weiter. Wenn aus keinem der Felder ein Typ hergeleitet werden kann, zeigt der „[C++ View]“-Knoten das Objekt als `PyObject`-Instanz an.

Um jederzeit eine sinnvolle Darstellung für benutzerdefiniert erstellte Typen zu erzielen, empfiehlt es sich, beim Registrieren des Typs mindestens eine Sonderfunktion zu registrieren und einen stark typisierten `self`-Parameter zu verwenden. Die meisten Typen erfüllen diese Voraussetzung von Natur aus. Sollte dies nicht der Fall sein, eignet sich `tp_init` in der Regel am besten für diesen Zweck. Eine Dummyimplementierung von `tp_init` für einen Typ, der nur dafür da ist, den Typrückschluss für den Debugger zu ermöglichen, kann sofort Null zurückgeben, wie in obigem Codebeispiel veranschaulicht.

## <a name="differences-from-standard-python-debugging"></a>Unterschiede zum standardmäßigen Debuggen in Python

Der Debugger für den gemischten Modus unterscheidet sich vom [Python-Standarddebugger](debugging.md) insofern, als einige zusätzliche Funktionen eingeführt werden, dafür aber einige Python-bezogene Funktionen fehlen:

- Nicht unterstützte Funktionen: Bedingte Haltepunkte, Fenster zum interaktiven Debuggen und plattformübergreifendes Remotedebuggen.
- Direktfenster: Ist verfügbar, aber mit eingeschränktem Funktionssatz – einschließlich aller hier aufgeführten Einschränkungen.
- Unterstützte Python-Versionen: Nur CPython 2.7 und 3.3+.
- Visual Studio Shell: Bei Verwendung von PTVS mit Visual Studio Shell (wenn Sie PTVS beispielsweise mithilfe des integrierten Installationsprogramms installiert haben) kann Visual Studio keine C++-Projekte öffnen, und für C++-Dateien stehen nur die Bearbeitungsfunktionen eines einfachen Text-Editors zur Verfügung. Das C/C++-Debuggen und das Debuggen im gemischten Modus werden in Shell jedoch vollständig unterstützt, einschließlich Quellcode, Einzelschrittausführung im nativen Code und C++-Ausdrucksauswertung in Debuggerfenstern.
- Anzeigen und Erweitern von Objekten: Beim Anzeigen von Python-Objekten in den Toolfenstern für lokale Variablen und Überwachung zeigt der Debugger im gemischten Modus nur die Struktur der Objekte an. Es werden weder automatisch Eigenschaften ausgewertet noch berechnete Attribute angezeigt. Bei Auflistungen werden nur Elemente für integrierte Auflistungstypen angezeigt (`tuple`, `list`, `dict`, `set`). Benutzerdefinierte Auflistungstypen werden nur dann als Auflistungen visualisiert, wenn sie von einem integrierten Auflistungstyp vererbt werden.
- Ausdrucksauswertung: Siehe oben.

### <a name="expression-evaluation"></a>Ausdrucksauswertung

Der Python-Standarddebugger ermöglicht die Auswertung beliebiger Python-Ausdrücke in Überwachungs- und Direktfenstern, wenn der Debuggingprozess an einem beliebigen Punkt im Code angehalten wird, sofern der Prozess nicht durch einen E/A-Vorgang oder einen anderen ähnlichen Systemaufruf blockiert wird. Beim Debuggen im gemischten Modus können beliebige Ausdrücke nur ausgewertet werden, wenn das Debuggen in Python-Code durch einen Haltepunkt oder durch Einzelschrittausführung im Code angehalten wurde. Die Auswertung kann darüber hinaus nur in dem Thread erfolgen, in dem der Haltepunkt erreicht oder der Einzelschrittvorgang ausgeführt wurde.

Wenn die Ausdrucksauswertung im nativen Code oder im Python-Code angehalten wird, sofern die oben genannten Bedingungen nicht zutreffen (z.B. nach einem „Ausführen bis Rücksprung“-Vorgang oder in einem anderen Thread), ist die Auswertung auf Folgendes beschränkt: Zugriff auf lokale und globale Variablen im Geltungsbereich des aktuell ausgewählten Rahmens, Zugriff auf die zugehörigen Felder und Indizierung integrierter Auflistungstypen mit Literalen. Der folgende Ausdruck kann z.B. in jedem Kontext ausgewertet werden (vorausgesetzt, dass alle Bezeichner auf vorhandene Variablen und Felder mit geeigneten Typen verweisen):

```python
foo.bar[0].baz['key']
```

Der Debugger für den gemischten Modus löst solche Ausdrücke ebenfalls anders auf. Alle Vorgänge mit Memberzugriff schlagen nur Felder nach, die ein direkter Teil des Objekts sind (z.B. ein Eintrag in `__dict__`- oder `__slots__`-Elementen oder einem Feld der nativen Struktur, die über `tp_members` für Python verfügbar gemacht wurde), und ignorieren alle `__getattr__`- und `__getattribute__`-Elemente sowie jegliche Deskriptorlogik. Alle Indizierungsvorgänge ignorieren `__getitem__` und greifen direkt auf die inneren Datenstrukturen von Auflistungen zu.

Aus Gründen der Konsistenz wird dieses Namensauflösungsschema für alle Ausdrücke verwendet, die die Bedingungen der eingeschränkten Ausdrucksauswertung erfüllen, unabhängig davon, ob beliebige Ausdrücke am aktuellen Haltepunkt zulässig sind oder nicht. Um eine ordnungsgemäße Python-Semantik zu erzwingen, wenn ein Auswerter mit vollständigem Funktionsumfang verfügbar ist, schließen Sie den Ausdruck in Klammern ein:

```python
(foo.bar[0].baz['key'])
```
