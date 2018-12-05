---
title: Speichern der Auslastungstestprotokolle für Testfehler in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 65e8632a161ac345408a030d2d536086abbe48af
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895118"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Vorgehensweise: Angeben, ob Testfehler mit dem Auslastungstest-Editor in Testprotokollen gespeichert werden

Nach dem Erstellen des Auslastungstests mit dem **Assistenten für neuen Auslastungstest** können Sie mit dem **Auslastungstest-Editor** die Auslastungstesteigenschaften ändern, um die Testanforderungen und -ziele zu erreichen. Siehe [Walkthrough: Create and run a load test (Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests)](../test/walkthrough-create-and-run-a-load-test.md). Sie können angeben, ob Sie das Testprotokoll speichern möchten, wenn ein Test in einem Auslastungstest fehlschlägt. Ändern Sie hierzu die Eigenschaft **Protokoll bei Testfehler speichern**.

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>So geben Sie an, ob das Testprotokoll gespeichert wird, wenn ein Test in einem Szenario fehlschlägt

1.  Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2.  Klicken Sie im Ordner **Laufzeiteinstellungen** der Auslastungsteststrukturen auf den Laufzeiteinstellungsknoten, für den Sie die maximale Anzahl von Testiterationen angeben möchten.

3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Laufzeiteinstellungskategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

4.  Wählen Sie in der Eigenschaft **Protokoll bei Testfehler speichern** entweder **TRUE** oder **FALSE** aus, um anzugeben, ob Sie das Testprotokoll im Fall eines Testfehlers im Szenario speichern möchten.

     Nachdem die Änderungen der Eigenschaft abgeschlossen sind, klicken Sie im Menü **Datei** auf die Option **Speichern**.

     Die im Protokoll gespeicherten Daten können mit der Tabellenansicht des Auslastungstest-Analyzers angezeigt werden. Weitere Informationen finden Sie unter [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Siehe auch

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)