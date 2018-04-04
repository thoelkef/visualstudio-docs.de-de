---
title: Hinzufügen von benutzerdefinierten Indikatorensätzen für Auslastungstests in Visual Studio| Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 8f691c0eac38dae9e9f419335eb1d3ae87c693df
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>How to: Add Custom Counter Sets Using the Load Test Editor

Wenn Sie mithilfe des **Assistenten für neuen Auslastungstest** einen Auslastungstest erstellen, fügen Sie einen anfänglichen Satz von Indikatoren hinzu. Dadurch erhalten Sie einen Satz vordefinierter Indikatorensätze für den Auslastungstest.

> [!NOTE]
> Bei der Verteilung der Auslastungstests auf mehrere Remotecomputer werden Indikatoren für Controller und Agents den Controller- und Agent-Indikatorensätzen zugeordnet. Weitere Informationen zur Verwendung von Remotecomputern im Auslastungstest finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten. Dem Test bereits hinzugefügte Indikatorensätze werden im Knoten **Indikatorensätze** des Auslastungstests angezeigt. Nach dem Erstellen eines Auslastungstests können Sie neue, benutzerdefinierte Indikatorensätze hinzufügen.

![Benutzerdefinierter Indikatorensatz](../test/media/loadtestcustomcounter.png "LoadTestCustomCounter")

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>So fügen Sie einen benutzerdefinierten Indikatorensatz zu einem Auslastungstest hinzu

1.  Öffnen Sie einen Auslastungstest.

2.  Erweitern Sie den Knoten **Indikatorensätze**. Alle dem Auslastungstest hinzugefügten Indikatorensätze werden angezeigt.

3.  Klicken Sie mit der rechten Maustaste auf den Knoten **Indikatorensätze**, und wählen Sie **Benutzerdefinierten Indikatorensatz hinzufügen** aus.

    > [!NOTE]
    > Der Indikatorensatz wird mit einen Standardnamen bezeichnet, z.B. **Custom1**. Sie können diesen Namen im Fenster **Eigenschaften** ändern. Drücken Sie F4, um das Fenster **Eigenschaften** anzuzeigen.

4.  Um dem benutzerdefinierten Indikatorensatz Indikatoren hinzuzufügen, klicken Sie mit der rechten Maustaste auf den neuen Indikatorensatz und dann auf **Indikatoren hinzufügen**. Weitere Informationen zum Hinzufügen von Indikatoren finden Sie unter [Vorgehensweise: Hinzufügen von Indikatoren zu Indikatorensätzen](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Sie können auch einen benutzerdefinierten Indikator hinzufügen, indem Sie mit der rechten Maustaste auf einen vorhandenen Indikatorensatz klicken, auf "Kopieren" klicken und den Indikator dann im Indikatorensatzknoten einfügen. Zusätzliche Indikatoren, die kopiert wurden, aber nicht benötigt werden, können gelöscht werden. Sie können den Namen des neuen Indikatorensatzes im Fenster **Eigenschaften** ändern.

## <a name="see-also"></a>Siehe auch

- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)