---
title: 'Schritt 4: Hinzufügen der CheckTheAnswer()-Methode'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c691b1db57fa1a00ad33441e36ff0f7f79716f11
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416511"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Schritt 4: Hinzufügen der CheckTheAnswer()-Methode
Im vierten Teil dieses Lernprogramms schreiben Sie eine Methode, `CheckTheAnswer()`, die bestimmt, ob die Antworten auf die Mathematikaufgaben korrekt sind. Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Wenn Sie weiterhin in Visual Basic arbeiten, verwenden Sie das Schlüsselwort `Function` anstelle des üblichen Schlüsselworts `Sub`, da diese Methode einen Wert zurückgibt. Es ist wirklich ganz einfach: Ein Sub-Schlüsselwort gibt keinen Wert zurück, aber ein Function-Schlüsselwort gibt einen Wert zurück.

## <a name="to-verify-whether-the-answers-are-correct"></a>So überprüfen Sie, ob die Antworten richtig sind

1. Fügen Sie die `CheckTheAnswer()`-Methode hinzu.

     Wenn diese Methode aufgerufen wird, werden die Werte von „addend1“ und „addend2“ hinzugefügt und das Ergebnis mit dem Wert im <xref:System.Windows.Forms.NumericUpDown>-Summensteuerelement verglichen. Wenn die Werte gleich sind, gibt die Methode den Wert `true` zurück. Anderenfalls gibt die Methode den Wert `false` zurück. Der Code sollte wie folgt aussehen.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     Nun überprüfen Sie die Antwort, indem Sie die Code in der Methode aktualisieren, damit der <xref:System.Windows.Forms.Timer.Tick>-Ereignishandler des Zeitgebers die neue `CheckTheAnswer()`-Methode aufruft.

2. Fügen Sie der `if else`-Anweisung folgenden Code hinzu.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Wenn die Antwort richtig ist, gibt `CheckTheAnswer()` `true` zurück. Der Ereignishandler beendet den Timer, zeigt eine Glückwunschmeldung an, und macht anschließend die Schaltfläche **Start** erneut verfügbar. Anderenfalls wird das Quiz fortgesetzt.

3. Speichern Sie das Programm, führen Sie es aus, starten Sie ein Quiz, und geben Sie eine richtige Antwort für die Additionsaufgabe an.

    > [!NOTE]
    > Bevor Sie die Antwort eingeben, müssen Sie entweder den Standardwert auswählen, oder Sie müssen die Null manuell löschen. Später in diesem Lernprogramm wird dieses Verhalten korrigiert.

     Wenn Sie eine richtige Antwort angeben, wird ein Meldungsfeld geöffnet, die Schaltfläche **Start** wird verfügbar, und der Timer wird angehalten.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter [Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 3: Hinzufügen eines Countdowntimers](../ide/step-3-add-a-countdown-timer.md).
