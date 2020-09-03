---
title: 'Schritt 9: Ausprobieren weiterer Funktionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299978"
---
# <a name="step-9-try-other-features"></a>Schritt 9: Ausprobieren weiterer Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um den Lerneffekt zu erhöhen, können Sie das Ändern von Symbolen und Farben, das Hinzufügen eines Spieltimers und das Hinzufügen von Sounds ausprobieren. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen, um das Spiel anspruchsvoller zu machen.

### <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus

- Ersetzen Sie die Symbole und Farben durch selbst gewählte Symbole und Farben.

    > [!TIP]
    > Beschäftigen Sie sich mit der [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx)-Eigenschaft des Bezeichnungsfelds.

- Fügen Sie einen Spieltimer hinzu und ermitteln Sie, wie lange es dauert, bis der Spieler gewinnt.

    > [!TIP]
    > Dazu können Sie ein Bezeichnungsfeld über dem TableLayoutPanel-Steuerelement hinzufügen und darin die bisher abgelaufene Zeit anzeigen, und dem Formular ein weiteres Zeitgeber-Steuerelement hinzufügen, das die Zeit misst. Verwenden Sie Code, um den Zeitgeber zu starten, wenn der Spieler das Spiel startet, und beenden Sie den Zeitgeber, nachdem die letzten zwei Symbole übereinstimmen.

- Fügen Sie einen Sound hinzu, der wiedergegeben wird, wenn der Spieler eine Übereinstimmung findet. Fügen Sie einen anderen Sound hinzu, der wiedergegeben wird, wenn der Spieler zwei nicht übereinstimmende Symbole aufdeckt, und einen dritten Sound für das Ausblenden der Symbole durch das Programm.

    > [!TIP]
    > Um Sounds wiederzugeben, können Sie den System.media-Namespace verwenden. Weitere Informationen finden Sie unter [Wiedergeben von Sounds in der Windows Forms-App (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) oder [So erfolgt die Audiowiedergabe in Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be).

- Machen Sie das Spiel schwieriger, indem Sie die Spielfläche vergrößern.

    > [!TIP]
    > Es genügt nicht, einfach nur Zeilen und Spalten im TableLayoutPanel-Steuerelement hinzuzufügen – Sie müssen außerdem die Anzahl von Symbolen beachten, die Sie erstellen.

- Gestalten Sie das Spiel anspruchsvoller, indem Sie das erste Symbol ausblenden, wenn der Spieler zu langsam ist und nach Ablauf einer bestimmten Zeit nicht das zweite Symbol gewählt hat.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Wenn Sie sich festfahren oder Probleme mit der Programmierung haben, versuchen Sie, Ihre Fragen in einem der MSDN-Foren zu stellen. Weitere Informationen finden Sie im Forum zu [Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) und [Visual C#-Forum](https://social.msdn.microsoft.com/Forums/en-US/home).

- Es stehen umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic Grundlagen: Entwicklung für Anfänger](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic C# finden Sie unter [C#-Grundlagen: Entwicklung für Anfänger](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Um zum vorherigen Tutorialschritt zurückzukehren, finden [Sie unterschritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)hat.
