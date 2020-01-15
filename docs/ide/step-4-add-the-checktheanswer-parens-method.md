---
title: 'Schritt 4: Hinzufügen der CheckTheAnswer()-Methode'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 658815849051aa8f86d70d0181b4f3b075fac9a8
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776050"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Schritt 4: Hinzufügen der CheckTheAnswer()-Methode

Im vierten Teil dieses Lernprogramms schreiben Sie eine Methode, `CheckTheAnswer()`, die bestimmt, ob die Antworten auf die Mathematikaufgaben korrekt sind. Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>So überprüfen Sie, ob die Antworten richtig sind

> [!NOTE]
> Wenn Sie weiterhin in Visual Basic arbeiten, verwenden Sie das Schlüsselwort `Function` anstelle des üblichen Schlüsselworts `Sub`, da diese Methode einen Wert zurückgibt. Es ist wirklich ganz einfach: Ein Sub-Schlüsselwort gibt keinen Wert zurück, aber ein Function-Schlüsselwort gibt einen Wert zurück.

1. Fügen Sie die `CheckTheAnswer()`-Methode hinzu.

     Wenn diese Methode aufgerufen wird, werden die Werte von „addend1“ und „addend2“ hinzugefügt und das Ergebnis mit dem Wert im <xref:System.Windows.Forms.NumericUpDown>-Summensteuerelement verglichen. Wenn die Werte gleich sind, gibt die Methode den Wert `true` zurück. Anderenfalls gibt die Methode den Wert `false` zurück. Der Code sollte wie folgt aussehen.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nun überprüfen Sie die Antwort, indem Sie die Code in der Methode aktualisieren, damit der <xref:System.Windows.Forms.Timer.Tick>-Ereignishandler des Zeitgebers die neue `CheckTheAnswer()`-Methode aufruft.

2. Fügen Sie der `if else`-Anweisung folgenden Code hinzu.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Wenn die Antwort richtig ist, gibt `CheckTheAnswer()``true` zurück. Der Ereignishandler beendet den Timer, zeigt eine Glückwunschmeldung an, und macht anschließend die Schaltfläche **Start** erneut verfügbar. Anderenfalls wird das Quiz fortgesetzt.

3. Speichern Sie das Programm, führen Sie es aus, starten Sie ein Quiz, und geben Sie eine richtige Antwort für die Additionsaufgabe an.

    > [!NOTE]
    > Bevor Sie die Antwort eingeben, müssen Sie entweder den Standardwert auswählen, oder Sie müssen die Null manuell löschen. Später in diesem Lernprogramm wird dieses Verhalten korrigiert.

     Wenn Sie eine richtige Antwort angeben, wird ein Meldungsfeld geöffnet, die Schaltfläche **Start** wird verfügbar, und der Timer wird angehalten.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 3: Hinzufügen eines Countdowntimers](../ide/step-3-add-a-countdown-timer.md).
