---
title: "Exemplarische Vorgehensweise: Ändern der Dokumentformatierung mit CheckBox-Steuerelementen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b99f1a5d05d1eac173c40e7cc0c3b989f7c0cd3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-changing-document-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der Dokumentformatierung mit CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Windows Forms-Steuerelemente in einer Anpassung auf Dokumentebene für Microsoft Office Word verwenden, um textformatierung zu ändern.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Text und ein Steuerelement auf das Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.  
  
-   Formatieren des Texts an, wenn eine Option ausgewählt ist.  
  
 Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel der Word-Steuerelemente unter [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **My Word Formatting**. Wählen Sie im Assistenten **erstellen Sie ein neues Dokument**.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **My Word Formatting** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-text-and-controls-to-the-word-document"></a>Hinzufügen von Text und Steuerelementen zu Word-Dokument  
 In dieser exemplarischen Vorgehensweise fügen Sie drei Kontrollkästchen und Text in einem <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement zum Word-Dokument. Die Kontrollkästchen werden Optionen zum Formatieren des Texts für den Benutzer anzuzeigen.  
  
#### <a name="to-add-three-check-boxes"></a>So fügen Sie drei Kontrollkästchen hinzu  
  
1.  Stellen Sie sicher, dass das Dokument im Visual Studio-Designer geöffnet ist.  
  
2.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, ziehen Sie das erste <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> -Steuerelement auf das Dokument.  
  
3.  Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Fett**|  
  
4.  Drücken Sie **EINGABETASTE** so verschieben Sie die Einfügemarke unter das erste aktivierte Kontrollkästchen.  
  
5.  Fügen Sie ein zweites Kontrollkästchen auf das Dokument unten die `ApplyBoldFont` Kontrollkästchen, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Kursiv**|  
  
6.  Drücken Sie **EINGABETASTE** so verschieben Sie die Einfügemarke unter das zweite Kontrollkästchen.  
  
7.  Fügen Sie ein drittes Kontrollkästchen auf das Dokument unten die `ApplyItalicFont` Kontrollkästchen, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**"Unterstreichen"**|  
  
#### <a name="to-add-text-and-a-bookmark-control"></a>So fügen Sie Text und Lesezeichen-Steuerelement hinzu  
  
1.  Verschieben der Einfügemarke unter dem Kontrollkästchen-Steuerelemente, und geben Sie den folgenden Text:  
  
     **Klicken Sie auf das Kontrollkästchen, um die Formatierung des Texts zu ändern.**  
  
2.  Aus der **Word-Steuerelemente** auf der Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement auf das Dokument.  
  
     Die **Lesezeichen-Steuerelement hinzufügen** Dialogfeld wird angezeigt.  
  
3.  Wählen Sie den Text, die Sie dem Dokument hinzugefügt, und klicken Sie auf **OK**.  
  
     Ein <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement namens **Bookmark1** den markierten Text im Dokument hinzugefügt wird.  
  
4.  In der **Eigenschaften** Fenster, ändern Sie den Wert von der **(Name)** Eigenschaft **FontText.**  
  
 Anschließend schreiben Sie den Code, um den Text zu formatieren, wenn Sie das Kontrollkästchen aktiviert oder deaktiviert ist.  
  
## <a name="formatting-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatieren den Text bei eines Kontrollkästchens ist aktiviert oder deaktiviert  
 Wenn der Benutzer eine Formatierungsoption aus auswählt, wird ändern Sie das Format des Texts im Dokument.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Zum Ändern der Formatierung, wenn Sie das Kontrollkästchen aktiviert ist  
  
1.  Mit der rechten Maustaste `ThisDocument` in **Projektmappen-Explorer**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Nur für c#, fügen Sie die folgenden Konstanten, mit denen die **ThisDocument** Klasse.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyBoldFont` Kontrollkästchen.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyItalicFont` Kontrollkästchen.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyUnderlineFont` Kontrollkästchen.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  In c# müssen Sie Ereignishandler für die Textfelder hinzufügen der <xref:Microsoft.Office.Tools.Word.Document.Startup> Ereignis. Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Ihr Dokument, um sicherzustellen, dass der Text korrekt formatiert ist, wenn Sie aktivieren bzw. Sie das Kontrollkästchen deaktivieren testen.  
  
#### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen.  
  
3.  Vergewissern Sie sich, dass der Text korrekt formatiert sind.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Kontrollkästchen und textformatierung in Word-Dokumenten programmgesteuert ändern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Verwenden Sie eine Schaltfläche, um ein Textfeld aufzufüllen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Auswählen von Diagrammformaten mithilfe von Optionsfeldern. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsschaltflächen](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
-  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  