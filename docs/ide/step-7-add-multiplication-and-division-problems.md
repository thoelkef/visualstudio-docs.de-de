---
title: "Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 481d1ad8050a0b028a7cbf23f9385c9920feb1a2
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben
Im siebenten Teil dieses Lernprogramms fügen Sie Multiplikations- und Divisionsaufgaben hinzu. Zunächst müssen Sie aber überlegen, wie diese Änderung vorgenommen wird. Überlegen Sie sich den ersten Schritt, der das Speichern von Werten einschließt.  
  
### <a name="to-add-multiplication-and-division-problems"></a>So fügen Sie Multiplikations- und Divisionsaufgaben hinzu  
  
1.  Fügen Sie dem Formular vier Ganzzahlvariablen hinzu.  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  Ändern Sie wie zuvor die `StartTheQuiz()`-Methode, damit die Multiplikations- und Divisionsaufgaben mit Zufallszahlen ausgefüllt werden.  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  Ändern Sie die `CheckTheAnswer()`-Methode, damit auch die Multiplikations- und Divisionsaufgaben überprüft werden.  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     Da es keine einfache Möglichkeit gibt, das Multiplikationszeichen (×) und das Divisionszeichen (÷) mit der Tastatur einzugeben, wird in Visual C# und Visual Basic ein Sternchen (*) für Multiplikation und ein Schrägstrich (/) für Division akzeptiert.  
  
4.  Ändern Sie den letzten Teil des Tick-Ereignishandlers des Timers, damit die richtige Antwort ausgegeben wird, wenn die Zeit abgelaufen ist.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  Speichern Sie das Programm, und führen Sie es aus.  
  
     Die Quizteilnehmer müssen vier Aufgaben beantworten, um das Quiz abzuschließen. Dies ist in der folgenden Abbildung veranschaulicht.  
  
     ![Mathetest mit vier Aufgaben](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Mathetest mit vier Aufgaben  
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 8: Anpassen des Quiz](../ide/step-8-customize-the-quiz.md).  
  
-   Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md).
