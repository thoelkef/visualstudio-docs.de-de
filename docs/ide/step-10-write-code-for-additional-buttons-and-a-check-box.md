---
title: 'Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5db017ac20c84b8d06832a9b40f98c6519842361
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918874"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen
Jetzt sind Sie bereit, die anderen vier Methoden abzuschließen. Sie können diesen Code zwar kopieren und einfügen, aber um bei diesem Lernprogramm den größtmöglichen Lerneffekt zu erzielen, sollten Sie den Code eingeben und IntelliSense verwenden.

Mit diesem Code wird den Schaltflächen die Funktionalität hinzugefügt, die Sie zuvor hinzugefügt haben. Ohne diesen Code haben die Schaltflächen keine Funktion. In den <xref:System.Windows.Forms.Control.Click>-Ereignissen der Schaltflächen wird Code verwendet (und im Kontrollkästchen wird das <xref:System.Windows.Forms.CheckBox.CheckedChanged>-Ereignis verwendet), damit unterschiedliche Aufgaben ausgeführt werden, wenn die Steuerelemente aktiviert werden. Zum Beispiel löscht das `clearButton_Click`-Ereignis, das aktiviert wird, wenn Sie die Schaltfläche **Bild löschen** auswählen, das aktuelle Bild, indem die Eigenschaft **Image** auf **NULL** (oder **nichts**) festlegt wird. Alle Ereignisse im Code enthalten Kommentare, in denen der Zweck des Codes erklärt wird.

![Videolink](../data-tools/media/playvideo.gif) Videos zu diesem Thema finden Sie unter [Tutorial 1: Create a picture viewer in Visual Basic – Video 5 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic – Video 5)](http://go.microsoft.com/fwlink/?LinkId=205216) und [Tutorial 1: Create a picture viewer in C# – Video 5 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in C# – Video 5)](http://go.microsoft.com/fwlink/?LinkId=205206). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

> [!NOTE]
> Bewährt hat sich folgende Methode: Kommentieren Sie stets Ihren Code. Kommentare stellen Informationen für andere Personen bereit, und Sie sollten sich die Zeit nehmen, den Code verständlich zu machen. Der gesamte Text in einer Kommentarzeile wird vom Programm ignoriert. In Visual C# kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile zwei Schrägstriche (//) eingegeben. In Visual Basic kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile ein einfaches Anführungszeichen (') einfügen.

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>So schreiben Sie Code für zusätzliche Schaltflächen und ein Kontrollkästchen

- Fügen Sie der Codedatei **Form1** (*Form1.cs* oder *Form1.vb*) den folgenden Code hinzu. Wählen Sie die Registerkarte **VB** aus, um Visual Basic-Code anzuzeigen.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter [Schritt 11: Ausführen des Programms und Ausprobieren weiterer Funktionen](../ide/step-11-run-your-program-and-try-other-features.md).

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md).
