---
title: "Lernprogramm 1: Erstellen eines Bildanzeigeprogramms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Lernprogramm 1: Erstellen eines Bildanzeigeprogramms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Lernprogramm erstellen Sie ein Programm, das ein Bild aus einer Datei lädt und in einem Fenster anzeigt.  Sie erfahren, wie Sie Steuerelemente, z. B. Schaltflächen und Bildfelder, auf das Formular ziehen, ihre Eigenschaften festlegen und mithilfe von Containern die Größe des Formulars stufenlos ändern können.  Sie fangen auch an, Code zu schreiben.  Sie lernen Folgendes:  
  
-   Erstellen Sie ein neues Projekt.  
  
-   Testen \(Debuggen\) einer Anwendung  
  
-   Hinzufügen grundlegender Steuerelemente, z. B. Kontrollkästchen und Schaltflächen, zu einem Formular  
  
-   Positionieren von Steuerelementen auf einem Formular mithilfe von Layouts  
  
-   Hinzufügen der Dialogfelder **Datei öffnen** und **Farbe** zu einem Formular.  
  
-   Schreiben von Code mithilfe von IntelliSense und Codeausschnitten  
  
-   Schreiben von Ereignishandlermethoden  
  
 Am Ende sieht das Programm so aus wie in der folgenden Abbildung.  
  
 ![Bild, das Sie in diesem Lernprogramm erstellen](../ide/media/express_pictureviewerdone.png "Express\_PictureViewerDone")  
Bild, das Sie in diesem Lernprogramm erstellen  
  
 Informationen zum Herunterladen einer abgeschlossenen Version des des Beispiels finden Sie im Beispiel des Lernprogramms [Complete Picture Viewer \(Ausführen des Bildbetrachtungsprogramms\)](http://code.msdn.microsoft.com/Complete-Matching-Game-7d91d3a8) finden Sie unter.  
  
 ![Link zu Video](../data-tools/media/playvideo.png "PlayVideo") Eine Videoversion dieses Themas finden Sie unter [Gewusst wie: Erstellen eines Bildbetrachtungsprogramms in Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) oder [Gewusst wie: Erstellen eines Bildbetrachtungsprogramms in C\#?](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können.  Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.  In diesem Lernprogramm wird sowohl Visual C\# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.  
>   
>  Um Code für Visual Basic anzuzeigen, wählen Sie die Registerkarte **VB** oben in den Codeblöcken aus. Um Code für Visual C\# anzuzeigen, wählen Sie die Registerkarte **C\#** aus.  Wenn Sie gern mehr über Visual C\+\+ erfahren möchten, finden Sie weitere Informationen unter [Erste Schritte](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) und [C\+\+ Language Tutorial](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Wenn Sie lernen möchten, wie Windows Store\-Apps in Visual C\# oder Visual Basic geschrieben werden, finden Sie weitere Informationen unter [Erstellen Ihrer ersten Windows Store\-App mit C\# oder Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx).  Informationen zum Erstellen von Windows Store\-Apps in JavaScript finden Sie unter [Erstellen Ihrer ersten Windows Store\-App mit JavaScript](http://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Schritt 1: Erstellen eines Windows Forms\-Anwendungsprojekts](../ide/step-1-create-a-windows-forms-application-project.md)|Beginnen Sie, indem Sie ein Windows Forms\-Anwendungsprojekt erstellen.|  
|[Schritt 2: Ausführen des Programms](../ide/step-2-run-your-program.md)|Führen Sie das Windows Forms\-Anwendungsprogramm aus, das Sie im vorherigen Schritt erstellt haben.|  
|[Schritt 3: Festlegen der Formulareigenschaften](../ide/step-3-set-your-form-properties.md)|Ändern Sie das Aussehen des Formulars mit dem **Eigenschaftenfenster**.|  
|[Schritt 4: Erstellen des Layouts für das Formular mit einem TableLayoutPanel\-Steuerelement](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Fügen Sie dem Formular ein `TableLayoutPanel`\-Steuerelement hinzu.|  
|[Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md)|Fügen Sie dem Formular Steuerelemente hinzu, z. B. ein `PictureBox`\-Steuerelement und ein `CheckBox`\-Steuerelement.  Fügen Sie dem Formular Schaltflächen hinzu.|  
|[Schritt 6: Benennen der Schaltflächen\-Steuerelemente](../ide/step-6-name-your-button-controls.md)|Benennen Sie die Schaltflächen um, damit die Namen aussagekräftiger sind.|  
|[Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md)|Fügen Sie dem Formular eine **OpenFileDialog**\-Komponente und eine **ColorDialog**\-Komponente hinzu.|  
|[Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche "Bild anzeigen"](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Schreiben Sie Code mit dem IntelliSense\-Tool.|  
|[Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md)|Prüfen und testen Sie den Code.  Fügen Sie bei Bedarf Kommentare hinzu.|  
|[Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Schreiben Sie mithilfe von IntelliSense Code, damit andere Schaltflächen und ein Kontrollkästchen funktionieren.|  
|[Schritt 11: Führen Sie das Programms aus und probieren Sie weitere Funktionen aus](../ide/step-11-run-your-program-and-try-other-features.md)|Führen Sie das Programm aus, und legen Sie die Hintergrundfarbe fest.  Probieren Sie andere Funktionen aus. Ändern Sie z. B. Farben, Schriftarten und Rahmen.|