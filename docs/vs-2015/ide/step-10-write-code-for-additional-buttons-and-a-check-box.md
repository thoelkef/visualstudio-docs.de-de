---
title: 'Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen | Microsoft-Dokumente'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851593"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jetzt sind Sie bereit, die anderen vier Methoden abzuschließen. Sie können diesen Code zwar kopieren und einfügen, aber um bei diesem Lernprogramm den größtmöglichen Lerneffekt zu erzielen, sollten Sie den Code eingeben und IntelliSense verwenden.

 Mit diesem Code wird den Schaltflächen die Funktionalität hinzugefügt, die Sie zuvor hinzugefügt haben. Ohne diesen Code haben die Schaltflächen keine Funktion. In den `Click`-Ereignissen der Schaltflächen wird Code verwendet (und im Kontrollkästchen wird das `CheckChanged`-Ereignis verwendet), damit unterschiedliche Aufgaben ausgeführt werden, wenn die Steuerelemente aktiviert werden. Zum Beispiel löscht das `clearButton_Click`-Ereignis, das aktiviert wird, wenn Sie die Schaltfläche **Bild löschen** auswählen, das aktuelle Bild, indem die `Image`-Eigenschaft auf `null` (oder `nothing`) festlegt wird. Alle Ereignisse im Code enthalten Kommentare, in denen der Zweck des Codes erklärt wird.

 ![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") Eine videoversion dieses Themas finden Sie unter [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) oder [Tutorial 1: Erstellen eines Bild Anzeige Programms C# in-Video 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

> [!NOTE]
> Als bewährte Methode empfiehlt es sich, den Code immer zu kommentieren. Kommentare stellen Informationen für andere Personen bereit, und Sie sollten sich die Zeit nehmen, den Code verständlich zu machen. Der gesamte Text in einer Kommentarzeile wird vom Programm ignoriert. In Visual C# kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile zwei Schrägstriche (//) eingegeben. In Visual Basic kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile ein einfaches Anführungszeichen (') einfügen.

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>So schreiben Sie Code für zusätzliche Schaltflächen und ein Kontrollkästchen

- Fügen Sie der Form1-Codedatei (Form1.cs oder Form1.vb) den folgenden Code hinzu. Wählen Sie die Registerkarte **VB** aus, um Visual Basic-Code anzuzeigen.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 11: Ausführen des Programms und Ausprobieren weiterer Funktionen](../ide/step-11-run-your-program-and-try-other-features.md).

- Um zum vorherigen Schritt des Tutorials zurückzukehren, klicken Sie auf [Schritt 9: Hinzufügen von Steuerelementen zum Formular](../ide/step-9-review-comment-and-test-your-code.md).
