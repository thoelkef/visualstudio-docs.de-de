---
title: "Schritt&#160;7: Hinzuf&#252;gen von Dialogfeldkomponenten zum Formular | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schritt&#160;7: Hinzuf&#252;gen von Dialogfeldkomponenten zum Formular
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Schritt fügen Sie dem Formular eine Komponente **OpenFileDialog** und eine Komponente **ColorDialog** hinzu, damit das Programm Bilddateien öffnen und eine Hintergrundfarbe auswählen kann.  
  
 Eine Komponente ist in gewisser Hinsicht mit einem Steuerelement vergleichbar.  Sie fügen dem Formular mithilfe der Toolbox eine Komponente hinzu, und legen die Eigenschaften im Eigenschaftenfenster fest.  Aber im Gegensatz zu einem Steuerelement wird dem Formular beim Hinzufügen einer Komponente kein für den Benutzer sichtbares Element hinzugefügt.  Stattdessen stellt die Komponente bestimmte Verhalten bereit, die Sie mit Code auslösen können.  Es handelt sich um eine Komponente, die das Dialogfeld **Datei öffnen** anzeigt.  
  
 ![Link zu Video](../data-tools/media/playvideo.png "PlayVideo") Eine Videoversion dieses Themas finden Sie im [Video 1 zum Lernprogramm 3: Erstellen eines Bildanzeigeprogramms in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=205213) oder im [Video 1 zum Lernprogramm 3: Erstellen eines Bildanzeigeprogramms in C\#](http://go.microsoft.com/fwlink/?LinkId=205202).  Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können.  Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.  
  
### So fügen Sie dem Formular Dialogfeldkomponenten hinzu  
  
1.  Wählen Sie den Windows Forms\-Designer \(Form1.cs \[Entwurf\] oder Form1.vb \[Entwurf\]\) aus, und öffnen Sie dann die Gruppe **Dialogfelder** im Werkzeugkasten aus.  
  
    > [!NOTE]
    >  Die Gruppe **Dialogfelder** in der Toolbox verfügt über Komponenten zum Öffnen vieler nützlicher Dialogfelder, die z. B. zum Öffnen und Speichern von Dateien, Durchsuchen von Ordnern und Auswählen von Schriftarten und Farben verwendet werden können.  Sie verwenden in diesem Projekt zwei Dialogfeldkomponenten: **OpenFileDialog** und **ColorDialog**.  
  
2.  Um dem Formular eine Komponente mit dem Namen **openFileDialog1** hinzuzufügen, doppelklicken Sie auf **OpenFileDialog**.  Um dem Formular eine Komponente mit dem Namen **colorDialog1** hinzuzufügen, doppelklicken Sie in der Toolbox auf **ColorDialog**. \(Sie verwenden diese Komponente im nächsten Lernprogrammschritt.\) Sie sollten unten im Windows Forms\-Designer einen Bereich sehen \(unterhalb des Picture Viewer\-Formulars\), das ein Symbol für jede der beiden hinzugefügten Dialogfeldkomponenten enthält, so wie im folgenden Bild gezeigt.  
  
     ![Dialogfeldkomponenten](../ide/media/express_dialogsadded.png "Express\_DialogsAdded")  
Dialogfeldkomponenten  
  
3.  Wählen Sie das Symbol **openFileDialog1** im Bereich unten im Windows Forms\-Designer aus.  Legen Sie zwei Eigenschaften fest:  
  
    -   Legen Sie die Eigenschaft **Filter** auf Folgendes fest \(Sie können den Code kopieren und einfügen\):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Legen Sie die **Title**\-Eigenschaft auf Folgendes fest: Select a picture file  
  
         Die Eigenschafteneinstellungen für **Filter** geben die Arten von Dateitypen an, die im Dateidialogfeld **Select a picture** angezeigt werden.  
  
    > [!NOTE]
    >  Um ein Beispiel für das Dialogfeld **Datei öffnen** in einer anderen Anwendung zu sehen, öffnen Sie Editor oder Paint, und wählen Sie in der Menüleiste **Datei**, **Öffnen** aus.  Unten befindet sich die Dropdownliste **Dateityp**.  Sie haben soeben die **Filter**\-Eigenschaft in der **OpenFileDialog**\-Komponente verwendet, um diese Dropdownliste einzurichten.  Beachten Sie auch, dass die **Title**\-Eigenschaft und die **Filter**\-Eigenschaft im **Eigenschaftenfenster** fett sind.  Hierdurch kennzeichnet die IDE alle Eigenschaften, deren Standardwerte geändert wurden.  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche "Bild anzeigen"](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 6: Benennen der Schaltflächen\-Steuerelemente](../ide/step-6-name-your-button-controls.md).