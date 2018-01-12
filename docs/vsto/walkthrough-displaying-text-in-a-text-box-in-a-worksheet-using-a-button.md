---
title: "Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche | Microsoft Docs"
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b88940aa1329bc330e5d8bb7d114c21fac3dacb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Microsoft Office Excel-Arbeitsblättern und Excel-Projekten, die mit Office-Entwicklungstools in Visual Studio zu erstellen. Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel der Excel-Steuerelemente unter [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt.  
  
-   Füllen Sie ein Textfeld aus, wenn auf eine Schaltfläche geklickt wird.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt mit Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine Excel-Schaltfläche**. Stellen Sie sicher, dass **erstellen Sie ein neues Dokument** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Schaltfläche** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In dieser exemplarischen Vorgehensweise benötigen Sie eine Schaltfläche und ein Textfeld auf das erste Arbeitsblatt.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>So fügen Sie eine Schaltfläche und ein Textfeld hinzu  
  
1.  Überprüfen Sie, ob die **meine Excel Button.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.  
  
2.  Aus der **Standardsteuerelementen** Registerkarte Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> zu `Sheet1`.  
  
3.  Aus der **Ansicht** klicken Sie im Menü **Fenster "Eigenschaften"**.  
  
4.  Stellen sicher, dass **TextBox1** wird angezeigt, in der **Eigenschaften** Fenster Dropdown-Feld und Ändern der **Namen** Eigenschaft des Textfelds um **DisplayText**.  
  
5.  Ziehen Sie eine **Schaltfläche** -Steuerelement auf `Sheet1` , und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**Text**|**Einfügen von Text**|  
  
 Schreiben Sie jetzt den Code ausführen, wenn die Schaltfläche geklickt wird.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Füllen das Textfeld aus, auf die Schaltfläche geklickt wird  
 Jedes Mal, die der Benutzer klickt auf die Schaltfläche **Hello World!** wird in das Textfeld angefügt.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **"Sheet1"**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Fügen Sie folgenden Code, der <xref:System.Windows.Forms.Control.Click> -Ereignishandler der Schaltfläche:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  In c# müssen Sie einen Ereignishandler hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass die Nachricht **Hello World!** wird im Textfeld angezeigt, wenn Sie die Schaltfläche klicken.  
  
#### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Klicken Sie auf die Schaltfläche.  
  
3.  Überprüfen Sie, ob **Hello World!** wird in das Textfeld angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
-   Verwenden Kontrollkästchen, um die Formatierung zu ändern. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern von Arbeitsblatt Formatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  