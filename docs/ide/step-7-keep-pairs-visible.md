---
title: "Schritt 7: Beibehalten der Sichtbarkeit von Paaren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schritt 7: Beibehalten der Sichtbarkeit von Paaren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Spiel funktioniert gut, solange der Spieler jeweils zwei Symbole auswählt, die nicht übereinstimmen.  Was soll aber passieren, wenn der Spieler ein übereinstimmendes Symbolpaar wählt?  Anstatt durch das Aktivieren des Zeitgebers \(mit der `Start()`\-Methode\) das Ausblenden der Symbole zu veranlassen, sollte sich das Spiel selbst zurücksetzen, damit die Verweisvariablen `firstClicked` und `secondClicked` nicht mehr auf Bezeichnungsfelder verweisen. Die Farben für die beiden gewählten Bezeichnungsfelder sollen jedoch nicht zurückgesetzt werden.  
  
### So behalten Sie die Sichtbarkeit von Paaren bei  
  
1.  Fügen Sie der `label_Click()`\-Ereignishandlermethode die folgende `if`\-Anweisung hinzu, und zwar im unteren Teil des Codes oberhalb der Anweisung, mit der Sie den Zeitgeber starten.  Sehen Sie sich den Code genau an, während Sie diesen dem Programm hinzufügen.  Machen Sie sich klar, wie der Code funktioniert.  
  
     [!code-cs[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]  
  
     Die erste Zeile der gerade hinzugefügten `if`\-Anweisung überprüft, ob das Symbol im ersten Bezeichnungsfeld, das der Spieler auswählt, dem Symbol im zweiten Bezeichnungsfeld entspricht.  Wenn die Symbole übereinstimmen, führt das Programm in die drei Anweisungen zwischen den geschweiften Klammern \(in C\#\) bzw. die drei Anweisungen innerhalb der `if`\-Anweisung \(in Visual Basic \) aus.  Die ersten beiden Anweisungen setzen die Verweisvariablen `firstClicked` und `secondClicked` zurück, damit diese nicht mehr auf Bezeichnungsfelder verweisen. \(Es kann sein, dass Sie diese beiden Anweisungen aus dem Tick\-Ereignishandler des Zeitgebers wiedererkennen.\) Die dritte Anweisung ist eine `return`\-Anweisung, die das Programm anweist, die restlichen Anweisungen in der Methode zu überspringen, statt sie auszuführen.  
  
     Beim Programmieren in Visual C\# ist Ihnen möglicherweise aufgefallen, dass in einigen Teilen des Codes ein einzelnes Gleichheitszeichen \(`=`\) verwendet wird, während in anderen Anweisungen zwei Gleichheitszeichen \(`==`\) verwendet werden.  Überlegen Sie, warum an einigen Stellen `=` und an anderen Stellen `==` verwendet wird.  
  
     Dies ist ein gutes Beispiel, das den Unterschied verdeutlicht.  Sehen Sie sich den Code zwischen den Klammern in der `if`\-Anweisung genau an.  
  
    ```vb#  
    firstClicked.Text = secondClicked.Text  
    ```  
  
    ```c#  
    firstClicked.Text == secondClicked.Text  
    ```  
  
     Achten Sie dann besonders auf die erste Anweisung im Codeblock nach der `if`\-Anweisung.  
  
    ```vb#  
    firstClicked = Nothing  
    ```  
  
    ```c#  
    firstClicked = null;  
    ```  
  
     Die erste dieser beiden Anweisungen überprüft, ob zwei Symbole miteinander übereinstimmen.  Da zwei Werte verglichen werden, verwendet das Visual C\#\-Programm den Gleichheitsoperator `==`.  Die zweite Anweisung nimmt dann die eigentliche Änderung des Werts \(als *Zuweisung* bezeichnet\) vor, indem sie die `firstClicked`\-Verweisvariable auf `null` festlegt, um diese zurückzusetzen.  Aus diesem Grund verwendet sie stattdessen den Zuweisungsoperator `=`.  Visual C\# verwendet `=` zum Festlegen von Werten und `==` zum Vergleichen dieser Werte.  Visual Basic verwendet `=` sowohl für die Zuweisung von Variablen als auch für den Vergleich.  
  
2.  Speichern und starten Sie das Programm, und beginnen Sie dann mit dem Auswählen von Symbolen im Formular.  Wenn Sie ein Paar auswählen, das nicht übereinstimmt, wird das Tick\-Ereignis des Zeitgebers ausgelöst, und beide Symbole werden ausgeblendet.  Wenn Sie ein übereinstimmendes Paar wählen, wird die neue `if`\-Anweisung ausgeführt, und die return\-Anweisung bewirkt, dass die Methode den Code überspringt, der den Zeitgeber startet, sodass die Symbole sichtbar bleiben. Dies ist in der folgenden Abbildung dargestellt.  
  
     ![Spiel, das Sie in diesem Lernprogramm erstellen](../ide/media/express_finishedgame.png "Express\_FinishedGame")  
Vergleichsspiel mit sichtbaren Symbolpaaren  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 6: Hinzufügen eines Zeitgebers](../ide/step-6-add-a-timer.md).