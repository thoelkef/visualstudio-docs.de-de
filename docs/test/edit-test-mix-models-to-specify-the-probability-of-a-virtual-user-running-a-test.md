---
title: Bearbeiten von Textmischungsmodellen in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9a95b42dac07fd74e1b2cc8f8e0c4018b4bf4560
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="edit-text-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt

Das *Testmischungsmodell* gibt die Wahrscheinlichkeit dafür an, dass ein virtueller Benutzer einen bestimmten Test in einem Auslastungstestszenario ausführt. Auf diese Weise können Sie Auslastungen realitätsnaher simulieren. Anstatt nur einen Workflow für die Anwendungen zu verwenden können Sie mehrere Workflows simulieren. Dies stellt eine bessere Annäherung an die tatsächliche Interaktion zwischen Endbenutzern und Anwendungen dar.

## <a name="test-mix-model-options"></a>Testmischungsmodelloptionen
 Sie können eine der folgenden Testmischungsmodelloptionen für das Auslastungstestszenario angeben:

-   **Auf Grundlage der Gesamtzahl der Tests:** Bestimmt, welcher Webleistungs- oder Komponententest ausgeführt wird, wenn ein virtueller Benutzer eine Testiteration startet. Am Ende des Auslastungstests stimmt die Häufigkeit der Ausführung eines bestimmten Tests mit der zugewiesenen Testverteilung überein. Verwenden Sie dieses Testmischungsmodell, wenn die Testmischung auf Transaktionsprozentsätzen in einem IIS-Protokoll oder in Produktionsdaten basiert.

-   **Auf Grundlage der Anzahl der virtuellen Benutzer:** Bestimmt den Prozentsatz von virtuellen Benutzern, die einen bestimmten Webleistungs- oder Komponententest ausführen werden. An jedem Punkt im Auslastungstest stimmt die Anzahl der Benutzer, die einen bestimmten Test ausführen, mit der zugewiesenen Verteilung überein. Verwenden Sie dieses Testmischungsmodell, wenn die Testmischung auf dem Prozentsatz von Benutzern, die einen bestimmten Test ausführen, basiert.

-   **Auf Grundlage der Benutzergeschwindigkeit:** Im Verlauf des Auslastungstests wird jeder Webleistungstest oder Komponententest so oft wie angegeben pro Benutzer und pro Stunde ausgeführt. Verwenden Sie dieses Testmischungsmodell, wenn Sie möchten, dass virtuelle Benutzer im Laufe des Auslastungstests Tests mit einer bestimmten Geschwindigkeit ausführen.

-   **Auf Grundlage der sequenziellen Reihenfolge:** Jeder virtuelle Benutzer führt die Webleistungstests oder Komponententests in der Reihenfolge aus, in der sie im Szenario definiert sind. Der virtuelle Benutzer durchläuft die Tests in dieser Reihenfolge so lange, bis der Auslastungstest abgeschlossen ist.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Angeben der Testmischung für den Auslastungstest:** Wenn Sie einen Auslastungstest erstellen, geben Sie im Assistent für neuen Auslastungstest Einstellungen für den Auslastungstest an. Im Assistent für neuen Auslastungstest wählen Sie vorhandene Web- und Komponententests aus, die dem Anfangsszenario hinzugefügt werden sollen. Nachdem Sie dem Szenario Tests hinzugefügt haben, geben Sie die Testmischung für das Szenario an.<br /><br /> Sie können Auslastungsmodelloptionen verwenden, um die realen Erwartungen an eine Website oder Anwendung, für die Sie einen Auslastungstest ausführen, genauer vorauszusagen. Dies ist wichtig, da ein Auslastungstest, der nicht auf einem genauen Auslastungsmodell basiert, irreführende Ergebnisse generieren kann.|-   [Emulating Expected Real-World Usage of a Web Site or Application (Emulieren der erwarteten Echtzeitverwendung einer Website oder Anwendung)](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Bearbeiten des Testmischungsmodells:** Sie können ein Auslastungstestszenario mit dem Auslastungstest-Editor ändern, um eines der Testmischungsmodelle zu verwenden.||
|**Konfigurieren der Geschwindigkeitsverzögerung für ein Testmischungsmodell nach Benutzergeschwindigkeit:** Wenn das Auslastungstestszenario für die Verwendung eines Testmischungsmodells konfiguriert ist und die Option **Auf Grundlage der Benutzergeschwindigkeit** aktiviert ist, können Sie die Verteilung der Geschwindigkeitsverzögerung konfigurieren.|-   [Vorgehensweise: Anwenden der Verteilung auf die Geschwindigkeitsverzögerung beim Verwenden eines Testmischungsmodells für die Benutzergeschwindigkeit](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Ändern des Testmischungsmodells in einem Szenario

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern.

> [!NOTE]
> Eine vollständige Liste der Auslastungseinstellungseigenschaften und deren Beschreibungen finden Sie unter [Auslastungstestszenario-Eigenschaften](../test/load-test-scenario-properties.md).

Mit dem Auslastungstest-Editor können Sie das Testmischungsmodell in einem Auslastungstestszenario ändern, indem Sie die Eigenschaft **Testmischungstyp** im Eigenschaftenfenster bearbeiten.

### <a name="to-change-the-test-mix-model"></a>So ändern Sie das Testmischungsmodell

1.  Öffnen Sie einen Auslastungstest.

     Der Auslastungstest-Editor wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2.  Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den Sie die maximale Anzahl von Testiterationen angeben möchten.

3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden angezeigt.

4.  Klicken Sie in der Eigenschaft **Testmischungstyp** auf die Schaltfläche mit den Auslassungspunkten (**…**).

     Das Dialogfeld "Testmischung bearbeiten" wird angezeigt.

5.  Klicken Sie auf die Dropdownliste unter **Testmischungsmodell**, und wählen Sie das Testmischungsmodell aus, das Sie für das Szenario verwenden möchten.

6.  (Optional) Ändern Sie die Testmischung mit den Schaltflächen **Hinzufügen**, **Entfernen** und **Verteilen** sowie mit den Schiebereglern für die Verteilung. Weitere Informationen finden Sie unter [Editing the Test Mix to Specify Which Tests to Include in a Load Test Scenario (Bearbeiten der Testmischung zum Angeben der Tests, die ein Auslastungstestszenario beinhalten sollen)](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  (Optional) Geben Sie mit den Kontrollkästchen und durch Auswählen der gewünschten Tests einen Webleistungs- oder Komponententest an, der initialisiert oder beendet werden soll. Weitere Informationen finden Sie unter [Emulating Expected Real-World Usage of a Web Site or Application (Emulieren der erwarteten Echtzeitverwendung einer Website oder Anwendung)](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Klicken Sie auf **OK**.

     Im Fenster **Eigenschaften** wird das neue Testmischungsmodell für die Eigenschaft **Testmischungstyp** angezeigt.

9. Klicken Sie nach dem Ändern der Eigenschaft auf **Speichern** im Menü **Datei**. Anschließend können Sie den Auslastungstest mithilfe des neuen Werts für **Testmischungstyp** ausführen.

## <a name="see-also"></a>Siehe auch

- [Editing Load Test Scenarios (Szenarios zum Bearbeiten von Auslastungstests)](../test/edit-load-test-scenarios.md)
- [Auslastungstestszenario-Eigenschaften](../test/load-test-scenario-properties.md)