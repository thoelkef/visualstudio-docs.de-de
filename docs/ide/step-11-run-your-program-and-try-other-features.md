---
title: 'Schritt 11: Ausführen des Programms und Ausprobieren weiterer Features'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbceecbbe03e84e1dac6c851f3bbb692c0e26539
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934652"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Schritt 11: Ausführen des Programms und Ausprobieren weiterer Features
Das Programm ist fertig und bereit zur Ausführung. Sie können das Programm ausführen und die Hintergrundfarbe von <xref:System.Windows.Forms.PictureBox> festlegen. Um den Lerneffekt zu erhöhen, können Sie das Programm verbessern, indem Sie die Farbe des Formulars ändern, die Schaltflächen und das Kontrollkästchen anpassen und die Eigenschaften des Formulars ändern.

 Informationen zum Herunterladen einer vollständigen Version des Beispiels finden Sie unter [Complete picture viewer tutorial sample (Tutorialbeispiel für vollständiges Bildanzeigeprogramm)](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

 ![Videolink](../data-tools/media/playvideo.gif) Videos zu diesem Thema finden Sie unter [Tutorial 1: Create a picture viewer in Visual Basic – Video 5 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic – Video 5)](http://go.microsoft.com/fwlink/?LinkId=205216) und [Tutorial 1: Create a picture viewer in C# – Video 5 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in C# – Video 5)](http://go.microsoft.com/fwlink/?LinkId=205206). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

## <a name="to-run-your-program-and-set-the-background-color"></a>So können Sie das Programm ausführen und die Hintergrundfarbe festlegen

1.  Drücken Sie **F5**, oder klicken Sie in der Menüleiste auf **Debuggen** > **Debuggen starten**.

2.  Bevor Sie ein Bild öffnen, wählen Sie die Schaltfläche **Hintergrundfarbe festlegen** aus. Das Dialogfeld **Farbe** wird geöffnet.

     ![Dialogfeld „Farbe“](../ide/media/express_colordialog.png)
 Dialogfeld **Farbe**

3.  Wählen Sie eine Farbe aus, um die PictureBox-Hintergrundfarbe festzulegen. Schauen Sie sich die `backgroundButton_Click()`-Methode genau an, um zu verstehen, wie sie funktioniert.

    > [!NOTE]
    >  Sie können aus dem Internet ein Bild laden, indem Sie die URL des Bilds in das Dialogfeld **Datei öffnen** einfügen. Versuchen Sie, ein Bild mit einem transparenten Hintergrund zu finden, damit die Hintergrundfarbe angezeigt wird.

4.  Wählen Sie die Schaltfläche **Bild löschen** aus, um sicherzustellen, das es gelöscht wird. Beenden Sie dann das Programm, indem Sie die Schaltfläche **Schließen** auswählen.

## <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus

-   Ändern Sie die Farbe des Formulars und der Schaltflächen mit der **BackColor**-Eigenschaft.

-   Passen Sie die Schaltflächen und das Kontrollkästchen mit den Eigenschaften **Font** und **ForeColor** an.

-   Ändern Sie die Eigenschaften **FormBorderStyle** und **ControlBox** des Formulars.

-   Verwenden Sie die Eigenschaften **AcceptButton** und **CancelButton** des Formulars, damit Schaltflächen automatisch ausgewählt werden, wenn der Benutzer die **EINGABETASTE** oder die **ESC-TASTE** drückt. Veranlassen Sie, dass das Programm das Dialogfeld **Datei öffnen** öffnet, wenn der Benutzer die **EINGABETASTE** drückt, und das Dialogfeld schließt, wenn der Benutzer die **ESC-TASTE** drückt.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

-   Weitere Informationen zum Programmieren in Visual Studio finden Sie unter [Programmierkonzepte](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Weitere Informationen zu Visual Basic finden Sie unter [Entwickeln von Anwendungen mit Visual Basic](/dotnet/visual-basic/developing-apps/index).

-   Weitere Informationen zu Visual C# finden Sie in der [Einführung in die Programmiersprache C# und in .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Das nächste Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
