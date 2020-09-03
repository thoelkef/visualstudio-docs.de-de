---
title: 'Schritt 5: Hinzufügen von Bezeichnungsverweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671741"
---
# <a name="step-5-add-label-references"></a>Schritt 5: Hinzufügen von Bezeichnungsverweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Programm muss nachverfolgen, welches Bezeichnungsfeld der Spieler wählt. Bisher zeigt das Programm alle Bezeichnungsfelder an, die der Spieler ausgewählt hat. Wir werden das ändern. Nachdem das erste Bezeichnungsfeld gewählt wurde, sollte das Programm das Symbol im Bezeichnungsfeld anzeigen. Nachdem das zweite Bezeichnungsfeld ausgewählt ist, sollte das Programm beide Symbole für eine kurze Zeit anzeigen und dann beide wieder ausblenden. Das Programm verfolgt nun mithilfe von *Verweis Variablen*, welches Bezeichnungsfeld zuerst ausgewählt und welches als zweites ausgewählt wird.

### <a name="to-add-label-references"></a>So fügen Sie Bezeichnungsverweise hinzu

1. Fügen Sie dem Formular Bezeichnungsverweise hinzu, indem Sie den folgenden Code verwenden.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Diese Verweisvariablen ähneln im Aussehen den Anweisungen, mit denen Sie zuvor dem Formular Objekte (wie `Timer`, `List` und `Random`) hinzugefügt haben. Diese Anweisungen bewirken jedoch nicht, dass im Formular zwei zusätzliche Bezeichnungsfelder angezeigt werden, da das Schlüsselwort `new` in keiner der beiden Anweisungen enthalten ist. Ohne das `new`-Schlüsselwort wird kein Objekt erstellt. `firstClicked` und `secondClicked` werden als Verweisvariablen bezeichnet, weil sie Verweise auf `Label`-Objekte speichern.

     Wenn eine Variable keinen Verweis auf ein Objekt enthält, wird sie auf einen besonderen Wert festgelegt: `null` in Visual C# und `Nothing` in Visual Basic. Beim Starten des Programms erhalten also sowohl `firstClicked` als auch `secondClicked` den Wert `null` bzw. `Nothing`. Dies bedeutet, dass die Variablen keine Objektverweise enthalten.

2. Ändern Sie den Click-Ereignishandler so, dass er die neue `firstClicked`-Verweisvariable verwendet. Entfernen Sie die letzte Anweisung in der `label_Click()`-Ereignishandlermethode (`clickedLabel.ForeColor = Color.Black;`), und ersetzen Sie diese durch die `if`-Anweisung, die darauf folgt. (Achten Sie darauf, den Kommentar und die gesamte `if`-Anweisung einzufügen.)

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Speichern Sie das Programm, und führen Sie es aus. Wählen Sie eines der Bezeichnungsfelder. Das entsprechende Symbol wird angezeigt.

4. Wählen Sie das nächste Bezeichnungsfeld. Sie werden bemerken, dass nichts passiert. Das Programm merkt sich bereits das erste Bezeichnungsfeld, auf das der Spieler geklickt hat, `firstClicked` entspricht also nicht `null` (in Visual C#) bzw. `Nothing` (in Visual Basic). Wenn die `if`-Anweisung `firstClicked` darauf überprüft, ob sie `null` oder `Nothing` entspricht, stellt sie fest, dass dies nicht der Fall ist. Die Anweisungen in der `if`-Anweisung werden also nicht ausgeführt. Deshalb wird nur die Farbe für das erste gewählte Symbol in Schwarz geändert. Die anderen Symbole bleiben ausgeblendet. Dies ist in der folgenden Abbildung dargestellt.

     ![Entsprechendes Spiel mit einem Symbol](../ide/media/express-tut4step5.png "Express_Tut4Step5") Entsprechendes Spiel mit einem Symbol

     Sie beheben diese Situation im nächsten Tutorialschritt, indem Sie ein **Timer**-Steuerelement hinzufügen.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, klicken [Sie auf Schritt 6: Hinzufügen eines Timers](../ide/step-6-add-a-timer.md).

- Um zum vorherigen Tutorialschritt zurückzukehren, [Klicken Sie auf Schritt 4: Hinzufügen eines Click-Ereignis Handlers zu jeder Bezeichnung](../ide/step-4-add-a-click-event-handler-to-each-label.md).
