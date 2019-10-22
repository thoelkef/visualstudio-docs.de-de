---
title: XSLT-Leistung
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2866e9b19ea2b79bf8435d81c93443bb20ff4fec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645904"
---
# <a name="the-xslt-profiler"></a>Der XSLT-Profiler

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

Der XSLT-Profiler ist Teil von Visual Studio und ist im **XML** -Menü verfügbar.

![XSLT-Profiler](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Der XSLT-Profiler ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="create-a-performance-report"></a>Erstellen eines Leistungs Berichts

1. Öffnen Sie in Visual Studio ein XSLT-Dokument.

2. Wählen Sie in der Menüleiste die Option **XML** - > **Profil XSLT**aus.

3. Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

   Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt. Die XSLT-Ausgabe ist ebenfalls sichtbar.

4. Nachdem die Leistungs Sitzung beendet wurde, überprüfen Sie den Leistungsbericht, um die XSLT-Leistung zu analysieren.

## <a name="get-all-available-views"></a>Alle verfügbaren Ansichten erhalten

1. Klicken Sie auf die Dropdown Liste **Aktuelle Ansicht** , um alle verfügbaren Ansichten zu erhalten.

2. Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Zusammenfassungs Ansicht** aus. Standardmäßig wird ein Leistungsbericht in der **Zusammenfassungs Ansicht**angezeigt. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. In der **Zusammenfassungs Ansicht** werden die folgenden Datenpunkte aufgeführt:

   - Am häufigsten aufgerufene Funktionen

   - Funktionen mit der meisten individuellen Arbeit

   - Funktionen mit der längsten Ausführungszeit

   Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Von jedem Datenpunkt in der **Zusammenfassungs Ansicht**aus können Sie zu detaillierteren Ansichten navigieren, indem Sie mit der rechten Maustaste auf die Funktionsdaten Punkte klicken.

3. Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Funktions Ansicht** aus. Die **Funktions Ansicht** Listet Funktionen auf, die während der Profilerstellung aufgerufen werden Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    - **Funktionsname**

    - **verstrichene inklusive Zeit**

    - **Verstrichene exklusive Zeit**

    - **Inklusive Anwendungszeit**

    - **exklusive Anwendungszeit**

    - **Anzahl der Aufrufe**

   Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **exklusiv** bezieht sich auf die Gesamtzeit, die eine Funktion für die Ausführung von anderen Funktionen aufgewendet hat, die während der Ausführung dieser Funktion aufgerufen wurden.

   Der Begriff **inklusiv** bezieht sich auf die Gesamtzeit, die für die Ausführung einer Funktion aufgewendet wurde, einschließlich der Ausführungszeit aller von ihr aufgerufenen Funktionen und der aufgerufenen Funktionen als andere Funktionen.

## <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Ansicht Aufrufer **/** aufgerufener aus. Die Aufrufer **-** /Aufgerufener-Ansicht besteht aus den folgenden drei Teilen:

- **Funktionen, die aufgerufen**haben: alle Funktionen, die eine bestimmte Funktion aufgerufen haben, werden im oberen Teil der Ansicht aufgelistet.

- **Current-Funktion**: die bestimmte Funktion, die aufgerufen wurde, wird im mittleren Teil der Ansicht aufgeführt.

- **Funktionen, die von aufgerufen wurden**: alle Funktionen, die von der jeweiligen Funktion aufgerufen wurden, werden im unteren Teil der Ansicht aufgelistet.

Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

- Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

- Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

## <a name="select-call-tree-view"></a>Aufrufstruktur Ansicht auswählen

- Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Auflistungs Strukturansicht** aus. Diese Ansicht ist eine Strukturansicht der Programmausführung.

   In der **Ansicht "Ansicht** " wird der Stamm der Struktur als Prozess Name angezeigt. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ähnelt der während des Debuggens verfügbaren Ansicht der **Ansichts Stapel Ansicht** . Zusätzlich zu den Spalten in der **Funktions Ansicht**gibt es in der **Ansicht "Aufrufe**" eine zusätzliche Spalte, in der der **Modulname**angezeigt wird.

- Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Markierungen** aus.

   Mit dem XSLT-Profiler sind Markierungen vorhanden, die im Daten Sammlungs Datenstrom mit einem zugeordneten Kommentar angezeigt werden. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden in einer Tabelle angezeigt, die die **Markierungs-ID**, den **Markierungs Namen** (**Start Programm**, das **Endprogramm**) und den **Zeitstempel**enthält. Die Markierungen werden nicht aggregiert und in der **Markierungs Ansicht** des Leistungs Berichts in chronologischer Reihenfolge angezeigt.

## <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

- Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Module** aus.

   Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Standardmäßig sind sowohl absolute Werte als auch Prozent zahlen für die **verstrichene inklusive Zeit**, **verstrichene exklusive Zeit**, **inklusive Anwendungszeit**, **exklusive Anwendungs**Zeit und **Anzahl von Aufrufen**vorhanden.

- Wählen Sie in der Dropdown Liste **Aktuelle Ansicht** die Option **Prozess** aus.

   In der Prozessansicht wird eine Tabelle mit der **Prozess-ID**, dem **Prozessnamen**, der **Anfangszeit**und der **Endzeit**angezeigt. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)