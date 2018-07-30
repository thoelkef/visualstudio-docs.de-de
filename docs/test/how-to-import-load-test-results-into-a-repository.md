---
title: 'Vorgehensweise: Importieren von Auslastungstestergebnissen in ein Repository in Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8c149f9febccb8363d5420c447c66bbdb5a5da6e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177772"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Gewusst wie: Importieren von Auslastungstestergebnissen in ein Repository

Alle Informationen, die während eines Auslastungstests erfasst werden, werden im Ergebnisrepository für Auslastungstests gespeichert. Das Ergebnisrepository für Auslastungstests enthält Leistungsindikatordaten und Informationen zu Fehlern. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md).

 Sie können Auslastungstestergebnisse aus dem Auslastungstest-Editor im Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** verwalten. Sie können Auslastungstestergebnisse öffnen, importieren, exportieren und entfernen.

## <a name="to-import-results-into-a-repository"></a>So importieren Sie Ergebnisse in ein Repository

1.  Öffnen Sie in einem Webleistungs- und Auslastungstestprojekt einen Auslastungstest.

2.  Klicken Sie auf der eingebetteten Symbolleiste auf **Ergebnisse öffnen und verwalten**.

     Das Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** wird angezeigt.

3.  Wählen Sie in **Controllernamen für die Suche nach Auslastungstestergebnissen eingeben** einen Controller aus. Wählen Sie **\<lokal>** aus, um auf lokal gespeicherte Ergebnisse zuzugreifen.

     Wenn Auslastungstestergebnisse verfügbar sind, werden diese in der Liste **Auslastungstestergebnisse** angezeigt. Die Spalten lauten **Time**, **Duration**, **User**, **Outcome**, **Test**, and **Description** (Zeit, Dauer, Benutzer, Ergebnis, Test und Beschreibung). Unter **Test** ist der Name des Tests und unter **Beschreibung** die optionale Beschreibung angegeben, die vor der Ausführung des Tests hinzugefügt werden kann.

4.  Wählen Sie **Importieren** aus.

     Das Dialogfeld **Auslastungstestergebnisse importieren** wird angezeigt.

5.  Geben Sie im Feld **Dateiname** den Namen einer archivierten Testergebnisdatei ein, und klicken Sie dann auf **Öffnen**.

     \- oder –

     Navigieren Sie zur Datei, und klicken Sie dann auf **Öffnen**.

    > [!NOTE]
    > Die in diesem Schritt angegebene archivierte Testergebnisdatei muss zuvor mit dem Exportvorgang erstellt worden sein.

     Die Ergebnisse werden importiert und in der Liste **Auslastungstestergebnisse** angezeigt.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Gewusst wie: Exportieren von Auslastungstestergebnissen aus einem Repository](../test/how-to-export-load-test-results-from-a-repository.md)