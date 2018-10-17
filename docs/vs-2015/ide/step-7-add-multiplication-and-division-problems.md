---
title: 'Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c0c2b069ebb75cbe4547528317544172b1d7ae2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195155"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im siebenten Teil dieses Lernprogramms fügen Sie Multiplikations- und Divisionsaufgaben hinzu. Zunächst müssen Sie aber überlegen, wie diese Änderung vorgenommen wird. Überlegen Sie sich den ersten Schritt, der das Speichern von Werten einschließt.  
  
### <a name="to-add-multiplication-and-division-problems"></a>So fügen Sie Multiplikations- und Divisionsaufgaben hinzu  
  
1.  Fügen Sie dem Formular vier Ganzzahlvariablen hinzu.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Ändern Sie wie zuvor die `StartTheQuiz()`-Methode, damit die Multiplikations- und Divisionsaufgaben mit Zufallszahlen ausgefüllt werden.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Ändern Sie die `CheckTheAnswer()`-Methode, damit auch die Multiplikations- und Divisionsaufgaben überprüft werden.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Da es keine einfache Möglichkeit gibt, das Multiplikationszeichen (×) und das Divisionszeichen (÷) mit der Tastatur einzugeben, wird in Visual C# und Visual Basic ein Sternchen (*) für Multiplikation und ein Schrägstrich (/) für Division akzeptiert.  
  
4.  Ändern Sie den letzten Teil des Tick-Ereignishandlers des Timers, damit die richtige Antwort ausgegeben wird, wenn die Zeit abgelaufen ist.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Speichern Sie das Programm, und führen Sie es aus.  
  
     Die Quizteilnehmer müssen vier Aufgaben beantworten, um das Quiz abzuschließen. Dies ist in der folgenden Abbildung veranschaulicht.  
  
     ![Mathetest mit vier Aufgaben](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Mathetest mit vier Aufgaben  
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 8: Anpassen des Quiz](../ide/step-8-customize-the-quiz.md).  
  
-   Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md).



