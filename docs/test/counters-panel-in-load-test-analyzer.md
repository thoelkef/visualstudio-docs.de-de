---
title: Indikatorenfenster für die Analyse von Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9e693872784519f5cdcacbd0691b6f69334af22e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Verwenden des Indikatorenfensters in der Diagramm- und Tabellenansicht

Das Indikatorenfenster wird in der Diagrammansicht und Tabellenansicht im Auslastungstest-Analyzer angezeigt, während ein Auslastungstest ausgeführt wird, oder wenn Sie ein Auslastungstestergebnis analysieren. Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md), [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) und [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md).

Im Indikatorenfenster wird eine strukturierte Ansicht aller Leistungsindikatoren angezeigt, die während des Auslastungstests erfasst wurden. Sie können das Indikatorenfenster ein- oder ausblenden, indem Sie auf der Symbolleiste des Auslastungstest-Analyzers auf **Indikatorenfenster anzeigen** klicken.

Die Indikatoren sind in einer Struktur organisiert, in der die Endknoten Leistungsindikatorinstanzen sind, die grafisch dargestellt werden können.

Das Indikatorenfenster bietet die folgenden Funktionen:

-   Anzeige von Informationen zu Schwellenwertverletzungen

-   Auswahl von Indikatoren für die grafische Darstellung

-   Eine strukturierte Ansicht aller während eines Auslastungstestlaufs erfassten Leistungsindikatoren mit den folgenden Hauptbranches:

    -   **Insgesamt:** enthält eine Zusammenfassung der Leistungsindikatordaten für jeden Test-Agent und den gesamten Auslastungstest.

    -   **Szenarioname:** Verzweigungen in der Leistungsindikatorstruktur, die mit den Namen von Auslastungstestszenarios beschriftet sind, enthalten alle einem bestimmten Auslastungstestszenario zugeordnete Auslastungstest-Indikatorinstanzen. Die meisten Auslastungstestindikatoren sind innerhalb eines Szenariobranches geschachtelt.

         Eine Szenarioverzweigung enthält Webleistungstestknoten. Die Webleistungstestknoten enthalten Knoten für Seiten, Anforderungen und Transaktionen. Jeder Endknoten in dieser Struktur ist ein Leistungsindikator, der einem Diagramm hinzugefügt werden kann.

    -   **Computer:** Diese Verzweigung enthält eine nach Computer gruppierte Auflistung aller Indikatorinstanzen, die keinem Auslastungstest zugeordnet sind. Der Branch „Computer“ enthält einen Knoten für jeden Computer, der dem im Abschnitt „Rollen“ der ausgewählten Testeinstellungen angegebenen Auslastungstestcontroller zugeordnet ist. Weitere Informationen finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

         Jeder Computerknoten enthält einen Satz von Leistungsindikatorkategorien, die von diesem Computer erfasst werden. Kategorien enthalten Indikatoren, und Indikatoren enthalten Namen von Leistungsindikatorinstanzen.

    -   **Fehler:** Diese Verzweigung enthält alle während des Auslastungstests erkannten Fehler. Der Fehlerknoten enthält mehrere Unterkategorie-Fehlerknoten. Die Unterkategorien sind spezifisch für verschiedene Arten von Fehlern, z.B. Ausnahmen und HTTP-Fehler.

### <a name="scenario-name-node-in-counters-panel"></a>Szenarioknoten im Indikatorenfenster

|||
|-|-|
|![Knoten für Szenarionamen des Zählerbereichs](../test/media/ltest__namenode.png)|1. Alle Scenario1 des Auslastungstests zugeordneten Leistungsindikatoren werden unter diesem Knoten angezeigt.<br />2. Alle Tests eines Szenarios befinden sich unter dem Szenarioknoten. Die Bezeichnung gibt den Testnamen an.<br />3. Blattknoten unter einem Testknoten sind Testfallindikatoren des Auslastungstests, wobei der Instanzname für den Indikator als Testname verwendet wird.<br />4. Alle einem Webleistungstestbranch zugeordneten Seitenindikatorinstanzen des Auslastungstests. In diesem Knoten sind alle Seitenindikatorinstanzen des Auslastungstests enthalten, die der Seite "Login GET" (Berichtsname) des Webleistungstests "IBuyBrowse" in Scenario1 des Auslastungstests zugeordnet sind.<br />5. Endknoten unter einem Seitenknoten sind Seitenindikatoren des Auslastungstests.<br />6. Alle einem Webleistungstest zugeordneten Anforderungsindikatorinstanzen des Auslastungstests sind in einem Webleistungstestbranch enthalten. In diesem Knoten sind alle Anforderungsindikatorinstanzen enthalten, die der Anforderung "Login GET" (Berichtsname) des Webleistungstests "IBuyBrowse" in Scenario1 des Auslastungstests zugeordnet sind.<br />7. Blattknoten unter einem Anforderungsknoten sind Anforderungsindikatoren des Auslastungstests.<br />8. Alle einem Webleistungstest zugeordneten Transaktionsindikatorinstanzen des Auslastungstests sind in einem Webleistungstestbranch enthalten. In diesem Knoten sind alle Transaktionsindikatorinstanzen enthalten, die der Transaktion „Transaction1“ des Webleistungstests „IBuyBrowse“ in Scenario1 des Auslastungstests zugeordnet sind.<br />9. Blattknoten unter einem Transaktionsknoten sind Transaktionsindikatoren des Auslastungstests.<br />10. Komponententestknoten.|

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Hinzufügen weiterer Leistungsindikatoren zu einem Diagramm in der Diagrammansicht:** Im Indikatorenfenster können Sie einem Auslastungstestdiagramm verschiedene Arten von Daten hinzufügen, indem Sie weitere Leistungsindikatoren im Diagramm hinzufügen.|-   [How to: Add and Delete Counters on Graphs (Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen)](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analysieren von im Auslastungstest angegebenen Schwellenwerten, gegen die verstoßen wurde:** Im Indikatorenfenster werden Symbole angezeigt, die Schwellenwertverletzungen darstellen. Diese können Sie dann zur weiteren Analyse zu Tabellen und Diagrammen hinzufügen.|-   [How to: Analyze Threshold Violations Using the Counters Panel (Vorgehensweise: Analysieren von Schwellenwertverletzungen mit dem Indikatorenfenster)](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analysieren von Fehlern, die während des Auslastungstestlaufs erkannt wurden:** Das Indikatorenfenster enthält einen Fehlerknoten, der Fehlerkategorien und -unterkategorien (z.B. HTTP-Fehler) enthält, mit denen Sie Fehler zur weiteren Analyse zu Diagrammen hinzufügen können.|-   [How to: Analyze Errors Using the Counters Panel (Vorgehensweise: Analysieren von Fehlern mithilfe des Indikatorenfensters)](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Überlegungen zum Leistungsindikator-Samplingintervall

Wählen Sie basierend auf der Länge des Auslastungstests einen Wert für die Eigenschaft **Samplingrate** in den Laufzeiteinstellungen des Auslastungstests aus. Eine kleinere Samplingrate (z. B. der Standardwert von fünf Sekunden) erfordert mehr Speicherplatz in der Datenbank für die Auslastungstestergebnisse. Bei längeren Auslastungstests wird durch eine höhere Samplingrate die gesammelte Datenmenge reduziert. Weitere Informationen finden Sie unter [How to: Specify the Sample Rate (Vorgehensweise: Angeben der Samplingrate)](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Die folgende Tabelle enthält Richtlinien für die Samplingraten:

|Dauer des Auslastungstests|Empfohlene Samplingrate|
|------------------------|-----------------------------|
|\< 1 Stunde|5 Sekunden|
|1 – 8 Stunden|15 Sekunden|
|8 – 24 Stunden|30 Sekunden|
|> 24 Stunden|60 Sekunden|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Überlegungen zum Einschließen von Details der zeitlichen Steuerung zur Erfassung von prozentualen Daten

In den Laufzeiteinstellungen im Auslastungstest-Editor ist eine Eigenschaft mit dem Namen **Speicher für Details der zeitlichen Steuerung** verfügbar. Wenn die Eigenschaft **Speicher für Details der zeitlichen Steuerung** aktiviert ist, werden die Zeiten für die Ausführung der einzelnen Tests, Transaktionen und Seiten beim Auslastungstest im entsprechenden Ergebnisrepository gespeichert. Dadurch können Daten für den 90. und 95. Prozentwert im Auslastungstest-Analyzer in den Tabellen „Tests“, „Transaktionen“ und „Seiten“ angezeigt werden.

Zum Aktivieren der Eigenschaft **Speicher für Details der zeitlichen Steuerung** sind zwei Optionen in den Laufzeiteinstellungseigenschaften verfügbar: **StatisticsOnly** und **AllIndividualDetails**. Mit beiden Optionen werden alle Einzeltests, Seiten und Transaktionen zeitlich gesteuert, und prozentuale Daten werden über die einzelnen Zeitsteuerungsdaten erfasst. Der Unterschied besteht darin, dass bei der Option **StatisticsOnly** die einzelnen Daten zur zeitlichen Steuerung aus dem Repository gelöscht werden, sobald die prozentualen Daten berechnet wurden. Dies reduziert den erforderlichen Speicherplatz im Repository, wenn Sie Details der zeitlichen Steuerung verwenden. Fortgeschrittene Benutzer möchten die Detaildaten der zeitlichen Steuerung jedoch möglicherweise mithilfe von SQL-Tools auf andere Weise verarbeiten. Wenn dies der Fall ist, sollte die Option **AllIndividualDetails** verwendet werden, damit die Detaildaten der zeitlichen Steuerung für diese Verarbeitung verfügbar sind. Wenn Sie die Eigenschaft auf **AllIndividualDetails** festlegen, können Sie zudem die Aktivitäten virtueller Benutzer nach Abschluss des Auslastungstests mithilfe des Diagramms für Aktivitäten virtueller Benutzer im Auslastungstest-Analyzer analysieren. Weitere Informationen finden Sie unter [Analyzing Virtual User Activity in the Details View (Analysieren der Aktivität virtueller Benutzer in der Detailansicht)](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Insbesondere bei langen Auslastungstests kann viel Speicherplatz erforderlich sein, um Detaildaten der zeitlichen Steuerung im Ergebnisrepository für Auslastungstests zu speichern. Zudem nimmt das Speichern der Daten im Ergebnisrepository für Auslastungstests am Ende des Tests mehr Zeit in Anspruch, da die Daten bis zum Abschluss der Ausführung auf den Auslastungstests-Agents gespeichert werden. Bei der Beendigung des Auslastungstests werden die Daten im Repository gespeichert. Die Eigenschaft **Speicher für Details der zeitlichen Steuerung** ist standardmäßig aktiviert. Falls dies in Ihrer Testumgebung ein Problem ist, sollten Sie **Speicher für Details der zeitlichen Steuerung** auf **Keine** festlegen.

Weitere Informationen finden Sie unter [How to: Specify the Timing Details Storage Property (Vorgehensweise: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“)](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)