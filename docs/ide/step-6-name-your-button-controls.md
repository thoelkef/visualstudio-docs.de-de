---
title: "Schritt 6: Benennen der Schaltflächen-Steuerelemente | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 09ce424d13fd6fa2e6e511370f509dd54a7c1a1e
ms.openlocfilehash: 9af9f76e799c39533785f9230be867ace4dbee6a
ms.contentlocale: de-de
ms.lasthandoff: 05/19/2017

---
# <a name="step-6-name-your-button-controls"></a>Schritt 6: Benennen der Schaltflächen-Steuerelemente
Es gibt nur ein PictureBox-Steuerelement im Formular. Als Sie es hinzugefügt haben, hat die IDE diesem Steuerelement automatisch den Namen **pictureBox1**gegeben. Es gibt nur ein Kontrollkästchen, das den Namen **checkBox1**trägt. Bald schreiben Sie einige Codezeilen, die auf das CheckBox- und das PictureBox-Steuerelement verweisen. Da jedes Steuerelement nur einmal vorhanden ist, wissen Sie, was sich hinter den Namen **pictureBox1** oder **checkBox1** im Code verbirgt.  
  
> [!NOTE]
>  In Visual Basic beginnen die Namen von Steuerelementen automatisch mit einem großen Anfangsbuchstaben. Daher lauten die Namen dort **PictureBox1**, **CheckBox1**usw.  
  
 Das Formular enthält vier Schaltflächen, und die IDE hat ihnen folgende Namen zugewiesen: **button1**, **button2**, **button3**und **button4**. Anhand der aktuellen Namen können Sie jedoch nicht erkennen, welches Steuerelement die Schaltfläche **Close** ist und welches Steuerelement die Schaltfläche **Show a picture** ist. Daher ist es hilfreich, den Schaltflächen-Steuerelementen aufschlussreichere Namen zu geben.  
  
 ![Link zum Video](../data-tools/media/playvideo.gif "Video wiedergeben")Eine Videoversion dieses Themas finden Sie im Video 3 zum [Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=205213) oder im Video 3 zum [Tutorial 1: Erstellen eines Bildanzeigeprogramms in C#](http://go.microsoft.com/fwlink/?LinkId=205202). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.  
  
### <a name="to-name-your-button-controls"></a>So benennen Sie die Schaltflächen-Steuerelemente  
  
1.  Wählen Sie im Formular die Schaltfläche **Schließen** aus. (Wenn alle Schaltflächen noch auswählt sind, wählen Sie die ESC-TASTE aus, um die Auswahl aufzuheben.) Scrollen Sie im Fenster **Eigenschaften**, bis Sie die Eigenschaft **(Name)** sehen. (Die Eigenschaft **(Name)** befindet sich oben in der Liste, wenn die Eigenschaften alphabetisch sortiert sind.) Ändern Sie den Namen in **closeButton**, wie im folgenden Bild gezeigt.  
  
     ![Eigenschaftenfenster mit closeButton-Name](../ide/media/express_setnameproperty.png "Express_SetNameProperty")  
Eigenschaftenfenster mit closeButton-Name  
  
    > [!NOTE]
    >  Wenn Sie versuchen, den Namen der Schaltfläche in **closeButton** zu ändern, also mit einem Leerzeichen zwischen den beiden Wörtern, zeigt die IDE eine Fehlermeldung an: "Der Eigenschaftswert ist ungültig". Leerzeichen (und einige andere Zeichen) sind in Steuerelementnamen nicht zulässig.  
  
2.  Benennen Sie die anderen drei Schaltflächen in **backgroundButton**, **clearButton**und **showButton**um. Sie können die Namen überprüfen, indem Sie im Fenster **Eigenschaften** die Steuerelementauswahl-Dropdownliste auswählen. Die neuen Schaltflächennamen werden angezeigt.  
  
3.  Doppelklicken Sie im Formular auf die Schaltfläche **Bild anzeigen** . Wählen Sie alternativ die Schaltfläche **Bild anzeigen** im Formular und anschließend die EINGABETASTE aus. Damit öffnet die IDE eine zusätzliche Registerkarte im Hauptfenster mit der Bezeichnung **Form1.cs** (**Form1.vb** bei Verwendung von Visual Basic). Auf dieser Registerkarte wird die Codedatei hinter dem Formular angezeigt, wie im folgenden Bild dargestellt.  
  
     ![Form1.cs-Registerkarte mit Visual C&#35;-Code](../ide/media/express_showbuttoncode.png "Express_ShowButtonCode")  
Form1.cs-Registerkarte mit Visual C#-Code  
  
4.  Konzentrieren Sie sich auf diesen Teil des Codes. (Wählen Sie bei Verwendung von Visual Basic die Registerkarte **VB** unten aus, um die Visual Basic-Version des Codes anzuzeigen.)  
  
     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]  [!code-cs[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]  
  
     Sie betrachten Code mit dem Namen `showButton_Click()`. Die IDE hat ihn dem Code des Formulars hinzugefügt, als Sie die Codedatei für die Schaltfläche **showButton** geöffnet haben. Wenn Sie zur Entwurfszeit die Codedatei für ein Steuerelement in einem Formular öffnen, wird Code für das Steuerelement generiert, wenn er nicht bereits vorhanden ist. Dieser Code, als *Methode*bezeichnet, wird ausgeführt, wenn Sie das Programm ausführen und das Steuerelement auswählen, in diesem Fall die Schaltfläche **Bild anzeigen** .  
  
    > [!NOTE]
    >  In diesem Lernprogramm wurde der automatisch generierte Visual Basic-Code vereinfacht, indem der zwischen Klammern, (), gesetzte Text entfernt wurde. In diesen Fällen können Sie den gleichen Code entfernen. Das Programm funktioniert so oder so. Für den Rest der Lernprogramme wird automatisch generierter Code vereinfacht, wann immer dies möglich ist.  
  
5.  Wählen Sie die Registerkarte "Windows Forms-Designer" erneut aus (**Form1.cs [Entwurf]** in Visual C#, **Form1.vb [Entwurf]** in Visual Basic), und öffnen Sie dann die Codedatei für die Schaltfläche **Bild löschen** , um eine Methode für sie im Code des Formulars zu erstellen. Wiederholen Sie diesen Vorgang für die verbleibenden beiden Schaltflächen. Die IDE fügt der Codedatei des Formulars jedes Mal eine neue Methode hinzu.  
  
6.  Um eine weitere Methode hinzuzufügen, öffnen Sie die Codedatei für das CheckBox-Steuerelement im Windows Forms-Designer, damit die IDE eine `checkBox1_CheckedChanged()` -Methode hinzufügt. Diese Methode wird immer dann aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert.  
  
    > [!NOTE]
    >  Wenn Sie an einem Programm arbeiten, wechseln Sie häufig zwischen dem Code-Editor und dem Windows Forms-Designer. Die IDE vereinfacht die Navigation im Projekt. Öffnen Sie den Windows Forms-Designer mit dem **Projektmappen-Explorer** , indem Sie in Visual C# auf **Form1.cs** oder in Visual Basic auf **Form1.vb** doppelklicken, oder wählen Sie in der Menüleiste **Ansicht**, **Designer**aus.  
  
     Im Folgenden sehen Sie den neuen Code, der im Code-Editor angezeigt wird.  
  
     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]  [!code-cs[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]  
  
     Die fünf Methoden, die Sie hinzugefügt haben, werden als *Ereignishandler*bezeichnet, da das Programm sie immer dann aufruft, wenn ein Ereignis eintritt (wenn z. B. ein Benutzer eine Schaltfläche auswählt oder ein Kontrollkästchen aktiviert).  
  
     Wenn Sie den Code für ein Steuerelement in der IDE zur Entwurfszeit anzeigen, fügt Visual Studio für dieses Steuerelement eine Ereignishandlermethode hinzu, wenn keine vorhanden ist. Wenn Sie z. B. auf eine Schaltfläche doppelklicken, fügt die IDE einen Ereignishandler für das Click-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer die Schaltfläche auswählt). Wenn Sie auf ein Kontrollkästchen doppelklicken, fügt die IDE einen Ereignishandler für das CheckedChanged-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert).  
  
     Nachdem Sie für ein Steuerelement einen Ereignishandler hinzugefügt haben, können Sie jederzeit vom Windows Forms-Designer aus zum Steuerelement zurückkehren, indem Sie auf das Steuerelement doppelklicken oder in der Menüleiste **Ansicht**, **Code**auswählen.  
  
     Namen sind wichtig, wenn Sie Programme erstellen, und für Methoden (und Ereignishandler) können Sie beliebige Namen verwenden. Wenn Sie mit der IDE einen Ereignishandler hinzufügen, erstellt die IDE basierend auf dem Namen des Steuerelements und des behandelten Ereignisses einen Namen. Das Click-Ereignis für eine Schaltfläche mit dem Namen **showButton** wird z. B. als `showButton_Click()` -Ereignishandlermethode bezeichnet. Normalerweise werden nach dem Methodennamen auch eine öffnende und eine schließende runde Klammer () hinzugefügt, um anzuzeigen, dass es sich um Methoden handelt. Wenn Sie einen Codevariablennamen ändern möchten, klicken Sie mit der rechten Maustaste auf die Variable im Code, und wählen Sie dann **Umgestalten**, **Umbenennen**aus. Alle Instanzen dieser Variable im Code werden umbenannt. Weitere Informationen finden Sie unter [Refactoring mit Umbenennen (C#)](../csharp-ide/refactoring/rename.md) oder [Refactoring mit Umbenennen (Visual Basic)](../vb-ide/refactoring/rename.md).
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
-   Um mit dem nächsten Tutorialschritt fortzufahren, klicken Sie auf [Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md).  
  
-   Um zum vorherigen Schritt des Tutorials zurückzukehren, klicken Sie auf [Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md).
