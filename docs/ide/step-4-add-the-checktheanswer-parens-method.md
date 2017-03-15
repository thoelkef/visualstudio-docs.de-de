---
title: "Schritt&#160;4: Hinzuf&#252;gen der CheckTheAnswer()-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schritt&#160;4: Hinzuf&#252;gen der CheckTheAnswer()-Methode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im vierten Teil dieses Lernprogramms schreiben Sie eine Methode, `CheckTheAnswer()`, die bestimmt, ob die Antworten auf die Mathematikaufgaben korrekt sind.  Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung.  Eine Übersicht des Lernprogramms finden Sie unter [Lernprogramm 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Wenn Sie weiterhin in Visual Basic arbeiten, verwenden Sie das Schlüsselwort `Function` anstelle des üblichen Schlüsselworts `Sub`, da diese Methode einen Wert zurückgibt.  Es ist wirklich ganz einfach: Ein Sub\-Schlüsselwort gibt keinen Wert zurück, aber ein Function\-Schlüsselwort gibt einen Wert zurück.  
  
### So überprüfen Sie, ob die Antworten richtig sind  
  
1.  Fügen Sie die `CheckTheAnswer()`\-Methode hinzu.  
  
     Wenn diese Methode aufgerufen wird, werden die Werte von addend1 und addend2 hinzugefügt und das Ergebnis mit dem Wert im `NumericUpDown`\-Steuerelement "sum" verglichen.  Wenn die Werte gleich sind, gibt die Methode den Wert `true` zurück.  Anderenfalls gibt die Methode den Wert `false` zurück.  Der Code sollte wie folgt aussehen.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-cs[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Nun überprüfen Sie die Antwort, indem Sie die Code in der Methode aktualisieren, damit der Tick\-Ereignishandler des Zeitgebers die neue `CheckTheAnswer()`\-Methode aufruft.  
  
2.  Fügen Sie der `if else`\-Anweisung folgenden Code hinzu.  
  
     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-cs[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  
  
     Wenn die Antwort richtig ist, gibt `CheckTheAnswer()` `true` zurück.  Der Ereignishandler beendet den Zeitgeber, zeigt eine Glückwunschmeldung an, und dann ist die Schaltfläche **Start** erneut verfügbar.  Anderenfalls wird das Quiz fortgesetzt.  
  
3.  Speichern Sie das Programm, führen Sie es aus, starten Sie ein Quiz, und geben Sie eine richtige Antwort für die Additionsaufgabe an.  
  
    > [!NOTE]
    >  Bevor Sie die Antwort eingeben, müssen Sie entweder den Standardwert auswählen, oder Sie müssen die Null manuell löschen.  Später in diesem Lernprogramm wird dieses Verhalten korrigiert.  
  
     Wenn Sie eine richtige Antwort angegeben, wird ein Meldungsfeld geöffnet, die Schaltfläche **Start** wird verfügbar, und der Zeitgeber wird angehalten.  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 5: Hinzufügen von Enter\-Ereignishandlern für die NumericUpDown\-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 3: Hinzufügen eines Countdownzeitgebers](../ide/step-3-add-a-countdown-timer.md).