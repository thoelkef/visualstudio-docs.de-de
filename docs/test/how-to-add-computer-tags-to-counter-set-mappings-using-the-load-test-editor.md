---
title: Hinzufügen von Computertags zu Indikatorensatzzuordnungen für Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 96ce122c78c20b741613ed45820f585236a0383b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203666"
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Vorgehensweise: Hinzufügen von Computertags zu Indikatorensatzzuordnungen mit dem Auslastungstest-Editor

Computertags ermöglichen es Ihnen, einen Computer anhand eines einfachen Namens zu identifizieren. Die Tags werden im Knoten **Indikatorensatzzuordnungen** in der Struktur im Auslastungstest-Editor angezeigt. Wichtiger ist jedoch, dass die Tags in Excel-Berichten angezeigt werden, sodass die Projektbeteiligten die Rolle des Computers im Auslastungstest erkennen können. Beispiel: "Webserver1 in Lab2" oder "SQL Server2 im Phoenix-Büro". Weitere Informationen finden Sie unter [Reporting Load Tests Results for Test Comparisons or Trend Analysis (Berichterstellung für Auslastungstestergebnisse für Testvergleiche oder die Trendanalyse)](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>So fügen Sie einem Computer ein Tag hinzu

1.  Öffnen Sie einen Auslastungstest.

2.  Klicken Sie auf die Schaltfläche **Indikatorensätze verwalten**.

     – oder –

     Klicken Sie in der Auslastungsteststruktur mit der rechten Maustaste auf den Ordner **Indikatorensätze**, und wählen Sie **Indikatorensätze verwalten** aus.

     Das Dialogfeld **Indikatorensätze verwalten** wird angezeigt.

3.  (Optional) Wählen Sie im Listenfeld **Die ausgewählten Computer und Indikatorensätze werden den folgenden standardmäßigen Laufzeiteinstellungen hinzugefügt** eine andere Laufzeiteinstellung aus.

    > [!NOTE]
    > Dies gilt nur, wenn der Auslastungstest mehrere Testlaufeinstellungen enthält.

4.  Wählen Sie unter **Zu überwachende Computer und Indikatorensätze** den Computer aus, für den Sie das Tag übernehmen möchten.

    > [!NOTE]
    > Informationen über das Hinzufügen eines Computers finden Sie unter [Vorgehensweise: Verwalten von Indikatorensätzen](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  Geben Sie im Textfeld **Computertags** ein Tag ein, das dem Computer zugeordnet werden soll, z. B. "TestMachine12 in lab3".

6.  Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Analysieren von Verstößen gegen Schwellenwertregeln](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Vorgehensweise: Verwalten von Indikatorensätzen](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)