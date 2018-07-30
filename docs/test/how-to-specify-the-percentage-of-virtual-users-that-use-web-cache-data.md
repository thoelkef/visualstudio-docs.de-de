---
title: Angeben des Prozentanteils virtueller Benutzer, die Webcachedaten für Auslastungstests in Visual Studio verwenden
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 360c8ea61a97256a316c726954bf53e4dcf3004b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180050"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Gewusst wie: Angeben des Prozentanteils virtueller Benutzer, die auf Webcachedaten zugreifen

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften ändern, um Ihre Testanforderungen und -ziele mithilfe des **Auslastungstest-Editors** zu erfüllen. Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load Test Scenario Properties (Auslastungstestszenario-Eigenschaften)](../test/load-test-scenario-properties.md).

Die Eigenschaft **Prozentsatz neuer Benutzer** wird im Eigenschaftenfenster festgelegt. Sie bearbeiten Eigenschaften von Auslastungstestszenarien im Auslastungstest-Editor.

Die Eigenschaft **Prozentsatz neuer Benutzer** wirkt sich auf die Simulation der Webbrowser-Zwischenspeicherung im Auslastungstest aus. In der Standardeinstellung ist die Eigenschaft **Prozentsatz neuer Benutzer** auf „0%“ festgelegt. Wenn der Wert für die Eigenschaft **Prozentsatz neuer Benutzer** auf „100%“ festgelegt ist, wird jeder Webleistungstestlauf in einem Auslastungstest wie ein erstmaliger Zugriff eines Benutzers auf eine Website behandelt, wobei der Browsercache des Benutzers keine Daten aus vorherigen Websiteaufrufen enthält. Daher werden alle Anforderungen im Webtest, einschließlich aller abhängigen Anforderungen, wie z.B. Bilder, heruntergeladen.

> [!NOTE]
> Wird die gleiche zwischenspeicherbare Ressource mehrmals in einem Webtest angefordert, werden die Anforderungen nicht heruntergeladen.

Wenn Sie einen Auslastungstest für eine Website ausführen, die eine erhebliche Anzahl von regelmäßigen Besuchern aufweist, bei denen der lokale Browsercache wahrscheinlich Bilder und andere zwischenspeicherbare Inhalte enthält, erfolgen durch die Verwendung der Einstellung „100%“ für die Eigenschaft **Prozentsatz neuer Benutzer** mehr Downloadanforderungen als in einer realistischen Umgebung. In diesem Fall sollten Sie einen prozentualen Schätzwert für die erstmaligen Websiteaufrufe festlegen und die Eigenschaft **Prozentsatz neuer Benutzer** entsprechend festlegen.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>So geben Sie den Prozentsatz neuer Benutzer für ein Szenario an

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den Sie den Prozentsatzwert neuer Benutzer ändern möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im Eigenschaftenfenster angezeigt.

4. Legen Sie den Wert für die Eigenschaft **Prozentsatz neuer Benutzer** fest, indem Sie eine Zahl für den prozentualen Anteil neuer Benutzer eingeben.

5. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, klicken Sie im Menü **Datei** auf die Option **Speichern**. Sie können anschließend den Auslastungstest mit dem neuen Wert für **Prozentsatz neuer Benutzer** ausführen.

## <a name="see-also"></a>Siehe auch

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Auslastungstestszenario-Eigenschaften](../test/load-test-scenario-properties.md)
- [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md)