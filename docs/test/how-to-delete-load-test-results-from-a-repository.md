---
title: 'Vorgehensweise: Löschen von Auslastungstestergebnissen von einem Repository in Visual Studio | Microsoft-Dokumentation'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7c76f18e55e079539d8348ee68c95f32431bff49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Gewusst wie: Löschen von Auslastungstestergebnissen aus einem Repository

Alle Informationen, die während eines Auslastungstests erfasst werden, werden im Ergebnisrepository für Auslastungstests gespeichert. Das Ergebnisrepository für Auslastungstests enthält Leistungsindikatordaten und Informationen zu Fehlern. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md).

 Sie können Auslastungstestergebnisse aus dem Auslastungstest-Editor im Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** verwalten. Sie können Auslastungstestergebnisse öffnen, importieren, exportieren und entfernen.

## <a name="to-delete-results-from-a-repository"></a>So löschen Sie Ergebnisse aus einem Repository

1.  Öffnen Sie in einem Webleistungs- und Auslastungstestprojekt einen Auslastungstest.

2.  Klicken Sie auf der eingebetteten Symbolleiste auf **Ergebnisse öffnen und verwalten**.

     Das Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** wird angezeigt.

3.  Wählen Sie unter **Enter a controller name to find load test results** (Controllernamen für die Suche nach Auslastungstestergebnissen eingeben) einen Controller aus. Wählen Sie **\<Local - No controller>** (<Lokal - Kein Controller>) aus, um auf lokal gespeicherte Ergebnisse zuzugreifen.

4.  Wählen Sie unter **Show results for the following load test** (Ergebnisse für den folgenden Auslastungstest anzeigen) den Auslastungstest aus, dessen Ergebnisse angezeigt werden sollen. Wählen Sie **\<Show results for all tests>** (<Ergebnisse für alle Tests anzeigen>) aus, um alle Ergebnisse für alle Tests anzuzeigen.

     Wenn Auslastungstestergebnisse verfügbar sind, werden diese in der Liste **Auslastungstestergebnisse** angezeigt. Die Spalten lauten **Time**, **Duration**, **User**, **Outcome**, **Test**, and **Description** (Zeit, Dauer, Benutzer, Ergebnis, Test und Beschreibung). **Test** ist der Name des Tests und unter **Beschreibung** wird die optionale Beschreibung angegeben, die vor der Ausführung des Tests hinzugefügt wurde. In der Spalte **Beschreibung** werden die kurzen Beschreibungen angezeigt, die in den **Analysekommentaren** für dieses Testergebnis eingegeben wurden.

5.  Klicken Sie in der Liste **Auslastungstestergebnisse** auf ein Ergebnis. Sie können die UMSCHALTTASTE und/oder STRG-TASTE verwenden, um mehr als ein Ergebnis auszuwählen.

6.  Klicken Sie auf **Entfernen**.

     Die Ergebnisse werden aus dem Repository entfernt.

    > [!NOTE]
    > Das Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** bleibt geöffnet, nachdem die Ergebnisse entfernt wurden.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Exportieren von Auslastungstestergebnissen aus einem Repository](../test/how-to-export-load-test-results-from-a-repository.md)
- [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Gewusst wie: Importieren von Auslastungstestergebnissen in ein Repository](../test/how-to-import-load-test-results-into-a-repository.md)