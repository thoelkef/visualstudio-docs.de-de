---
title: Anzeigen von Daten- und Diagnoseanlagen für Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 5d955412195a32a69e069ccac2b40456a9ffb986
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Vorgehensweise: Anzeigen von Daten- und Diagnoseanlagen mit dem Auslastungstest-Analyzer

Bevor Sie einen Auslastungstest ausführen, können Sie eine Testeinstellung auswählen, in der die zu verwendenden Diagnose- und Datenadapter angegeben werden. Nach Abschluss des Auslastungstests können Sie die Details für diese Diagnose- und Datenadapter beim Analysieren der Ergebnisse im Auslastungstest-Analyzer anzeigen. Klicken Sie zum Anzeigen der Details für die Daten- und Diagnoseadapter auf der Symbolleiste des Auslastungstest-Analyzers auf die Schaltfläche **Daten- und Diagnoseanlagen anzeigen**. Wenn für den Auslastungstest z. B. der Adapter "Systeminformationen" in der Testeinstellung konfiguriert ist, können Sie die Systeminformationen für den Computer anzeigen, der bei der Ausführung des Auslastungstests verwendet wurde.

![Dialogfeld „Auswählen von Anlagen für Adapter für diagnostische Daten“](../test/media/load_adapterdialog.png "Load_AdapterDialog")

Ein weiteres Beispiel ist ein Auslastungstest, dessen Testeinstellung den Adapter "IntelliTrace" enthält. Der Adapter "IntelliTrace" ermöglicht es Ihnen, die Seite "IntelliTrace-Zusammenfassung" zu öffnen.

![IntelliTrace-Zusammenfassung](../test/media/load_intellitrace.png "Load_IntelliTrace")

Weitere Informationen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md) und [Collect IntelliTrace data (Erfassen von IntelliTrace-Daten)](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>So zeigen Sie Daten- und Diagnoseanlagen in einem Auslastungstest im Auslastungstest-Analyzer an

1.  Klicken Sie nach Abschluss eines Auslastungstests oder nach dem Öffnen eines Auslastungstestergebnisses auf der Symbolleiste des Auslastungstest-Analyzers auf **Daten- und Diagnoseanlagen anzeigen**.

     Das Dialogfeld **Adapter für diagnostische Daten auswählen** wird angezeigt.

2.  Wählen Sie die Anlage des Adapters für diagnostische Daten aus, die Sie analysieren möchten, und klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)