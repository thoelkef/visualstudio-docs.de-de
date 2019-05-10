---
title: XSLT-Leistung
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ecc5482c8519ceadfe1e6d5db7880c98b3d2ceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988052"
---
# <a name="the-xslt-profiler"></a>Die XSLT-Profiler

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

Die XSLT-Profiler ist Teil von Visual Studio und steht in der **XML** Menü.

![XSLT-Profiler](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Die XSLT-Profiler ist nur verfügbar, in der Enterprise Edition von Visual Studio.

## <a name="create-a-performance-report"></a>Erstellen von Leistungsberichten

1. Öffnen Sie in Visual Studio ein XSLT-Dokument.

2. Wählen Sie auf der Menüleiste **XML** > **XSLT-Profil**.

3. Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

   Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt. Die XSLT-Ausgabe wird ebenfalls angezeigt.

4. Nachdem die leistungssitzung beendet wurde, Überprüfen der Leistungsbericht zum Analysieren der XSLT-Leistung.

## <a name="get-all-available-views"></a>Erhalten Sie alle verfügbare Ansichten

1. Klicken Sie auf die **aktuelle Ansicht** Dropdown-Liste aus, um alle verfügbaren Ansichten abzurufen.

2. Wählen Sie die **Zusammenfassungsansicht** option die **aktuelle Ansicht** Dropdown-Liste. Standardmäßig ein Leistungsbericht angezeigt wird, der **Zusammenfassungsansicht**. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. Die **Zusammenfassungsansicht** enthält die folgenden Datenpunkte:

   - Am häufigsten aufgerufene Funktionen

   - Funktionen mit der meisten individuellen Arbeit

   - Funktionen mit der längsten Ausführungszeit

   Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Von den einzelnen point-in die **Zusammenfassungsansicht**, Sie können mit der rechten Maustaste auf die funktionsdatenpunkte zu detaillierteren Ansichten navigieren.

3. Wählen Sie die **Funktionsansicht** option die **aktuelle Ansicht** Dropdown-Liste. Die **Funktionsansicht** werden während der profilerstellung aufgerufenen Funktionen aufgeführt. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    - **Funktionsname**

    - **verstrichene inklusive Zeit**

    - **verstrichene exklusive Zeit**

    - **inklusive Anwendungszeit**

    - **exklusive Anwendungszeit**

    - **Anzahl der Aufrufe**

   Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **exklusive** bezieht sich auf die gesamte Zeit eine Funktion ohne die Zeit, die von anderen Funktionen, die während der Ausführung dieser Funktion aufgerufen wird.

   Der Begriff **inklusive** bezieht sich auf die gesamte Ausführungszeit eine Funktion für die Ausführung, einschließlich der Ausführungszeit aller Funktionen aufgerufen und gibt an, ob diese aufgerufenen Funktionen anderen Funktionen aufgerufen.

## <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

Wählen Sie **Aufrufer-/Aufgerufener** anzeigen in der **aktuelle Ansicht** Dropdown-Liste. Die **Aufrufer-/Aufgerufener** Sicht hat die folgenden drei Teilen:

- **Funktionen, die aufgerufen**: Alle Funktionen, die eine bestimmte Funktion aufgerufen werden im oberen Teil der Ansicht aufgeführt.

- **Aktuelle Funktion**: Die bestimmte Funktion, die aufgerufen wurde, wird im mittleren Teil der Ansicht aufgeführt.

- **Funktionen, die vom aufgerufenen**: Alle Funktionen, die von der jeweiligen Funktion aufgerufen wurden werden im unteren Teil der Ansicht aufgelistet.

Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

- Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

- Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

## <a name="select-call-tree-view"></a>Wählen Sie die Aufrufstrukturansicht

- Wählen Sie **Call Tree View** in die **aktuelle Ansicht** Dropdown-Liste. Diese Ansicht ist eine Strukturansicht der Programmausführung.

   Die **Call Tree View** wird der Stamm der Struktur als Prozessname. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ist ähnlich wie die **Call Stack View** während des Debuggens verfügbar. Zusätzlich zu den Spalten in der **Funktionsansicht**in der **Call Tree View**, es wird eine zusätzliche Spalte zum Anzeigen der **Modulname**.

- Wählen Sie **Markierungen** in die **aktuelle Ansicht** Dropdown-Liste.

   Die XSLT-Profiler werden Markierungen verwendet, die in den Datenstrom für die Sammlung mit einem Kommentar werden angezeigt. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden angezeigt, in einer Tabelle mit den **Markierungs-ID**, **Markierungsnamen** (**Startprogramm**, **Programm beenden**), und die  **Zeitstempel**. Die Markierungen werden nicht aggregiert und in chronologischer Reihenfolge in der **Ansicht "Markierungen"** des Leistungsberichts.

## <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

- Wählen Sie **Module** in die **aktuelle Ansicht** Dropdown-Liste.

   Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Es werden standardmäßig sowohl Absolute Werte als auch Prozentzahlen für **verstrichene inklusive Zeit**, **verstrichene exklusive Zeit**, **aufgewendete inklusive Anwendungszeit**, **Aufgewendete exklusive Anwendungszeit**, und **die Anzahl der Aufrufe**.

- Wählen Sie **Prozess** in die **aktuelle Ansicht** Dropdown-Liste.

   Die Prozessansicht zeigt eine Tabelle mit den **Prozess-ID**, **Prozessnamen**, **Anfangszeit**, und die **Endzeit**. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)