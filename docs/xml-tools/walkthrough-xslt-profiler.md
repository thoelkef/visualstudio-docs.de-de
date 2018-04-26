---
title: 'Exemplarische Vorgehensweise: XSLT-Profiler'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c36b1e079027bd0513a7396e703db610dd737639
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-xslt-profiler"></a>Exemplarische Vorgehensweise: XSLT-Profiler

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

## <a name="prerequisites"></a>Erforderliche Komponenten

Die Prozeduren in der folgenden exemplarischen Vorgehensweise ist erforderlich, Visual Studio und .NET Framework, Version 4.0 oder höher.

### <a name="create-the-performance-report"></a>Erstellen des Leistungsberichts

1.  Öffnen Sie in Visual Studio ein XSLT-Dokument.

2.  Klicken Sie auf die **Profil XSLT** Option, die in XML-Menü verfügbar ist.

3.  Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

4.  Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt.

5.  Die XSLT-Ausgabe wird im Ausgabebereich angezeigt.

6.  Überprüfen Sie den Leistungsbericht nach der Leistungssitzung. Anhand der Daten in einem Leistungsbericht können Sie die XSLT-Leistung anzeigen und analysieren.

### <a name="get-all-the-available-views"></a>Abrufen aller verfügbaren Ansichten

1.  Klicken Sie auf die **aktuelle Ansicht** Dropdown-Liste aus, um alle verfügbaren Ansichten abzurufen.

2.  Wählen Sie die **Zusammenfassungsansicht** -Option in der **aktuelle Ansicht** Dropdown-Liste. Standardmäßig wird ein Leistungsbericht angezeigt, der **Zusammenfassungsansicht**. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. Die **Zusammenfassungsansicht** sind die folgenden Datenpunkte aufgeführt:

    -   Am häufigsten aufgerufene Funktionen

    -   Funktionen mit der meisten individuellen Arbeit

    -   Funktionen mit der längsten Ausführungszeit

3.  Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Zeigen Sie von den einzelnen der **Zusammenfassungsansicht**, Sie können zu detaillierteren Ansichten navigieren, indem Sie mit der rechten Maustaste auf den Datenpunkten der Funktion.

4.  Wählen Sie die **Funktionsansicht** -Option in der **aktuelle Ansicht** Dropdown-Liste. Die **Funktionsansicht** werden während der profilerstellung aufgerufenen Funktionen aufgeführt. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    -   **Funktionsname**

    -   **verstrichene inklusive Zeit**

    -   **verstrichene exklusive Zeit**

    -   **inklusive Anwendungszeit**

    -   **exklusive Anwendungszeit**

    -   **Anzahl der Aufrufe**

5.  Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **exklusive** bezieht sich auf die gesamte Ausführungszeit eine Funktion ohne die Ausführungszeit anderer Funktionen, die während der Ausführung dieser Funktion aufgerufen wurden.

6.  Der Begriff **inklusive** bezieht sich auf die gesamte Ausführungszeit eine Funktion, einschließlich der Ausführungszeit aller Funktionen aufgerufen und gibt an, ob anderer von diesen Funktionen aufgerufenen Funktionen.

### <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

1.  Wählen Sie **Aufrufer-/Aufgerufener** anzeigen in der **aktuelle Ansicht** Dropdown-Liste.

2.  Die **Aufrufer-/Aufgerufener** Sicht hat die folgenden drei Teilen:

    -   **Aufgerufenen Funktionen**: alle Funktionen, die eine bestimmte Funktion aufgerufen werden im oberen Teil der Ansicht aufgelistet.

    -   **Aktuelle Funktion**: die bestimmte Funktion, die aufgerufen wurde im mittleren Teil der Ansicht aufgeführt wird.

    -   **Vom aufgerufenen Funktionen** : alle Funktionen, die von bestimmten Funktion aufgerufen wurden, werden im unteren Bereich der Ansicht aufgeführt.

3.  Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

4.  Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

5.  Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

### <a name="select-calltree-view"></a>Auswählen der Ansicht "Aufrufstruktur"

1.  Wählen Sie **Call Tree View** in der **aktuelle Ansicht** Dropdown-Liste. Diese Ansicht ist eine Strukturansicht der Programmausführung.

2.  Die **Call Tree View** wird der Stamm der Struktur als Prozessname. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ist ähnlich wie die **Stapelansicht Aufrufen** während des Debuggens verfügbar. Neben den Spalten in der **Funktionsansicht**in der **Call Tree View**, es wird eine zusätzliche Spalte zum Anzeigen der **Modulname**.

3.  Wählen Sie **Markierungen** in der **aktuelle Ansicht** Dropdown-Liste.

4.  Im XSLT-Profiler werden Markierungen verwendet, die im Datensammlungsdatenstrom zusammen mit einem Kommentar angezeigt werden. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden angezeigt, in eine Tabelle mit den **Markierungs-ID**, **Markierungsname** (**Startprogramm**, **Programm beenden**), und die  **Zeitstempel**. Die Markierungen werden nicht aggregiert und angezeigt werden in chronologischer Reihenfolge in der **Ansicht "Markierungen"** des Leistungsberichts.

### <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

1.  Wählen Sie **Module** in der **aktuelle Ansicht** Dropdown-Liste.

2.  Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Es werden standardmäßig sowohl Absolute Werte als auch Prozentzahlen für **verstrichene inklusive Zeit**, **verstrichene exklusive Zeit**, **inklusive Anwendungszeit**, **Exklusive Anwendungszeit**, und **Anzahl der Aufrufe**.

3.  Wählen Sie **Prozess** in der **aktuelle Ansicht** Dropdown-Liste.

4.  Prozessansicht wird eine Tabelle mit den **Prozess-ID**, **Prozessnamen**, **Anfangszeit**, und die **Endzeit**. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)