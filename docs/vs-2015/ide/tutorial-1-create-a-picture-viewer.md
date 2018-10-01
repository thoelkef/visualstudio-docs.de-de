---
title: 'Tutorial 1: Erstellen eines Bildanzeigeprogramms | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1472d682ea6c00807318873a3f738f792875d1bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510077"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Lernprogramm 1: Erstellen eines Bildanzeigeprogramms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Tutorial 1: Erstellen eines Bildanzeigeprogramms](https://docs.microsoft.com/visualstudio/ide/tutorial-1-create-a-picture-viewer).  
  
In diesem Lernprogramm erstellen Sie ein Programm, das ein Bild aus einer Datei lädt und in einem Fenster anzeigt. Sie erfahren, wie Sie Steuerelemente, z. B. Schaltflächen und Bildfelder, auf das Formular ziehen, ihre Eigenschaften festlegen und mithilfe von Containern die Größe des Formulars stufenlos ändern können. Sie fangen auch an, Code zu schreiben. Sie lernen Folgendes:  
  
-   Erstellen Sie ein neues Projekt.  
  
-   Testen (Debuggen) einer Anwendung  
  
-   Hinzufügen grundlegender Steuerelemente, z. B. Kontrollkästchen und Schaltflächen, zu einem Formular  
  
-   Positionieren von Steuerelementen auf einem Formular mithilfe von Layouts  
  
-   Hinzufügen der Dialogfelder **Datei öffnen** und **Farbe** zu einem Formular.  
  
-   Schreiben von Code mithilfe von IntelliSense und Codeausschnitten  
  
-   Schreiben von Ereignishandlermethoden  
  
 Am Ende sieht das Programm so aus wie in der folgenden Abbildung.  
  
 ![Bild, das Sie in diesem Tutorial erstellen](../ide/media/express-pictureviewerdone.png "Express_BildanzeigeprogrammFertig")  
Bild, das Sie in diesem Lernprogramm erstellen  
  
 Informationen zum Herunterladen einer vollständige Version des Beispiels finden Sie unter [Tutorialbeispiel für vollständiges Bildanzeigeprogramm](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![Link zum Video](../data-tools/media/playvideo.gif "Videoabspielen")Eine Videoversion dieses Themas finden Sie unter [How Do I: Create a Picture Viewer in Visual Basic? (Wie erstelle ich eine Bildanzeige in Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=205207) oder [How Do I: Create a Picture Viewer in C#? (Wie erstelle ich eine Bildanzeige in C#)](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise. In diesem Lernprogramm wird sowohl Visual C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.  
>   
>  Um Code für Visual Basic anzuzeigen, wählen Sie die Registerkarte **VB** oben in den Codeblöcken aus. Um Code für Visual C# anzuzeigen, wählen Sie die Registerkarte **C#** aus. Wenn Sie Informationen zu Visual C++ benötigen, finden Sie diese unter [Erste Schritte](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) und im [C++ Sprachtutorial](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Wenn Sie lernen möchten, wie Windows Store-Apps in Visual C# oder Visual Basic geschrieben werden, finden Sie weitere Informationen unter [Erstellen Ihrer ersten Windows Store-App mit C# oder Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Informationen zum Erstellen von Windows Store-Apps in JavaScript finden Sie unter [Erstellen Ihrer ersten Windows Store-App mit JavaScript](http://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Schritt 1: Erstellen eines Windows Forms-Anwendungsprojekts](../ide/step-1-create-a-windows-forms-application-project.md)|Beginnen Sie, indem Sie ein Windows Forms-Anwendungsprojekt erstellen.|  
|[Schritt 2: Ausführen des Programms](../ide/step-2-run-your-program.md)|Führen Sie das Windows Forms-Anwendungsprogramm aus, das Sie im vorherigen Schritt erstellt haben.|  
|[Schritt 3: Festlegen der Formulareigenschaften](../ide/step-3-set-your-form-properties.md)|Ändern Sie das Aussehen des Formulars mit dem **Eigenschaftenfenster**.|  
|[Schritt 4: Erstellen des Layouts für das Formular mit einem TableLayoutPanel-Steuerelement](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Fügen Sie Ihrem Formular ein `TableLayoutPanel`-Steuerelement hinzu.|  
|[Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md)|Fügen Sie dem Formular Steuerelemente hinzu, z.B. ein `PictureBox`-Steuerelement und ein `CheckBox`-Steuerelement. Fügen Sie dem Formular Schaltflächen hinzu.|  
|[Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md)|Benennen Sie die Schaltflächen um, damit die Namen aussagekräftiger sind.|  
|[Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md)|Fügen Sie dem Formular eine **OpenFileDialog**-Komponente und eine **ColorDialog**-Komponente hinzu.|  
|[Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Schreiben Sie Code mit dem IntelliSense-Tool.|  
|[Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md)|Prüfen und testen Sie den Code. Fügen Sie bei Bedarf Kommentare hinzu.|  
|[Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Schreiben Sie mithilfe von IntelliSense Code, damit andere Schaltflächen und ein Kontrollkästchen funktionieren.|  
|[Schritt 11: Ausführen des Programms und Ausprobieren weiterer Funktionen](../ide/step-11-run-your-program-and-try-other-features.md)|Führen Sie das Programm aus, und legen Sie die Hintergrundfarbe fest. Probieren Sie andere Funktionen aus. Ändern Sie z. B. Farben, Schriftarten und Rahmen.|



