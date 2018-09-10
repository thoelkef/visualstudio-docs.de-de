---
title: Speichern von Auslastungstestprotokollen in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3464ffc1db1a757ac20e3f77d0d901ec731a7cab
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381933"
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Vorgehensweise: Angeben der Speicherungshäufigkeit von Testprotokollen mithilfe des Auslastungstest-Editors

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Auslastungstesteigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern. Weitere Informationen finden Sie unter [Walkthrough: Create and run a load test (Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests)](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Sie können angeben, wie häufig das Testprotokoll in einem Auslastungstest gespeichert werden soll. Ändern Sie dazu mithilfe des **Auslastungstest-Editors** im **Eigenschaftenfenster** die Eigenschaft **Protokollhäufigkeit für abgeschlossene Tests speichern**.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>So geben Sie die Häufigkeit des Speicherns des Testprotokolls in einem Auslastungstest an

1.  Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Im Editor wird die Auslastungsteststruktur angezeigt.

2.  Klicken Sie im Ordner **Laufzeiteinstellungen** der Auslastungsteststruktur auf den Laufzeiteinstellungsknoten, für den Sie angeben möchten, wie häufig das Testprotokoll gespeichert werden soll.

3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

4.  Geben Sie im Textfeld für die Eigenschaft **Protokollhäufigkeit für abgeschlossene Tests speichern** eine Zahl ein, um die Häufigkeit anzugeben, mit der das Testprotokoll geschrieben wird. Die Zahl gibt an, dass von jeder eingegebenen Anzahl von Tests jeweils ein Test im Testprotokoll gespeichert wird. Durch Eingabe des Werts zehn wird z. B. angegeben, dass der zehnte, zwanzigste und dreißigste Test in das Testprotokoll geschrieben wird.

    > [!NOTE]
    > Der Wert 0 für die Eigenschaft **Protokollhäufigkeit für abgeschlossene Tests speichern** bedeutet, dass keine Testprotokolle gespeichert werden.

5.  Nachdem die Änderungen der Eigenschaft abgeschlossen sind, klicken Sie im Menü **Datei** auf die Option **Speichern**.

     Die im Protokoll gespeicherten Daten können mit der Tabellenansicht des Auslastungstest-Analyzers angezeigt werden. Weitere Informationen finden Sie unter [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Siehe auch

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)
- [Vorgehensweise: Angeben, ob Testfehler in Testprotokollen gespeichert werden](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Vorgehensweise: Konfigurieren der Erfassung aller Details zur Verwendung des Diagramms für Aktivitäten virtueller Benutzer](../test/how-to-configure-load-tests-to-collect-full-details.md)