---
title: Anwenden der Verteilung auf Geschwindigkeitsverzögerung für Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 5140a3ca9cb8274a9b6d9f74260adadfed6201ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model"></a>How to: Apply Distribution to Pacing Delay When Using a User Pace Test Mix Model

Nachdem Sie den Auslastungstest mithilfe des Assistenten für neuen Auslastungstest erstellt haben, können Sie die Szenarioeigenschaften mit dem Auslastungstest-Editor entsprechend Ihren Testanforderungen und -zielen ändern.

Die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** wird mit dem Eigenschaftenfenster festgelegt. Eigenschaften für Auslastungstestszenarien werden mit dem Auslastungstest-Editor geändert.

> [!NOTE]
> Die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** gilt nur, wenn die *Auslastungstestmischung* auf Grundlage der Benutzergeschwindigkeit konfiguriert ist. Weitere Informationen finden Sie unter [Editing Text Mix Models to Specify the Probability of a Virtual User Running a Test (Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt)](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Der Wert für **Verteilung auf Geschwindigkeitsverzögerung anwenden** kann auf TRUE oder FALSE festgelegt werden:

-   **TRUE**: Das Szenario wendet herkömmliche statistische Verteilungsverzögerungen an, die über den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld „Testmischung bearbeiten“ angegeben werden. Weitere Informationen finden Sie unter [Editing Text Mix Models to Specify the Probability of a Virtual User Running a Test (Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt)](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld „Testmischung bearbeiten“ für den Test ist auf zwei Benutzer pro Stunde festgelegt. Ist die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **TRUE** festgelegt, wird auf die Wartezeit zwischen den Tests eine herkömmliche statistische Verteilung angewendet. Es werden weiterhin zwei Tests pro Stunde ausgeführt, zwischen ihnen ist jedoch nicht notwendigerweise eine Verzögerung von 30 Minuten. Der erste Test konnte nach 4 Minuten und der zweite Test nach 45 Minuten ausgeführt werden.

-   **FALSE**: Die Tests werden mit der Geschwindigkeit ausgeführt, die Sie für den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld „Testmischung bearbeiten“ angegeben haben. Weitere Informationen finden Sie unter [Editing Text Mix Models to Specify the Probability of a Virtual User Running a Test (Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt)](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld „Testmischung bearbeiten“ für den Test ist auf zwei Benutzer pro Stunde festgelegt. Wenn die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **FALSE** festgelegt ist, ist kein Spielraum für die Testausführung vorhanden. Der Test wird alle 30 Minuten ausgeführt. So ist sichergestellt, dass Sie zwei Tests pro Stunde ausführen.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>So geben Sie die Eigenschafteneinstellung "Verteilung auf Geschwindigkeitsverzögerung anwenden" für ein Szenario an

1.  Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2.  Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den Sie die zu verwendenden Agents angeben möchten.

3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im Fenster **Eigenschaften** angezeigt.

4.  Wählen Sie im Eigenschaftswert für **Verteilung auf Geschwindigkeitsverzögerung anwenden** entweder **TRUE** oder **FALSE** aus.

5.  Klicken Sie nach dem Ändern der Eigenschaft im Menü **Datei** auf **Speichern**. Sie können dann den Auslastungstest mit dem neuen Wert von **Verteilung auf Geschwindigkeitsverzögerung anwenden** ausführen.

## <a name="see-also"></a>Siehe auch

- [Editing Load Test Scenarios (Szenarios zum Bearbeiten von Auslastungstests)](../test/edit-load-test-scenarios.md)
- [Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Auslastungstestszenario-Eigenschaften](../test/load-test-scenario-properties.md)