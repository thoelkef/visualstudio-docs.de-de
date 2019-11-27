---
title: 'Schritt 11: Ausführen des Programms und Ausprobieren weiterer Funktionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d79bf8205e4233a89effcd04196b18f9c11df26
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295767"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Schritt 11: Führen Sie das Programms aus und probieren Sie weitere Funktionen aus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Programm ist fertig und bereit zur Ausführung. Sie können das Programm ausführen und die Hintergrundfarbe von PictureBox festlegen. Um den Lerneffekt zu erhöhen, können Sie das Programm verbessern, indem Sie die Farbe des Formulars ändern, die Schaltflächen und das Kontrollkästchen anpassen und die Eigenschaften des Formulars ändern.

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") Eine videoversion dieses Themas finden Sie unter [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 5](https://go.microsoft.com/fwlink/?LinkId=205216) oder [Tutorial 1: Erstellen eines Bild Anzeige Programms C# in-Video 5](https://go.microsoft.com/fwlink/?LinkId=205206). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

### <a name="to-run-your-program-and-set-the-background-color"></a>So können Sie das Programm ausführen und die Hintergrundfarbe festlegen

1. Wählen Sie F5 oder in der Menüleiste **Debuggen**, **Debuggen starten** aus.

2. Bevor Sie ein Bild öffnen, wählen Sie die Schaltfläche **Hintergrundfarbe festlegen** aus. Das Dialogfeld **Farbe** wird geöffnet.

     ![Farbe (Dialogfeld](../ide/media/express-colordialog.png "Express_ColorDialog") ) Farbe (Dialogfeld)

3. Wählen Sie eine Farbe aus, um die PictureBox-Hintergrundfarbe festzulegen. Schauen Sie sich die `backgroundButton_Click()`-Methode genau an, um zu verstehen, wie sie funktioniert.

    > [!NOTE]
    > Sie können aus dem Internet ein Bild laden, indem Sie die URL des Bilds in das Dialogfeld **Datei öffnen** einfügen. Versuchen Sie, ein Bild mit einem transparenten Hintergrund zu finden, damit die Hintergrundfarbe angezeigt wird.

4. Wählen Sie die Schaltfläche **Bild löschen** aus, um sicherzustellen, das es gelöscht wird. Beenden Sie dann das Programm, indem Sie die Schaltfläche **Schließen** auswählen.

### <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus

- Ändern Sie die Farbe des Formulars und der Schaltflächen mit der **BackColor**-Eigenschaft.

- Passen Sie die Schaltflächen und das Kontrollkästchen mit den Eigenschaften **Font** und **ForeColor** an.

- Ändern Sie die Eigenschaften **FormBorderStyle** und **ControlBox** des Formulars.

- Verwenden Sie die Eigenschaften **AcceptButton** und **CancelButton** des Formulars, damit Schaltflächen automatisch ausgewählt werden, wenn der Benutzer die EINGABETASTE oder ESC-TASTE auswählt. Veranlassen Sie, dass das Programm das Dialogfeld **Datei öffnen** öffnet, wenn der Benutzer die EINGABETASTE auswählt, und das Dialogfeld schließt, wenn der Benutzer ESC auswählt.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Weitere Informationen zum Programmieren in Visual Studio finden Sie unter [Programmierkonzepte](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Weitere Informationen zu Visual Basic finden Sie unter [Entwickeln von Anwendungen mit Visual Basic](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).

- Weitere Informationen zu Visual C# finden Sie in der [Einführung in die Programmiersprache C# und in .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).

- Um zum nächsten Tutorial zu wechseln, klicken Sie auf [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Um zum vorhergehenden Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
