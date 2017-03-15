---
title: "Schritt 6: Hinzuf&#252;gen eines Zeitgebers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Schritt 6: Hinzuf&#252;gen eines Zeitgebers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Als Nächstes fügen Sie dem Spiel ein **Zeitgeber**\-Steuerelement hinzu.  Ein solcher Zeitgeber wartet eine angegebene Anzahl von Millisekunden und löst anschließend ein Ereignis aus, das als *Tick* bezeichnet wird.  Dies ist nützlich für den Start einer Aktion oder die regelmäßige Wiederholung eine Aktion.  In diesem Fall verwenden Sie einen Zeitgeber, um dem Spieler zu ermöglichen, zwei Symbole auszuwählen, und um die beiden Symbole nach einer kurzen Zeit wieder auszublenden, sofern sie nicht übereinstimmen.  
  
### So fügen Sie einen Zeitgeber hinzu  
  
1.  Wählen Sie **Zeitgeber** im Werkzeugkasten des Windows Forms\-Designers \(in der Kategorie **Komponenten**\) und anschließend die EINGABETASTE, oder doppelklicken Sie auf den Zeitgeber, um dem Formular ein Zeitgeber\-Steuerelement hinzuzufügen.  Das Symbol des Zeitgebers mit dem Namen **Zeitgeber1** wird in einem Bereich unterhalb des Formulars angezeigt, wie in der folgenden Abbildung dargestellt.  
  
     ![Zeitgeber](../ide/media/express_timer.png "Express\_Timer")  
Zeitgeber  
  
    > [!NOTE]
    >  Wenn der Werkzeugkasten leer ist, haben Sie zuvor möglicherweise nicht den Formular\-Designer aktiviert, sondern den Code für das Formular.  
  
2.  Wählen Sie das Symbol **Zeitgeber1**, um den Zeitgeber auszuwählen.  Im Fenster **Eigenschaften** wechseln Sie von der Anzeige der Ereignisse zur Anzeige der Eigenschaften.  Legen Sie die **Interval**\-Eigenschaft des Zeitgebers auf 750 fest, ohne den Wert **False** der **Enabled**\-Eigenschaft zu ändern.  Die Eigenschaft **Intervall** gibt an, wie lange der Zeitgeber zwischen *Ticks* wartet bzw. wann das Tick\-Ereignis auslöst werden soll.  Mit dem Wert 750 wartet der Zeitgeber eine Dreiviertelsekunde \(750 Millisekunden\), bevor er das Tick\-Ereignis auslöst.  Sie rufen die `Start()`\-Methode für den Start des Zeitgeber nur auf, nachdem der Spieler das zweite Bezeichnungsfeld auswählt hat.  
  
3.  Wählen Sie das Symbol des Zeitgeber\-Steuerelements im Windows Forms\-Designer und dann die EINGABETASTE, oder doppelklicken Sie auf den Zeitgeber, um einen leeren **Tick**\-Ereignishandler hinzuzufügen.  Ersetzen Sie entweder den Code durch den folgenden Code, oder geben Sie den folgenden Code manuell in den Ereignishandler ein.  
  
     [!code-cs[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]  
  
     Der Tick\-Ereignishandler bewirkt drei Dinge. Zuerst beendet er den Zeitgeber, indem er die `Stop()`\-Methode aufruft.  Anschließend verwendet er die beiden Verweisvariablen `firstClicked` und `secondClicked`, um die Symbole für die zwei Bezeichnungsfelder, die der Spieler gewählt hat, wieder unsichtbar zu machen.  Zuletzt setzt er die Verweisvariablen `firstClicked` und `secondClicked` in Visual C\# auf `null` und in Visual Basic auf `Nothing` zurück.  Dieser Schritt ist wichtig, weil sich das Programm auf diese Weise selbst zurücksetzt.  In diesem Zustand werden keine `Label`\-Steuerelemente überwacht, und das Programm ist wieder für eine Auswahl des Spielers bereit.  
  
    > [!NOTE]
    >  Ein `Timer`\-Objekt verfügt über eine `Start()`\-Methode, die den Zeitgeber startet, und eine `Stop()`\-Methode, die den Zeitgeber stoppt.  Wenn Sie die **Enabled**\-Eigenschaft des Zeitgebers im Eigenschaftenfenster auf **True** festlegen,fängt dieser an zu laufen, sobald das Programm beginnt.  Wenn Sie die Eigenschaft jedoch auf **False** festgelegt lassen, fängt dieser erst an zu laufen, wenn seine `Start()`\-Methode aufgerufen wird.  Normalerweise löst ein Zeitgeber sein Tick\-Ereignis immer wieder aus, wobei in der **Interval**\-Eigenschaft festgelegt ist, wie viele Millisekunden zwischen Ticks gewartet wird.  Sie haben möglicherweise bemerkt, dass im Tick\-Ereignis die `Stop()`\-Methode des Zeitgebers aufgerufen wird.  Damit wird der Zeitgeber in den *Einmalmodus* versetzt, was bedeutet, dass er nach dem Aufruf der `Start()`\-Methode das festgelegte Zeitintervall wartet, dann ein Tick\-Ereignis auslöst und anschließend stoppt.  
  
4.  Um den neuen Zeitgeber in Aktion zu sehen, wechseln Sie zum Code\-Editor und fügen am Anfang und Ende der `label_Click()`\-Ereignishandlermethode den folgenden Code hinzu. \(Sie fügen am Anfang eine `if`\-Anweisung und am Ende drei Anweisungen hinzu. Der Rest der Methode bleibt unverändert.\)  
  
     [!code-cs[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]  
  
     Der Code am Anfang der Methode ermittelt durch Überprüfung des Werts der **Enabled**\-Eigenschaft, ob der Zeitgeber gestartet wurde.  Wenn der Spieler also das erste und zweite `Label`\-Steuerelement wählt und der Zeitgeber gestartet wird, hat die Auswahl eines dritten Steuerelements keinerlei Auswirkungen.  
  
     Mit dem Code am Ende der Methode wird die `secondClicked`\-Verweisvariable festgelegt, um das zweite `Label`\-Steuerelement zu ermitteln, das der Spieler gewählt hat. Anschließend wird die Farbe des Symbols im Bezeichnungsfeld auf Schwarz festgelegt, um es sichtbar zu machen.  Dann startet der Code den Zeitgeber im Einmalmodus, sodass dieser 750 Millisekunden lang wartet und dann ein einzelnes Tick\-Ereignis auslöst.  Der Tick\-Ereignishandler des Zeitgebers blendet dann die beiden Symbole aus und setzt die Verweisvariablen `firstClicked` und `secondClicked` zurück, damit das Formular dafür bereit ist, dass der Spieler ein anderes Symbol wählt.  
  
5.  Speichern Sie das Programm, und führen Sie es aus.  Wenn Sie ein Symbol wählen, wird es sichtbar.  
  
6.  Wählen Sie ein anderes Symbol.  Es wird kurz angezeigt, und dann werden beide Symbole wieder ausgeblendet.  Wiederholen Sie dies mehrere Male.  Das Formular überwacht jetzt das erste und zweite gewählte Symbol und verwendet den Zeitgeber, um bis zum Ausblenden der Symbole zu warten.  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 7: Beibehalten der Sichtbarkeit von Paaren](../ide/step-7-keep-pairs-visible.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 5: Hinzufügen von Bezeichnungsverweisen](../ide/step-5-add-label-references.md).