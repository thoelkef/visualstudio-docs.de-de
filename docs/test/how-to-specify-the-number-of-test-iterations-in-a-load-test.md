---
title: Festlegen der Anzahl von Testiterationen in einer Testlaufeinstellung für Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ec11561a3ebe084517d1a30266f9caa6491544a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>How to: Specify the Number of Test Iterations in a Load Test Run Setting

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md).

Sie können mit dem **Auslastungstest-Editor** die Eigenschaft **Testiterationen** eines Laufzeiteinstellungswerts im Eigenschaftenfenster bearbeiten. Die Eigenschaft **Testiterationen** gibt die Anzahl der Iterationen an, die in allen Webleistungs- und Komponententests in allen Szenarios eines Auslastungstests mit dem **Auslastungstest-Editor** verwendet werden sollen.

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Load Test Run Settings Properties (Eigenschaften von Laufzeiteinstellungen für Auslastungstests)](../test/load-test-run-settings-properties.md).


## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>So geben Sie die Anzahl der Testiterationen in einer Testlaufeinstellung an

1.  Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird geöffnet und zeigt die Auslastungsteststruktur an.

2.  Klicken Sie in der Auslastungsteststruktur im Ordner **Laufzeiteinstellungen** auf eine Testlaufeinstellung.

3.  Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenfenster** aus, um die Kategorien und Eigenschaften der Testlaufeinstellung für Auslastungstests anzuzeigen.

4.  Legen Sie die Eigenschaft **Testiterationen verwenden** auf **TRUE** fest.

5.  Geben Sie in der Eigenschaft **Testiterationen** eine Zahl ein, die die Anzahl der während des Auslastungstests ausgeführten Testiterationen angibt.

6.  Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können anschließend den Auslastungstest mithilfe des neuen Werts für **Testiterationen** ausführen.

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Auslastungstestszenario-Eigenschaften](../test/load-test-scenario-properties.md)