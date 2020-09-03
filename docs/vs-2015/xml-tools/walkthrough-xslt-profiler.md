---
title: 'Exemplarische Vorgehensweise: XSLT-Profiler | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669525"
---
# <a name="walkthrough-xslt-profiler"></a>Exemplarische Vorgehensweise: XSLT-Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

## <a name="prerequisites"></a>Voraussetzungen
 Für die Verfahren in der folgenden exemplarischen Vorgehensweise sind Visual Studio 2010 und .NET Framework Version 4.0 erforderlich. Der XSLT-Profiler ist nur in Microsoft Visual Studio Team System mit installierten Profilerstellungstools verfügbar.

### <a name="create-the-performance-report"></a>Erstellen des Leistungsberichts

1. Öffnen Sie in Visual Studio ein XSLT-Dokument.

2. Klicken Sie auf die Option **Profil-XSLT** , die im XML-Menü verfügbar ist.

3. Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

4. Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt.

5. Die XSLT-Ausgabe wird im Ausgabebereich angezeigt.

6. Überprüfen Sie den Leistungsbericht nach der Leistungssitzung. Anhand der Daten in einem Leistungsbericht können Sie die XSLT-Leistung anzeigen und analysieren.

### <a name="get-all-the-available-views"></a>Abrufen aller verfügbaren Ansichten

1. Klicken Sie auf die Dropdownliste **Aktuelle Ansicht**, um alle verfügbaren Ansichten abzurufen.

2. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option für die **Zusammenfassungsansicht** aus. Leistungsberichte werden standardmäßig in der **Zusammenfassungsansicht** angezeigt. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. In der **Zusammenfassungsansicht** werden die folgenden Datenpunkte angezeigt:

    - Am häufigsten aufgerufene Funktionen

    - Funktionen mit der meisten individuellen Arbeit

    - Funktionen mit der längsten Ausführungszeit

3. Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Von den einzelnen Datenpunkten in der **Zusammenfassungsansicht** können Sie zu detaillierteren Ansichten navigieren, indem Sie mit der rechten Maustaste auf die Funktionsdatenpunkte klicken.

4. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option für die **Funktionsansicht** aus. In der **Funktionsansicht** werden die während der Profilerstellung aufgerufenen Funktionen aufgeführt. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    - **Funktionsname**

    - **verstrichene inklusive Zeit**

    - **verstrichene exklusive Zeit**

    - **inklusive Anwendungszeit**

    - **exklusive Anwendungszeit**

    - **Anzahl der Aufrufe**

5. Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **Exklusiv** bezieht sich auf die gesamte Ausführungszeit einer Funktion ohne die Ausführungszeit anderer Funktionen, die während der Ausführung dieser Funktion aufgerufen wurden.

6. Der Begriff **Inklusiv** bezieht sich auf die gesamte Ausführungszeit einer Funktion einschließlich der Ausführungszeit aller von ihr aufgerufenen Funktionen und anderer von diesen Funktionen aufgerufenen Funktionen.

### <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

1. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Ansicht **Aufrufer/Aufgerufener** aus.

2. Die Ansicht **Aufrufer/Aufgerufener** besteht aus den folgenden drei Teilen:

    - **Funktionen, die aufgerufen haben**: Alle Funktionen, die eine bestimmte Funktion aufgerufen haben, werden im oberen Teil der Ansicht aufgelistet.

    - **Aktuelle Funktion**: Die aufgerufene Funktion wird im mittleren Teil der Ansicht angezeigt.

    - **Funktionen, die von aufgerufen wurden** : alle Funktionen, die von der jeweiligen Funktion aufgerufen wurden, werden im unteren Teil der Ansicht aufgelistet.

3. Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

4. Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

5. Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

### <a name="select-calltree-view"></a>Auswählen der Ansicht "Aufrufstruktur"

1. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Ansicht **Aufrufstrukturansicht** aus. Diese Ansicht ist eine Strukturansicht der Programmausführung.

2. In der **Aufrufstrukturansicht** wird der Stamm der Struktur als Prozessname angezeigt. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ähnelt der beim Debuggen verfügbaren **Aufruflistenansicht**. Neben den Spalten in der **Funktionsansicht** enthält die **Aufrufstrukturansicht** eine weitere Spalte für den **Modulnamen**.

3. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Markierungen** aus.

4. Im XSLT-Profiler werden Markierungen verwendet, die im Datensammlungsdatenstrom zusammen mit einem Kommentar angezeigt werden. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden in einer Tabelle mit **Markierungs-ID**, **Markierungsname** (**Programm starten**, **Programm beenden**) und dem **Zeitstempel** angezeigt. Die Markierungen werden nicht aggregiert und in chronologischer Reihenfolge in der **Markierungsansicht** des Leistungsberichts angezeigt.

### <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

1. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Module** aus.

2. Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Standardmäßig werden sowohl absolute Werte als auch Prozentzahlen für **Verstrichene inklusive Zeit**, **Verstrichene exklusive Zeit**, **Inklusive Anwendungszeit**, **Exklusive Anwendungszeit** und **Anzahl der Aufrufe** angezeigt.

3. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Prozess** aus.

4. In der Prozessansicht wird eine Tabelle mit **Prozess-ID**, **Prozessname**, **Anfangszeit** und **Endzeit** angezeigt. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Weitere Informationen
 [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)
