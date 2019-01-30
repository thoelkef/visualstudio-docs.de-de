---
title: Auswählen der Laufzeiteinstellung für einen Auslastungstest
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: bfac4a278908b9e3c4d3d184266384fb553df211
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969849"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Vorgehensweise: Auswählen der aktiven Laufzeiteinstellungen für einen Auslastungstest

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ein Auslastungstest kann mehrere *Laufzeiteinstellungen* enthalten. Laufzeiteinstellungen sind eine Gruppe von Eigenschaften, die die Art der Ausführung eines Auslastungstests beeinflussen. Laufzeiteinstellungen werden nach Kategorien im **Eigenschaftenfenster** strukturiert. Bei der Ausführung eines Auslastungstests wird die Testlaufeinstellung verwendet, die derzeit als aktiv festgelegt ist.

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Wenn Ihr Auslastungstest im Ordner **Laufzeiteinstellungen** nur einen Laufzeiteinstellungsknoten enthält, handelt es sich bei diesem Knoten immer um den aktiven Knoten. Wenn der Auslastungstest mehrere Laufzeiteinstellungsknoten enthält, können Sie den Knoten auswählen, der bei der Ausführung des Auslastungstests verwendet werden soll. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von weiteren Laufzeiteinstellungen zu einem Auslastungstest](../test/how-to-add-additional-run-settings-to-a-load-test.md).

Im **Auslastungstest-Editor** wird die aktive Testlaufeinstellung durch das Suffix "[Aktiv]" gekennzeichnet.

## <a name="select-the-active-run-setting"></a>Auswählen der aktiven Testlaufeinstellung

1.  Öffnen Sie einen Auslastungstest.

2.  Erweitern Sie den Ordner **Laufzeiteinstellungen**.

3.  Klicken Sie mit der rechten Maustaste auf den Laufzeiteinstellungsknoten, der der aktive Knoten sein soll, und klicken Sie anschließend auf **Als aktiv festlegen**.

     Im **Auslastungstest-Editor** wird der betroffene Laufzeiteinstellungsknoten mit dem Suffix „[Aktiv]“ gekennzeichnet.

     Die ausgewählte Testlaufeinstellung wird und bleibt aktiv, bis Sie eine andere Testlaufeinstellung als aktiv festlegen.

> [!NOTE]
> Sie können die aktive Testlaufeinstellung überschreiben, indem Sie eine Umgebungsvariable mit dem Namen `Test.UseRunSetting=<run setting name>` festlegen. Dies ist sinnvoll, wenn Sie einen Auslastungstest von der Befehlszeile oder von einer Batchdatei aus ausführen. Sie können hierdurch verschiedene Laufzeiteinstellungen auswählen, ohne den Auslastungstest zu öffnen.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Angeben der zu verwendenden Testlaufeinstellung über die Befehlszeile

Sie können die Standardlaufzeiteinstellungen im Auslastungstest überschreiben, indem Sie eine Umgebungsvariable über die Befehlszeile festlegen:

**Set Test.UseRunSetting=PreProdEnvironment**

Führen Sie anschließend den Test aus:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Vorgehensweise: Hinzufügen von weiteren Laufzeiteinstellungen zu einem Auslastungstest](../test/how-to-add-additional-run-settings-to-a-load-test.md)