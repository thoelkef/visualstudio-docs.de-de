---
title: 'Exemplarische Vorgehensweise: XSLT-Profiler'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f41515ddf04300c075fd82f67bf588d3c17ecc9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835551"
---
# <a name="walkthrough-xslt-profiler"></a>Exemplarische Vorgehensweise: XSLT-Profiler

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

## <a name="prerequisites"></a>Vorraussetzungen

Die Verfahren in der folgenden exemplarischen Vorgehensweise benötigen Visual Studio und .NET Framework Version 4.0 oder höher.

### <a name="create-the-performance-report"></a>Erstellen des Leistungsberichts

1.  Öffnen Sie in Visual Studio ein XSLT-Dokument.

2.  Klicken Sie auf die **XSLT-Profil** Option aus, in der XML-Menü verfügbar ist.

3.  Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

4.  Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt.

5.  Die XSLT-Ausgabe wird im Ausgabebereich angezeigt.

6.  Überprüfen Sie den Leistungsbericht nach der Leistungssitzung. Anhand der Daten in einem Leistungsbericht können Sie die XSLT-Leistung anzeigen und analysieren.

### <a name="get-all-the-available-views"></a>Abrufen aller verfügbaren Ansichten

1.  Klicken Sie auf die **aktuelle Ansicht** Dropdown-Liste aus, um alle verfügbaren Ansichten abzurufen.

2.  Wählen Sie die **Zusammenfassungsansicht** option die **aktuelle Ansicht** Dropdown-Liste. Standardmäßig ein Leistungsbericht angezeigt wird, der **Zusammenfassungsansicht**. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. Die **Zusammenfassungsansicht** enthält die folgenden Datenpunkte:

    -   Am häufigsten aufgerufene Funktionen

    -   Funktionen mit der meisten individuellen Arbeit

    -   Funktionen mit der längsten Ausführungszeit

3.  Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Von den einzelnen point-in die **Zusammenfassungsansicht**, Sie können mit der rechten Maustaste auf die funktionsdatenpunkte zu detaillierteren Ansichten navigieren.

4.  Wählen Sie die **Funktionsansicht** option die **aktuelle Ansicht** Dropdown-Liste. Die **Funktionsansicht** werden während der profilerstellung aufgerufenen Funktionen aufgeführt. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    -   **Funktionsname**

    -   **verstrichene inklusive Zeit**

    -   **verstrichene exklusive Zeit**

    -   **inklusive Anwendungszeit**

    -   **exklusive Anwendungszeit**

    -   **Anzahl der Aufrufe**

5.  Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **exklusive** bezieht sich auf die gesamte Zeit eine Funktion ohne die Zeit, die von anderen Funktionen, die während der Ausführung dieser Funktion aufgerufen wird.

6.  Der Begriff **inklusive** bezieht sich auf die gesamte Ausführungszeit eine Funktion für die Ausführung, einschließlich der Ausführungszeit aller Funktionen aufgerufen und gibt an, ob diese aufgerufenen Funktionen anderen Funktionen aufgerufen.

### <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

1.  Wählen Sie **Aufrufer-/Aufgerufener** anzeigen in der **aktuelle Ansicht** Dropdown-Liste.

2.  Die **Aufrufer-/Aufgerufener** Sicht hat die folgenden drei Teilen:

    -   **Funktionen, die aufgerufen**: Alle Funktionen, die eine bestimmte Funktion aufgerufen werden im oberen Teil der Ansicht aufgeführt.

    -   **Aktuelle Funktion**: Die bestimmte Funktion, die aufgerufen wurde, wird im mittleren Teil der Ansicht aufgeführt.

    -   **Funktionen, die vom aufgerufenen** : Alle Funktionen, die von der jeweiligen Funktion aufgerufen wurden werden im unteren Teil der Ansicht aufgelistet.

3.  Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

4.  Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

5.  Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

### <a name="select-call-tree-view"></a>Wählen Sie die Aufrufstrukturansicht

1.  Wählen Sie **Call Tree View** in die **aktuelle Ansicht** Dropdown-Liste. Diese Ansicht ist eine Strukturansicht der Programmausführung.

2.  Die **Call Tree View** wird der Stamm der Struktur als Prozessname. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ist ähnlich wie die **Call Stack View** während des Debuggens verfügbar. Zusätzlich zu den Spalten in der **Funktionsansicht**in der **Call Tree View**, es wird eine zusätzliche Spalte zum Anzeigen der **Modulname**.

3.  Wählen Sie **Markierungen** in die **aktuelle Ansicht** Dropdown-Liste.

4.  Im XSLT-Profiler werden Markierungen verwendet, die im Datensammlungsdatenstrom zusammen mit einem Kommentar angezeigt werden. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden angezeigt, in einer Tabelle mit den **Markierungs-ID**, **Markierungsnamen** (**Startprogramm**, **Programm beenden**), und die  **Zeitstempel**. Die Markierungen werden nicht aggregiert und in chronologischer Reihenfolge in der **Ansicht "Markierungen"** des Leistungsberichts.

### <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

1.  Wählen Sie **Module** in die **aktuelle Ansicht** Dropdown-Liste.

2.  Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Es werden standardmäßig sowohl Absolute Werte als auch Prozentzahlen für **verstrichene inklusive Zeit**, **verstrichene exklusive Zeit**, **aufgewendete inklusive Anwendungszeit**, **Aufgewendete exklusive Anwendungszeit**, und **die Anzahl der Aufrufe**.

3.  Wählen Sie **Prozess** in die **aktuelle Ansicht** Dropdown-Liste.

4.  Die Prozessansicht zeigt eine Tabelle mit den **Prozess-ID**, **Prozessnamen**, **Anfangszeit**, und die **Endzeit**. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)