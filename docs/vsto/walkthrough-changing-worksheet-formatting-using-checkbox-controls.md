---
title: "Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen | Microsoft Docs"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Kontrollkästchen in einem Microsoft Office Excel-Arbeitsblatt zum Ändern der Formatierung. Sie verwenden Office-Entwicklungstools in Visual Studio erstellen, und fügen Sie dem Projekt Code hinzu. Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel der Excel-Steuerelemente unter [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Text und Steuerelementen zu einem Arbeitsblatt.  
  
-   Formatieren Sie den Text aus, wenn eine Option ausgewählt ist.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt mit Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine Excel-Formatierung**. Stellen Sie sicher, dass **erstellen Sie ein neues Dokument** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Formatierung** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Hinzufügen von Text und Steuerelementen zum Arbeitsblatt  
 In dieser exemplarischen Vorgehensweise benötigen Sie drei <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> Steuerelemente und Text in einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement.  
  
#### <a name="to-add-three-check-boxes"></a>So fügen Sie drei Kontrollkästchen hinzu  
  
1.  Stellen Sie sicher, dass die Arbeitsmappe öffnen, in dem Visual Studio-Designer und die `Sheet1` geöffnet ist.  
  
2.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> Steuerelement in der Nähe von Zelle **B2** in **"Sheet1"**.  
  
3.  Aus der **Ansicht** klicken Sie im Menü **Eigenschaften** Fenster.  
  
4.  Achten Sie darauf, **Checkbox1** sichtbar ist, im Namen-Listenfeld die **Eigenschaften** Fenster, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Fett**|  
  
5.  Ziehen Sie ein zweites Kontrollkästchen auf oder nahe Zelle **B4** , und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Kursiv**|  
  
6.  Ziehen Sie ein drittes Kontrollkästchen auf oder nahe Zelle **B6** , und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**"Unterstreichen"**|  
  
7.  Wählen Sie alle drei Kontrollkästchen-Steuerelemente beim Klicken die STRG-Taste gedrückt.  
  
8.  Klicken Sie in der Gruppe anordnen der Format-Registerkarte in Excel auf **ausrichten**, und klicken Sie dann auf **linksbündig**.  
  
     Die drei Kontrollkästchen-Steuerelemente werden auf der linken Seite, an der Position des ersten Steuerelements ausgerichtet, die Sie ausgewählt haben.  
  
     Ziehen Sie als Nächstes eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelements zum Arbeitsblatt.  
  
    > [!NOTE]  
    >  Sie können auch hinzufügen der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement durch Eingabe **Name TextFont** in der **Namen** Feld.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Hinzufügen von Text zu einem NamedRange-Steuerelement  
  
1.  Aus der **Excel-Steuerelementen** Registerkarte Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **B9**.  
  
2.  Überprüfen Sie, ob **$B$ 9** wird angezeigt, in das Bearbeitungsfeld, und dass die Zelle **B9** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **B9** um es auszuwählen.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Zelle **B9** wird zu einem Bereich mit dem Namen `NamedRange1`.  
  
     Es ist nicht erkennbar, auf dem Arbeitsblatt jedoch `NamedRange1` wird angezeigt, der **Namenfeld** (direkt über dem Arbeitsblatt auf der linken Seite) Wenn Zelle **B9** ausgewählt ist.  
  
5.  Achten Sie darauf, **NamedRange1** sichtbar ist, im Namen-Listenfeld die **Eigenschaften** Fenster, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**Name textFont**|  
    |**Wert2**|**Klicken Sie auf das Kontrollkästchen, um die Formatierung des Texts zu ändern.**|  
  
 Anschließend schreiben Sie den Code, um den Text zu formatieren, wenn eine Option ausgewählt ist.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>Wenn eine Option der Text formatieren ausgewählt ist  
 In diesem Abschnitt werden Sie Code schreiben, sodass, wenn der Benutzer eine Formatierungsoption aus auswählt, die das Format des Texts im Arbeitsblatt geändert wird.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Zum Ändern der Formatierung, wenn Sie das Kontrollkästchen aktiviert ist  
  
1.  Mit der rechten Maustaste **"Sheet1"**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyBoldFont` Kontrollkästchen:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyItalicFont` Kontrollkästchen:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der `applyUnderlineFont` Kontrollkästchen:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  In c# müssen Sie Ereignishandler für die Kontrollkästchen zum Hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass der Text korrekt formatiert ist, wenn Sie aktivieren bzw. Sie das Kontrollkästchen deaktivieren.  
  
#### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen.  
  
3.  Vergewissern Sie sich, dass der Text korrekt formatiert sind.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Kontrollkästchen und Formatieren von Text in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  