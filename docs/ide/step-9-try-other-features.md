---
title: "Schritt 9: Ausprobieren weiterer Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schritt 9: Ausprobieren weiterer Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um den Lerneffekt zu erhöhen, können Sie das Ändern von Symbolen und Farben, das Hinzufügen eines Spielzeitgebers und das Hinzufügen von Sounds ausprobieren.  Versuchen Sie, die Spielfläche zu vergrößern und den Zeitgeber anzupassen, um das Spiel anspruchsvoller zu machen.  
  
 Informationen zum Herunterladen einer abgeschlossenen Version des des Beispiels finden Sie im Beispiel des Lernprogramms [Complete Matching Game \(Durchführen des Abgleichspiels\)](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) finden Sie unter.  
  
### So probieren Sie weitere Funktionen aus  
  
-   Ersetzen Sie die Symbole und Farben durch selbst gewählte Symbole und Farben.  
  
    > [!TIP]
    >  Beschäftigen Sie sich mit der [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx)\-Eigenschaft des Bezeichnungsfelds.  
  
-   Fügen Sie einen Spielzeitgeber hinzu und ermitteln Sie, wie lange es dauert, bis der Spieler gewinnt.  
  
    > [!TIP]
    >  Dazu können Sie ein Bezeichnungsfeld über dem TableLayoutPanel\-Steuerelement hinzufügen und darin die bisher abgelaufene Zeit anzeigen, und dem Formular ein weiteres Zeitgeber\-Steuerelement hinzufügen, das die Zeit misst.  Verwenden Sie Code, um den Zeitgeber zu starten, wenn der Spieler das Spiel startet, und beenden Sie den Zeitgeber, nachdem die letzten zwei Symbole übereinstimmen.  
  
-   Fügen Sie einen Sound hinzu, der wiedergegeben wird, wenn der Spieler eine Übereinstimmung findet. Fügen Sie einen anderen Sound hinzu, der wiedergegeben wird, wenn der Spieler zwei nicht übereinstimmende Symbole aufdeckt, und einen dritten Sound für das Ausblenden der Symbole durch das Programm.  
  
    > [!TIP]
    >  Um Sounds wiederzugeben, können Sie den System.media\-Namespace verwenden.  Weitere Informationen finden Sie unter [Wiedergeben von Sounds in der  Windows Forms\-App \(C\#\)](http://youtu.be/qOh4ooHg1UU) oder [So erfolgt die Audiowiedergabe in Visual Basic](http://youtu.be/-4oPDeQrtMs).  
  
-   Machen Sie das Spiel schwieriger, indem Sie die Spielfläche vergrößern.  
  
    > [!TIP]
    >  Es genügt nicht, einfach nur Zeilen und Spalten im TableLayoutPanel\-Steuerelement hinzuzufügen – Sie müssen außerdem die Anzahl von Symbolen beachten, die Sie erstellen.  
  
-   Gestalten Sie das Spiel anspruchsvoller, indem Sie das erste Symbol ausblenden, wenn der Spieler zu langsam ist und nach Ablauf einer bestimmten Zeit nicht das zweite Symbol gewählt hat.  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Wenn Sie sich festfahren oder Probleme mit der Programmierung haben, versuchen Sie, Ihre Fragen in einem der MSDN\-Foren zu stellen.  Siehe [Forum zu Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) und [Visual C\#\-Forum](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Es stehen umfangreiche kostenlose Videoschulungen zur Verfügung.  Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic\-Grundlagen: Entwicklung für Anfänger](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).  Weitere Informationen zum Programmieren in Visual Basic C\# finden Sie unter [C\#\-Grundlagen: Entwicklung für Anfänger](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Weitere Informationen, um zum vorherigen Lernprogrammschritt zurückzukehren, finden Sie unter [Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).