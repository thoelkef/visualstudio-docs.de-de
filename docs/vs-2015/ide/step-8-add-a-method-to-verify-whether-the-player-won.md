---
title: 'Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 278d8d71378c0d14047fe8e012fed21951101548
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306630"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie haben ein unterhaltsames Spiel erstellt, aber es benötigt noch eine zusätzliche Funktion. Das Spiel soll enden, wenn der Spieler gewonnen hat. Sie müssen also eine `CheckForWinner()`-Methode hinzufügen, mit der überprüft wird, ob der Spieler gewonnen hat.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>So fügen Sie eine Methode hinzu, mit der überprüft wird, ob der Spieler gewonnen hat  
  
1.  Fügen Sie eine `CheckForWinner()`-Methode am Ende Ihres Codes hinzu, unter dem `timer1_Tick()`-Ereignishandler, wie im folgenden Code gezeigt.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]  
  
     Die Methode verwendet eine weitere `foreach`-Schleife in Visual C# bzw. eine weitere `For Each`-Schleife in Visual Basic, um die einzelnen Bezeichnungen im TableLayoutPanel zu durchlaufen. Mithilfe des Gleichheitsoperators (`==` in Visual C# und `=` in Visual Basic) wird die Symbolfarbe der einzelnen Bezeichnungen darauf überprüft, ob diese mit dem Hintergrund übereinstimmt. Wenn die Farben übereinstimmen, bleibt das Symbol sichtbar. Dies bedeutet, dass der Spieler noch nicht alle Symbolpaare gefunden hat. Das Programm verwendet in diesem Fall eine `return`-Anweisung, um den Rest der Methode zu überspringen. Falls die Schleife alle Bezeichnungsfelder durchlaufen kann, ohne dass die `return`-Anweisung ausgeführt wird, bedeutet dies, dass alle Symbole des Formulars gefunden wurden. Das Programm zeigt eine MessageBox an, in der dem Spieler zum gewonnenen Spiel gratuliert wird, und ruft dann die `Close()`-Methode des Formulars auf, um das Spiel zu beenden.  
  
2.  Legen Sie als Nächstes fest, dass der Click-Ereignishandler der Bezeichnung die neue `CheckForWinner()`-Methode aufruft. Stellen Sie sicher, dass das Programm die Gewinnprüfung sofort durchführt, nachdem es das zweite Symbol angezeigt hat, das vom Spieler gewählt wurde. Suchen Sie nach der Zeile, in der Sie die Farbe des zweiten gewählten Symbols festgelegt haben, und rufen Sie direkt danach die `CheckForWinner()`-Methode auf. Dies ist im folgenden Code dargestellt.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]  
  
3.  Speichern Sie das Programm, und führen Sie es aus. Spielen Sie das Spiel, und finden Sie alle übereinstimmenden Symbolpaare. Wenn Sie gewonnen haben, zeigt das Programm eine MessageBox mit einem Glückwunsch an (wie in der folgenden Abbildung dargestellt) und schließt diese dann.  
  
     ![Memory-Spiel mit MessageBox](../ide/media/express-tut4step8.png "Express_Tutorial4Schritt8")  
Vergleichsspiel mit MessageBox  
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Tutorialschritt zu wechseln, klicken Sie auf [Schritt 9: Ausprobieren weiterer Funktionen](../ide/step-9-try-other-features.md).  
  
-   Wenn Sie zum vorherigen Tutorialschritt zurückkehren möchten, klicken Sie auf [Schritt 7: Beibehalten der Sichtbarkeit von Paaren](../ide/step-7-keep-pairs-visible.md).



