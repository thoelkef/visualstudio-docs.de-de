---
title: 'Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f813c2f9affdfa6715655afba5954b664ead74ca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110401"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche
  In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Microsoft Office Excel-Arbeitsblättern, und Erstellen von Excel-Projekten, die mit Office-Entwicklungstools in Visual Studio. Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel des Excel-Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Hinzufügen von Steuerelementen zu einem Arbeitsblatt.

- Füllen Sie das Textfeld aus, wenn auf eine Schaltfläche geklickt wird.

- Testen Sie das Projekt ein.

> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen eines Projekts
 In diesem Schritt erstellen Sie ein Excel-Workbook-Projekt, das mithilfe von Visual Studio.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **Meine Schaltfläche "Excel"**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine Schaltfläche "Excel"** Projekt **Projektmappen-Explorer**.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 In dieser exemplarischen Vorgehensweise benötigen Sie eine Schaltfläche und ein Textfeld auf das erste Arbeitsblatt.

### <a name="to-add-a-button-and-a-text-box"></a>So fügen Sie eine Schaltfläche und ein Textfeld hinzu

1. Überprüfen Sie, ob die **Mein Excel Button.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.

2. Von der **Standardsteuerelementen** Registerkarte der Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> zu `Sheet1`.

3. Von der **Ansicht** , wählen Sie im Menü **Fenster "Eigenschaften"**.

4. Achten Sie darauf, **TextBox1** werden in der **Eigenschaften** Fenster Dropdown-Listenfeld, und Ändern der **Namen** Eigenschaft des Textfelds, das auf **DisplayText**.

5. Ziehen Sie eine **Schaltfläche** -Steuerelement auf `Sheet1` , und ändern Sie die folgenden Eigenschaften:

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Einfügen von Text**|

   Jetzt schreiben Sie Code ausführen, wenn die Schaltfläche geklickt wird.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Füllen Sie im Textfeld aus, wenn die Schaltfläche geklickt wird
 Jedes Mal, die der Benutzer klickt auf die Schaltfläche **Hello World!** in das Textfeld wird angefügt werden.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld

1. In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.

2. Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler der Schaltfläche:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. In c# müssen Sie einen Ereignishandler hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können nun testen, die Arbeitsmappe, um sicherzustellen, dass die Nachricht **Hello World!** wird in das Textfeld angezeigt, wenn Sie die Schaltfläche klicken.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** um Ihr Projekt auszuführen.

2. Klicken Sie auf die Schaltfläche.

3. Überprüfen Sie, ob **Hallo Welt!** wird in das Textfeld angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:

- Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).

- Verwenden Sie die Kontrollkästchen zum Ändern der Formatierung. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Änderung arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)
- [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
