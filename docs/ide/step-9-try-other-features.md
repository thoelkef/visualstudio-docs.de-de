---
title: 'Schritt 9: Ausprobieren weiterer Features'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af132efde0c1a49e5404fa602363aab0554e6f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572465"
---
# <a name="step-9-try-other-features"></a>Schritt 9: Ausprobieren weiterer Features
Um den Lerneffekt zu erhöhen, können Sie das Ändern von Symbolen und Farben, das Hinzufügen eines Spieltimers und das Hinzufügen von Sounds ausprobieren. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen, um das Spiel anspruchsvoller zu machen.

Ein vollständige Version des Beispiels können Sie unter [Complete Matching Game tutorial sample (Durchführen des Abgleichspiels)](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) herunterladen.

## <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus

- Ersetzen Sie die Symbole und Farben durch selbst gewählte Symbole und Farben.

    > [!TIP]
    > Beschäftigen Sie sich mit der [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>)-Eigenschaft des Bezeichnungsfelds.

- Fügen Sie einen Spieltimer hinzu und ermitteln Sie, wie lange es dauert, bis der Spieler gewinnt.

    > [!TIP]
    > Dazu können Sie ein Bezeichnungsfeld über dem <xref:System.Windows.Forms.TableLayoutPanel>-Steuerelement hinzufügen, um die bisher abgelaufene Zeit anzuzeigen, und dem Formular ein weiteres Zeitgeber-Steuerelement hinzufügen, das die Zeit misst. Verwenden Sie Code, um den Zeitgeber zu starten, wenn der Spieler das Spiel startet, und beenden Sie den Zeitgeber, nachdem die letzten zwei Symbole übereinstimmen.

- Fügen Sie einen Sound hinzu, der wiedergegeben wird, wenn der Spieler eine Übereinstimmung findet. Fügen Sie einen anderen Sound hinzu, der wiedergegeben wird, wenn der Spieler zwei nicht übereinstimmende Symbole aufdeckt, und einen dritten Sound für das Ausblenden der Symbole durch das Programm.

    > [!TIP]
    > Um Sounds wiederzugeben, können Sie den <xref:System.Media>-Namespace verwenden. Weitere Informationen finden Sie in den Videos [Play sounds in Windows Forms app (C#) (Wiedergeben von Sound in der Windows Forms-App (C#))](http://youtu.be/qOh4ooHg1UU) oder [How to play audio in Visual Basic (Audiowiedergabe in Visual Basic)](http://youtu.be/-4oPDeQrtMs).

- Machen Sie das Spiel schwieriger, indem Sie die Spielfläche vergrößern.

    > [!TIP]
    > Es genügt nicht, einfach nur Zeilen und Spalten im TableLayoutPanel-Steuerelement hinzuzufügen – Sie müssen außerdem die Anzahl von Symbolen beachten, die Sie erstellen.

- Gestalten Sie das Spiel anspruchsvoller, indem Sie das erste Symbol ausblenden, wenn der Spieler zu langsam ist und nach Ablauf einer bestimmten Zeit nicht das zweite Symbol gewählt hat.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Es stehen umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic fundamentals: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in C# finden Sie unter [C#-Grundlagen: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 8: Hinzufügen einer Methode, um zu überprüfen, ob ein Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
