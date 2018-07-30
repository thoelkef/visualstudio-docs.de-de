---
title: Seitenantwortzeit in einem Auslastungstest in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 85991c25844cb6e781240a394c38f798251a68b6
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178292"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Gewusst wie: Anzeigen der Antwortzeit von Websites in einem Auslastungstest mit dem Auslastungstest-Analyzer

Die Zeit, die Websites benötigen, bis sie vollständig geladen sind, wird *Antwortzeit* genannt. Beim Erstellen eines Webleistungstests können Sie für jede Webseitenanforderung im Webleistungstest ein Antwortzeitziel festlegen.

Wenn der Webleistungstest unter Belastung in einem Auslastungstest ausgeführt wird, können für jede Seite folgende Informationen analysiert werden:

-   Die durchschnittliche Antwortzeit der Seite.

-   Testiterationen in Prozent, die dem Antwortzeitziel der Seite entsprechen.

-   Sie können die Antwortzeiten von Webseiten mit der Ansicht „Tabellen“ oder „Diagramme“ im Auslastungstest-Analyzer analysieren:

-   Analysieren der Antwortzeiten von Webseiten in der Tabellenansicht

-   Analysieren der Antwortzeiten von Webseiten in der Diagrammansicht

## <a name="view-response-time-data-in-a-table"></a>Anzeigen der Antwortzeitdaten in einer Tabelle

### <a name="to-view-response-time-data-in-a-table"></a>So zeigen Sie Antwortzeitdaten in einer Tabelle an

1.  Klicken Sie in der Auslastungstestanalyse auf der Symbolleiste auf **Tabellen**, um sicherzustellen, dass das Tabellenraster angezeigt wird.

2.  Wählen Sie im Dropdown-Listenfeld **Tabelle** die Option **Seiten** aus.

3.  Die Daten für jede Seite werden im Raster angezeigt. Normalerweise werden die nachfolgend aufgeführten Spalten angezeigt.

    |Spaltenüberschrift|Beschreibung |
    |-|-|
    |**Seite**|Der Name der Website.|
    |**Szenario**|Der Name des Szenarios. Wichtig, wenn mehr als ein Szenario im Webleistungstest enthalten ist.|
    |**Test**|Der Name des Webleistungstests. Wichtig, wenn mehr als ein Webleistungstest im Auslastungstest enthalten ist.|
    |**Network**|Der Netzwerktyp.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Gesamt**|Gesamtzahl der für die Webseite ausgeführten Anforderungen. Gesamtzahl für alle Iterationen im Auslastungstest.|
    |**Durchschn.**|Durchschnittliche Seitenantwortzeit.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Min**|Die minimale Seitenantwortzeit.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Median**|Der Medianwert für die Seitenantwortzeit.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**90%**|90 Prozent entsprachen der Antwortzeit. Das bedeutet, dass 90 Prozent der Seiten schneller antworteten als die festgelegte Zeit, und 10 Prozent der Seiten langsamer.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**95%**|95 Prozent entsprachen der Antwortzeit. Das bedeutet, dass 95 Prozent der Seiten schneller antworteten als die festgelegte Zeit, und 5 Prozent der Seiten langsamer.|
    |**99%**|99 Prozent entsprachen der Antwortzeit. Das bedeutet, dass 99 Prozent der Seiten schneller antworteten als die festgelegte Zeit, und 1 Prozent der Seiten langsamer.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Max**|Die maximale Seitenantwortzeit.<br /><br /> Diese Daten werden in der Standardeinstellung nicht gesammelt. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Standardabweichung**|Standardmäßig werden die Standardabweichungsdaten nicht erfasst. Wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Testlaufeinstellungsknoten aus, der geändert werden soll, um diese Daten zu erfassen. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** die Option **AllIndividualDetails** aus.|
    |**Seitenzeit**|Die durchschnittliche Antwortzeit für alle Anforderungen, die für die Webseite ausgeführt wurden.|
    |**Ziel**|Das Seitenzeitziel. Dies ist ein konstanter Wert für die Seite. **Hinweis**: Das Seitenzeitziel wird nur angezeigt, wenn für die Anforderung ein Ziel im Webleistungstest definiert wurde.|
    |**%: Ziel erreicht**|Prozentualer Anteil der für die Webseite ausgeführten Anforderungen, die dem Antwortzeitziel entsprachen.|

 Weitere Informationen finden Sie unter [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Anzeigen von Antwortzeitdaten in einem Diagramm

Die Antwortzeitdaten können auch in einem Diagramm angezeigt werden. So können Sie die Änderungen während des Auslastungstests verfolgen. Diese Funktion ist besonders hilfreich, wenn sich das Auslastungsmuster im Verlauf des Tests erhöht (was z. B. bei einem schrittweisen Auslastungsmuster der Fall ist). Weitere Informationen finden Sie unter [Editing Load Patterns to Model Virtual User Activities (Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten)](../test/edit-load-patterns-to-model-virtual-user-activities.md).

### <a name="to-view-response-time-data-in-a-graph"></a>So zeigen Sie Antwortzeitdaten in einem Diagramm an

1.  Klicken Sie im Auslastungstest-Analyzer in der Symbolleiste auf **Diagramme**, um sicherzustellen, dass das Diagramm angezeigt wird.

2.  Erweitern Sie im Fenster **Indikatoren** den Knoten des gewünschten Szenarios, z.B. `Scenario1`.

3.  Erweitern Sie den Knoten des gewünschten Webleistungstests.

4.  Erweitern Sie den Knoten **Seiten**.

5.  Erweitern Sie den Knoten der gewünschten Seite.

6.  Klicken Sie mit der rechten Maustaste auf **% Seiten: Ziel erreicht**, und klicken Sie dann auf **Indikator im Diagramm anzeigen**.

     Die Daten werden dem Diagramm hinzugefügt.

7.  (Optional) Wiederholen Sie den vorherigen Schritt für die Durchschnittswerte von Seitenzeit, Seitenantwortzeitziel und Seiten insgesamt.

    > [!NOTE]
    > Seitenantwortzeitziel ist ein konstanter Wert.

 Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Gewusst wie: Zugreifen auf Auslastungstestergebnisse für die Analyse](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)