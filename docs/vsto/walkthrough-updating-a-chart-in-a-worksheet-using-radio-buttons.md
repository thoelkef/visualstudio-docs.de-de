---
title: 'Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51733e50bc6711630283d8059c7c6cf42e462df7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672375"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern
  In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Optionsfeldern in einem Microsoft Office Excel-Arbeitsblatt, Benutzern eine Möglichkeit, schnell zwischen den Optionen wechseln. Ändern Sie die Optionen in diesem Fall den Stil eines Diagramms.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel des Excel-Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen einer Gruppenstatus von Optionsfeldern in einem Arbeitsblatt.  
  
-   Ändern der Diagrammformatvorlage, wenn eine Option ausgewählt ist.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="add-a-chart-to-a-worksheet"></a>Hinzufügen eines Diagramms zu einem Arbeitsblatt  
 Sie können ein Excel-Workbook-Projekt erstellen, die eine vorhandene Arbeitsmappe anpasst. In dieser exemplarischen Vorgehensweise Sie ein Diagramm mit einer Arbeitsmappe hinzufügen und dann diese Arbeitsmappe in einer neuen Excel-Projektmappe verwendet. Die Datenquelle in dieser exemplarischen Vorgehensweise ist ein Arbeitsblatt mit dem Namen **Daten für Diagramm**.  
  
### <a name="to-add-the-data"></a>Die Daten hinzufügen  
  
1.  Öffnen Sie Microsoft Excel.  
  
2.  Mit der rechten Maustaste die **Sheet3** Registerkarte, und klicken Sie dann auf **umbenennen** im Kontextmenü auf.  
  
3.  Benennen Sie die Tabelle zu **Daten für Diagramm**.  
  
4.  Fügen Sie die folgenden Daten zum **Daten für Diagramm** mit Zelle A4 wird die obere linke Ecke und E8 der unteren rechten Ecke.  
  
    ||Q1|IM 2. QUARTAL|3. QUARTAL|Q4|  
    |-|--------|--------|--------|--------|  
    |West|500|550|550|600|  
    |Osten|600|625|675|700|  
    |Nordamerika|450|470|490|510|  
    |Süd|800|750|775|790|  
  
 Als Nächstes fügen Sie ein Diagramm, um das erste Arbeitsblatt zum Anzeigen der Daten.  
  
### <a name="to-add-a-chart-in-excel"></a>Ein Diagramm in Excel hinzufügen  
  
1.  Auf der **einfügen** Registerkarte die **Diagramme** gruppieren, klicken Sie auf **Spalte**, und klicken Sie dann auf **alle Diagrammtypen**.  
  
2.  In der **Diagramm einfügen** Dialogfeld klicken Sie auf **OK**.  
  
3.  Auf der **Entwurf** Registerkarte die **Daten** auf **Daten auswählen**.  
  
4.  In der **Auswählen einer Datenquelle** (Dialogfeld), klicken Sie in der **Diagrammdaten Bereich** und deaktivieren Sie die Standardauswahl.  
  
5.  In der **Daten für Diagramm** wählen den Block von Zellen, die die Zahlen enthält, der A4 in der oberen linken Ecke bis E8 in der unteren rechten Ecke enthält.  
  
6.  In der **Auswählen einer Datenquelle** Dialogfeld klicken Sie auf **OK**.  
  
7.  Positionieren Sie das Diagramm neu, sodass der oberen rechten Ecke der Zelle mit richtet **E2**.  
  
8.  Speichern Sie die Datei auf Laufwerk C, und nennen Sie sie **ExcelChart.xlsx**.  
  
9. Beenden Sie Excel.  
  
## <a name="create-a-new-project"></a>Erstellt ein neues Projekt  
 In diesem Schritt erstellen Sie eine Excel-Arbeitsmappenprojekt basierend auf den **ExcelChart** Arbeitsmappe.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **Mein Excel-Diagramm**. Wählen Sie im Assistenten **vorhandenes Dokument kopieren**.  
  
     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf die **Durchsuchen** Schaltfläche, und navigieren Sie zu der Arbeitsmappe, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben.  
  
3.  Klicken Sie auf **OK**.  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Mein Excel-Diagramm** Projekt **Projektmappen-Explorer**.  
  
## <a name="set-properties-of-the-chart"></a>Festlegen von Eigenschaften des Diagramms  
 Wenn Sie ein neues Excel-Arbeitsmappenprojekt, das eine vorhandene Arbeitsmappe verwendet erstellen, werden die Host-Steuerelementen für alle benannten Bereichen, Objekte in der Liste und Diagramme in der Arbeitsmappe automatisch erstellt. Sie können den Namen des Ändern der <xref:Microsoft.Office.Tools.Excel.Chart> -Steuerelement unter Verwendung der **Eigenschaften** Fenster.  
  
### <a name="to-change-the-name-of-the-chart-control"></a>So ändern Sie den Namen des Diagrammsteuerelements  
  
1.  Wählen Sie die <xref:Microsoft.Office.Tools.Excel.Chart> steuern im Designer, und ändern Sie die folgenden Eigenschaften in der **Eigenschaften** Fenster.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="add-controls"></a>Hinzufügen von Steuerelementen  
 Dieses Arbeitsblatt verwendet Optionsfelder, um Benutzern eine Möglichkeit, schnell ändern, die Diagrammformatvorlage gewähren. Allerdings Optionsfelder exklusiv sein müssen, wenn eine Schaltfläche aktiviert ist, kann keine andere Schaltfläche in der Gruppe gleichzeitig ausgewählt werden. Dieses Verhalten erfolgt nicht standardmäßig, wenn Sie verschiedene Optionsfelder in einem Arbeitsblatt hinzufügen.  
  
 Eine Möglichkeit zum Hinzufügen, dass dieses Verhalten ist, auf die Gruppe der Optionsfelder auf ein Benutzersteuerelement, Schreiben Sie Ihren Code hinter das Benutzersteuerelement, und fügen Sie dann das Benutzersteuerelement in das Arbeitsblatt.  
  
### <a name="to-add-a-user-control"></a>So fügen Sie ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie die **Mein Excel-Diagramm** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **Benutzersteuerelement**, benennen Sie das Steuerelement **ChartOptions** , und klicken Sie auf **hinzufügen**.  
  
### <a name="to-add-radio-buttons-to-the-user-control"></a>Optionsfelder auf das Benutzersteuerelement hinzufügen  
  
1.  Wenn das Benutzersteuerelement nicht im Designer sichtbar ist, doppelklicken Sie auf **ChartOptions** in **Projektmappen-Explorer**.  
  
2.  Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, ziehen Sie eine **Optionsfeld** steuern, auf das Benutzersteuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**columnChart**|  
    |**Text**|**Säulendiagramm**|  
  
3.  Fügen Sie auf das Benutzersteuerelement ein zweites Optionsfeld aus, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**Text**|**Balkendiagramm**|  
  
4.  Fügen Sie auf das Benutzersteuerelement ein drittes Optionsfeld aus, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**Text**|**Liniendiagramm**|  
  
5.  Fügen Sie auf das Benutzersteuerelement ein viertes Optionsfeld aus, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|**Flächendiagramm**|  
  
 Als Nächstes schreiben Sie den Code, um das Diagramm aktualisiert, wenn auf ein Optionsfeld geklickt wird.  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Ändern der Diagrammformatvorlage, wenn ein Optionsfeld ausgewählt ist  
 Jetzt können Sie den Code zum Ändern der Diagrammformatvorlage hinzufügen. Zu diesem Zweck erstellen Sie ein öffentliches Ereignis für das Benutzersteuerelement, fügen Sie eine Eigenschaft, um den Auswahltyp festzulegen, und erstellen Sie einen Ereignishandler für die `CheckedChanged` -Ereignis der einzelnen Optionsfelder.  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>So erstellen Sie ein Ereignis und eine Eigenschaft auf einem Benutzersteuerelement  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Benutzersteuerelement, und klicken Sie dann auf **Ansichtscode**.  
  
2.  Fügen Sie Code in die `ChartOptions` -Klasse zur Erstellung einer `SelectionChanged` Ereignis und die `Selection` Eigenschaft.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Das CheckedChanged-Ereignis der Optionsfelder behandeln  
  
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
  
5.  In C# müssen Sie Ereignishandler für die Optionsfelder hinzufügen. Sie können den Code dem `ChartOptions`-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`. Weitere Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="add-the-user-control-to-the-worksheet"></a>Fügen Sie das Benutzersteuerelement in das Arbeitsblatt  
 Wenn Sie die Projektmappe erstellen, wird das neue Benutzersteuerelement automatisch um hinzugefügt der **Toolbox**. Sie können dann das Steuerelement ziehen die **Toolbox** in das Arbeitsblatt.  
  
### <a name="to-add-the-user-control-your-worksheet"></a>So fügen Sie das Arbeitsblatt dem Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Die **ChartOptions** Benutzersteuerelement wird hinzugefügt, die **Toolbox**.  
  
2.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Ansicht-Designer**.  
  
3.  Ziehen Sie die **ChartOptions** -Steuerelement aus der **Toolbox** in das Arbeitsblatt.  
  
     Ein neues Steuerelement mit dem Namen `my_Excel_Chart_ChartOptions1` zu Ihrem Projekt hinzugefügt wird.  
  
4.  Ändern Sie den Namen des Steuerelements **ChartOptions1**.  
  
## <a name="change-the-chart-type"></a>Ändern des Diagrammtyps  
 Um den Diagrammtyp ändern zu können, erstellen Sie einen Ereignishandler, der den Stil entsprechend der im Benutzersteuerelement ausgewählten Option festlegt.  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>So ändern Sie den Typ des Diagramms, das im Arbeitsblatt angezeigt wird  
  
1.  Fügen Sie der `Sheet1`-Klasse den folgenden Ereignishandler hinzu.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  In c# müssen Sie einen Ereignishandler für das Benutzersteuerelement zum Hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Weitere Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass das Diagramm ordnungsgemäß formatiert wird, wenn Sie ein Optionsfeld auswählen.  
  
### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie **F5** um Ihr Projekt auszuführen.  
  
2.  Wählen Sie verschiedene Optionsfelder aus.  
  
3.  Stellen Sie sicher, dass sich die Diagrammformatvorlage ändert, um der Auswahl zu entsprechen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Optionsfeldern und Diagrammformatvorlagen in Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
-   Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Ändern Sie die Formatierung in einem Arbeitsblatt mithilfe der Kontrollkästchen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Änderung arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)  
  
  