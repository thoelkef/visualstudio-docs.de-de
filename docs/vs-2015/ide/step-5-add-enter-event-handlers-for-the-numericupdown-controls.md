---
title: 'Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 566bcf10d681b9ea81ee78601bf8536e9e6d9985
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671746"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im fünften Teil dieses Lernprogramms fügen Sie Enter-Ereignishandler hinzu, um die Eingabe von Antworten auf Quizfragen zu vereinfachen. Mit diesem Code wird der aktuelle Wert in den einzelnen NumericUpDown-Steuerelementen markiert und gelöscht, sobald ein Quizteilnehmer das Steuerelement ausgewählt und einen anderen Wert eingibt.

> [!NOTE]
> Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht des Tutorials finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-verify-the-default-behavior"></a>So überprüfen Sie das Standardverhalten

1. Führen Sie das Programm aus, und starten Sie das Quiz.

     Im NumericUpDown-Steuerelement für die Additionsaufgabe blinkt der Cursor neben der **0** (Null).

2. Geben Sie `3` ein, und beachten Sie, dass das Steuerelement **30** anzeigt.

3. Geben Sie `5` ein, und beachten Sie, dass der Wert **350** angezeigt wird, sich aber nach einer Sekunde in **100** ändert.

     Bevor Sie dieses Problem beheben, denken Sie über das nach, was geschieht. Überlegen Sie, warum die **0** nicht verschwunden ist, als Sie `3` eingegeben haben, und warum **350** in **100** geändert wurde, die Änderung jedoch nicht unmittelbar stattgefunden hat.

     Dieses Verhalten scheint ungewöhnlich, ist jedoch vor dem Hintergrund der Logik des Codes sinnvoll. Wenn Sie die Schaltfläche **Start** auswählen, wird die **Enabled**-Eigenschaft der Schaltfläche auf **False** gesetzt, und die Schaltfläche ist abgeblendet und nicht verfügbar. Das Programm wechselt die aktuelle Auswahl (Fokus) auf das Steuerelement mit dem nächstniedrigen TabIndex-Wert. Dies ist das NumericUpDown-Steuerelement für die Additionsaufgabe. Wenn Sie mit der TAB-TASTE zu einem NumericUpDown-Steuerelement wechseln, wird der Cursor automatisch an den Anfang des Steuerelements positioniert. Dies bewirkt, dass die von Ihnen eingegebenen Zahlen von links und nicht von rechts angezeigt werden. Wenn Sie eine Zahl angeben, die höher als der Wert der Eigenschaft **MaximumValue** ist, der auf 100 festgelegt ist, wird die von Ihnen eingegebene Zahl durch den Wert dieser Eigenschaft ersetzt.

### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>So fügen Sie einen Enter-Ereignishandler für ein NumericUpDown-Steuerelement hinzu

1. Wählen Sie das erste NumericUpDown-Steuerelement (namens „sum“) im Formular aus, und wählen Sie im Dialogfeld **Eigenschaften** das Symbol **Ereignisse** auf der Symbolleiste aus.

     Auf der Registerkarte **Ereignisse** im Dialogfeld **Eigenschaften** werden alle Ereignisse angezeigt, auf die Sie für das Element reagieren können (Handler), das Sie im Formular ausgewählt haben. Da Sie das NumericUpDown-Steuerelement ausgewählt haben, sind alle aufgeführten Ereignisse betroffen.

2. Wählen Sie das **Enter** Ereignis aus, geben Sie `answer_Enter` ein, und drücken Sie dann die EINGABETASTE.

     ![Eigenschaften (Dialogfeld](../ide/media/express-answerenter.png "Express_AnswerEnter") ) Eigenschaften (Dialogfeld)

     Sie haben soeben einen Enter-Ereignishandler für das NumericUpDown-Steuerelement „sum“ hinzugefügt, und Sie haben den Handler **answer_Enter** genannt.

3. Fügen Sie in der Methode für den **answer_Enter**-Ereignishandler den folgenden Code hinzu.

     [!code-csharp[VbExpressTutorial3Step5_6#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial3Step5_6#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#11)]

     Dieser Code sieht komplex aus, aber Sie können ihn verstehen, wenn Sie ihn schrittweise überprüfen. Schauen Sie sich zuerst den Beginn der Methode an: `object sender` in C# oder `sender As System.Object` in Visual Basic. Dieser Parameter verweist auf das Objekt, dessen Ereignis ausgelöst wird, das als Absender bezeichnet wird. In diesem Fall ist das Absenderobjekt das NumericUpDown-Steuerelement. Geben Sie in der ersten Zeile der Methode an, dass der Absender nicht nur ein beliebiges generisches Objekt ist, sondern speziell ein NumericUpDown-Steuerelement. (Jedes NumericUpDown-Steuerelement ist ein Objekt, aber nicht jedes Objekt ist ein NumericUpDown-Steuerelement.) Das NumericUpDown-Steuerelement wird in dieser Methode als **beantwortes Feld** benannt, da es für alle NumericUpDown-Steuerelemente im Formular verwendet wird, nicht nur für das NumericUpDown-Steuerelement Sum. Da Sie die Variable "answerBox" in dieser Methode deklarieren, gilt der Bereich nur für diese Methode. Das bedeutet, dass die Variable nur innerhalb dieser Methode verwendet werden kann.

     Die nächste Zeile überprüft, ob answerBox erfolgreich von einem Objekt in ein NumericUpDown-Steuerelement konvertiert (umgewandelt) wurde. Wenn die Konvertierung nicht erfolgreich war, hat die Variable einen Wert von `null` (C#) oder `Nothing` (Visual Basic). In der dritten Zeile wird die Länge der Antwort angegeben, die im NumericUpDown-Steuerelement angezeigt wird. In der vierten Zeile wird der aktuelle Wert im Steuerelement auf der Grundlage dieser Länge ausgewählt. Wenn der Quizteilnehmer nun das Steuerelement aktiviert, löst Visual Studio das Ereignis aus. Daraufhin wird die aktuelle Antwort ausgewählt. Sobald der Quizteilnehmer eine andere Antwort eingibt, wird die vorherige Antwort gelöscht und durch die neue Antwort ersetzt.

4. Wählen Sie im Windows Forms-Designer das NumericUpDown-Steuerelement "difference" aus.

5. Führen Sie auf der Seite **Ereignisse** des Dialogfelds **Eigenschaften** einen Bildlauf bis zum **Enter**-Ereignis durch, wählen Sie den Dropdownpfeil am Ende der Zeile aus, und wählen Sie dann den `answer_Enter`-Ereignishandler aus, den Sie gerade hinzugefügt haben.

6. Wiederholen Sie den vorherigen Schritt für die NumericUpDown-Steuerelemente "product" und "quotient".

7. Speichern Sie das Programm, und führen Sie es aus.

     Wenn Sie ein NumericUpDown-Steuerelement auswählen, wird der vorhandene Wert automatisch aktiviert und dann gelöscht, wenn Sie einen anderen Wert eingeben.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md).

- Um zum vorhergehenden Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 4: Hinzufügen der CheckTheAnswer()-Methode](../ide/step-4-add-the-checktheanswer-parens-method.md).
