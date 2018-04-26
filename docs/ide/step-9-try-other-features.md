---
title: 'Schritt 9: Ausprobieren weiterer Funktionen'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac46fb97c0d199554e395907cf8e7caa3a634bc3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="step-9-try-other-features"></a>Schritt 9: Ausprobieren weiterer Funktionen
Um den Lerneffekt zu erhöhen, können Sie das Ändern von Symbolen und Farben, das Hinzufügen eines Spieltimers und das Hinzufügen von Sounds ausprobieren. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen, um das Spiel anspruchsvoller zu machen.  

 Ein vollständige Version des Beispiels können Sie unter [Complete Matching Game tutorial sample (Durchführen des Abgleichspiels)](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) herunterladen.  

### <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus  

-   Ersetzen Sie die Symbole und Farben durch selbst gewählte Symbole und Farben.  

    > [!TIP]
    >  Beschäftigen Sie sich mit der [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx)-Eigenschaft des Bezeichnungsfelds.  

-   Fügen Sie einen Spieltimer hinzu und ermitteln Sie, wie lange es dauert, bis der Spieler gewinnt.  

    > [!TIP]
    >  Dazu können Sie ein Bezeichnungsfeld über dem TableLayoutPanel-Steuerelement hinzufügen und darin die bisher abgelaufene Zeit anzeigen, und dem Formular ein weiteres Zeitgeber-Steuerelement hinzufügen, das die Zeit misst. Verwenden Sie Code, um den Zeitgeber zu starten, wenn der Spieler das Spiel startet, und beenden Sie den Zeitgeber, nachdem die letzten zwei Symbole übereinstimmen.  

-   Fügen Sie einen Sound hinzu, der wiedergegeben wird, wenn der Spieler eine Übereinstimmung findet. Fügen Sie einen anderen Sound hinzu, der wiedergegeben wird, wenn der Spieler zwei nicht übereinstimmende Symbole aufdeckt, und einen dritten Sound für das Ausblenden der Symbole durch das Programm.  

    > [!TIP]
    >  Um Sounds wiederzugeben, können Sie den System.media-Namespace verwenden. Weitere Informationen finden Sie in den Videos zum [Wiedergeben von Sound in der Windows Forms-App (C#)](http://youtu.be/qOh4ooHg1UU) oder zur [Audiowiedergabe in Visual Basic](http://youtu.be/-4oPDeQrtMs).  

-   Machen Sie das Spiel schwieriger, indem Sie die Spielfläche vergrößern.  

    > [!TIP]
    >  Es genügt nicht, einfach nur Zeilen und Spalten im TableLayoutPanel-Steuerelement hinzuzufügen – Sie müssen außerdem die Anzahl von Symbolen beachten, die Sie erstellen.  

-   Gestalten Sie das Spiel anspruchsvoller, indem Sie das erste Symbol ausblenden, wenn der Spieler zu langsam ist und nach Ablauf einer bestimmten Zeit nicht das zweite Symbol gewählt hat.  

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  

-   Wenn Sie sich festfahren oder Probleme mit der Programmierung haben, versuchen Sie, Ihre Fragen in einem der MSDN-Foren zu stellen. Weitere Informationen finden Sie im Forum zu [Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) und [Visual C#-Forum](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  

-   Es stehen umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic-Grundlagen: Entwicklung für Anfänger](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic C# finden Sie unter [C#-Grundlagen: Entwicklung für Anfänger](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  

-   Weitere Informationen, um zum vorherigen Tutorialschritt zurückzukehren, finden Sie unter [Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
