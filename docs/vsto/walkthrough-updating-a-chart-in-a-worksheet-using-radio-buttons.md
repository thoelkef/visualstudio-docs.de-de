---
title: 'Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern | Microsoft Docs'
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
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74bd005514fa2fe72450a95d84f38dd17a7b639f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Optionsfeldern in einem Microsoft Office Excel-Arbeitsblatt, dem Benutzer eine Möglichkeit, wechseln Sie schnell zwischen den Optionen. Ändern Sie die Optionen in diesem Fall den Stil eines Diagramms.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel der Excel-Steuerelemente unter [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen einer Gruppenstatus von Optionsfeldern in einem Arbeitsblatt.  
  
-   Ändern der Diagrammformatvorlage, wenn eine Option ausgewählt ist.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="adding-a-chart-to-a-worksheet"></a>Hinzufügen eines Diagramms zu einem Arbeitsblatt  
 Sie können ein Excel-Arbeitsmappenprojekt erstellen, die eine vorhandene Arbeitsmappe passt. In dieser exemplarischen Vorgehensweise fügen ein Diagramm mit einer Arbeitsmappe und verwenden Sie diese Arbeitsmappe in einer neuen Excel-Projektmappe. Die Datenquelle in dieser exemplarischen Vorgehensweise wird ein Arbeitsblatt mit dem Namen **Daten für Diagramm**.  
  
#### <a name="to-add-the-data"></a>So fügen Sie die Daten hinzu  
  
1.  Öffnen Sie Microsoft Excel.  
  
2.  Mit der rechten Maustaste die **Sheet3** Registerkarte, und klicken Sie dann auf **umbenennen** im Kontextmenü.  
  
3.  Benennen Sie die Tabelle zu **Daten für Diagramm**.  
  
4.  Fügen Sie die folgenden Daten zu **Daten für Diagramm** mit Zelle A4 wird die obere linke Ecke sowie E8 die untere rechte Ecke.  
  
    ||Q1|Q2|F3|Q4|  
    |-|--------|--------|--------|--------|  
    |West|500|550|550|600|  
    |Osten|600|625|675|700|  
    |Nordamerika|450|470|490|510|  
    |Südafrika|800|750|775|790|  
  
 Als Nächstes fügen Sie ein Diagramm, um das erste Arbeitsblatt zum Anzeigen der Daten.  
  
#### <a name="to-add-a-chart-in-excel"></a>So fügen Sie ein Diagramm in Excel hinzu  
  
1.  Auf der **einfügen** Registerkarte die **Diagramme** zu gruppieren, klicken Sie auf **Spalte**, und klicken Sie dann auf **alle Diagrammtypen**.  
  
2.  In der **Diagramm einfügen** (Dialogfeld), klicken Sie auf **OK**.  
  
3.  Auf der **Entwurf** Registerkarte die **Daten** zu gruppieren, klicken Sie auf **Daten auswählen**.  
  
4.  In der **Auswählen einer Datenquelle** (Dialogfeld), klicken Sie in der **Chartdata Bereich** und deaktivieren Sie die Standardauswahl.  
  
5.  In der **Daten für Diagramm** Blatt, wählen Sie den Block von Zellen, die die Zahlen enthält, die in der oberen linken Ecke bis E8 in der unteren rechten Ecke A4 enthält.  
  
6.  In der **Auswählen einer Datenquelle** (Dialogfeld), klicken Sie auf **OK**.  
  
7.  Positionieren Sie das Diagramm die obere rechte Ecke der Zelle ausgerichtet **E2**.  
  
8.  Speichern Sie die Datei auf Laufwerk C, und nennen Sie sie **ExcelChart.xlsx**.  
  
9. Beenden Sie Excel.  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt basierend auf den **ExcelChart** Arbeitsmappe.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine Excel-Diagramm**. Wählen Sie im Assistenten **vorhandenes Dokument kopieren**.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf die **Durchsuchen** Buttonand, navigieren Sie zu der Arbeitsmappe, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben.  
  
3.  Klicken Sie auf **OK**.  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Diagramm** Projekt **Projektmappen-Explorer**.  
  
## <a name="setting-properties-of-the-chart"></a>Festlegen von Eigenschaften des Diagramms  
 Wenn Sie ein neues Excel-Arbeitsmappenprojekt, das eine vorhandene Arbeitsmappe verwendet erstellen, werden die Hoststeuerelemente für alle benannten Bereichen und Listenobjekten Diagramme in der Arbeitsmappe automatisch erstellt. Sie können den Namen des ändern die <xref:Microsoft.Office.Tools.Excel.Chart> Steuerung mithilfe des der **Eigenschaften** Fenster.  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>So ändern Sie den Namen des Diagrammsteuerelements  
  
1.  Wählen Sie die <xref:Microsoft.Office.Tools.Excel.Chart> steuern, die im Designer, und ändern Sie die folgenden Eigenschaften in der **Eigenschaften** Fenster.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>Hinzufügen von Steuerelementen  
 Dieses Arbeitsblatt verwendet Optionsfelder darin, Benutzern eine Möglichkeit, schnell die Diagrammformatvorlage ändern. Allerdings müssen Optionsfelder exklusiv sein – wenn eine Schaltfläche aktiviert ist, kann keine Schaltfläche "Sonstige" in der Gruppe gleichzeitig ausgewählt werden. Dieses Verhalten wird nicht standardmäßig ausgeführt, wenn Sie verschiedene Optionsfelder zu einem Arbeitsblatt hinzufügen.  
  
 Eine Möglichkeit zum Hinzufügen eines dieses Verhalten ist, um die Optionsfelder auf einem Benutzersteuerelement gruppieren schreiben Sie Code hinter das Benutzersteuerelement, und fügen Sie das Benutzersteuerelement in das Arbeitsblatt.  
  
#### <a name="to-add-a-user-control"></a>So fügen Sie ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie die **meine Excel-Diagramm** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **Benutzersteuerelement**, benennen Sie das Steuerelement **ChartOptions** , und klicken Sie auf **hinzufügen**.  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>So fügen Sie die Optionsfelder auf das Benutzersteuerelement hinzu  
  
1.  Wenn das Benutzersteuerelement nicht im Designer sichtbar ist, doppelklicken Sie auf **ChartOptions** in **Projektmappen-Explorer**.  
  
2.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, ziehen Sie eine **Optionsfeld** -Steuerelement auf das Benutzersteuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**columnChart**|  
    |**Text**|**Säulendiagramm**|  
  
3.  Fügen Sie ein zweites Optionsfeld auf das Benutzersteuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**Text**|**Balkendiagramm**|  
  
4.  Fügen Sie ein drittes Optionsfeld auf das Benutzersteuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**Text**|**Liniendiagramm**|  
  
5.  Fügen Sie auf das Benutzersteuerelement ein viertes Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|**Flächendiagramm**|  
  
 Anschließend schreiben Sie den Code um das Diagramm zu aktualisieren, wenn auf ein Optionsfeld geklickt wird.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Ändern das Diagramm Stil beim ein Optionsfeld ausgewählt ist  
 Jetzt können Sie den Code zum Ändern der Diagrammformatvorlage hinzufügen. Zu diesem Zweck erstellen Sie ein öffentliches Ereignis auf das Benutzersteuerelement, fügen Sie eine Eigenschaft, um den Auswahltyp festzulegen, und erstellen Sie einen Ereignishandler für das `CheckedChanged` -Ereignis der einzelnen Optionsfelder.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>So erstellen Sie ein Ereignis und eine Eigenschaft auf einem Benutzersteuerelement  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Benutzersteuerelement, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Code zu der `ChartOptions` -Klasse zum Erstellen einer `SelectionChanged` Ereignis und die `Selection` Eigenschaft.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Behandelt das CheckedChanged-Ereignis der Optionsfelder  
  
1.  Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `areaBlockChart`-Optionsfelds fest, und erhöhen Sie dann das Ereignis.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `barChart`-Optionsfelds fest.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `columnChart`-Optionsfelds fest.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `lineChart`-Optionsfelds fest.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  In C# müssen Sie Ereignishandler für die Optionsfelder hinzufügen. Sie können den Code dem `ChartOptions`-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`. Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>Hinzufügen des Benutzersteuerelements zum Arbeitsblatt  
 Wenn Sie die Projektmappe zu erstellen, wird das neue Benutzersteuerelement automatisch um hinzugefügt der **Toolbox**. Anschließend können Sie das Steuerelement aus ziehen die **Toolbox** in das Arbeitsblatt.  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>So fügen Sie Ihrem Arbeitsblatt der Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Die **ChartOptions** Benutzersteuerelement wird hinzugefügt, um die **Toolbox**.  
  
2.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Sicht-Designer**.  
  
3.  Ziehen Sie die **ChartOptions** -Steuerelement aus der **Toolbox** in das Arbeitsblatt.  
  
     Ein neues Steuerelement mit dem Namen `my_Excel_Chart_ChartOptions1` wird dem Projekt hinzugefügt.  
  
4.  Ändern Sie den Namen des Steuerelements **ChartOptions1**.  
  
## <a name="changing-the-chart-type"></a>Ändern des Diagrammtyps  
 Um den Diagrammtyp ändern möchten, erstellen Sie einen Ereignishandler, der den Stil entsprechend der im Benutzersteuerelement ausgewählten Option festlegt.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>So ändern Sie den Typ des Diagramms, das im Arbeitsblatt angezeigt wird  
  
1.  Fügen Sie der `Sheet1`-Klasse den folgenden Ereignishandler hinzu.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  In c# müssen Sie einen Ereignishandler für das Benutzersteuerelement zum Hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass das Diagramm ordnungsgemäß formatiert wird, wenn Sie ein Optionsfeld auswählen.  
  
#### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie verschiedene Optionsfelder aus.  
  
3.  Stellen Sie sicher, dass sich die Diagrammformatvorlage ändert, um der Auswahl zu entsprechen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Optionsfeldern und Diagrammformatvorlagen in Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
-   Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Ändern der Formatierung in einem Arbeitsblatt mithilfe der Kontrollkästchen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern von Arbeitsblatt Formatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)  
  
  